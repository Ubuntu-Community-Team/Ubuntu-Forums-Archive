---
title: "Installing ubuntu on a laptop and desktop"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by parkland on 2007-12-20
Hi, i just was hoping for a little direction. 

I have a AMD 64 bit desktop, 80gb, 512mb that already had ubuntu running on it, along with windows. 
When i reinstalled windows, it f'd up the boot loader, and now i'm gonna reinstall ubuntu.

I also just got a LG laptop, 2.2Ghz centrino duo, 4 GB , 200GB, 256 video nvidia, etc...

I downloaded linux ubuntu 7.10 desktop amd-64 iso, wich is supposed to work for amd/intel 64 cpu's. 

Any steps to make it run on the laptop with the duo?

thanks in advance.

Barely know anything about linux.

---

### Post by Pumalite on 2007-12-20
You can use 32 bit or 64 bit. On your Desktop, you can reinstall Ubuntu:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
On your laptop, try and see. Post with any problems.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by parkland on 2007-12-20
yeah, i probably will "rescue" my current desktop ubuntu, but after backing up files, i'm gonna install the newest one.


I have the 7.10 ubuntu 64 bit, so fine. that should work for both, but will it work for the centrino duo? 

I heard i might need an "SMP" kernel?

---

### Post by Pumalite on 2007-12-20
If you have two cores in your processor; SMP is installed by default.

---

### Post by igknighted on 2007-12-20
> **parkland said:**
> yeah, i probably will "rescue" my current desktop ubuntu, but after backing up files, i'm gonna install the newest one.


I have the 7.10 ubuntu 64 bit, so fine. that should work for both, but will it work for the centrino duo? 

I heard i might need an "SMP" kernel?

The default kernel is 'generic', which has SMP support built in.  Back in the Dapper days you did need to manually select an SMP kernel to use both cores, but we've come a long way in 2 years :).

That install disk should work fine with the centrino duo.  If it won't work you will know in the first 10 seconds of booting the liveCD, so theres really no risk.

One final thought... if you have Vista on the laptop and plan on keeping it to dual boot, do not use Ubuntu's partition tool to shrink the Vista partition, it will probably ruin your Vista install.  I think Vista has a tool built in that can do it, so try that instead.  Ubuntu's tool can overwrite anything and re-size Windows XP and early perfectly.

---

### Post by parkland on 2007-12-20
thanks guys, if i have anything interesting to say, i'll post it here.

---

### Post by Pumalite on 2007-12-20
pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
pumalite@pumalite-desktop:~$

---

### Post by igknighted on 2007-12-20
> **parkland said:**
> thanks guys, if i have anything interesting to say, i'll post it here.

Oh it doesn't have to be interesting, but those are always welcome too.  Hell, this post isn't interesting...

---

### Post by Pumalite on 2007-12-20
I bet is interesting to the OP.

---

### Post by parkland on 2007-12-20
I downloaded the 7.10 live cd, burned it with nero on a cd/rw, 

Booting the cd, and the desktop says "CD error".

the laptop boots up, and then i go to "start/ install " , then i get the low resolution message, when i press continue, i just get a black screen.

I tried the low-res graphics, same thing. 

I tried re-burning the CD, same thing.


.........?

---

### Post by Pumalite on 2007-12-20
Use Super Grub then: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by parkland on 2007-12-20
i'm gonna try finding a blank CD, instead of the cd/rw.....

mabye that will work better...

---

