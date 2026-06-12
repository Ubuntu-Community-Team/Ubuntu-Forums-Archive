---
title: "Howto launch GUI Desktop from commandline?"
date: 2005-09-18
forum: Installation &amp; Upgrades
---

### Post by Palug on 2005-09-18
Well my warthog installed nicely on my laptop.  Now when I boot from the hard drive I come to the command line.  How do I start the GUI desktop from the commandline?  I am lost at the command line.

Thanks.

---

### Post by mlomker on 2005-09-18
Well, that's not normal--it should boot into the GUI automatically.  Perhaps you did a server or expert install and didn't install a GUI?  You could try **startx**.

Try **apt-get install ubuntu-desktop** to install gnome or **kubuntu-desktop** to install KDE.

---

### Post by Palug on 2005-09-18
Thank you for the hints, I will try them now!

---

### Post by Goldberg on 2005-10-11
Hi

First of all thanks for a brilliant forum :) This is my first post.

I have used Linux at uni 5 years ago! And have just built a machine out of old parts and stuck Ubuntu 5.04 on :)

First impressions very very cool! But 1 big problem!

2 nights ago I 'logged out' of the GUI. Now I can't get back in?

When I reboot I get the black shell/dos looking screen. I log in and type 'startx' but it does not recommend it?

anyhelp?

Thanks in advance.

---

### Post by mlomker on 2005-10-11
> When I reboot I get the black shell/dos looking screen. I log in and type 'startx' but it does not recommend it?


You'll want to post the exact error message.  You could check the /var/log/Xorg.0.log file for errors if it is trying to load.

---

