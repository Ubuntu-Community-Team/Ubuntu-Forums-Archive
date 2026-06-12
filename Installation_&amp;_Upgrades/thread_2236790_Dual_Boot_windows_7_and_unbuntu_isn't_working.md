---
title: "Dual Boot windows 7 and unbuntu isn't working"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by jonathan48 on 2014-07-29
I have been trying to dual boot unbuntu ann linux all night to no avail. I started by partitioning my a 2 tb hard drive into another 500 gb partition on windows 7 I left the space unallocated. From there i made an install of unbuntu on an 8 gb usb stick. After that i installed unbuntu on the 500 gb partition. I got all the way through the instalation and it asked to restart i said yes but then it rebooted and immediately launched windows. Now when i restart with the unbuntu install pin drive inserted it doesn't even give me the option to install unbuntu. I'm a noob at linux os's and dual booting in general, that being said i really wanna run unbuntu becasue it is obviously the superior os XD

---

### Post by Bucky Ball on 2014-07-29
Welcome. Are you positive you have Ubuntu installed on the hard drive? Which release are your using and is it a UEFI or legacy install? Win 7 is generally legacy, unless there has been a custom install. 

If you have Ubuntu installed on the hard drive, Boot Repair could be your friend:

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

You say you can't boot from the USB now? You are hitting the correct key at boot to get the device boot menu (or getting into BIOS) and setting the USB to boot first? Might seem a silly question, but best to confirm. ;)

How did you create the USB? You say you 'installed' to the USB. How? You have made a LiveUSB (an installer) or you have actually done a persistent install to the USB (which is NOT an installer)?

---

### Post by jonathan48 on 2014-07-29
I'm not getting any option to get into the bios it just automatically launches windows 7 

And i created the usb using this program 

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by Bucky Ball on 2014-07-29
Depends on the model, but you need to hit the correct key at boot to get to BIOS (how did you boot from USB originally and how are you changing your boot device?).

It will say at the boot screen (at boot) which key, but it will be brief so you have to be alert. Some machines it's the 'del' key, others F2, F12. It varies. You might need to look in the manual or online (or both) to find it. F12 usually gets you to a device boot list on most machines, though. That will do it.

Never used the Universal USB Installer you link to, but from what I have read (and as is obvious from the 'Installer' in the name), it IS capable of making a persistence install to a USB. That is NOT what you want if you want to install Ubuntu to the hard drive. You want to create a regular LiveUSB that installs USB.

* Always used UNetbootin myself, but not sure if that's available for Win. :-k

---

### Post by jonathan48 on 2014-07-29
i have restarted my system numerous times and have lookedfor the option to acces the bios but it never appears. Also my computer is custom built so to look in the manual would i just look in the MOBO manual?

---

### Post by mastablasta on 2014-07-29
> **jonathan48 said:**
> i have restarted my system numerous times and have lookedfor the option to acces the bios but it never appears. Also my computer is custom built so to look in the manual would i just look in the MOBO manual?

yes. that is where the BIOS/UEFI is

how did you boot from USB if you can't access BIOS? can you still boot using Ubuntu pen drive and then get to desktop and run boot repair tool and within it the boot info summary.: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

post results here to see how the whole thing is setup, it might be you've put GRUB on USB instead of hard disk.

> **Bucky Ball said:**
> 
* Always used UNetbootin myself, but not sure if that's available for Win. :-k

it is.

---

### Post by jonathan48 on 2014-07-29
alright i figured it out. Thanks guys for the help ):P

---

### Post by UltimateCat on 2014-07-30
I could be mistaken but I think with a 2TB drive you might need to perform a special kind of "GPT Partitioning"

If you can't use these links maybe they will help another member-

[https://wiki.archlinux.org/index.php/GUID_Partition_Table](https://wiki.archlinux.org/index.php/GUID_Partition_Table)
[http://www.linux.com/learn/tutorials/730440-using-the-new-guid-partition-table-in-linux-good-bye-ancient-mbr-](http://www.linux.com/learn/tutorials/730440-using-the-new-guid-partition-table-in-linux-good-bye-ancient-mbr-)

---

### Post by Bucky Ball on 2014-07-31
Please outline how you got things going to help others.

Mark thread as solved by following the instructions in the second lik of my signature ...

Good luck. ;)

---

