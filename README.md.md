# Open Data Zimbabwe

## 🏛️ Zimbabwe's Definitive Open Data Platform

Open Data Zimbabwe is a comprehensive initiative to systematically collect, standardize, and publish high-quality public interest datasets from Zimbabwe's official sources. We provide trusted, enterprise-grade data infrastructure serving citizens, researchers, journalists, and civic organizations.

### 🎯 What Makes Us Different

- **Enterprise-grade data governance** with comprehensive quality assurance
- **Complete provenance tracking** and confidence scoring for every record
- **Longitudinal data models** designed for historical analysis from day one
- **Community-driven validation** and transparent feedback mechanisms
- **Developer-friendly APIs** with both bulk downloads and versioned REST endpoints

## 📊 Coming Datasets

### Members of Parliament (MPs)
- **Coverage**: All current and historical MPs with complete term tracking
- **Updates**: Twice weekly (Monday & Thursday)
- **Confidence Score**: 95%+
- **Records**: 350+ MPs across 10 parliamentary sessions

### Constituencies
- **Coverage**: All 210 National Assembly constituencies
- **Geographic Data**: Boundaries, area calculations, and demographic links
- **Historical Representation**: Complete MP succession records
- **Updates**: Monthly or as boundaries change

## 🚀 Quick Start

### Using the API

```bash
# Get all current MPs
curl "https://api.opendatazw.org/api/v1/mps"

# Get specific MP details with full history
curl "https://api.opendatazw.org/api/v1/mps/a1b2c3d4-e5f6-7890-1234-567890abcdef"

# Search for MPs by name or constituency
curl "https://api.opendatazw.org/api/v1/search/mps?q=harare"

# Get constituency representation on specific date
curl "https://api.opendatazw.org/api/v1/constituencies/f0e9d8c7-b6a5-4321-fedc-ba9876543210/representation?date=2023-01-15"
```

### Bulk Downloads

```bash
# Download complete datasets
wget https://api.opendatazw.org/api/v1/bulk/mps.json
wget https://api.opendatazw.org/api/v1/bulk/constituencies.json

# CSV format also available
wget https://api.opendatazw.org/api/v1/bulk/mps.csv
wget https://api.opendatazw.org/api/v1/bulk/constituencies.csv
```

### Python Example

```python
import requests

# Get all MPs
response = requests.get("https://api.opendatazw.org/api/v1/mps")
mps = response.json()

for mp in mps['data']:
    print(f"{mp['personal']['full_name']} - {mp['terms_of_service'][-1]['constituency']['name']}")

# Get MP history
mp_response = requests.get("https://api.opendatazw.org/api/v1/mps/a1b2c3d4-e5f6-7890-1234-567890abcdef")
mp_data = mp_response.json()

# Access all terms of service
for term in mp_data['terms_of_service']:
    print(f"Parliament {term['parliament']}: {term['constituency']['name']} ({term['start_date']} - {term['end_date'] or 'present'})")
```

## 📋 Data Schema

### MP Record Structure
```json
{
  "id": "a1b2c3d4-e5f6-7890-1234-567890abcdef",
  "slug": "jane-doe-harare-north",
  "schema_version": "3.0.0",
  "record_metadata": {
    "confidence_score": 0.95,
    "last_updated": "2025-01-15T10:30:00Z",
    "provenance": {
      "primary_source": "https://parlzim.gov.zw/members/jane-doe",
      "verification_sources": ["https://zec.gov.zw/candidates/jane-doe"]
    }
  },
  "personal": {
    "full_name": "Jane Doe",
    "honorific": "Hon.",
    "gender": "Female"
  },
  "terms_of_service": [
    {
      "term_id": "trm-98765432-1fed-cba9-8765-43210fedcba9",
      "parliament": 10,
      "constituency": {
        "id": "f0e9d8c7-b6a5-4321-fedc-ba9876543210",
        "name": "Harare North"
      },
      "party": {
        "id": "pty-cba98765-4321-fedc-ba98-76543210fed",
        "name": "XYZ Party"
      },
      "start_date": "2023-08-23",
      "end_date": null,
      "status": "serving"
    }
  ]
}
```

## 🔧 API Documentation

### Authentication
- **Public Access**: 1,000 requests/hour
- **Registered Users**: 10,000 requests/hour  
- **Verified Organizations**: 100,000 requests/hour


