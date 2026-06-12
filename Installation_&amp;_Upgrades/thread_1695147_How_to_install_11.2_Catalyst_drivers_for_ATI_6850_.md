---
title: "How to install 11.2 Catalyst drivers for ATI 6850 - short GUIDE"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by SkyHiRider on 2011-02-25
DO NOT USE the official drivers from Canonical if you have ATI 6850 HD, IT WILL BREAK YOUR SYSTEM (I know, I tried)

This worked for me and my 6850 card, each line is a single line in the terminal.

```
su
apt-get install libqtgui4
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run
apt-get install dkms
sh ati-driver-installer-11-2-x86.x86_64.run --buildpkg Ubuntu/maverick
dpkg -i *.deb
aticonfig --initial
```

This has been done on a newly installed 10.10 64 bit version on Ubuntu and I am still alive and kicking while writing this post.

Cheers,
Sky

---

### Post by sannder on 2011-03-12
Hello, SkyHiRider.
 I am new as user of linux and I would be charmed with a bit of helping since I see that you know on the problem of the ATI 6800 series.

 I have also 6850 and and installed Ubuntu 10.10 from zero and and followed your steps. (I have put password to root to enter like root).

 And I write the command as you have written them your.
 And ultimately I have problems with:
fglrx
fglrx-connon or seemed 
fglrx - _____

 In the step
dpkg -i *.deb

I wait to have explained well I am Spanish and do not have a good English and in the Spanish forums nobody gives me support.
 Not the only thing that need is to use the resolution 1920x1080.
Please help me.

Edit:
I have a 64bits and the default kernel in Ubuntu 10.10 .

---

### Post by Nospoonzz on 2011-04-07
To the poster at the top of page. THANK YOU ! ! ! ! ! ! !   I followed the instructions and
now have FULL 3D acceleration. It worked perfectly except. I used sudo instead of su 
when entering commands in the terminal.:P

---

### Post by OzCrossfire on 2011-04-30
Thank you Sky worked perfectly with a ASUS EAH6850 on Kubuntu 10.10 after removing nvidia drivers from a previous card.  There has been an update to version 11.4 now so an easy mod to the driver link.

Cheers

---

