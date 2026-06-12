---
title: "php/mysql error"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by ehajj on 2006-10-27
**[COLOR="Green"]Well I installed apache, php and mysql from synaptic package manager. Now I started Apache, and I tried to open a php page but it dosn't open. I guess I did not start php or mysql. Can anybody tell me how to do that??[/COLOR]**

---

### Post by DaveBorealis on 2006-10-27
Hello,

What kind of error messages do you get?  You could look in the httpd-error.log, which is found in /var/log on my FreeBSD system.

You shouldn't have to start php, but I believe that MySQL should started along with Apache.  On my box the command 'ps axx | grep mysql' shows that MySQL is running.  Try it on yours and see if anything lists for it.

Best regards,
Dave

---

### Post by ehajj on 2006-10-27
[COLOR="Green"]**Dave, I just installed all of them, and when I try to access a php page on my server, I get problem opening this page. But if I run an html page it works normally.**[/COLOR]

---

### Post by Max Luebbe on 2006-10-27
You need the apache modules installed in addition to just having PHP and MySql installed.

Look for packages that start with mod, such as mod_php.

If these are there, you are experiencing problems with apache directives and need to set up a handler for php files.

Hope that makes sense.

---

### Post by ehajj on 2006-10-27
**[COLOR="Green"]I don't have in my Synaptic Package manager something called mod+php, I have PHP5 which I installed. If I need to set up the apache directives can you help me up here, cause I am new to linux, and I don't know what these are.[/COLOR]**

---

