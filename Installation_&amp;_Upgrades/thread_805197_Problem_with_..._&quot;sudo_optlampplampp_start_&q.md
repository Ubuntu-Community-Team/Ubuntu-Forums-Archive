---
title: "Problem with ... &quot;sudo /opt/lampp/lampp start &quot; (XAMPP)"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by Muzze on 2008-05-23
Hello guys, I'm new
Look this is my problem.

When i put in the terminal the command sudo **/opt/lampp/lampp start**
downside said:

[B]XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Another FTP daemon is already running.[/B]
XAMPP for Linux started.

How can i stop the other process

I tried stopping the all process and restart, reinstall, etc.

Help Please, Thank you-

PD: Sorry for my english

---

### Post by h_kerrigan on 2008-05-24
I have the same problem, can anyone help?:confused:

---

### Post by KC_Ransom on 2008-07-15
I just installed Xubuntu on an old desktop myself. I think if you simply go to the opt/lampp directory and stop everything, you should be fine::guitar:

> cd /opt/lampp
> sudo ./lampp stop

Then your should see the various pieces stop, with Apache being the last one.
Your problem might be that you are not doing this as root, therefore always use the sudo command as a prefix to anything you do with lammp administration.

Good luck,
KC

---

### Post by vivalavisca on 2011-04-24
sudo /opt/lampp/lampp start

&

sudo /opt/lampp/lampp stop

---

