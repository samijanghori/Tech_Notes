What is JWT?

JWT stands for JSON Web Token.

It’s a compact, secure way to transmit information between two parties — usually between a client (like a frontend app or mobile app) and a server (like your Laravel backend).

It’s mainly used for authentication — verifying who a user is — in stateless APIs.

🧱 JWT Structure

A JWT has three parts, separated by dots (.):

xxxxx.yyyyy.zzzzz


Each part is Base64-encoded:

Header → contains the token type and hashing algorithm

Payload → contains the user data (e.g., user ID, role, etc.)

Signature → ensures the token hasn’t been tampered with

Example (decoded):

{
  "header": {
    "alg": "HS256",
    "typ": "JWT"
  },
  "payload": {
    "id": 1,
    "email": "user@example.com",
    "iat": 1730812237,
    "exp": 1730815837
  }
}

🚀 Why Use JWT in Laravel?

Laravel has built-in authentication (sessions, cookies), but JWT is ideal for API-based apps — especially when your frontend is built with React, Vue, Flutter, etc.

Here’s why developers use JWT in Laravel:

1. Stateless Authentication

JWT doesn’t rely on sessions or cookies.

The server doesn’t store login sessions — all user info is inside the token.

Perfect for RESTful APIs.

2. Easier Scalability

Because the server doesn’t keep session data, it’s easier to scale horizontally (multiple servers).

3. Secure and Self-contained

Each token contains all necessary user information.

It’s digitally signed — so the server can verify it hasn’t been changed.

4. Cross-platform Support

Works seamlessly with mobile apps, SPAs (Single Page Apps), and even external clients.

🛠 How JWT Works (in Laravel)

User logs in with email & password.

Server verifies the credentials and returns a JWT token.

The client stores the token (e.g., in localStorage).

For each next request, the client sends the token in the header:

Authorization: Bearer <token>


Laravel checks the token and authenticates the user.

📦 Common Packages for JWT in Laravel

tymon/jwt-auth
 — the most popular JWT library for Laravel

php-open-source-saver/jwt-auth
 — updated fork of tymon’s package

Installation example:

composer require php-open-source-saver/jwt-auth


Then publish config:

php artisan vendor:publish --provider="PHPOpenSourceSaver\JWTAuth\Providers\LaravelServiceProvider"
php artisan jwt:secret
