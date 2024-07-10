# File-Organization-Script
This Python script is designed to categorize files found in the download folder of your computer. It organizes the files smartly by their type and the date when they are created to keep the working space as clean as possible.

## Features

- **Intelligent File Sorting**: Automatically classifies files into dedicated folders based on their type (e.g., documents, images, videos, archives).
- **Date-Based Subfolders**: Organizes files into subfolders based on their creation date.
- **Customizable Categories**: Easily add or modify file type categories and their corresponding extensions.

## Prerequisites

- Python 3.x
- The `os` and `shutil` libraries (part of the Python Standard Library)

## Installation

Clone this repository to your local machine:

```bash
git clone https://github.com/roninastic/file-organization-script.git
```

## Usage

1. **Specify the Download Folder Path**: Update the `download_folder` variable in the script with the path to your download folder.
2. **Define File Type Categories**: Add or modify file extensions in the `file_types` dictionary to match the types of files you want to categorize.
3. **Run the Script**: Execute the script using Python.

### Example

Here's an example of how to use the script:

```python
# Define the download folder path
download_folder = '/path/to/your/downloads'

# Define the file type categories
file_types = {
    'Documents': ['.pdf', '.docx', '.txt', '.pptx', '.xlsx'],
    'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp'],
    'Videos': ['.mp4', '.avi', '.mov', '.mkv'],
    'Archives': ['.zip', '.rar', '.tar.gz'],
    'Audio': ['.mp3', '.wav', '.aac'],
    'Scripts': ['.py', '.js', '.sh', '.bat']
}
```

Run the script:

```bash
python organize_files.py
```

### Script Overview

```python
import os
import shutil
from datetime import datetime

# Define the download folder path
download_folder = '/path/to/your/downloads'

# Define the file type categories
file_types = {
    'Documents': ['.pdf', '.docx', '.txt', '.pptx', '.xlsx'],
    'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp'],
    'Videos': ['.mp4', '.avi', '.mov', '.mkv'],
    'Archives': ['.zip', '.rar', '.tar.gz'],
    'Audio': ['.mp3', '.wav', '.aac'],
    'Scripts': ['.py', '.js', '.sh', '.bat']
}

def create_folder(folder_path):
    if not os.path.exists(folder_path):
        os.makedirs(folder_path)

def organize_files():
    for filename in os.listdir(download_folder):
        if filename.startswith('.'):
            continue  # Skip hidden files
        file_path = os.path.join(download_folder, filename)
        if os.path.isfile(file_path):
            file_extension = os.path.splitext(filename)[1].lower()
            for category, extensions in file_types.items():
                if file_extension in extensions:
                    category_folder = os.path.join(download_folder, category)
                    create_folder(category_folder)
                    
                    # Sort files into subfolders based on creation date
                    creation_time = os.path.getctime(file_path)
                    date_folder = datetime.fromtimestamp(creation_time).strftime('%Y-%m-%d')
                    date_folder_path = os.path.join(category_folder, date_folder)
                    create_folder(date_folder_path)
                    
                    shutil.move(file_path, os.path.join(date_folder_path, filename))
                    break
            else:
                # If file type doesn't match any category, move to 'Others'
                other_folder = os.path.join(download_folder, 'Others')
                create_folder(other_folder)
                shutil.move(file_path, os.path.join(other_folder, filename))

if __name__ == "__main__":
    organize_files()
```

### How It Works

- **create_folder**: This function checks if a folder exists; if not, it creates it.
- **organize_files**: This function scans through files in the download folder, identifies their type based on extension, and moves them to corresponding category folders. Files are further organized into subfolders by their creation date.
- **File Type Categories**: Customize the categories and their corresponding file extensions in the `file_types` dictionary.
- **Hidden Files**: The script skips hidden files (those starting with a dot).

## Contributing

Contributions are welcome! Please fork this repository and submit a pull request with your improvements.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.

## Contact

