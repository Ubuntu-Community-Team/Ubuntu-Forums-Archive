---
title: "Dokuwiki works from localhost, not over LAN"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2008-01-12
I installed Dokuwiki on Feisty, using synaptic package manager.  

It works  when I access as localhost from the Ubuntu box.  It didn't work locally when I accessed as the hostname, despite having the 127.0.1.1 entry with the hostname in /etc/hosts.  When I added the hostname to the 127.0.0.1 line, I was able to access locally by name.

When I try to access from the LAN, whether by name or IP address, or by name from the Ubuntu system, I get error 403.  

There was no link in /var/www for dokuwiki after the installation, so I don't understand how [http://localhost/dokuwiiki](http://localhost/dokuwiiki) finds the files.  I created a link, but it doesn't make any difference.

I have other PHP applications running fine on the system.

Any help greatly appreciated. Thanks!
Mike

---

### Post by NewKindaArt on 2008-02-27
Assuming you are using apache2...

in /etc/apache2/conf.d you will find a file called "dokuwiki.conf" which reads:

```

Alias /dokuwiki         /usr/share/dokuwiki
<Directory /usr/share/dokuwiki/>
        Options +FollowSymLinks
        AllowOverride All
        order allow,deny
        allow from 127.0.0.1
</Directory>

```

The Alias line is how it finds the files

change "allow from 127.0.0.1" to "allow from All" when you're ready to go

be sure to have locked everything down before you do this!  visit the dokuwiki security page

don't forget to do a "sudo apache2ctl restart" after you change the .conf file to make it take effect

---

### Post by 5circles on 2008-02-27
Thanks for the explanation about the configuration.  The file is exactly as you wrote.

I ended up moving to WordPress, in part because I couldn't find a solution.  But I may go back. 

At least I understand the configuration now!

---

