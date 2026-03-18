# Environment Configuration

This repository contains environment configuration examples for the ARMS application.

## Database Configuration

Database credentials should be stored in environment variables, not hardcoded in your application.

### Using Environment Variables

Create a `.env` file in your project root with the following content:

```
DB_HOST=localhost
DB_NAME=arms_db
DB_USER=root
DB_PASSWORD=your_secure_password
```

### PHP Database Connection

Update your connection script to use environment variables:

```php
<?php
$host = getenv('DB_HOST') ?: 'localhost';
$db_name = getenv('DB_NAME') ?: 'arms_db';
$username = getenv('DB_USER') ?: 'root';
$password = getenv('DB_PASSWORD') ?: '';

$conn = new mysqli($host, $username, $password, $db_name);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>
```

## Setup Instructions

1. Copy `.env.example` to `.env`
2. Update the `.env` file with your actual credentials
3. Add `.env` to your `.gitignore` file to prevent credentials from being committed

## Security Best Practices

- Never commit `.env` files or hardcode credentials in your source code
- Use environment variables for sensitive information
- Keep database passwords strong and secure
- Regularly rotate database credentials
