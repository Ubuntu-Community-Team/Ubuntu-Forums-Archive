---
title: "Xampp install"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by Geowilky on 2008-03-24
george@DualCoreRed1:~$ tar xvfz xampp-linux-1.6.6.tar.gz -C /opt
tar: xampp-linux-1.6.6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by dilaang on 2008-03-24
look if you are in the correct place... is xampp in your home?.. dont forget type sudo before uncompress.

---

### Post by Geowilky on 2008-03-24
It's in my desktop currently

---

### Post by Geowilky on 2008-03-24
george@DualCoreRed1:~$ sudo tar xvfz xampp-linux-1.6.4.tar.gz -C /opt
[sudo] password for george:
tar: xampp-linux-1.6.4.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors



This is what i get.

---

### Post by louieb on 2008-03-24
The Ultimate XAMPP thread for Ubuntu. This help me get XAMPP up and running, [HOWTO: (XAMPP) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=223410")

Sound like you are not in the same directory as the xampp tarball.

---

### Post by Geowilky on 2008-03-24
Yea, that was one of the first things I tried.  I've tried to extract into the /opt directory without success also.

---

### Post by crmoreira on 2008-04-20
Heya    ^^

@ Geowilky

Check the case spelling...  in my installation, desktop are correctly typed as Desktop, change the case that might probably work fine...


Regards...

---

