---
title: "apache2 localhost subfolders"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TDragon on 2008-09-22
I recently decided to wipe my PC and install the lastest build of Intrepid. However, I forgot how to properly set up Apache2 to use subfolders such as [http://localhost/NewFolder](http://localhost/NewFolder).
 
I had it set up properly in the past when I had Ampache installed prior to the wipe ([http://localhost/ampache/](http://localhost/ampache/) & [http://myIPaddress/ampache/](http://myIPaddress/ampache/)), but now i can only get it to work as a VirtualHost, [http://ampache/](http://ampache/) (and not [http://myIPaddress/ampache/](http://myIPaddress/ampache/)), which doesn't work to well with DynDNS.
 

Installed (Latest Builds):
[LIST]
[*]Apache2
[*]PHP5
[*]MySQL
[*]Ampache 3.4.3
[/LIST]The only way I got it to work is using 127.0.0.2 for ampache virtualhost (in /etc/hosts/ w/ localhost as 127.0.0.1), and a ampache.conf file in the sites-enabled directory. Folder is located in /var/www/ampache/ and the localhost document root is /var/www/. I cannot post config files until I get home later tonight. 
 
I would like to figure this out in general so i can host other items in the future.

---

### Post by superprash2003 on 2008-09-22
thats probably a problem with the DOCUMENTROOT .. open the default file under /etc/apache2/sites-enabled .. and ensure that the DocumentRoot is set correctly.. if you are not sure.. post the current documentroot

---

### Post by TDragon on 2008-09-23
Here is my default file, sorry for the delay conky caused my xserver to be broken (in intrepid) and I had to remove it from the command line in recovery mode.

---

### Post by TDragon on 2008-09-24
***bump***

---

### Post by dmizer on 2008-09-24
Moved this to Intrepid testing where I hope you might get a better response.

---

### Post by TDragon on 2008-09-25
***bump***

---

