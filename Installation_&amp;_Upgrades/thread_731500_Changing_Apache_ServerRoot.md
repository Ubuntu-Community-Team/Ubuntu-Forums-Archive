---
title: "Changing Apache ServerRoot"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by emotionlovesyou on 2008-03-21
I've just used Synaptic to install Apache2 and PHP5.

(I'm honestly not real sure if it's even working, because when I go to [http://localhost](http://localhost) Firefox asks if I want to download a .phtml file but that's not my question.)

**My question is, can I change the server root to my home directory such as /home/emotion.**

I changed the ServerRoot value in /etc/apache2/apache2.conf to /home/emotion but when I restart Apache it says that ServerRoot must be a valid directory.

](*,)

[COLOR="Gray"]I'm running Ubuntu Gutsy Gibbon 7.10 on an HP Pavilion dv2000[/COLOR]

---

### Post by Oldsoldier2003 on 2008-03-23
> **emotionlovesyou said:**
> I've just used Synaptic to install Apache2 and PHP5.

(I'm honestly not real sure if it's even working, because when I go to [http://localhost](http://localhost) Firefox asks if I want to download a .phtml file but that's not my question.)

**My question is, can I change the server root to my home directory such as /home/emotion.**

I changed the ServerRoot value in /etc/apache2/apache2.conf to /home/emotion but when I restart Apache it says that ServerRoot must be a valid directory.

](*,)

[COLOR="Gray"]I'm running Ubuntu Gutsy Gibbon 7.10 on an HP Pavilion dv2000[/COLOR]

yes you can change the document root. Edit /etc/apache2/sites-available/default and restart apache

```
sudo /etc/init.d/apache2 restart
```

---

### Post by emotionlovesyou on 2008-03-23
That might have worked, but [http://localhost](http://localhost) just displays a 403 Forbidden page.

[INDENT]You don't have permission to access / on this server.
Apache/2.2.4 (Ubuntu) Server at localhost Port 80
[/INDENT]
I've changed both ServerRoot in /etc/apache2/apache2.conf and DocumentRoot in /etc/apache2/sites-available/default to /home/emotion/Web which is where all my websites are kept.

---

### Post by rich86 on 2008-03-25
You need to set the permissions correctly set the folder group to the group found in apache2.conf (around line 120 you will find User: xxxx Group: xxxx  think the default is: httpweb. 
Also add yourself to the httpweb group in "users and groups"

That should work.

---

### Post by Kulgan on 2008-03-25
Just as a tip, it is by FAR easier to set up a local FTP server and use an editor with FTP capabilities (for PHP, ZDE is great) that messing around with the files. 
There's a tutorial for proftpd if you're interested:
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

After you've done it a few times, the entire process takes about 5 minutes.
-K

---

