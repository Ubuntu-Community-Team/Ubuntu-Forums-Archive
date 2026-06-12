---
title: "Super User Trouble With ATI"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by jakeiscrazy on 2008-07-03
OK so iv been have so screen flicker problems that i think are related to not have the correct driver. So i went to the ATI website and got the driver. I ran it in terminal and it told me I have to be Super User. The problem is it open a new terminal window each time so I'm not able to login in as root. if the file is in /home/jake/desktop/ and the filename is ati-driver-installer-8-6-x86.x86_64.run what command would I use.

---

### Post by griffinjones on 2009-06-21
I too am trying to install the ATI driver, same one.

I have this problem as well...It's like after realizing I have to be a superuser to install it, the ATI Driver reconfigured what my authentication is.

---

### Post by Mark Phelps on 2009-06-21
If you're going to install drivers in Linux, this is not MS Windows --- the first thing to learn to do is read the instructions.  I believe there is a text file in the download named something like installer, or install, or something like that.  It provides step-by-step instructions on what to do.

As to Super user, it's called root. and you have to open a terminal and type "sudo -i" and supply your password.  You know when you've switched from general user to root when your terminal prompt changes from "$" to "#".

---

### Post by griffinjones on 2009-12-28
> **Mark Phelps said:**
> If you're going to install drivers in Linux, this is not MS Windows --- the first thing to learn to do is read the instructions.  I believe there is a text file in the download named something like installer, or install, or something like that.  It provides step-by-step instructions on what to do.

As to Super user, it's called root. and you have to open a terminal and type "sudo -i" and supply your password.  You know when you've switched from general user to root when your terminal prompt changes from "$" to "#".

Sudo, indeed, solved the issue. I have trouble accepting the no longer supported universal su command though in modern ubuntu.

---

