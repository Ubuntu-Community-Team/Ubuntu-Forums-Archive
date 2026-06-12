---
title: "Blank Screen"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by theerga on 2005-05-01
I get a blank screen while booting ubuntu after a installing it as a second os on my master hard drive what should i do

---

### Post by defkewl on 2005-05-02
Did you install grub?
Check /boot/grub/menu.lst make sure it has the same information with /etc/fstab to tell where it should boot up and everything :)

---

### Post by theerga on 2005-05-02
yes i have grub while installing it gose tall the way to a blank comand prompt with nothing but an insertion point the keyboard and mouse wont work either i restart a try to boot in ubuntu and all i get is a blank screen

---

### Post by alastair on 2005-05-02
So - explain :

Grub is installed but does not work?

Do you get a GRUB menu?

What type of hardware (disks) do you have? ATA,SATA?

Is your disk primary master? or how many disks? GRUB on which disk?

---

### Post by theerga on 2005-05-02
grub works
I have ata
and its a primary or master drive i have it on i have 2 hds and grub is theon the master.

---

### Post by krinor1966 on 2005-05-03
I experienced the same ... do you have a flat LCD screen as well ?

Anyhow, this is what I did after a lot of browsing and "hard work" (for a  newbie)

I rebooted in Fail Safe mode and then I typed gdm and by doing so I got my empty screen i.e. there was something in the gnome desktop manager startup that didn't work.

So back in fail safe mode I typed dpkg-reconfigure xserver-xorg and by doing so I "reinstalled" peripherals like monitor and keyboard etc. 

First I tried to settings the the Live CD used (had printed that) but that didn't work (ATI driver for some reason), then I chose the Vesa driver (I recalled I'd seen it somewhere on the net) and "Behold", the screen worked on reboot (even though I experienced a bottom on top/top on bottom separation after fisrt boot).

It is a bit slow in updating the screen, but at least it works.

So, to sum up:

Check if it is gdm that causes the blank screen by ininate it in failsafe mode (just type gdm

Try to reconfigure by using dpkg-reconficure xserver-xorg in failsafe mode, and try to select Vesa or any other driver that might make sense to you and see if that works.

Kman

---

### Post by theerga on 2005-05-04
thank this helped alot time all i need to do now is figure out the right driver

---

