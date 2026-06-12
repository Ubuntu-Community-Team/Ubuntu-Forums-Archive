---
title: "I want to dual boot but dont wont to destroy my ubuntu install"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by CameronCalver on 2008-07-14
Hello i have decided i want to dual boot because i need windows for a few games and i want to know how.
I have a 160gb drive for ubuntu and a 80gb drive that i will put windows on.
I already have ubuntu 8.04 installed and the 80gb is in the computer as a secondary master. What steps do i need to do so i don't destroy GRUB?

---

### Post by logos34 on 2008-07-14
In order to install windows you'll have to make the target drive (80 gb sec. master) the boot drive in the Bios.  Then install.  The windows bootloader will go on the mbr of that drive.

Once windows is up an running, reboot and go into the Bios and change the boot order back to the 1. ubuntu 2.windows.  Boot into ubuntu, open menu.lst

gksudo gedit /boot/grub/menu.lst

Add a windows [entry like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") to bottom.

Add [windows to fstab]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.04%20LTS%20%28Hardy%20Heron%29").

Get [fs-driver]("http://www.fs-driver.org/") for windows.

---

### Post by CameronCalver on 2008-07-14
in my bios i cant actually change the boot order or hard drives?

---

### Post by logos34 on 2008-07-14
Are you sure? Unless this is a pretty strange bios, you should be able to change the **device** boot order (floppy, cdrom, hard disk) **and** **hard disk boot priority** for when you have more than one disk.  Again, the target drive has to be the boot drive, otherwise windows will not install (that's my experience)

---

### Post by CameronCalver on 2008-07-14
i have boot order like , floppy , cd , hard drive , usbhardrive ... etc but nothing else

---

### Post by logos34 on 2008-07-14
There's no submenu for hard disk boot order?  Check again...I'll check the manual for that motherboard in the meantime

---

### Post by logos34 on 2008-07-14
BIOS>advanced bios features>Hard disk boot priorty [press enter]

[http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1784](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1784)
(>manual>english)

[http://america.giga-byte.com/FileList/Manual/motherboard_manual_sata_raid_os_nforce3_e.pdf](http://america.giga-byte.com/FileList/Manual/motherboard_manual_sata_raid_os_nforce3_e.pdf)
(see **figure 4**)

---

