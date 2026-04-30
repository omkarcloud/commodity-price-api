# Commodity Price API

REST API for real-time commodity futures prices — gold, silver, crude oil, natural gas, coffee, wheat, and 25+ more. Prices from CME, NYMEX, and CBOT in USD.

## Features

- Real-time futures prices for 30+ commodities
- Covers precious metals, energy, agriculture, and livestock
- Prices sourced from CME, NYMEX, and CBOT exchanges
- 100 requests/month on free tier
- Example Response:
```json
{
  "commodity_name": "Silver Futures",
  "exchange": "CME",
  "price_usd": 79.665,
  "updated_at": "2026-02-09T11:45:04+00:00"
}
```

## Get API Key

Create an account at [omkar.cloud](https://www.omkar.cloud/auth/sign-up?redirect=/api-key) to get your API key, and use it in requests. 100 requests are free every month.

## Quick Start

```bash
curl -X GET "https://commodity-price-api.omkar.cloud/commodity-price?name=silver" \
  -H "API-Key: YOUR_API_KEY"
```

```json
{
  "commodity_name": "Silver Futures",
  "exchange": "CME",
  "price_usd": 79.665,
  "updated_at": "2026-02-09T11:45:04+00:00"
}
```

## Installation

### Python

```bash
pip install requests
```

```python
import requests

response = requests.get(
    "https://commodity-price-api.omkar.cloud/commodity-price",
    params={"name": "silver"},
    headers={"API-Key": "YOUR_API_KEY"}
)

data = response.json()
print(f"{data['commodity_name']}: ${data['price_usd']} ({data['exchange']})")
```

### Node.js

```bash
npm install axios
```

```javascript
import axios from "axios";

const response = await axios.get("https://commodity-price-api.omkar.cloud/commodity-price", {
    params: { name: "silver" },
    headers: { "API-Key": "YOUR_API_KEY" }
});

console.log(`${response.data.commodity_name}: $${response.data.price_usd}`);
```

## API Reference

### Endpoint

```
GET https://commodity-price-api.omkar.cloud/commodity-price
```

### Headers

| Header | Required | Description |
|--------|----------|-------------|
| `API-Key` | Yes | API key from [omkar.cloud/api-key](https://www.omkar.cloud/api-key) |

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `name` | Yes | Commodity name (see supported commodities below) |

### Supported Commodities

| Category | Commodities |
|----------|-------------|
| **Precious Metals** | `gold`, `silver`, `platinum`, `palladium`, `micro_gold`, `micro_silver` |
| **Energy** | `crude_oil`, `brent_crude_oil`, `natural_gas`, `gasoline_rbob`, `heating_oil` |
| **Agriculture** | `wheat`, `corn`, `soybean`, `soybean_oil`, `soybean_meal`, `oat`, `rough_rice`, `lumber`, `coffee`, `cocoa`, `sugar`, `cotton`, `orange_juice` |
| **Livestock** | `live_cattle`, `feeder_cattle`, `lean_hogs`, `class_3_milk` |
| **Metals** | `copper`, `aluminum` |

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `commodity_name` | string | Full futures contract name (e.g., "Silver Futures") |
| `exchange` | string | Trading exchange — CME, NYMEX, or CBOT |
| `price_usd` | number | Current futures price in USD |
| `updated_at` | string | ISO 8601 timestamp of last price update |

## Examples

### Get gold price

```python
response = requests.get(
    "https://commodity-price-api.omkar.cloud/commodity-price",
    params={"name": "gold"},
    headers={"API-Key": "YOUR_API_KEY"}
)

gold = response.json()
print(f"Gold: ${gold['price_usd']} on {gold['exchange']}")
```

### Get crude oil price

```python
response = requests.get(
    "https://commodity-price-api.omkar.cloud/commodity-price",
    params={"name": "crude_oil"},
    headers={"API-Key": "YOUR_API_KEY"}
)

oil = response.json()
print(f"WTI Crude: ${oil['price_usd']}")
```

### Get natural gas price

```python
response = requests.get(
    "https://commodity-price-api.omkar.cloud/commodity-price",
    params={"name": "natural_gas"},
    headers={"API-Key": "YOUR_API_KEY"}
)

gas = response.json()
print(f"Natural Gas: ${gas['price_usd']}")
```

## Error Handling

```python
response = requests.get(
    "https://commodity-price-api.omkar.cloud/commodity-price",
    params={"name": "gold"},
    headers={"API-Key": "YOUR_API_KEY"}
)

if response.status_code == 200:
    data = response.json()
elif response.status_code == 401:
    # Invalid API key
    pass
elif response.status_code == 429:
    # Rate limit exceeded
    pass
```

## Rate Limits

| Plan | Price | Requests/Month |
|------|-------|----------------|
| Free | $0 | 100 |
| Starter | $16 | 3,000 |
| Grow | $48 | 15,000 |
| Scale | $148 | 75,000 |

## Questions? We have answers.

Reach out anytime. We will solve your query within 1 working day.

[![Contact Us on WhatsApp about Commodity Price API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/whatsapp-us.png)](https://api.whatsapp.com/send?phone=918178804274&text=I%20have%20a%20question%20about%20the%20Commodity%20Price%20API.)

[![Contact Us on Email about Commodity Price API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/ask-on-email.png)](mailto:happy.to.help@omkar.cloud?subject=Commodity%20Price%20API%20Question)
