---
title: "[SOLVED] Ubuntu 7.10 does not get to desk top"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by Roy :-) on 2008-01-03
Grub starts Ubunt, shows the Ubuntu Logo with orange bar then goes to text mode and stops at
"Running local boot scripts(/etc/rc.local)"

It does not continue to the ubuntu graphics desktop.

Is there somthing I need to do at the Grub level?

or if I press Esc key it asks for a login & password.

After completing the login password it still sits at a text level - how do I get to the graphics enviroment?

I have a pentium 3 system.

---

### Post by Partyboi2 on 2008-01-03
to start xserver
```
startx
```

---

### Post by Partyboi2 on 2008-01-03
When I have run into this problem in the past I have been able to boot into recovery and had the option to fix xorg. Which fixed my problem.

---

### Post by Roy :-) on 2008-01-03
Thanks for the reply.

After going CTRL ALT and Fx to select a terminal window and then logging in I typed "startx", then I receive a "Fatal server error" and "no screens found".

Now what???? :(

Also how do I use the suggested xorg????? :confused:

---

### Post by teetii on 2008-01-03
you could try to reconfigure your xorg.conf by
**sudo dpkg-reconfigure xserver-xorg**

It makes backup your current xorg.conf, but if you feel like it, backup it beforehand. (found in /etc/X11/xorg.conf )

all you need to know is what display driver you want to use, and almost everything else is suggested almost right :)

---

### Post by Roy :-) on 2008-01-03
In ubuntu recover I typed
dpkg-reconfigure xserver
but ubuntu said xserver is not installed.

then tried
dpkg-reconfigure xorg
nut nothing apeared to happen.

tried 
dpkg-reconfigure xserver~xorg
but had xserver~xorg is not installed

what next :confused:

---

### Post by Partyboi2 on 2008-01-03
what happens if you try and install xserver-xorg
```
sudo apt-get install xserver-xorg
```Then try
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Roy :-) on 2008-01-04
Thanks for your help.

Have solved the problem, installed a better graphics card and reinstalled ubuntu - yay we are in.

---

