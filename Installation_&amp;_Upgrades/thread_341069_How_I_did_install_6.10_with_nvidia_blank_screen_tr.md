---
title: "How I did install 6.10 with nvidia blank screen trouble"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by rpradeep on 2007-01-18
After trying several times to install edgy on HP Visualize X class with nvidia quadro I always end up with blank screen with stuck machine.

So i decided to check the nvidia driver comes in the iso. I downloaded the alternate install CD and the install was painless except the machine stuck during gdm as usual (expected). After that i rebooted the machine with live cd 6.06 and mess up with /etc/X11/xorg.conf file so the x server wont start.

Now rebooted my machine with the error regarding the xorg.conf file. OK now go to another console ALT+CTRL+F2 stop gdm sudo /etc/init.d/gdm stop.

Go to the directory where i downloaded the nvidia drivers from the nvidia web site.

install the driver

sudo dpkg-reconfigure xserver-xorg

select the driver as nvidia (not nv)

restarted gdm. WOW for the first time i was able to log into 6.10

Hope this helps someone.

---

### Post by Pobega on 2007-01-18
Congratulations!

I personally think ways to get the video card working in Linux should be available in a sticky in the Absolute Beginner's Forum, since if your video card doesn't work and if you're new that is where you'd be posting.

---

