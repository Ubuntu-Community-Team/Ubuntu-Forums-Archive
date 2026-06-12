---
title: "bios disabled - cannot configure to boot from CD! =["
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by CC_machine on 2008-04-14
my friend wants to try out Linux, so i took a Ubuntu CD to his house and popped it in.
like most hardware, it wasn't configed to boot off the CD.
so i tried the BIOS. it was password protected. after a quick chat with my friend, he told me the password. but when i hit enter, it told me "System Disabled - 00762". I'm sure the password IS correct, because when i entered any other password it simply told me "Invalid Password". I cannot do anything else with the laptop with this message onscreen, and so have to reset.

so frustrating :mad::(

is there a way to make the CD boot from inside XP, for example? or should i go for something like the Wubi installer for windows? bah =[

update: i now know the password is WRONG, because no matter what password i try, it says "system disabled" after three attempts with any password.

---

### Post by pytheas22 on 2008-04-14
What if you disconnect the hard drive temporarily?  If it doesn't find a bootable hard disk it will probably try booting to the CD next.

EDIT: actually on second thought this would not work really well, because there'd obviously be no hard disk to install Ubuntu to (unless you have more than one).  But a work around would be taking the hard drive to another machine and installing Ubuntu from there, then putting it back in your friend's computer.  You'd probably have to reconfigure some things once the drive is back in your friend's computer (e.g. X might not work until it gets reconfigured for your friend's hardware), but at least you'd have an Ubuntu system to boot to.

---

### Post by logos34 on 2008-04-14
Remove the CMOS battery from the motherboard for about 30 seconds, then pop it back in.  Hopefully that will clear the Bios settings.

Alternatively, if the Bios boot order is 1. removable/floppy 2. HDD, then you could try using the [Smart Boot manager]("https://help.ubuntu.com/community/SmartBootManager").  You boot to the floppy, then choose cdrom from the menu.

---

### Post by koenn on 2008-04-14
> **pytheas22 said:**
> What if you disconnect the hard drive temporarily?  If it doesn't find a bootable hard disk it will probably try booting to the CD next.

EDIT: actually on second thought this would not work really well, because there'd obviously be no hard disk to install Ubuntu to (unless you have more than one).  But a work around would be taking the hard drive to another machine and installing Ubuntu from there, then putting it back in your friend's computer.  You'd probably have to reconfigure some things once the drive is back in your friend's computer (e.g. X might not work until it gets reconfigured for your friend's hardware), but at least you'd have an Ubuntu system to boot to.

Removing the hard disk temporarily  would probably work OK to just use the Live CD as a demo

installing on the harddisk elsewhere, then putting it back in, will probably require more tweaking than just fixing X. kernels can be rather processor-specific. large differences in chipsets or pheripheral hardware (nic, ...) will require different modules (drivers).
The boot record of that disk will still have Windows boot code. Grub won't be installed correctly,  Those are just the first things that come to mind ...

On the other hand : Smart Boot Manager sounds like a good idea

---

