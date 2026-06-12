---
title: "ATi drivers"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by ELD on 2010-07-09
Ok before when i have downloaded and installed ATi drivers from their website it worked fine, but this time around it doesn't work at all, i get this from terminal:

> 
liam@liam-udesktop:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15
It seems to be in low graphics mode, scrolling in firefox is unbelievably slow :(

---

### Post by Mark Phelps on 2010-07-10
Would help if you would tell us what make/model is your video card.  If it's not one of the newer HD 3x/4x/5x cards, you're wasting your time because the current drivers won't work with the older, now considered Legacy, cards.

---

### Post by ELD on 2010-07-11
No need for the slight rudeness - i got it emailed before you edited it.

It is a HD 4850 not a legacy card.

---

### Post by ELD on 2010-07-12
Okay so i tried the ati config script and also get this:
> 
liam@liam-udesktop:~$ /usr/bin/aticonfig --initial
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
/usr/bin/aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.


Can someone help me figure out why it didn't install properly?

---

### Post by markbuntu on 2010-07-12
In the installer instructions it says you need to run aticonfig --initial as root after running the installer or the driver will not be properly intitialized and will fail to run. 

On ubuntu that means

sudo aticonfig --initial

You need to use sudo because users do not have permission to write to etc/X11/xorg.conf


You are also instructed to remove any already installed driver before installing a new one. This is too prevent a problem with kernel updates/upgrades where the new kernel build script comes across more than one set of kernel modules and so will not install any of them.

rtfm.

---

### Post by QIII on 2010-07-12
"RTFM"?

Wait.  I thought this was an Ubuntu forum not a Windows forum.

---

### Post by ELD on 2010-07-12
"rtfm" what an extremely hostile way to end what would have otherwise been a nice reply.

I did try it with root permissions using sudo to which i got the exact same result, as you can see from my reply it's not a problem with permissions or else it would have told me so, the problem it tells me is this "Bad file descriptor.".

---

### Post by markbuntu on 2010-07-12
Your previous post indicated that you did not implement the command as root.

> 
iam@liam-udesktop:~$ /usr/bin/aticonfig --initial


No need for the full path, just

sudo aticonfig --initial

You can also force aticonfig with sudo aticonfig --initial -f. This used to be a problem on a very few systems using 64 bit. "bad file descriptor" is the error you get if you do not run aticonfig as root. Permission flags are file descriptors. 

You also need to reboot before the driver will work, just reloading X can give you all sorts of weird problems. There are also some drivers that do not work with the latest Xorg release and some newer kernels so it is important to take a few minutes and read the release notes and installer instructions at the ati download page if you wish to avoid problems.

---

### Post by ELD on 2010-07-12
I did use the sudo command as i stated in my post, to quote myself:
"I did try it with root permissions using sudo to which i got the exact  same result".
If i hadn't tried it i wouldn't have said i got the same result, maybe i should have put "as well" in my post...

The command i entered is exactly why i got when i "rtfm" as you so childishly said, so i did "rtfm".

I did restart and i also know for a fact the drivers support the stable version of ubuntu's xorg.

I'm not exactly a newbie to this.

---

### Post by QIII on 2010-07-12
ELD --

I don't have time to do much searching, but have you tried looking through launchpad?  I know there are outstanding problems with the HD 4980 cards.  I wonder if you are running into something similar.

---

### Post by ELD on 2010-07-13
> **QIII said:**
> ELD --

I don't have time to do much searching, but have you tried looking through launchpad?  I know there are outstanding problems with the HD 4980 cards.  I wonder if you are running into something similar.

It should work fine, it has done perfectly before it's just this time around it seems to be borked, unless there has been an update since LTS has been out that broke it.

---

### Post by ELD on 2010-07-13
Sorry to bump again but nothing seems to work, what am i missing?

Edit > Well even though i had "installed" the latest drivers via atis website i used the hardware drivers manager to install them, rebooted and now i have it working properly and the control centre tells me i'm on 10.6 which is the latest...hardware drivers manager must install something lacking in the base ubuntu install?

---

### Post by ELD on 2010-08-06
Sorry to update my old thread but i found out what the problem was.

ATi 10.7 drivers added support for 10.04, i didn't realise they didn't support it before, they installed perfectly fine.

---

