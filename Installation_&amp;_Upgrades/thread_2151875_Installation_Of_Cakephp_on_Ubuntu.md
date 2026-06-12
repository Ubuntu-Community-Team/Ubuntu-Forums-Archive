---
title: "Installation Of Cakephp on Ubuntu"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by planetwildlife on 2013-06-06
**[COLOR=#DD7E6B][FONT=Arial][B]_CAKEPHP_**[/FONT][/COLOR][COLOR=#000000][FONT=Arial]**_ INSTALLATION - UBUNTU_**[/FONT][/COLOR]


[LIST]
[*]Install Apache Server, MySQL, PHP
[/LIST]


[LIST]
[*]Download the current release from [[COLOR=#1155CC]_cakephp.org_[/COLOR]]("http://cakephp.org") and un(zip/tar).
[/LIST]


[LIST]
[*]Copy the unzip cakephp files into **var/www/** folder.
[/LIST]


[LIST]
[*]Now give the permissions to the cakephp folder by entering the command line in terminal
[/LIST]

[COLOR=#0000FF][FONT=Arial]**sudo chmod -R 777 /var/www/cakephp**[/FONT][/COLOR]


[LIST]
[*]Enter [COLOR=#0000FF]localhost/cakephp[/COLOR] in browser. We will get warnings like
[/LIST]

[COLOR=#FF0000][FONT=Arial]Notice (1024): Please change the value of 'Security.salt' in app/Config/core.php to a salt value specific to your application [CORE/Cake/Utility/Debugger.php, line 851][/FONT][/COLOR]

[COLOR=#FF0000][FONT=Arial]Please change the value of 'Security.cipherSeed' in app/Config/core.php to a numeric (digits only) seed value specific to your application [CORE/Cake/Utility/Debugger.php, line 855][/FONT][/COLOR]


[LIST]
[*]Edit the file **core.php** in **cakephp/app/config/core.php**
[/LIST]


[LIST]
[*]Change the random string for **Security.salt** (* configure random string used in security hashing methods just by generating 63 random alpha numeric characters for random strings.Get the random strings from the mentioned url*[COLOR=#1155CC]**_[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)_**[/COLOR])
[/LIST]


[LIST]
[*]Now change the numeric string for **Security.cipherSeed ***(Enter any  29 random numbers).*
[/LIST]


[LIST]
[*]Create a database for cakephp in phpmyadmin.
[/LIST]


[LIST]
[*]Now rename the file **cakephp/app/config/database.php.default   **to  **database.php.**
[/LIST]


[LIST]
[*]Change the details of the database
[/LIST]

[COLOR=#000000][FONT=Arial]public $default = array( [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]'datasource' => 'Database/Mysql', [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]'persistent' => false, [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]'host' => 'localhost', [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]'login' => 'root',[/FONT][/COLOR][COLOR=#000000][FONT=Arial]** ------------->**[/FONT][/COLOR][COLOR=#000000][FONT=Arial]([/FONT][/COLOR][COLOR=#CC4125][FONT=Arial]*Enter username of phpmyadmin*[/FONT][/COLOR][COLOR=#000000][FONT=Arial]*)*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]'password' => 'password', [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**------------->**[/FONT][/COLOR][COLOR=#000000][FONT=Arial]([/FONT][/COLOR][COLOR=#CC4125][FONT=Arial]*Enter password of phpmyadmin*[/FONT][/COLOR][COLOR=#000000][FONT=Arial]*)*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]'database' => 'database_name', [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**------------->**[/FONT][/COLOR][COLOR=#000000][FONT=Arial]([/FONT][/COLOR][COLOR=#CC4125][FONT=Arial]*Enter created database name*[/FONT][/COLOR][COLOR=#000000][FONT=Arial]*)*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]'prefix' => '', [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]//'encoding' => 'utf8', );[/FONT][/COLOR]

[LIST]
[*]Now edit the **000-default** file in **/etc/apache2/sites-enabled/000-default**
[/LIST]

[COLOR=#0000FF][FONT=Arial]**sudo gedit /etc/apache2/sites-enabled/000-default**[/FONT][/COLOR]


[LIST]
[*]And change the [COLOR=#006600]**AllowOverride None**[/COLOR]   to**    [COLOR=#006600]AllowOverride All[/COLOR]**
[/LIST]

[COLOR=#000000][FONT=Arial]          <Directory /var/www/> [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        Options Indexes FollowSymLinks MultiViews [/FONT][/COLOR]
[COLOR=#006600][FONT=Arial]AllowOverride None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        Order allow,deny [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        allow from all [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    </Directory>  [/FONT][/COLOR]

[COLOR=#cc00ff][FONT=Arial]**    to**[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]           <Directory /var/www/> [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        Options Indexes FollowSymLinks MultiViews [/FONT][/COLOR]
[COLOR=#006600][FONT=Arial]AllowOverride All [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        Order allow,deny [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        allow from all [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    </Directory>[/FONT][/COLOR]


[LIST]
[*]Now enable the mode rewrite
[/LIST]

[COLOR=#0000FF][FONT=Arial]**sudo a2enmod rewrite**[/FONT][/COLOR]


[LIST]
[*]Now restart the apache2
[/LIST]

[COLOR=#0000FF][FONT=Arial]**sudo /etc/init.d/apache2 restart**[/FONT][/COLOR]






[/B]

---

