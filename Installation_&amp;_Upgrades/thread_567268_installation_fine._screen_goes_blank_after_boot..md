---
title: "installation fine. screen goes blank after boot."
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by nk1t on 2007-10-04
hey there. Am a complete newbie. ive installed ubuntu 7.04 about 6 times now. formattin the drives again. no results... :(

at the first install. it worked fine. the shut down was erronous. a wierd sound and it got stuck. so had to go for an improper shutdown,

after reboot, it boots loads but goes blank at startup

installed it again ( 5 times). boots from live CD. installs fine. but after the reboot i see a blank screen again at the point i need to login.

compaq V6000
AMD turion 64(x2) mobile
1 GB RAM 
Geforce geo 6150
video bios version 5.51.28.42.44
force wear version 84.64

the comp was a windows XP original. with a seperate drive for recovery. i had to delete that drive to install ubuntu. people with the same comp/ processor without the original XP version are doin fine with linux. only i am facing a problem. please help.

---

### Post by mindtrick on 2007-10-04
When you get the blank screen press Ctrl + Alt + F1 to get a command line. 

Type "sudo dpkg-reconfigure xserver-xorg" to the line and hit enter. 

Choose "nv" for your graphic card. Go through other settings, finish it. 

Then restart or type startx.

---

### Post by nk1t on 2007-10-06
cant access the ctrl+alt+f1 screen.....no command thingy opens up.....:(

---

### Post by taurus on 2007-10-06
Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure xserver-xorg
```
When done, reboot with

```
shutdown -r now
```

p.s.  You need to log in with your username and password if you press <Ctrl><Alt>F1 (or F2) first before you can reconfigure your X.

---

### Post by pitbullcarfc on 2007-10-06
Hi, I have a Compaq Presario F566LA with nVidia GeForce Go 6100, AMD Turion 64, 1G RAM.... and have the same problem, after the Ubuntu loading screen the screen goes blank, but before the loading screen i can see a message like PCI: BIOS BUG, but i can't see the whole message, 'cause the screen changes to fast.. i tried to do the posted before but it doesn't fit it. When i run the live cd i have tu edit the boot command adding vga=792 for it to work, i also tried doing the same with the grub command but i doesn't work either... any idea of what i'm doing wrong?

---

