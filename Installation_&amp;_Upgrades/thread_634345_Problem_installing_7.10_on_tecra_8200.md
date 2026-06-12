---
title: "Problem installing 7.10 on tecra 8200"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by Warpedflash on 2007-12-07
i am currently trying to install ubuntu 7.10 on an old toshiba tecra 8200 laptop.

now the problem: I cannot get into the gui, of the live CD. I start and whether i choose safe graphics or normal install mode the laptop wont display the desktop.
The top 1/2 of the screen is blue with squares of other colors (looks corrupr type thing) and the bottom 1/2 is just black. i know the desktop boots as i get the startup sounds...
any help would be appreciated
Thanks :)
warpedflash

---

### Post by Pumalite on 2007-12-07
Post specs. 256 MB of RAM or less> Xubuntu Alternate CD.
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Pumalite on 2007-12-07
You can boot a Live CD and install a heavier system if you make a 500 MB /swap partition ahead of time. You can use Gparted Live CD for that.

---

### Post by Warpedflash on 2007-12-07
> **Pumalite said:**
> Post specs. 256 MB of RAM or less> Xubuntu Alternate CD.
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

SPECS (APPROX)
512 ram
1ghz pentium III (or 800mhz)
30 gig hdd

its easily good enuf to run ubuntu as the one i use atm has worse specs and runs it great. its as far as i can tell a graphic card problem... but no idea what or how to fix it...

---

### Post by Pumalite on 2007-12-07
Hit F6 and add  pci=noacpi to the boot parameter.

---

### Post by kanketsu on 2008-02-17
Hi, excuse me for bringing this up again. I got the same problem, but it was solved eventually by adding the pci=noacp to the boot parameter.

However, I'm confused to read this line at:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba)

"After installation add pci=noacpi to the kernel commandline in /boot/grub/menu.lst to fix this permanently."

Where exactly should I put the pci=noacpi in that file?

---

### Post by Pumalite on 2008-02-17
At the end of something similar to this:

kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=74c86936-3364-4efd-b34a-fe8459d7eeda ro quiet splash

In other words, the kernel line.

---

### Post by kanketsu on 2008-02-17
Thanks. But now I can't save the change... 

Could not save the file /boot/grub/menu.lst
You do not have the permission necessary to save the file.
Please check that you typed the locaton correctly and try again.

---

### Post by some1l8 on 2008-05-25
login with root

---

### Post by durand on 2008-05-25
To edit the file as root, use
```
sudo nano /boot/grub/menu.lst
```

---

