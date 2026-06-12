---
title: "login screen too big to fit after upgrade to 8.04"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by ubnewbie2 on 2008-04-30
I upgraded last night, and ever since, the login screen is too big to fit the screen.  Luckily, enough is visible to be able to see enough that I can still actually log in. I am using the standard human theme it defaults too.

Changing the screen in system administration doesn't fix it.

How can I get it to fit?

---

### Post by hermes0710 on 2008-04-30
> **ubnewbie2 said:**
> I upgraded last night, and ever since, the login screen is too big to fit the screen.  Luckily, enough is visible to be able to see enough that I can still actually log in. I am using the standard human theme it defaults too.

Changing the screen in system administration doesn't fix it.

How can I get it to fit?

Go to System > Administration > Login Window and try to reapply the theme

---

### Post by albert.neu on 2008-04-30
Hi!

I can confirm these problems:

1) ubuntu upgrade 8.04 login screen is too big
2) Xnest does not work, Xming does not work

Solution:

edit /etc/X11/xorg.conf e.g. with this command
sudo gedit /etc/X11/xorg.conf

and change the resolution to something appropriate. 

I changed it from 
Virtual 1680    1050
to
Virtual 1280    800




ref:
[http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)

---

### Post by ubnewbie2 on 2008-04-30
> **albert.neu said:**
> Hi!
Solution:

edit /etc/X11/xorg.conf e.g. with this command
sudo gedit /etc/X11/xorg.conf

and change the resolution to something appropriate. 

I changed it from 
Virtual 1680    1050
to
Virtual 1280    800




ref:
[http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)


Yes, this fixed it.  Thank you very much

---

### Post by herger on 2008-11-13
Thanks!
That works perfectly!
In my Dell XPS I put 1280x960, but it's the same.
Thanks a lot

H

---

