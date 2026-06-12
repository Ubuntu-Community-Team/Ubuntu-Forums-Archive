---
title: "PHP &amp; Permissions."
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by daGrevis on 2010-12-28
I just installed PHP 5.

I did like this...

```
sudo apt-get install apache2
sudo apt-get install php5
sudo /etc/init.d/apache2 restart
```

Then I tried to save index.php (to test PHP) in /var/www/, but it said that I don't have permissions to do it.

My friend helped me and here's solution:

```
sudo chown my_username:www-data /var/www -R
```

Then I saved it in right folder, open 127.0.0.1 using web browser and PHP works! ...yeay!

I created folder 'x' in /var/www/, tried to access it via web browser and... "Forbidden"!

Any solutions?

---

### Post by daGrevis on 2010-12-28
```
Server error.

The website encountered an error while retrieving http://127.0.0.1/. It may be down for maintenance or configured incorrectly.
```

---

### Post by Dragonbite on 2010-12-28
What are the permissions for the newly created folder ( #ls -l /var/www )?

---

### Post by daGrevis on 2010-12-28
drwxr-xr-x for /www/.

---

### Post by Dragonbite on 2010-12-28
> **daGrevis said:**
> drwxr-xr-x for /www/.

And who is the owner/group?

---

### Post by daGrevis on 2010-12-29
```
dagrevis@dagrevis-desktop:~$ sudo ls -l /var/www
[sudo] password for dagrevis: 
total 4
drwx------ 4 dagrevis dagrevis 4096 2010-12-29 07:48 uploader
dagrevis@dagrevis-desktop:~$ sudo ls -l /var/www/uploader
total 16
-rwxr-xr-x 1 dagrevis dagrevis  941 2010-12-28 02:49 do__upload.php
drwx------ 2 dagrevis dagrevis 4096 2010-12-29 07:48 includes
-rwxr-xr-x 1 dagrevis dagrevis 1105 2010-12-28 02:51 index.php
drwx------ 2 dagrevis dagrevis 4096 2010-12-28 02:55 uploads
```

---

### Post by daGrevis on 2010-12-29
Solution.

```
sudo chmod -R 555 /var/www/*
```

---

### Post by daGrevis on 2010-12-29
And this is improvement for solution. Do what I said and...

```
getent passwd

sudo chown -R www-data /var/www
sudo chmod -R 500 /var/www
```

---

