# JSluice URL and Secrets Processor

This tool recursively processes JavaScript files to extract URLs and secrets using the jsluice command-line utility. It starts with an initial URL, processes all JavaScript files it encounters, and outputs a comprehensive list of unique URLs and any secrets found.

## Features

- Recursively processes JavaScript files
- Extracts URLs from various JavaScript contexts
- Detects secrets (API keys, tokens, etc.) in JavaScript files
- Resolves relative URLs to absolute URLs
- Outputs unique URLs and secrets in an organized format

## Prerequisites

- Python 3.6+
- jsluice command-line tool
- curl

## Installation

1. Ensure you have Python 3.6+ installed on your system.
2. Install the jsluice command-line tool. (Refer to the jsluice documentation for installation instructions)
3. Clone this repository or download the `process_jsluice_recursive.py` script.
4. Make the script executable:

   ```bash
   chmod +x process_jsluice_recursive.py
   ```

## Usage

You can use the script in two ways:

1. Process a single URL:

   ```bash
   echo "https://example.com/script.js" | ./process_jsluice_recursive.py
   ```

2. Process multiple URLs from a file:

   ```bash
   cat js_urls.txt | ./process_jsluice_recursive.py
   ```

## Output

The script outputs two main sections:

1. **URLs**: A sorted list of unique URLs found in the processed JavaScript files.
2. **Secrets**: Any secrets (like API keys or tokens) discovered in the JavaScript files.

Example output:

```
URLs:
https://api.example.com/v1/users
https://cdn.example.com/assets/main.css
https://example.com/about
...

Secrets:
{"kind": "AWSAccessKey", "data": {"key": "AKIAIOSFODNN7EXAMPLE", "secret": "wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY"}, "filename": "https://example.com/config.js", "severity": "high", "context": {"awsRegion": "us-west-2", "bucketName": "example-uploads"}}
...
```

## Customization

You can modify the script to adjust its behavior:

- Change the `is_js_file()` function to include or exclude certain file types.
- Modify the `process_jsluice_output()` function to handle additional types of data or to change how URLs and secrets are processed.

## Notes

- This script relies on the jsluice tool for actual URL and secret extraction. Make sure jsluice is properly installed and accessible in your system's PATH.
- The script uses curl to fetch content from URLs. Ensure you have the necessary permissions and network access to fetch the content.
- Be cautious when processing JavaScript from untrusted sources.

## Troubleshooting

If you encounter any issues:

1. Ensure jsluice is correctly installed and accessible from the command line.
2. Check that you have permission to execute curl and access the URLs you're trying to process.
3. Verify that the input URLs are correctly formatted.

## Contributing

Contributions to improve the script are welcome. Please submit a pull request or open an issue to discuss proposed changes.

## License

[Specify the license under which you're releasing this script]

## Disclaimer

This tool is for educational and ethical testing purposes only. Always ensure you have permission to scan and analyze websites or JavaScript files that you do not own or have explicit permission to test.
