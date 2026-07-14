# MedEase - Medical Store Management System

A comprehensive full-stack web application for managing medical store operations with separate interfaces for customers and administrators.

## 🚀 Features

### Customer Features
- **User Authentication**: Secure registration and login system
- **Product Catalog**: Browse and search medical products
- **Shopping Cart**: Add/remove products, adjust quantities
- **Order Management**: Place orders from cart, track order status
- **Profile Management**: Update personal information
- **Responsive Design**: Works on desktop and mobile devices

### Admin Features
- **Dashboard**: Overview of customers, products, orders, and revenue
- **Customer Management**: View and manage customer accounts
- **Product Management**: Add, edit, and delete products
- **Order Management**: View all orders, update order status
- **Analytics**: Sales statistics and performance metrics

## 🛠️ Technology Stack

### Frontend
- **React.js** - Modern UI library
- **React Router** - Client-side routing
- **Tailwind CSS** - Utility-first CSS framework
- **Lucide React** - Beautiful icons
- **Axios** - HTTP client for API calls
- **Vite** - Fast development build tool

### Backend
- **FastAPI** - High-performance Python web framework
- **SQLAlchemy** - Python SQL toolkit and ORM
- **Pydantic** - Data validation using Python type annotations
- **Uvicorn** - ASGI web server
- **Passlib** - Password hashing utilities
- **Jose** - JWT token handling
- **Python-dotenv** - Environment variable management

### Database
- **MySQL** - Relational database management system
- **mysql-connector-python** - MySQL driver for Python

## 📊 Database Design

### Entity Relationship Diagram
The system uses a relational database with the following main entities:

#### Tables:
1. **Customers** - User account information
2. **Products** - Medical product catalog
3. **Orders** - Customer orders
4. **Cart** - Shopping cart items
5. **Suppliers** - Product suppliers
6. **DeliveryMen** - Delivery personnel
7. **DeliveryManReviews** - Delivery ratings
8. **Admin** - Administrator accounts

### Key Relationships:
- One-to-Many: Customer → Orders, Customer → Cart
- Many-to-One: Orders → Products, Cart → Products
- Many-to-One: Products → Suppliers
- Many-to-One: Orders → DeliveryMen

## 🏗️ System Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │   Backend       │    │   Database      │
│   (React)       │◄──►│   (FastAPI)     │◄──►│   (MySQL)       │
│                 │    │                 │    │                 │
│ • User Interface│    │ • REST API      │    │ • Data Storage  │
│ • State Mgmt    │    │ • Authentication│    │ • Relationships │
│ • Routing       │    │ • Business Logic│    │ • Constraints   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 🔧 Installation & Setup

### Prerequisites
- Node.js (v14 or higher)
- Python (v3.8 or higher)
- MySQL Server
- Git

### Backend Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd med-ease/backend
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Environment Configuration**
   Create a `.env` file in the backend directory:
   ```env
   DATABASE_URL=mysql+mysqlconnector://username:password@localhost:3306/medease
   SECRET_KEY=your-secret-key-here
   ALGORITHM=HS256
   ACCESS_TOKEN_EXPIRE_MINUTES=30
   ```

5. **Database Setup**
   ```bash
   mysql -u root -p
   CREATE DATABASE medease;
   USE medease;
   SOURCE Database\ Creation\ \&\ Population\ \(D3\)/medease_creation.sql;
   SOURCE Database\ Creation\ \&\ Population\ \(D3\)/querypopulation.sql;
   ```

6. **Start the backend server**
   ```bash
   uvicorn main:app --reload --host 0.0.0.0 --port 8000
   ```

### Frontend Setup

