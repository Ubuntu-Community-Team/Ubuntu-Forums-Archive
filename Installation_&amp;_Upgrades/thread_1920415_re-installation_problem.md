---
title: "re-installation problem"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by TXbirder on 2012-02-04
I have a computer with 2 hard drives.  I have had Win7 on one and Ubuntu 10.04 on the other for a couple of years.  Until recently, when I started the computer, after the BIOS screen, I'd get a Grub(?) screen that let me choose between Win7 and Ubuntu.
 
I recently had to replace the hard drives which meant clean installs of both OSs.  Now, when I start the PC, Win7 opens up immediately with no option of opening Ubuntu.  As far as I know, Ubuntu is on the 2nd drive. It seems to have installed OK.
 
How to I get the screen that lets me chose which OS to open?  
 
John

---

### Post by Azxff on 2012-02-04
There are probably a number of ways to solve this. I guess you put Win 7 on the primary master drive and Ubuntu on the slave...Simply switch them temporarily and after starting ubuntu start start up manager..You don't have to do anything...It will find the other drive. Then open a terminal and enter sudo update-grub...That's it.

---

### Post by jerrrys on 2012-02-04
Can't say what went wrong, but this may help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+dual+hdd+drives&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+dual+hdd+drives&sa=Search&cof=FORID:9)

---

### Post by smo0th on 2012-02-04
I guess first you need to install win and then ubuntu, otherwise the grub loader will get wasted by win installation

---

### Post by TXbirder on 2012-02-10
jerrrys
Thanks for the Google hits.   I'll try again when I have a free day.
John

---

### Post by efflandt on 2012-02-10
Unless your PC is very old, you should be able to go into CMOS setup at BIOS splash screen (by pressing F1 or F2, or possibly different key) and change boot order to boot from your second drive.  If that is where grub is, that should then be able to boot both drives.  Or your BIOS splash screen may show another key like F12 or Esc to select boot device on the fly.

My desktop has Win7 and Maverick on sda, and boots those or 11.10 in sdb from 11.10's grub on sdb (all 64-bit).

My tablet PC defaults to booting Win7 on its internal SSD if no keyboard is connected. So to boot 11.10 in its SD slot, I have to hold Windows button while turning on, and have keyboard attached to be able to hit F12 to select booting SD (where grub is).

---

