---
title: "GRUB 21 error"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Gwendolyn on 2007-11-14
I've done a few searches and nothing is similar. I can use the live CD and install. I get the restart and all will be well and then *POW* Gruib Error 21.

It's an ollllldddd Athlon 1.5 thunderbird machine I had lying around in the basement. It's a clean 40GB harddrive. Windows XP (the origional) was working fine on it for a few days until I got around to installing Ubuntu 7.1


Trying to boot from the first hard disk using the CD brings me to the same error.

Uhhh do you need to know more? Any ideas? Help!


I'm not a complete noob but it's been 6 years since I've touched linux.

---

### Post by Gwendolyn on 2007-11-15
I've also tried the instructions found here:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
Finished that tutorial. Still getting error 21
*sigh*

---

### Post by Gwendolyn on 2007-11-15
OK! Now even when I boot with the live CD Gnome isn't installing properly. 

The hell?

---

### Post by Gwendolyn on 2007-11-15
I just tried the 6.06 and I'm having very similar problems only instead of a grub error it just rests and restarts the computer.

---

### Post by benjo3683 on 2007-11-15
[SIZE="4"][COLOR="DarkOrange"]Hi ....i need help.....i downloaded Ubuntu 7.10 i386 iso....burn it to CD then install to my Harddisk....when boot from harddisk ...Grub 1.5 error occur.....what is my next step....?????[/COLOR][/SIZE]

[SIZE="4"][COLOR="SandyBrown"]I tried on 

Pentium 4   2.4 Ghz   640 MB ram   GF440 64mb graphic card 

and

AMD 600 Duron 256MB ram    TNT AGP graphic card

Both also same Grub 1.5 error.

 [/COLOR][/SIZE]

---

### Post by meierfra on 2007-11-15
Gwendolyn:

Try SuperGrub:  [Hermanzone Info on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

If that did not work out, open a terminal (Applications->Accessories->Terminal) 
type 

```
sudo fdisk -l
```

and copy the output and post it here.

---

### Post by meierfra on 2007-11-15
benjo3683:  Please start your own thread. (otherwise things get too confusing)

---

