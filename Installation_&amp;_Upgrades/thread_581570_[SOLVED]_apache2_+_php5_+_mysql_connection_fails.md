---
title: "[SOLVED] apache2 + php5 + mysql: connection fails"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by ingridt on 2007-10-19
new install ubuntu feisty fawn and I used synaptic to install this trio to create my localhost. Also installed phpmyadmin.

With mysql and phpmyadmin I was able to create the databases and restore the content from previous mysqldump. :)

Now connecting to the mysql with any of my php fails: all code after the mysql_connect is ignored :confused:

What to do?

---

### Post by disasm on 2007-10-19
> **ingridt said:**
> new install ubuntu feisty fawn and I used synaptic to install this trio to create my localhost. Also installed phpmyadmin.

With mysql and phpmyadmin I was able to create the databases and restore the content from previous mysqldump. :)

Now connecting to the mysql with any of my php fails: all code after the mysql_connect is ignored :confused:

What to do?

create this simple script:
<?php
phpinfo();
?>

View the output of that in apache. Look for something that says mysql. If you don't see anything, configure your php.ini to use mysql

check /etc/php5/apache2/php.ini. Make sure the mysql extension is enabled. If you use a default setup and aren't comfortable mucking with the php config files, you can always apt-get --purge remove <all php packages installed here>

Then reinstall them, but my suggestion would be to try to find out why your config isn't working. look for a line extension=, I know that's where it used to have problems in edgy, but I think things changed a bit in feisty.

Sam

Sam

---

### Post by disasm on 2007-10-19
Another note. I just looked on a feisty install, and the extension= has been moved into /etc/php5/apache2/conf.d In there, you'll find a mysql.ini that has just that extension line on it. I'm still looking into where conf.d scripts are sourced.

Sam

---

### Post by ingridt on 2007-10-19
There is nothing about mysql in phpinfo.
I found php.ini and it has no extension defined:

;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;
;
; If you wish to have an extension loaded automatically, use the following
; syntax:
;
;   extension=modulename.extension
;
.... nothing but explanation and example

so I should copy the line as I find it in mysql.ini:

extension=mysql.so

into php.ini
Is that it?

---

### Post by disasm on 2007-10-19
> **ingridt said:**
> There is nothing about mysql in phpinfo.
I found php.ini and it has no extension defined:

;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;
;
; If you wish to have an extension loaded automatically, use the following
; syntax:
;
;   extension=modulename.extension
;
.... nothing but explanation and example

so I should copy the line as I find it in mysql.ini:

extension=mysql.so

into php.ini
Is that it?

I'm not sure. It used to be in there, but my working version doesn't have it in there anymore. it's only in the conf.d.

When you ran the phpinfo() script, did you get any output?

Sam

---

### Post by ingridt on 2007-10-19
phpinfo gave the full information page: nothing in there about mysql
(find sql gives only one result: sql.safe_mode	Off which is probably not relevant here)

phpmyadmin  works! But this might have it's own php.ini settings?

I will add this little sentence (extension=) into php.ini and keep you informed.

---

### Post by ingridt on 2007-10-19
Solved!

connection no longer fails and phpinfo gives a new chapter of parameters on mysql.

thanx ):P

---

