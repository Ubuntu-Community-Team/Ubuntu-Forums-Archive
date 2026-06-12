---
title: "After 14.04 update can't get to /var/www from net or localhost"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by cearlp on 2014-04-20
I was running 13.10 and had html files in /var/www that were accessible from the web via a static IP address or using localhost on the box itself.
After upgrading to 14.04 (successfully?) things seem okay, but from the web and from localhost all I get is Not Found errors. (The requested URL /xxx.html was not found on this server)
With just the IP address I get Index of /, the column headings, and the indication that it is Apache/2.4.7 (Ubuntu) Server at (IP address or localhost) Port 80.
The upgrade wanted to remove third party applications saying I could re-activate or re-install them later, (I think virtual box was a problem), but everything seems to be working as it did under 13.10.
What am I missing? 
I welcome any suggestions?

---

### Post by peter104 on 2014-04-22
Hello,

Having the exact same problem with 2 of my Ubuntu servers with web services. Cant find URL after upgrade. Everything looks normal (to my eyes) Would really appreciate some expert assistance :)

/Pete

---

### Post by tydfil2 on 2014-04-22
Same problem here!! Checked apache2 conf file and default directory still /var/www but cannot access any site there.

---

### Post by Danger_Monkey on 2014-04-22
I had a similar issue.  I looked at the 000-default virtual host.  It had the DocumentRoot as /var/www/html instead of /var/www.  Once I change that, and restarted Apache, all was well with the world again.

```

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www



```

---

### Post by tydfil2 on 2014-04-22
Thanks a lot.  Solved it for me and taught me a little about apache configuration!

---

### Post by cearlp on 2014-04-22
Okay, Thanks DM.

---

### Post by Iowan on 2014-04-22
> **Danger_Monkey said:**
> On mine, the /etc/apache2/sites-available/000-default.conf file had changed; the DocumentRoot pointed to /var/www/html after the upgrade.  I edited it to /var/www and it was able to "see" the web sites again.
^^^

---

### Post by peter104 on 2014-04-23
Hey guys,

A big thanks to Danger_Monkey. This worked perfectly on one of my 2 webservers. However, one is using https and i cant seam to find the correct virtual host. Would it be possible to get some help with this aswell? :) Thanks in advance.

Edit: Nevermind, some googeling did the trick :) I just needed to edit default-ssl.conf Same change as in the 000-default

/Pete

---

### Post by bruce-euphon on 2014-07-16
I cannot find that file in /etc/apache2. I just installed 14.04 on a laptop and only wish to use dwww for local docs on the loopback. The apache2 config shipped has changed from earlier releases and the package install for debian docs did not catch the change. The earlier configs expected the Document root at /var/www. It think it is shipped as /var/www/html, now.

---

### Post by bruce-euphon on 2014-07-16
OK, so I found the file and edited Documentroot to be /var/www. Now, it sees /cgi-bin/dwww but just displays the perl script. I suspect that my apache2 is unconfiged. Why would either the package install of debian document browser not find the dependancy and config the web server if it needs to?

---

### Post by lingkon on 2014-09-07
Create a directory under the www directory and name it html.Then put your project under the html directory.Its working for me.

---

### Post by Xiguus on 2014-09-22
I have a similar problem to the cases described here.
I'm running 14.04 from a clean install and am running dwww via from Netsurf, an arrangement that worked on my previous 12.04. Location bar shows eg
```
http://<user_name>/cgi-bin/dwww/usr/share/doc/apt-doc/offline.html/index.html?type=html
```
and the browser is giving me the message
```
The requested URL /cgi-bin/dwww/usr/share/doc/apt-doc/offline.html/index.html was not found on this server.
```
with the status line
```
Apache/2.4.7 (Ubuntu) Server at <user_name> Port 80
```
I've checked the conf files as indicated, and 000_default.conf has DocumentRoot at /var/www as required above, while default-ssl.conf had /var/www/html, which I edited as suggested. I'm still getting the same error message. Firefox gives me the same problem, so it's not a browser issue.
Any suggestions?
Thanks.

---

### Post by Xiguus on 2014-09-24
Following up from my previous:
```
$ apache2ctl -k start
```
gives me
```
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message

```
Wisdom of the web is that this is an advisory, not an error. However, putting
```
ServerName localhost
```
into /etc/apache2/apache2.conf at line 69 suppresses the message.
Now, /usr/lib/cgi-bin/dwww has, at line 7:
```
#  (if you are using apache2, please run `a2enmod cgi')
```
(The hash is a comment indicator, not a root prompt.)
So, execute the program as root:
```
$ sudo a2enmod cgi
```
*Provided* apache2 is running (eg as above) dwww now starts in the directory pointed to by doc-base settings in .conf files, eg /var/www/dwww, and can access all documents as required.
BTW my understanding of /var/www/html is that it contains an apache status file, "if you can see this your installation is working".
So all that remains to have a fully-functioning dwww is a running apache server, eg enabled at startup.
BR...;) ;)

---

