### netlify
_redirects ==>  /*    /index.html   200

### web site  route problem solve 
## react
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /index.html [L]
</IfModule>

## Vite 

<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  
  # Redirect all requests to index.html except for existing files or directories
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /index.html [L]
  
  # Ensure correct MIME types for JavaScript and other assets
  AddType application/javascript .js
  AddType text/css .css
  
  # Enable compression for faster loading
  <IfModule mod_deflate.c>
    AddOutputFilterByType DEFLATE text/html text/plain text/xml text/css text/javascript application/javascript
  </IfModule>
</IfModule>
