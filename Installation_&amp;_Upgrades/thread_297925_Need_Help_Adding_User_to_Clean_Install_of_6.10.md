---
title: "Need Help Adding User to Clean Install of 6.10"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by ncc74656m on 2006-11-11
Hey Guys,

I'm a n00b around here, and something of an advanced n00b to Linux in general. I've fought Gentoo on many occasions, always to lose, and have successfully installed several other distros, though never used them for long. This is my first collective time using Ubuntu, and so I'm definitely out of any waters I know.

Anyway, I installed from the CD, and wound up never being prompted to add a user/password. ](*,) Since root is locked, I have no idea how I could go about setting up an actual user on this system.

Is there anything I can do, aside from doing a clean install? I just don't want to do that since it takes like two hours to do on this particular system.

Oh, and if I do have to do a clean install, for a n00b, should I stick with Gnome or KDE, or should I be bold and use xubuntu since this is an older laptop?

Specs:
PIII 650
64 MB RAM
12 GB HDD

---

### Post by taurus on 2006-11-11
Wait a second!  Did you use alternate CD to install Ubuntu on your machine?  If you are using the Dapper alternate CD, then you have to log in as oem with the password that you have created during the installing process.  Then, run "oem-config-prepare" to create a new user with administrative rights, sudo...  However, I would strongly recommand you use the xubuntu since you only have 64MB of RAM.  Running Gnome or KDE on that machine is not highly recommend and you will have it more when you try to open something!  Therefore, stick with XFce4 or do the server and install fluxbox.

---

### Post by ncc74656m on 2006-11-12
Thanks for the quick reply man. I tried using oem per your instructions, and that didn't work either. Instead I'm just going to burn xubuntu now and install a clean install off that.

I'll report back with my success when I'm done.

---

### Post by ncc74656m on 2006-11-12
Sorry, in more direct answer to your question:

Yes, I used the alternate install CD. I am using an Edgy install, AFAIK (6.10), and I'm not using a command line to install. I got to the login screen (running X and Gnome), but couldn't log in. No user name or anything I tried could log me in. Anyway, I'm installing xubuntu as we speak, and we'll see what happens this time around.

---

