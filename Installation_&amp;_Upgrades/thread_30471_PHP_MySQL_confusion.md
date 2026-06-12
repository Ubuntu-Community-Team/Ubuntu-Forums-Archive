---
title: "PHP MySQL confusion"
date: 2005-04-28
forum: Installation &amp; Upgrades
---

### Post by ajdphoto on 2005-04-28
Ok, Ive got everything set up correctly. Apache, MySQL, and PHP (or so i thought)  I did the apt-get install apache2-mod-.... or something like that for php support in apache.  and it works.  I have php 4.3 installed.  Now i was doing some work trying to get php to connect to the mysql server and i get an error telling my that it there is an undentified function "mysql_connect()"  so im figuring that i dont have the MySQL module installed.  So when i didnt apt-get install php4-mysql, it wants to uninstall apache2-mod-php4 (or something like that) and then my page doesnt work at all.  Any suggestions?

---

### Post by dalbjerg on 2005-04-29
[QUOTE=ajdphoto]Ok, Ive got everything set up correctly. Apache, MySQL, and PHP (or so i thought)  I did the apt-get install apache2-mod-.... or something like that for php support in apache.  and it works.  I have php 4.3 installed.  Now i was doing some work trying to get php to connect to the mysql server and i get an error telling my that it there is an undentified function "mysql_connect()"  so im figuring that i dont have the MySQL module installed.  So when i didnt apt-get install php4-mysql, it wants to uninstall apache2-mod-php4 (or something like that) and then my page doesnt work at all.  Any suggestions?[/QUOTE]
 use the this:

apt-get install php4 php4-mysql

It shall then uninstall apache-mod-php4. But PHP4 will work after this.

---

### Post by ajdphoto on 2005-04-29
[QUOTE=dalbjerg]use the this:

apt-get install php4 php4-mysql

It shall then uninstall apache-mod-php4. But PHP4 will work after this.[/QUOTE]
 that will download and install.  But when i browse to my index.php page it wants me to download the script instead of displaying it.

---

### Post by ajdphoto on 2005-04-30
anyone have any ideas for getting mysql functions to work with php.  They dont seem to work at all with them.

---

### Post by zakili on 2005-05-05
[QUOTE=ajdphoto]anyone have any ideas for getting mysql functions to work with php.  They dont seem to work at all with them.[/QUOTE]
 you must compile php with enable mysql ...

---