1. **Navigate to frontend directory**
   ```bash
   cd med-ease/frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Access the application**
   - Frontend: http://localhost:5173
   - Backend API: http://localhost:8000
   - API Documentation: http://localhost:8000/docs

## 👥 User Accounts

### Sample Customer Accounts
| Email | Password | Name |
|-------|----------|------|
| shreyashi@example.com | password123 | Shreyashi Kumar |
| priya@example.com | password456 | Priya Sharma |
| amit@example.com | password789 | Amit Patel |

### Admin Account
| Username | Password |
|----------|----------|
| admin | admin123 |

## 🔐 API Endpoints

### Authentication
- `POST /auth/register` - Register new customer
- `POST /auth/login` - Customer login
- `POST /auth/admin/login` - Admin login

### Products
- `GET /products` - Get all products
- `GET /products/{id}` - Get specific product

### Cart
- `GET /cart` - Get user's cart items
- `POST /cart` - Add item to cart
- `PUT /cart/{id}` - Update cart item
- `DELETE /cart/{id}` - Remove cart item

### Orders
- `GET /orders` - Get user's orders
- `POST /orders` - Create new order
- `POST /orders/place-from-cart` - Place order from cart
- `GET /admin/orders` - Get all orders (admin)
- `PUT /admin/orders/{id}` - Update order status (admin)

### Customers
- `GET /customers/me` - Get current user profile
- `PUT /customers/me` - Update user profile
- `GET /customers` - Get all customers (admin)

## 📱 User Interface

### Customer Interface
- **Homepage**: Hero section with featured products
- **Products Page**: Grid layout with search and filters
- **Cart Page**: Item management and checkout
- **Orders Page**: Order history and tracking
- **Profile Page**: Account settings

### Admin Interface
- **Dashboard**: Statistics and overview
- **Customer Management**: User accounts table
- **Product Management**: Inventory control
- **Order Management**: Order processing and status updates

## 🎨 Design System

### Color Palette
- Primary: Blue (#2563eb)
- Secondary: Purple (#7c3aed)
- Success: Green (#16a34a)
- Warning: Yellow (#eab308)
- Error: Red (#dc2626)

### Components
- **Cards**: Elevated surfaces with shadows
- **Buttons**: Primary and secondary styles
- **Forms**: Consistent input styling
- **Navigation**: Responsive navbar and tabs

## 🔒 Security Features

- **JWT Authentication**: Secure token-based auth
- **Password Hashing**: Bcrypt for password security
- **Input Validation**: Pydantic models for data validation
- **CORS Protection**: Configured for frontend origin
- **SQL Injection Protection**: ORM-based queries

## 📈 Performance Optimization

- **Lazy Loading**: Components loaded on demand
- **Caching**: Browser caching for static assets
- **Database Indexing**: Optimized queries
- **Response Compression**: Reduced payload sizes

## 🧪 Testing

### Running Tests
```bash
# Backend tests
cd backend
python -m pytest

# Frontend tests
cd frontend
npm test
```

## 🚀 Deployment

### Production Setup
1. **Build Frontend**
   ```bash
   npm run build
   ```

2. **Configure Environment**
   - Set production database credentials
   - Update CORS origins
   - Configure SSL certificates

3. **Deploy Backend**
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 8000 --workers 4
   ```

## 📝 Future Enhancements

- **Payment Integration**: Online payment processing
- **Real-time Notifications**: WebSocket implementation
- **Mobile App**: React Native mobile application
- **Analytics Dashboard**: Advanced reporting
- **Inventory Management**: Stock alerts and reordering
- **Multi-language Support**: Internationalization
- **API Rate Limiting**: Request throttling
- **Backup & Recovery**: Automated database backups

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**MedEase** - Simplifying medical store management with modern technology.

## Overview

MedEase is an online medicine delivery application designed to facilitate the purchase and delivery of pharmaceutical products to customers. This repository contains the database schema and the initial application code for managing orders, customer information, product inventory, and delivery personnel.

## Database Configuration

### Tables

1. **Customers**
   - Stores information about customers including their personal details, contact information, and loyalty points.

2. **Suppliers**
   - Contains details of suppliers who provide the products.

3. **Products**
   - Holds information about the products available for purchase, including their descriptions, prices, and supplier details.

4. **DeliveryMen**
   - Maintains details of delivery personnel responsible for delivering orders to customers.

5. **Orders**
   - Records information about customer orders, including the product details, quantity, price, delivery address, and order status.

6. **OrderHistory**
   - Archives past orders, including details about the customer, product, quantity, price, delivery address, and order status.

7. **Cart**
   - Tracks items added to the cart by customers before they place an order.

8. **DeliveryManReviews**
   - Contains customer reviews and ratings for delivery personnel.


## Application Code

The application is built using Python and Tkinter for the GUI and connects to a MySQL database for data storage and retrieval. The key features of the application include:

- Placing orders
- Viewing product statistics
- Viewing and managing customer orders
- Reviewing delivery personnel

