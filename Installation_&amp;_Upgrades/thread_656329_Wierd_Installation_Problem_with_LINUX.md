---
title: "Wierd Installation Problem with LINUX ?"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by arvin88 on 2008-01-02
Hey !

**PC Specifications :**

I have Pentium 4, 1 GB RAM , 64 MB Video Card. I just now bought a new 250GB Hard disk, I also have a 40 GB Hard Disk as slave.

[ more Details about my PC](http://h10025.www1.hp.com/ewfrf/wc/product?cc=pe&lc=en&dlc=es&product=421470)

I have Ubuntu ( 5 , 6 and Even 7.04) , Freespire Linux versions. When ever i am trying to install Ubuntu Linux (V 5), system reboots automatically. I tried installing new versions of Ubuntu and Freespire, i m getting a black screen with some message like this " INT 0005399 STACK err0000000.....blah bla  ".

I tried Live CDS of Ubuntu and other linux versions, still having the same problem. Also tried starting Linux in Safe Graphics Mode. But no use..!

I have Installed Linux in Pentium 3 with 256 MB ram, but why it is not working with P 4 ?

---

### Post by arvin88 on 2008-01-02
It seems this is a common error with Compaq Pesario systems

Anyway this is the error :

Int 14: cr2 cf800000 err00000000 eipc020c384 cs00000060 flags00010007
stack: c00f7da0 c03f129b c0371d8c 00000002 c00f7da9 000f7da0 00000000 000000000

---

### Post by arvin88 on 2008-01-02
I have Compaq Pesario SR1130IL


[IMG]http://i82.photobucket.com/albums/j264/Airforce_sf/UbuntuError.jpg[/IMG]

Screen shot of Image

---

### Post by arvin88 on 2008-01-02
I found a solution from this forum : "linux acpi=off maxcpus=0" . It did work, but after installation... when i did the first reboot...i didnt get a boot screen with xp then when i clicked ubuntu os, i got the same error.

[SIZE="6"]Please help me[/SIZE]

---

### Post by Partyboi2 on 2008-01-02
You will need to add "linux acpi=off maxcpus=0" to your grub menu.lst so that each time you boot it will use those boot options.
Open up grub menu.lst
```
gksudo gedit /boot/grub/menu.lst
```look for some lines like this
```
 ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
[COLOR=Red] # defoptions=quiet splash[/COLOR]
```Where you see the line
```
 #defoptions=quiet splash
```at the end of the line after splash add
 ```
linux acpi=off maxcpus=0
```save and close
In a Terminal (Applications>Accessories>Terminal)
```
sudo update-grub
```

---

### Post by arvin88 on 2008-01-03
Now i am able to install linux, but i get a new error...! when i shut down...!

I get this ubuntu Logo with the loading bar comes to end...! but nothing happens after that..!! the page freezes...!

---

### Post by Roberterher on 2008-01-03
I have a Compaq presario also, I get the same error, although everything works for me with "acpi=off" on the boot promt on the cd.
Hope you get rid of the errors :)

---

### Post by Partyboi2 on 2008-01-03
Try adding acpi=force to your 
/boot/grub/menu.lst as well, has worked for some.

---

### Post by arvin88 on 2008-01-06
acpi=force ....that made ubuntu not bootable.... 

my current acpi=off . But this makes my shutdown incomplete, loading bar becomes complete...but system is not shutting down. 

if i edit the acpi by removing it...i m not able to login to linux.

---

### Post by Partyboi2 on 2008-01-06
There is a known bug with ubuntu not shuting down properly.
[http://ubuntuforums.org/showthread.php?t=591229](http://ubuntuforums.org/showthread.php?t=591229)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308)

---

