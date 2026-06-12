---
title: "how to completely Uninstall apache and apache2"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by jactheman on 2007-01-23
I need some help I have ran the following command:
sudo apt-get install apache2 apache2-common apache2-mpm-prefork apache2-utils ssl-cert

But when my apache2 tries to start I get a message saying it failed because it is missing 
/etc/apache2/apache2.conf

How Can I uninstall apache and all its modules and do a clean install that will overwrite all my conf files the thing is that I try 
sudo apt-get remove apache2 apache2-common apache2-mpm-prefork apache2-utils ssl-cert

and remove my apache2 folder from /etc
??????

and reinstall it using the first command noted but again I get the message above .... apache2.con missing...

---

### Post by djf_jeff on 2007-01-23
You can try to do :

apt-get remove --purge apache2 apache2-common apache2-mpm-prefork apache2-utils ssl-cert

I don't know if it will help. Come back to give the results if you have the time.

---

### Post by jactheman on 2007-01-23
you are good ... it did fix the problem thanks a lot.

---

### Post by BillRebey on 2007-02-17
djf_jeff, Thanks!  I had the same problem, and toiled with it for hours, wearing out Google in the process, and I finally stumbled across your answer.  Apparently, that very specific list of things to remove is the key.  I thought I'd removed, autoremoved, and purged just about everything I could think of, but apparently I missed something.  I know I never removed the ssl thing.  Maybe that was key.  I don't know exactly what the deal was, but I'm not processing PHP correctly.  

Thanks again!

...now if only I could get MySQL working....

---

### Post by macewan on 2007-02-23
This is completely ridiculous. I've been dicking with this L.A.M.P. problem on Edgy for a couple of days. Never had this much trouble before.

Has anyone step by stepped this for others yet?

---

### Post by hasmind on 2007-08-25
hey all,

I was trying to figure out how to compile stuff in linux, so I got Apache's source and went through the whole process of compiling and installing. Thing is that Synaptic Package Manager didn't realize it. I wanted to do a clean install of Apache, but I have absolutely no idea how to get rid of it.  it installed in /usr/local/ so I can't just delete everything. djf_jeff's thing obviously did something,  but It still had no obvious effect. Should I just log in as root and delete everything, or is there some obvious thing you're meant to do that I haven't realized?

---

