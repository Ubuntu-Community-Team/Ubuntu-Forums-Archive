---
title: "Scrambled Video on install"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by gnat60 on 2007-08-30
Hi there,

Well I decided to jump ship (off the ss microsoft) and take refuge with Ubuntu. Being fairly familiar with DOS and Windows I thought this would be a snap, however....

I am having grief trying to install Ubuntu 7.04 Desktop. The video gets all garbled during the install and I get no further. My system is:

AMD Athlon XP 2000+
ATI All in Wonder 9600XT - 128MB
Over 80GB free space on 2 drives
1GB RAM

Any help out there?

Thanks

---

### Post by Pumalite on 2007-08-30
Do you have a command line?. If not, try Ctrl+Alt+F1. If you get a command line: sudo dpkg-reconfigure xserver-xorg, choose most defaults, choose 'vesa' as your driver. Then: startx

---

### Post by gnat60 on 2007-08-30
Thanks Pumalite, I will try it and get back to you.
:)

---

### Post by gnat60 on 2007-08-30
Well I'm back.

I tried what you suggested and I did get a command prompt.
I went through all the questions and chose "Versa", answered a few more questions then it returned me to a command prompt where I then entered: "startx" (no quotes of course) and then it returned the following:

Fatal Server Error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.x0-lock and start again

Well from there I was completely stumped so here I am again :)

Next?

---

### Post by Pumalite on 2007-08-30
Well, lets do this: at the prompt, sudo /etc/init.d/gdm stop
Then try sudo dpkg-reconfigure xserver-xorg again (driver is vesa)
If it doen't work, maybe you should try Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) Check box below 'Start Download'

---

### Post by gnat60 on 2007-08-30
OkeeDokee,

Will give it a shot.
Thanks again....

Back in a few moments with the result (unless of course it starts installing and hence takes up time)

---

### Post by Pumalite on 2007-08-30
I thought you ended up with garbled graphics AT THE END of the install. If it's not that, then you should just go for the Alternate CD.

---

### Post by gnat60 on 2007-08-30
Okay then....

I tried it and no happiness there. I will now download the alternate CD.

Sorry about the confusion, hopefully if I can install the damned thing I will be able to work around other issues without having to reboot, my 3 fingers are getting sore :)

---

