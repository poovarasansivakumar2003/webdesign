### 🚀 Program 9(2)
Write PHP program how to send mail using PHP.
---
To send an email using PHP on XAMPP, follow these step-by-step instructions:

#### 1. Install XAMPP

Make sure XAMPP is installed on your system. You can download it from the [official XAMPP website](https://www.apachefriends.org/) and follow the installation instructions for your operating system.

#### 2. Start Apache and SMTP Server (Sendmail)
<ol>
  <li>Launch XAMPP Control Panel: Open the XAMPP control panel.</li>
  <li>Start Apache: Click on the "Start" button next to Apache.</li>
</ol>
  
#### 3. Configure php.ini for Email Sending

PHP uses the mail() function to send emails. To make it work on XAMPP, you'll need to configure the php.ini file to use a mail server.

<ol>
  <li>Locate the php.ini file:
    
    • Open the XAMPP Control Panel.
    
    • Click on "Config" next to Apache, then select "php.ini."
    
    • This will open the php.ini file in your default text editor.
  </li>
  <li>Edit php.ini settings: Look for the following line and update it as needed:</li>
</ol>


```
[mail function]
; For Win32 only.
; http://php.net/smtp
SMTP = smtp.gmail.com
smtp_port = 587
```

Uncomment and set the sendmail_from and sendmail_path directive as below
```
sendmail_from = <--your gmail id-->
sendmail_path = "\"C:\xampp\sendmail\sendmail.exe\" -t"
```
Save the file after making these changes.

#### 4. Configure sendmail.ini

<ol>
  <li>Locate sendmail.ini: Navigate to the file `C:\xampp\sendmail\sendmail.ini` in File Explorer.</li>
  <li>Edit sendmail.ini: Open sendmail.ini and find the following section:</li>
</ol> 

```
smtp_server=smtp.gmail.com
smtp_port=587
smtp_ssl=auto
auth_username=<--your gmail id-->
auth_password=<--Follow step 5 to get password-->
hostname=localhost
```
Save the file after making these changes.

#### 5.Create an App Password for Gmail
[Click here and follow steps to get app password](https://itsupport.umd.edu/itsupport?id=kb_article_view&sysparm_article=KB0015112)

#### 6. Restart Apache

After making the changes to php.ini and sendmail.ini, restart Apache through the XAMPP Control Panel to apply the changes.

#### 7. Create Your PHP Script
<ol>
  <li>
    Create a PHP file (e.g., send_email.php) in the htdocs folder of XAMPP.
    You can navigate to can htdocs folder through path given `C:\xampp\htdocs\`
  </li>
  <li>>Add the code you shared:</li>
  
```
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $to = "example@gmail.com"; // Replace with the recipient's email address
    $subject = "Test Email";
    $message = "This is a test email sent from a PHP script.";
     // Set the From header and other optional headers
    $headers = "From: Your Name <your-email@example.com>" . "\r\n" .
               "Reply-To: example@gmail.com" . "\r\n" .
               "X-Mailer: PHP/" . phpversion();

    if (mail($to, $subject, $message, $headers)) {
        echo "Email sent successfully!";
    } else {
        echo "Email sending failed.";
    }
}
?>
<!DOCTYPE html>
<html>
<head>
    <title>Send Email</title>
</head>
<body>
    <h1>Send Email</h1>
    <form method="post">
        <input type="submit" value="Send Email">
    </form>
</body>
</html>

```

<li>Save the file in the htdocs folder.</li>
</ol>

#### 8. Test the Script
Open your browser.

Go to `http://localhost/send_email.php.`

Click the "Send Email" button to trigger the email
