# JSON Array Viewer

A simple, single-file web application for viewing and exploring JSON data in a tabular format. Load JSON from a URL, file, or clipboard, and view arrays as sortable, filterable tables.

## Features

- **Multiple Data Sources**
  - Load JSON from any URL
  - Upload local JSON files
  - Paste JSON from clipboard

- **Smart Array Detection**
  - Automatically finds all arrays in nested JSON structures
  - Detects and unwraps single-property wrapper objects
  - Shows array path and row count for selection

- **Interactive Table View**
  - Sort columns by clicking headers (ascending/descending)
  - Filter by column values (for columns with ≤50 unique values)
  - Global search across all fields
  - Shows filtered vs. total row counts

- **Simple & Portable**
  - Single HTML file - no build process or dependencies
  - Works entirely in the browser
  - No server required

## Usage

### Option 1: Use Online

Visit the hosted version at: `https://skierpage.github.io/json_array_table_viewer/json_array_table_viewer.html`

*(You'll need to enable GitHub Pages in your repository settings for this to work)*

### Option 2: Use Locally

1. Download `json_array_table_viewer.html`
2. Open it in any modern web browser
3. Load your JSON data

### Loading Data

**From URL:**
- Enter a URL in the input field and click "Load"
- Note: Some URLs may be blocked by CORS policies. If so, open the URL in a new tab, copy the JSON, and use the clipboard option instead.

**From File:**
- Click "Upload JSON File" and select a local `.json` file

**From Clipboard:**
- Copy JSON to your clipboard
- Click "Paste JSON from Clipboard"
- If a "Paste" tooltip appears (browser security), click it to grant permission

### Viewing Data

- If the JSON contains multiple arrays, you'll see a selection screen showing each array's path and row count
- Click an array to view it as a table
- Use column headers to sort data
- Use dropdown filters (shown for columns with ≤50 unique values) to filter rows
- Use the search box to filter across all fields

## Example JSON Structures

The viewer handles various JSON structures:

**Simple array:**
```json
[
  { "name": "Alice", "age": 30 },
  { "name": "Bob", "age": 25 }
]
```

**Nested structure:**
```json
{
  "status": "success",
  "data": {
    "users": [
      { "name": "Alice", "age": 30 },
      { "name": "Bob", "age": 25 }
    ]
  }
}
```

**Wrapped arrays** (automatically unwrapped):
```json
{
  "Vehicles": [
    { "Veh": { "vin": "123", "model": "GV60" } },
    { "Veh": { "vin": "456", "model": "GV70" } }
  ]
}
```
The viewer detects the wrapper pattern and displays the inner data directly.

## Technical Details

- Built with React 18 (via CDN)
- Styled with Tailwind CSS (via CDN)
- JSX transformed in-browser with Babel Standalone
- No external dependencies to install

## Browser Support

Works in all modern browsers that support:
- ES6+ JavaScript
- Clipboard API
- Fetch API

Tested in Firefox and Chrome.

## CORS Limitations

When loading from URLs, some APIs may block requests due to CORS (Cross-Origin Resource Sharing) policies. If you encounter a CORS error:

1. Right-click the URL link and "Copy Link"
2. Open the URL in a new browser tab
3. Copy the JSON response
4. Return to the viewer and use "Paste JSON from Clipboard"

## License

MIT License - feel free to use, modify, and distribute.

## Contributing

Issues and pull requests welcome at https://github.com/skierpage/json_array_table_viewer