#to do
[(Add Link to)Register for Access →](https://com)

### Endpoints

| Endpoint | Description | Example |
|----------|-------------|---------|
| `GET /api/v1/mps` | List all MPs | [Try it](https://api.opendatazw.org/api/v3/mps) |
| `GET /api/v1/mps/{id}` | Get MP details | [Try it](https://api.opendatazw.org/api/v3/mps/a1b2c3d4-e5f6-7890-1234-567890abcdef) |
| `GET /api/v1/constituencies` | List all constituencies | [Try it](https://api.opendatazw.org/api/v3/constituencies) |
| `GET /api/v1/search/mps` | Search MPs | [Try it](https://api.opendatazw.org/api/v3/search/mps?q=harare) |
| `GET /api/v1/metadata/health` | System health check | [Try it](https://api.opendatazw.org/api/v3/metadata/health) |

**Full API Documentation**: [docs](https://) #to-do add link to docs

## 📈 Data Quality & Trust

### Our Quality Framework

- **Completeness**: 
- **Accuracy**: 
- **Timeliness**: 
- **Consistency**: Standardized formats and terminologies
- **Provenance**: Complete audit trail from source to publication

### Confidence Scoring
Every record includes confidence indicators:
- **Source Authority Score**: Government sources (0.9-1.0), secondary sources (0.6-0.8)
- **Verification Score**: Cross-validated across multiple sources
- **Freshness Score**: Based on age relative to expected update frequency

### Data Sources Priority
1. **Level 1**: Official Electoral Commission (ZEC) & Government Gazette
2. **Level 2**: Official Parliament of Zimbabwe website
3. **Level 3**: State-owned media reports
4. **Level 4**: Reputable independent media

## 🤝 Contributing

We welcome community contributions! Here's how you can help:

### Report Data Issues
Found an error? [Create an issue](https://) with:
- Record ID or URL
- Description of the issue
- Authoritative source for correction
- Your contact information (optional)

### Suggest New Datasets
Have ideas for new datasets? [Open a discussion](https://github.com/) and tell us:
- What dataset you'd like to see
- Why it would be valuable
- Known sources for the data
- Potential use cases

### Development Contributions
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code of Conduct
Please read our [Code of Conduct](CODE_OF_CONDUCT.md) before contributing.

## 🛠️ Technical Architecture

### Data Pipeline
```
┌─────────────────────┐    ┌──────────────────────┐    ┌─────────────────────┐
│   Data Sources      │    │   ETL Pipeline       │    │   Publication       │
│ • Parliament.gov.zw │────│ • Resilient Scraping │────│ • GitHub Repository │
│ • ZEC.gov.zw        │    │ • Data Validation    │    │ • REST API          │
│ • Gazette           │    │ • Confidence Scoring │    │ • Bulk Downloads    │
└─────────────────────┘    └──────────────────────┘    └─────────────────────┘
```

### Tech Stack
- **Data Storage**: JSON files in Git + PostgreSQL for queries
- **API**: FastAPI with automatic OpenAPI documentation
- **Pipeline**: Python with GitHub Actions for automation
- **Monitoring**: Comprehensive health checks and quality metrics
- **Frontend**: React-based documentation site

## 📊 Usage Statistics

- **Monthly API Requests**: 
- **Registered Developers**: 
- **Downstream Applications**: 
- **Academic Citations**: 
- **Media References**: 

## 🔗 Related Projects

### Built with Open Data Zimbabwe
- **[ZimParliWatch](https://zimparliwatch.org)**: Parliamentary monitoring platform
- **[ConstituencyMap](https://constituencymap.co.zw)**: Interactive constituency boundaries
- **[ElectionTracker](https://electiontracker.co.zw)**: Real-time election monitoring

### Research & Analysis
- **[ZimGov Analytics](https://zimgov.analytics)**: Government performance dashboards
- **[Academic Research Portal](https://research.opendatazw.org)**: Datasets for researchers

## 📄 License & Attribution

### Data License
All datasets are licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

**You are free to:**
- Share — copy and redistribute the material in any medium or format
- Adapt — remix, transform, and build upon the material
- Commercial use — use the material for commercial purposes

**Under the following terms:**
- Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made

### How to Cite
**Academic Papers:**
```
Open Data Zimbabwe. (2025). Zimbabwe Parliamentary and Electoral Data [Data set]. 
Retrieved from https://
```

**News Articles:**
```
Data from Open Data Zimbabwe 
```

**Applications:**
```
Powered by Open Data Zimbabwe -
```

## 💰 Sustainability

### Funding Sources
- 

### Support Our Work
- ⭐ Star this repository
- 🐛 Report bugs and suggest improvements
- 💡 Contribute new features
- 💰 [Sponsor the project](https://)
- 🗣️ Spread the word in your networks

## 📞 Contact & Support

### Get Help
- **Documentation**: [docs.opendatazw.org](https://) #to-do add link to docs
- **Community Forum**: [forum.opendatazw.org](https://) #to-do add link to forum
- **GitHub Issues**: [Report bugs](https://github.com/) #to-do add link to issues
- **Email**: [support@opendatazw.org](mailto:) #to-do add email
### Connect With Us
- **Twitter**: [@OpenDataZW](https://twitter.com/) #to-do add twitter link

### Team
- **Technical Lead**: Tawanda Moyo [Github](https://github.com/tawandamoyo), [website](https://tawanda.dev)

---

## 🗺️ Roadmap

### Current Phase: Version 1.0 (Public Launch)
- [ ] Core MP and Constituency datasets
- [ ] REST API v3 with longitudinal data
- [ ] Data confidence framework
- [ ] Community feedback system
- [ ] Admin curation dashboard
- [ ] Performance optimization

### Future Phases: Version 2.0+
- [ ] Budget and procurement datasets
- [ ] Advanced analytics and visualizations
- [ ] Mobile app with offline capabilities 
- [ ] Real-time election result feeds
- [ ] Parliamentary voting records
- [ ] Committee meeting transcripts

### Long-term Vision
- Expand to cover all Southern African countries
- Become the standard for parliamentary data APIs
- Build sustainable funding model
- Establish academic research partnerships

---

**Built with ❤️ for transparency and accountability in Zimbabwe**

*Last updated: July 5, 2025*