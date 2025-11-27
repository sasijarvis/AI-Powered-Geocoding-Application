# 🗺️ AI-Powered Geocoding Application

A modern, interactive web application that combines geocoding services with AI-powered location insights. Search for any location worldwide, get coordinates, reverse geocode addresses, and learn interesting facts about places through an integrated AI assistant.

![Version](https://img.shields.io/badge/version-1.0.0-green.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

## 📋 Table of Contents

- [Features](#features)
- [Demo](#demo)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage Guide](#usage-guide)
- [API Integration](#api-integration)
- [Architecture](#architecture)
- [Technologies Used](#technologies-used)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

### Core Functionality

- **Forward Geocoding**: Search for any location by name or address and get precise coordinates
- **Reverse Geocoding**: Enter coordinates to find the corresponding address
- **Interactive Map**: Visual representation using Leaflet.js and OpenStreetMap
- **Multiple Results**: Display and compare multiple location matches
- **Real-time Search**: Instant results with loading indicators

### AI Integration

- **Smart Assistant**: AI-powered chatbot for natural language location queries
- **Auto-Information**: Automatically provides interesting facts about searched locations
- **Conversational Interface**: Ask questions in plain English
- **Context Awareness**: Maintains conversation history for follow-up questions
- **Location Insights**: Historical information, cultural significance, and tourist attractions

### User Experience

- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices
- **Persistent Settings**: API keys and preferences saved in browser localStorage
- **Error Handling**: Clear error messages and validation
- **Loading States**: Visual feedback during API calls

## 🎯 Demo

### Search Location
```
Input: "Eiffel Tower"
Output: 
- Map shows location in Paris
- Coordinates: 48.8584, 2.2945
- AI provides: "The Eiffel Tower is one of the most iconic landmarks..."
```

### Reverse Geocode
```
Input: Lat: 40.7128, Lon: -74.0060
Output:
- Address: New York, NY, USA
- Map zooms to location
- AI explains: "This is Manhattan, the heart of New York City..."
```

### AI Conversation
```
You: "Find the Taj Mahal"
AI: "I'll search for the Taj Mahal for you!"
[Automatically searches and displays on map]
AI: "The Taj Mahal is a UNESCO World Heritage Site built in 1653..."
```

## 🔧 Prerequisites

Before you begin, ensure you have the following:

### Required
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection

### Optional (for full functionality)
- **Geocode.maps.co API Key**: For enhanced geocoding features
  - Sign up at: https://geocode.maps.co/
  - Free tier available with rate limits
  
- **Azure OpenAI API Key**: For AI chat functionality
  - Azure subscription required
  - OpenAI service deployed in Azure
  - GPT-4o-mini or compatible model

## 📦 Installation

### Option 1: Direct Download

1. Download the `geocoding-app.html` file
2. Open it in any modern web browser
3. That's it! No build process required.

### Option 2: Web Server (Recommended for Production)

```bash
# Using Python
python -m http.server 8000

# Using Node.js (http-server)
npx http-server

# Using PHP
php -S localhost:8000
```

Then navigate to: `http://localhost:8000/geocoding-app.html`

### Option 3: Deploy to Web

Upload the HTML file to any web hosting service:
- GitHub Pages
- Netlify
- Vercel
- AWS S3
- Azure Static Web Apps

## ⚙️ Configuration

### 1. Geocoding API Setup

#### Get API Key (Optional but Recommended)
1. Visit [geocode.maps.co](https://geocode.maps.co/)
2. Sign up for a free account
3. Copy your API key from the dashboard

#### Configure in Application
1. Open the application
2. Find the "API Key" field at the top
3. Paste your geocode.maps.co API key
4. Status will change to "Active" (green)

**Note**: The application works without an API key but has rate limits.

### 2. Azure OpenAI Setup

#### Prerequisites
1. Azure subscription
2. Azure OpenAI service deployed
3. GPT-4o-mini (or compatible) model deployment

#### Get Your Credentials
1. Go to Azure Portal
2. Navigate to your OpenAI resource
3. Go to "Keys and Endpoint"
4. Copy:
   - API Key (KEY 1 or KEY 2)
   - Deployment Name (usually "gpt-4o-mini")

#### Configure in Application
1. Click the chat button (💬) in the bottom-right
2. Enter your Azure OpenAI API Key
3. Enter your deployment name (default: gpt-4o-mini)
4. Credentials are saved automatically

### 3. Customization Options

#### Modify Base Endpoint
If your Azure OpenAI endpoint is different, update line in the code:
```javascript
const AZURE_BASE_URL = 'https://your-service.openai.azure.com';
```

#### Change Brand Colors
Update CSS variables at the top of the `<style>` section:
```css
/* Primary: #018e47 */
/* Secondary: #5ab355 */
```

## 📖 Usage Guide

### Basic Location Search

1. **Find a Place by Name**
   - Type location name in "Search Location" field
   - Examples: "Statue of Liberty", "Tokyo Tower", "Big Ben London"
   - Click "Search Location" or press Enter
   - Results appear on map and in results panel
   - Click any result to zoom to that location

2. **Reverse Geocode Coordinates**
   - Enter latitude in "Latitude" field
   - Enter longitude in "Longitude" field
   - Click "Get Address"
   - Address appears in results panel
   - Map shows marker at coordinates

### Using the AI Assistant

1. **Open Chat**
   - Click the 💬 button in bottom-right corner
   - Chat panel slides open

2. **Natural Language Queries**
   ```
   "Find the Colosseum"
   "What's at coordinates 51.5074, -0.1278?"
   "Show me the Golden Gate Bridge"
   "Where is the Great Wall of China?"
   ```

3. **Get Location Information**
   - Search for any location using the main interface
   - Chat automatically asks AI about the location
   - AI provides historical facts, significance, and details

4. **Ask Follow-up Questions**
   ```
   "What else is nearby?"
   "When was it built?"
   "What's the best time to visit?"
   "Tell me more about its history"
   ```

### Advanced Features

#### Multiple Results
- When searching returns multiple matches
- All results shown on map with markers
- Click result cards to focus on specific location
- Click markers to see popup information

#### Map Interaction
- **Zoom**: Mouse wheel or +/- buttons
- **Pan**: Click and drag
- **Markers**: Click for location details
- **Auto-zoom**: Automatically fits results in view

#### Coordinate Formats
Supported latitude/longitude formats:
- Decimal: `40.7128, -74.0060`
- Positive/Negative: `48.8584, 2.2945`
- Range: Lat (-90 to 90), Lon (-180 to 180)

## 🔌 API Integration

### Geocode.maps.co API

**Endpoints Used**:

1. **Forward Geocoding**
   ```
   GET https://geocode.maps.co/search?q={query}&api_key={key}
   ```
   - Parameters: 
     - `q`: Location query string
     - `api_key`: Your API key (optional)

2. **Reverse Geocoding**
   ```
   GET https://geocode.maps.co/reverse?lat={lat}&lon={lon}&api_key={key}
   ```
   - Parameters:
     - `lat`: Latitude (-90 to 90)
     - `lon`: Longitude (-180 to 180)
     - `api_key`: Your API key (optional)

**Rate Limits**:
- Without API key: 1 request per second
- With free API key: Higher limits (check provider)
- Paid plans: Custom limits

### Azure OpenAI API

**Endpoint Format**:
```
POST https://{resource}.openai.azure.com/openai/deployments/{deployment}/chat/completions?api-version={version}
```

**Request Headers**:
```json
{
  "Content-Type": "application/json",
  "api-key": "your-api-key"
}
```

**Request Body**:
```json
{
  "messages": [
    {"role": "system", "content": "System prompt"},
    {"role": "user", "content": "User message"}
  ],
  "max_tokens": 500,
  "temperature": 0.7
}
```

**Response Format**:
```json
{
  "choices": [
    {
      "message": {
        "role": "assistant",
        "content": "AI response"
      }
    }
  ]
}
```

## 🏗️ Architecture

### Application Structure

```
geocoding-app.html
├── HTML Structure
│   ├── Header (API key inputs)
│   ├── Search Cards (Forward/Reverse)
│   ├── Results Panel
│   ├── Map Container
│   └── Chat Panel
├── CSS Styling
│   ├── Responsive Grid Layout
│   ├── Brand Colors
│   ├── Animations
│   └── Mobile Adaptations
└── JavaScript Logic
    ├── Geocoding Functions
    ├── Map Initialization
    ├── AI Chat Integration
    └── Event Handlers
```

### Data Flow

```
User Input
    ↓
Search/Reverse Geocode Function
    ↓
API Call (geocode.maps.co)
    ↓
Process Response
    ↓
Update Map & Results
    ↓
Send to AI Chat (if open)
    ↓
AI Analysis (Azure OpenAI)
    ↓
Display Insights
```

### State Management

- **localStorage**: API keys, deployment names
- **JavaScript Variables**: 
  - `conversationHistory`: Chat message history
  - `markers`: Map marker references
  - `chatHistory`: AI conversation context

## 🛠️ Technologies Used

### Frontend
- **HTML5**: Semantic markup
- **CSS3**: Modern styling with gradients, animations
- **Vanilla JavaScript**: No framework dependencies

### Libraries
- **Leaflet.js** (v1.9.4): Interactive map library
- **OpenStreetMap**: Free map tiles

### APIs
- **geocode.maps.co**: Geocoding service
- **Azure OpenAI**: AI chat functionality

### Browser APIs
- **Fetch API**: HTTP requests
- **localStorage**: Persistent storage
- **Geolocation API**: (Future enhancement)

## 🐛 Troubleshooting

### Common Issues

#### 1. "API Error: 401" or "Access Denied"

**Problem**: Invalid API key

**Solutions**:
- Verify API key is correct
- Check for extra spaces in key
- Ensure key is active in provider dashboard
- For Azure: Check key hasn't expired

#### 2. "No results found"

**Problem**: Location not recognized

**Solutions**:
- Try more specific search terms
  - Instead of "Tower", try "Eiffel Tower Paris"
- Check spelling
- Try alternative names
- Use coordinates if address search fails

#### 3. Map not loading

**Problem**: Network or CDN issue

**Solutions**:
- Check internet connection
- Verify Leaflet.js CDN is accessible
- Clear browser cache
- Try different browser

#### 4. Chat not responding

**Problem**: Azure OpenAI configuration issue

**Solutions**:
- Verify Azure API key is entered
- Check deployment name matches Azure portal
- Ensure Azure subscription is active
- Check Azure service region/endpoint
- Verify model deployment is active

#### 5. Rate limit errors

**Problem**: Too many requests

**Solutions**:
- Add API key for higher limits
- Wait before retry
- Reduce request frequency
- Consider paid API plan

### Debug Mode

Open browser console (F12) to see:
- API request URLs
- Response data
- Error messages
- Network activity

## ❓ FAQ

### General Questions

**Q: Is this application free to use?**
A: Yes, the application is free. API costs depend on your usage:
- geocode.maps.co: Free tier available
- Azure OpenAI: Pay-as-you-go pricing

**Q: Does it work offline?**
A: No, requires internet for API calls and map tiles.

**Q: Can I use it commercially?**
A: Yes, but check API provider terms of service.

**Q: What browsers are supported?**
A: All modern browsers: Chrome, Firefox, Safari, Edge (last 2 versions)

### API Questions

**Q: Do I need API keys?**
A: Not required but recommended:
- Works without keys (limited)
- Better with keys (higher limits)

**Q: Where do I get API keys?**
A: 
- Geocoding: https://geocode.maps.co/
- Azure OpenAI: https://portal.azure.com/

**Q: Are my API keys secure?**
A: Keys are stored in browser localStorage only. For production, implement backend proxy.

**Q: Can I use different AI models?**
A: Yes, update deployment name to use other Azure OpenAI models.

### Feature Questions

**Q: Can I search multiple locations at once?**
A: No, but search returns multiple matches when available.

**Q: Can I save my searches?**
A: Not currently, but can be added as future enhancement.

**Q: Does it support other languages?**
A: AI responses depend on model. Geocoding supports international addresses.

**Q: Can I export location data?**
A: Not built-in, but coordinates visible in results (can be copied).

## 🤝 Contributing

### How to Contribute

1. **Report Bugs**
   - Open an issue with detailed description
   - Include browser version and steps to reproduce
   - Add screenshots if applicable

2. **Suggest Features**
   - Open an issue with [Feature Request] tag
   - Describe use case and expected behavior
   - Explain why it would be valuable

3. **Submit Code**
   - Fork the repository
   - Create feature branch
   - Make changes with clear comments
   - Test thoroughly
   - Submit pull request with description

### Development Guidelines

- Follow existing code style
- Add comments for complex logic
- Test on multiple browsers
- Update documentation
- Keep dependencies minimal

## 📄 License

MIT License

Copyright (c) 2025 Sasikumar 

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## 📞 Support

### Getting Help

- **Documentation**: Read this README thoroughly
- **Issues**: Check existing issues on repository
- **Email**: sasijarvis@gmail.com.com

### Resources

- [Geocode.maps.co Documentation](https://geocode.maps.co/documentation)
- [Azure OpenAI Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/)
- [Leaflet.js Documentation](https://leafletjs.com/reference.html)
- [OpenStreetMap Wiki](https://wiki.openstreetmap.org/)

## 🔄 Version History

### v1.0.0 (Current)
- Initial release
- Forward and reverse geocoding
- Interactive map with markers
- AI chat integration
- Auto-information feature
- Responsive design
- API key management
- localStorage persistence

### Planned Features
- [ ] Batch geocoding
- [ ] Export results to CSV/JSON
- [ ] Save favorite locations
- [ ] Offline map tiles
- [ ] Multiple language support
- [ ] Dark mode
- [ ] Advanced filters
- [ ] Route planning
- [ ] Distance calculator
- [ ] Location sharing

## 🙏 Acknowledgments

- **Geocode.maps.co** for geocoding API
- **Microsoft Azure** for AI services
- **Leaflet.js** for mapping library
- **OpenStreetMap** for map data

## 📊 Stats

- **Lines of Code**: ~700
- **Dependencies**: 2 (Leaflet.js, external APIs)
- **File Size**: ~35KB (uncompressed)
- **Load Time**: <2s (typical connection)
- **Supported Browsers**: 5+
- **API Integrations**: 2

---

**Built with ❤️**

For questions, issues, or contributions, please visit our repository or contact support.

Last Updated: November 27, 2025
