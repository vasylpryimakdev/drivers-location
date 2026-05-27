# Muber

A Node.js/Express API for managing drivers with geolocation capabilities using MongoDB.

## Features

- Create, read, update, and delete drivers
- Geospatial queries to find drivers near a specific location
- MongoDB with Mongoose ODM for data persistence
- RESTful API design
- Express middleware for error handling

## Tech Stack

- **Node.js** - JavaScript runtime
- **Express** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling
- **Mocha** - Test framework
- **Supertest** - HTTP assertion library
- **Nodemon** - Development tool for auto-restart

## Installation

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```

3. Ensure MongoDB is running on `localhost:27017`

## Usage

### Start the server

```bash
npm start
```

The server will run on port `3050`.

### Run tests

```bash
npm test
```

## API Endpoints

### Create a driver
```http
POST /api/drivers
Content-Type: application/json

{
  "email": "driver@example.com",
  "driving": false,
  "geometry": {
    "type": "Point",
    "coordinates": [longitude, latitude]
  }
}
```

### Get drivers near a location
```http
GET /api/drivers?lng=<longitude>&lat=<latitude>
```

Returns drivers within 200km of the specified coordinates.

### Update a driver
```http
PUT /api/drivers/:id
Content-Type: application/json

{
  "email": "updated@example.com",
  "driving": true
}
```

### Delete a driver
```http
DELETE /api/drivers/:id
```

## Project Structure

```
drivers-project/
├── app.js                      # Express app configuration
├── index.js                    # Server entry point
├── package.json                # Dependencies and scripts
├── controllers/
│   └── drivers_controller.js  # Driver CRUD logic
├── models/
│   └── Driver.js              # Driver Mongoose model
├── routes/
│   └── routes.js              # API route definitions
└── test/
    ├── app_test.js            # App tests
    ├── test_helper.js         # Test utilities
    └── controllers/
        └── drivers_controller_test.js  # Controller tests
```

## Database Schema

### Driver Model

- `email` (String, required) - Driver's email address
- `driving` (Boolean, default: false) - Driver availability status
- `geometry` (GeoJSON Point) - Driver's location coordinates

## Environment Variables

- `NODE_ENV` - Set to `test` when running tests to avoid database connection