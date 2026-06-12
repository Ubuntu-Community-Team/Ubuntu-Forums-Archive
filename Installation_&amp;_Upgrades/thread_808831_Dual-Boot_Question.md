---
title: "Dual-Boot Question"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by dbodoh on 2008-05-26
Hello, Im currently using Windows XP sp3.  I would like to switch to Ubuntu exclusively, but i enjoy playing games to much.  So i have a few questions.    

1.  For dual booting, i have read the guides on how XP/Ubuntu installation is suppose to be, and i was wonder on how do u switch between the 2 operating systems.

2.  The windows emulators(VMplayer), do u get a performance loss, and if so how much.  I play WoW, which performance isnt that big of a deal, but i also play FPS's where performance is key.

3.  I have a laptop also, with Windows MCE sp2, would that have any issues with dual booting Ubuntu?

4.  I used Linux(Fedora Core 2), and was wondering...is it still that difficult to install a program...?

---

### Post by Pumalite on 2008-05-26
1.-Grub gives you a menu where you can choose.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by dbodoh on 2008-05-26
That comes right with the SuperGrub install?

---

### Post by Pumalite on 2008-05-26
That comes with Ubuntu. The best boot loader around.

---

### Post by dbodoh on 2008-05-26
Will partition magic allow me to make a partition? or do i have to pay for the full version?   Whats a decent partition for linux counting  install/updates, other stuff.    Any info on is it any easier to install?

---

### Post by Pumalite on 2008-05-26
Are you using XP or Vista?

---

### Post by dbodoh on 2008-05-26
XP sp2 for desktop, and Media Center Edition sp2, for laptop

---

### Post by Pumalite on 2008-05-26
Gparted Live CD is your best bet:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP and choose 'resize'. A good scheme is:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home

---

### Post by dbodoh on 2008-05-26
what do u have to do to install programs and such...i remember having to type in multiple commands to install a simple program..  is it still this complicated, or is it now one of the few nice features windows has?

---

### Post by Pumalite on 2008-05-26
You can do it through a Package Manager (Synaptic) or the Terminal:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

