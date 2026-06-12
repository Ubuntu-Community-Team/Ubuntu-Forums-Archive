---
title: "Apache, php and wordpress installed. but..."
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by Vexiphne on 2010-07-04
I've installed Wordpress, apache, php5 and phpmyadmin using this tutorial. [http://blog.csmonkey.com/2007/05/how-to-setup-apache-mysql-php.html]("http://blog.csmonkey.com/2007/05/how-to-setup-apache-mysql-php.html")

But I have a couple of questions that I hope a friendly soul can answer :)

* How can I move /var/www to home/hanna/public_html ? 
I want home/hanna/public_html to be the new /var/www and NOT just a user. 

* I'm also unsure about the phpmyadmin username. I've entered the password when I installed it, but what username should I use?

B.t.w. If I move /www to /public_html will myphpadmin still work?

---

### Post by phillw on 2010-07-04
Hi, you're using pretty old instructions for installing the LAMP server (Apache, MySQL and PHP) and the phpmyadmin so I'm giving no guarantees that your installation is okay.

However, where you altering > Find the following and replace None with All
DocumentRoot /var/www/

Options FollowSymLinks
AllowOverride None you can see the DocumentRoot is set to /var/www - you can alter this, then restart the apache server again for the changes to take effect.

Your default username for phpmyadmin is root, using the password you put in when you installed it. the moving of the Document root *should* not affect your phpmyadmin access.

For anyone following on, as of 9.10 the correct way to install LAMP is to use tasksel. The details for that and adding phpmyadmin can be found at [http://forum.phillw.net/viewtopic.php?f=4&t=4&start=0](http://forum.phillw.net/viewtopic.php?f=4&t=4&start=0) I'd suggest putting on, checking the LAMP and myphpadmin are 'happy' then install Wordpress. The below I lifted from instructions for 10.04 > After phpMyAdmin installation, you can again open the browser and hit URL [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/). Et voilà! You can now get inside your MySQL database world through your browser using the user root and the password chosen above (but be aware that user root has full access to your databases and should be used wisely).

Now, we only need to download WordPress 3.0 from the official WordPress web page:

[http://wordpress.org/latest.zip](http://wordpress.org/latest.zip) (2.2MB) or [http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz) (2.0MB)

Unpack this package (I&#8217;ll use here folder /var/www as it is a standard location where the web server will look for web pages) using unzip (for the .zip archive) or tar (for the .tar.gz archive). After unpacking, you&#8217;ll get a folder WordPress extracted to your chosen location:

miguel@c31828:/var/www$ ls -al
total 2912
drwxr-xr-x  3 root   root      4096 2010-06-30 18:00 .
drwxr-xr-x 17 root   root      4096 2010-06-30 16:32 ..
-rw-r&#8211;r&#8211;  1 root   root       177 2010-06-30 16:32 index.html
drwxr-xr-x  5 root   root      4096 2010-06-17 17:05 wordpress
-rw-r&#8211;r&#8211;  1 miguel miguel 2964966 2010-06-30 17:38 wordpress-3.0.zip

You can now delete the .zip or .tar.gz archive.

Now all we&#8217;re missing is creating a MySQL database and configure WordPress!

For creating a database using phpMyAdmin, follow these steps:

Start by choosing a name for your WordPress database (like &#8216;wordpress&#8216; or &#8216;blog&#8216;), enter it in the Create new database field, and click Create (choose the right Connection Collation for you or use utf8_general_ci).
Click the Home icon in the upper left to return to the main page, then click Privileges. If a user relating to WordPress does not already exist in the list of users, create one:
Click Add a new User.
Chose a username for WordPress (like &#8216;wordpress&#8216;) and enter it in the User name field. (Be sure Use text field: is selected from the dropdown.)
Choose a strong password password (use strongpasswordgenerator.com), and enter it in the Password field. (Be sure Use text field: is selected from the dropdown.) Re-enter the password in the Re-type field.
Write down the username and password you chose.
Leave all options under Global privileges at their defaults.
Click Go.
Return to the Privileges screen and click the Edit privileges icon (on the right-most column) on the user you&#8217;ve just created for WordPress. In the Database-specific privileges section, select the database you&#8217;ve just created for WordPress under the Add privileges to the following database drop down. The page will refresh with privileges for that database. Click Check All to select all privileges, and click Go.
On the resulting page, make note of the host name listed after Server: at the top of the page. (This will usually be localhost.) which look pretty good, except that once again they are not using tasksel to put on the LAMP server (Grrrrrr...) The post is over at [http://www.ubuntugeek.com/installing-wordpress-3-0-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/installing-wordpress-3-0-on-ubuntu-10-04-lucid-lynx.html)

Regards,

Phill.

---

### Post by Vexiphne on 2010-07-04
Thank you for your help phillw. I'll try it out now :)

---

