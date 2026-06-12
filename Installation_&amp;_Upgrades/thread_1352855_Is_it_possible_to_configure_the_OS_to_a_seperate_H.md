---
title: "Is it possible to configure the OS to a seperate HDD and then hook it to a desktop?"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by karan03130 on 2009-12-12
Hi Fellas,

this question has been nagging me for a long time. I'm new to linux OS installations, but i'm familiar with the OS as i work on remote server monitoring. 

I have got this 5 yr old desktop which i seldom use and that too since it doesn't have a monitor. Now my query is, can i install ubuntu to a HDD via USB-IDE connector and then hook it into my old desktop and connect to it via putty ?? remember i dont have a monitor for my desktop..

---

### Post by earthpigg on 2009-12-12
you would need to fully configure sshd on the hard drive prior to moving it over to the server.

possibly, the best way to install ubuntu would be via ubuntu's 'usb startup disk creator', since it is intended to detect the computers hardware every time it boots.

will that computer's bios even let it boot without a keyboard/monitor, btw?

---

### Post by karan03130 on 2009-12-12
that machine already ran on WinXP and i have worked with it in remote after booting up with out a monitor, but i had the mouse and keyboard connected.. but somehow its OS corrupted and i'm planning to turn it into a linux box now..

I'm gonna experiment with it in a couple of days, but till then pls keep pouring in ur ideas.. ;)

---

### Post by earthpigg on 2009-12-12
the easiest thing might be to plug the hard drive and a monitor from your other computer into the computer, install/configure ubuntu/ssh, and remove the monitor after its all set up.

---

### Post by efflandt on 2009-12-12
It should work as long as you BIOS is set to ignore video or mouse/keyboard missing or errors, and /etc/fstab has UUID's for partitions (which is the default now) instead of /dev/sda-whatever entries.  I have installed 64-bit Ubuntu to the back end of WD Passport portable USB drive (after shrinking vfat partition) and it boots fine on various computers whether the drive ends up as sdb or sdf, with different video/monitors supported by standard modules.

Near the end of install, at summary before it proceeds, make sure you use the **Advanced** button to put grub on the mbr of "that" drive, instead of default to your main hard drive.

X will not be running since there would be nobody to log into that from the missing monitor.  But if you use **ForwardX11 yes** in ~/.ssh/config, you should still be able to run X programs remotely.

---

