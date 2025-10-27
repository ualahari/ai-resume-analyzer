Here is a complete README.md file for your project, formatted in Markdown.

AI-Powered Resume Ranker 🤖
This project is a web application that helps recruiters and hiring managers automatically rank candidate resumes against a job description.

It uses NLP (TF-IDF and Cosine Similarity) to analyze and score multiple PDF resumes, saving hours of manual screening time. The results are displayed in a clean, ranked table with a percentage match score, and can be exported as a CSV file.

Screenshot
Features
Batch Resume Upload: Upload multiple PDF resumes at once.

Job Description Input: A large text area to paste the full job description.

NLP-Based Scoring: Uses TF-IDF (Term Frequency-Inverse Document Frequency) and Cosine Similarity to calculate a relevance score for each resume.

Ranked Results: Displays a clean table of all resumes, ranked from highest (best match) to lowest score.

Percentage Match: Shows the score as an easy-to-understand percentage (e.g., "87.52%").

CSV Export: Download the final ranking as a resume_ranking.csv file for your records.

Technology Stack
Backend: Flask (A lightweight Python web framework)

NLP / Scoring: scikit-learn (for TF-IDF & Cosine Similarity), SpaCy (for text preprocessing like lemmatization and stop-word removal)

PDF Extraction: pdfplumber

Data Handling: pandas

Web Tunneling: pyngrok (To expose the local Flask app to the internet, perfect for Google Colab)

Frontend: Simple HTML & CSS

How to Run (Google Colab)
This app is designed to be run easily within a Google Colab notebook.

Open in Colab: Open a new Google Colab notebook and paste the entire app.py script into a single cell.

Get ngrok Token:

Go to https.dashboard.ngrok.com and sign up for a free account.

Copy your Auth Token.

Set Token in Code:

Find this line in STEP 6 of the code:

Python

NGROK_AUTH_TOKEN = "YOUR_NGROK_AUTH_TOKEN_HERE"
Replace "YOUR_NGROK_AUTH_TOKEN_HERE" with your actual token.

Run the Cell:

Run the entire Colab cell. It will install all dependencies, download the SpaCy model, and start the Flask server.

Access the App:

At the bottom of the output, you will see a public URL printed, like this:

🎉 Your Flask app is live! Open this URL in your browser:
https://peritrichate-unfabling-addie.ngrok-free.dev/

Click this URL to open the app in your browser.

How to Use the App
Paste Job Description: Copy the full job description from your posting and paste it into the "Job Description" text box.

Upload Resumes: Click the "Choose Files" button and select all the candidate PDF resumes you want to rank.

Rank: Click the "Rank Resumes" button.

View Results: The page will reload, showing a table with the resumes ranked by their "Score (Percentage)".

Download (Optional): Click the "Download Ranking as CSV" link to save the results.

How It Works (The Core Logic)
PDF Extraction: The extract_text_from_pdf function uses pdfplumber to read all text from each uploaded PDF.

NLP Preprocessing: The preprocess_text function uses spacy to clean both the job description and the resume text. This involves:

Converting all text to lowercase.

Lemmatization: Reducing words to their root form (e.g., "running" -> "run").

Removing stop words (e.g., "the", "a", "is") and non-alphabetic tokens.

Vectorization (TF-IDF): The rank_resumes function converts the cleaned text into numerical vectors using TfidfVectorizer. This process gives higher weight to words that are important to the job description but less common across all the resumes.

Scoring (Cosine Similarity): It then calculates the cosine similarity between the job description's vector and each resume's vector. This produces a score from 0.0 (no match) to 1.0 (perfect match).

Ranking: The scores are converted to percentages (e.g., 0.8752 -> 87.52%) and sorted to produce the final ranked list.
