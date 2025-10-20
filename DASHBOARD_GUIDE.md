# Invoice Transaction Dashboard - User Guide

## Overview
A standalone HTML dashboard for analyzing invoice transactions between customer entities and trading partners across different countries.

## Quick Start

1. **Open the Dashboard**
   - Double-click `invoice-dashboard.html` to open it in your web browser
   - No installation or server required - works completely offline

2. **Upload Data Files**
   - **Required:** Transaction Report.xlsx
   - **Optional:** Customer Legal Entity.xlsx (for customer name lookups)
   - **Optional:** Trading Partner Legal Entity.xlsx (for partner name lookups)
   - **Optional:** config.json (to customize analysis parameters)
   - If lookup files are not provided, the system will use IDs as display names
   - Each file input will turn green when successfully loaded

3. **Generate Dashboard**
   - Once the Transaction Report is uploaded, click "Generate Dashboard"
   - The system will process the data and display the analytics
   - Configuration can also be adjusted later via the Settings button

## Dashboard Features

### Executive Summary Tab
- **Key Statistics**: Total invoices, customers, partners, and countries
- **Intelligence Insights**: Automatically generated insights about trends and patterns
- **Monthly Trend Chart**: Visual representation of invoice volume over time
- **Month-over-Month Table**: Detailed breakdown with growth percentages

### Customer Entities Tab
- **Filter by Customer**: Dropdown to focus on specific customer entities
- **Customer Cards**: Each customer shows:
  - Total invoice count
  - Number of trading partners
  - Geographic reach
  - Monthly volume chart
  - Top trading partners with percentage breakdown

### File Size Tab
- **Automatic Column Detection**: Analyzes any columns containing "File size"
- **Summary Statistics**: Total, average, median, min, max for each file size column
- **File Size by Customer**: Total and average file sizes per customer entity
- **File Size by Trading Partner**: Top 15 partners by file size
- **Monthly Trends**: Track file size changes over time
- **Top Transactions**: List of 20 largest transactions by file size
- **Interactive Charts**:
  - Horizontal bar charts for customer and partner comparisons
  - Line chart showing file size trends over time
  - All sizes displayed in both KB and MB

### Countries Tab
- **Geographic Analysis**:
  - Sender and receiver country distributions
  - Route analysis (Country A → Country B)
  - Top 10 routes with volume and percentages
- **Interactive Charts**:
  - Horizontal bar chart for top routes
  - Pie charts for sender/receiver country distributions

## Configuration

### Analysis Parameters
The dashboard supports customizable analysis parameters that can be configured in two ways:

1. **Upload config.json** - Upload a configuration file when loading data
2. **Settings Button** - Click the Settings button in the dashboard header to adjust parameters

### Available Parameters

**config.json structure:**
```json
{
  "trendThresholdPercent": 20,
  "trendComparisonMonths": 3,
  "anomalyDetectionSigma": 2,
  "forecastHorizonMonths": 3
}
```

**Parameter Descriptions:**
- **trendThresholdPercent** (default: 20)
  - Percentage change required to flag partners/customers as growing or declining
  - Example: 20 means ±20% change is significant

- **trendComparisonMonths** (default: 3)
  - Number of months to compare for trend analysis
  - Compares recent N months vs previous N months
  - Example: 3 means compare last 3 months to previous 3 months

- **anomalyDetectionSigma** (default: 2)
  - Standard deviation threshold for flagging anomalies
  - Higher values = fewer anomalies detected (stricter)
  - Example: 2 means flag values beyond 2σ from mean

- **forecastHorizonMonths** (default: 3)
  - How many months ahead to forecast
  - Uses linear regression on historical data
  - Example: 3 means predict next 3 months

### Adjusting Configuration
- Upload config.json at startup for initial settings
- Click **Settings** button in dashboard to modify anytime
- Click **Apply Configuration** to recalculate analysis with new parameters
- Changes apply immediately to the Analysis tab with visual confirmation

### Saving Configurations
The **Download Config** button in the Settings modal allows you to save your current configuration:

