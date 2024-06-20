import PyPDF2

# Open the PDF file
file_path = '/mnt/data/Muhammad Subhan Ayub_resume-1.pdf'
pdf_file = open(file_path, 'rb')

# Create a PDF reader object
pdf_reader = PyPDF2.PdfReader(pdf_file)

# Extract text from each page
pdf_text = ''
for page_num in range(len(pdf_reader.pages)):
    page = pdf_reader.pages[page_num]
    pdf_text += page.extract_text()

# Close the PDF file
pdf_file.close()

# Search for relevant information regarding "Giskard Scan method" and LLM vulnerabilities
giskard_scan_info = ''
search_keywords = ["Giskard Scan method", "LLM vulnerabilities", "categories"]
for line in pdf_text.split('\n'):
    if any(keyword in line for keyword in search_keywords):
        giskard_scan_info += line + '\n'

giskard_scan_info.strip()  # Return the extracted information