If you have any questions or suggestions, feel free to open an issue or contact me at [your-email@example.com].

---

Feel free to customize the README file further to suit your needs before uploading it to GitHub.

## Features

- **Intelligent File Sorting**: Automatically classifies files into dedicated folders based on their type (e.g., documents, images, videos, archives).
- **Date-Based Subfolders**: Organizes files into subfolders based on their creation date.
- **Customizable Categories**: Easily add or modify file type categories and their corresponding extensions.

## Prerequisites

- Python 3.x
- The `os` and `shutil` libraries (part of the Python Standard Library)

## Installation

Clone this repository to your local machine:

```bash
git clone https://github.com/your-username/file-organization-script.git
```

## Usage

1. **Specify the Download Folder Path**: Update the `download_folder` variable in the script with the path to your download folder.
2. **Define File Type Categories**: Add or modify file extensions in the `file_types` dictionary to match the types of files you want to categorize.
3. **Run the Script**: Execute the script using Python.

### Example

Here's an example of how to use the script:

```python
# Define the download folder path
download_folder = '/path/to/your/downloads'

# Define the file type categories
file_types = {
    'Documents': ['.pdf', '.docx', '.txt', '.pptx', '.xlsx'],
    'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp'],
    'Videos': ['.mp4', '.avi', '.mov', '.mkv'],
    'Archives': ['.zip', '.rar', '.tar.gz'],
    'Audio': ['.mp3', '.wav', '.aac'],
    'Scripts': ['.py', '.js', '.sh', '.bat']
}
```

Run the script:

```bash
python organize_files.py
```

### Script Overview

```python
import os
import shutil
from datetime import datetime

# Define the download folder path
download_folder = '/path/to/your/downloads'

# Define the file type categories
file_types = {
    'Documents': ['.pdf', '.docx', '.txt', '.pptx', '.xlsx'],
    'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp'],
    'Videos': ['.mp4', '.avi', '.mov', '.mkv'],
    'Archives': ['.zip', '.rar', '.tar.gz'],
    'Audio': ['.mp3', '.wav', '.aac'],
    'Scripts': ['.py', '.js', '.sh', '.bat']
}

def create_folder(folder_path):
    if not os.path.exists(folder_path):
        os.makedirs(folder_path)

def organize_files():
    for filename in os.listdir(download_folder):
        if filename.startswith('.'):
            continue  # Skip hidden files
        file_path = os.path.join(download_folder, filename)
        if os.path.isfile(file_path):
            file_extension = os.path.splitext(filename)[1].lower()
            for category, extensions in file_types.items():
                if file_extension in extensions:
                    category_folder = os.path.join(download_folder, category)
                    create_folder(category_folder)
                    
                    # Sort files into subfolders based on creation date
                    creation_time = os.path.getctime(file_path)
                    date_folder = datetime.fromtimestamp(creation_time).strftime('%Y-%m-%d')
                    date_folder_path = os.path.join(category_folder, date_folder)
                    create_folder(date_folder_path)
                    
                    shutil.move(file_path, os.path.join(date_folder_path, filename))
                    break
            else:
                # If file type doesn't match any category, move to 'Others'
                other_folder = os.path.join(download_folder, 'Others')
                create_folder(other_folder)
                shutil.move(file_path, os.path.join(other_folder, filename))

if __name__ == "__main__":
    organize_files()
```

### How It Works

- **create_folder**: This function checks if a folder exists; if not, it creates it.
- **organize_files**: This function scans through files in the download folder, identifies their type based on extension, and moves them to corresponding category folders. Files are further organized into subfolders by their creation date.
- **File Type Categories**: Customize the categories and their corresponding file extensions in the `file_types` dictionary.
- **Hidden Files**: The script skips hidden files (those starting with a dot).

## Contributing

Contributions are welcome! Please fork this repository and submit a pull request with your improvements.

## License



## Contact

If you have any questions or suggestions, feel free to open an issue or contact me at [ayushp31ca@example.com]

---