1. Click **Settings** button in dashboard header
2. Adjust parameters as desired
3. Click **Download Config** button
4. Enter a custom filename (e.g., `config-customer-acme.json`)
5. Configuration file downloads to your computer

**Use Cases:**
- Create customer-specific configurations: `config-customer-acme.json`, `config-customer-globex.json`
- Create scenario-based configs: `config-strict-anomalies.json`, `config-6month-trends.json`
- Share standardized settings across team members
- Maintain different analysis profiles for different reporting needs

**Example Workflow:**
1. Adjust trend threshold to 15% for sensitive customer
2. Download as `config-customer-sensitive.json`
3. Later, upload this config when analyzing that customer's data
4. Consistent analysis parameters every time

## Key Features

### Interactivity
- Filter data by customer entity
- Hover over charts for detailed tooltips
- Sort tables by clicking column headers
- Drill down into specific months or routes
- Configure analysis parameters to match your needs

### Intelligence Features
- Automatic trend detection (configurable growth/decline thresholds)
- Top performer identification
- Average size calculations
- Geographic pattern recognition
- Month-over-month comparisons
- Statistical anomaly detection
- Predictive forecasting

### Save & Share
- Click "Save Report" to download a complete HTML file
- The saved file includes all data and visualizations
- Can be emailed and opened by anyone with a web browser
- No internet connection required to view saved reports
- Configuration settings are preserved in saved reports

## Technical Details

### Data Processing
- Customer names are looked up from "Customer Legal Entity.xlsx" using "Sender Unique ID"
- Trading partner names are looked up from "Trading Partner Legal Entity.xlsx" using "Receiver Unique ID"
- Invoice dates are parsed and grouped by month
- All processing happens client-side in the browser

### Technologies Used
- SheetJS (xlsx.js) for Excel file reading
- Chart.js for interactive visualizations
- Bootstrap 5 for responsive design
- Pure JavaScript (no backend required)

### Browser Compatibility
- Chrome/Edge (recommended)
- Firefox
- Safari
- Modern browsers with JavaScript enabled

## Data Structure Requirements

### Transaction Report.xlsx (Required)
Required columns:
- Sender Unique ID
- Receiver Unique ID
- Transaction Start Time
- Sender Country Code
- Receiver country Code
- Total File Size(kb)
- Status
- Other columns will be preserved but not analyzed

### Customer Legal Entity.xlsx (Optional)
If provided, required columns:
- Legal ID (VAT Number)
- Bunge Entity name

Note: If not provided, Sender Unique ID will be displayed as customer names

### Trading Partner Legal Entity.xlsx (Optional)
If provided, required columns:
- Legal ID (VAT Number)
- Legal Entity Name

Note: If not provided, Receiver Unique ID will be displayed as partner names

## Troubleshooting

**Files not loading?**
- Ensure files are .xlsx or .xls format
- Check that column names match the expected structure
- Try re-uploading the files

**Dashboard not generating?**
- Verify all three files are uploaded (all inputs should be green)
- Check browser console for errors (F12)
- Ensure JavaScript is enabled in your browser

**Charts not displaying?**
- Some browsers block Chart.js when running from file://
- Try opening in a different browser
- Ensure internet connection for initial load (CDN resources)

**Save function not working?**
- Modern browsers should support download
- Check download folder for the saved file
- Try a different browser if issues persist

## Tips for Best Results

1. **Regular Updates**: Upload fresh data monthly to track trends
2. **Share Insights**: Save and distribute reports to stakeholders
3. **Filter Strategically**: Use customer filter to focus on specific entities
4. **Monitor Trends**: Watch the intelligence insights for actionable information
5. **Cross-Reference**: Compare Executive Summary with detailed tabs for comprehensive view

## Support

For issues or questions about the dashboard:
1. Check this guide first
2. Verify data file formats match requirements
3. Try in a different browser
4. Review browser console for technical errors

---

**Generated**: 2025-10-20
**Version**: 1.0
