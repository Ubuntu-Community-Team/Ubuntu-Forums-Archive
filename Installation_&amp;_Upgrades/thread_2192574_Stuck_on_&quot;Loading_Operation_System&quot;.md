---
title: "Stuck on &quot;Loading Operation System&quot;"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by alexanderiiv on 2013-12-08
Im tryinh to install from a USB and i keep getting stuck on"Loading Operation System" when i boot from the flashdrive.....I've tried with a loaded Ubuntu 12.04 LTS ISO file on the drive, with just extracted files from the ISO and after installing ubuntu on the USB drive which seems for dual booting(which i dont want) Note: Internal hard drive is newly formated.

Im running a homemade system with Gigabyte AMD motherboard and an AMD processor.


Side note: I've been wanting to give Ubuntu a try for awhile and since win 7 started crashing I think its time.... please help me give Windows the  perma Ban!

If more info is required please let me know

---

### Post by mörgæs on 2013-12-08
How exactly did you create the USB stick?

---

### Post by alexanderiiv on 2013-12-08
Ok I belive i found the answer....  after a few hours of searching i found an install guide that mentioned a USB installer program that i needed  [https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick)

---

### Post by Bashing-om on 2013-12-08
alexanderiiv; Hi ! Welcome to the forum .

See mörgæs's last.

Where to start with this response:
Look, We want you on 'buntu, but maybe you are rushing into this. It is not a good idea at all to abandon the Windows you are accustomed to until such time you are familiar with 'buntu. What most do is dual boot Windows and ubuntu.
To this end there is a process to get both operating systems functional on the machine.

Preparation:
 download the .iso of your choice - say you want the flagship edition ubuntu: Here:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Verify the integrity of the .iso image;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn that .iso as an image to an install medium;
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

Now boot that install medium -> "try ubuntu" mode insures all hardware is functional, and you like what you see.

Install:
Make a backup of any important Windows data !  Murphy's Law always applies.
At this point, as a new user, I recommend that you take the easy path, and let the install wizard set up the install. All That will be required of you is to answer a very few simple questions the installer will ask of you.
Choose the option "install along side of " and The install process begins, The only real warning I can give is to watch where grub (GRand Unified Bootloader) is going to be installed to. If this is a single hard disk (or) the primary boot hard disk is the 1st hard disk, make sure grub installs to "sda" (hard disk) and NOT to the USB device.

All there is to it.

Then it is 
[INDENT][INDENT]happy ubuntu'n[/INDENT][/INDENT]

---

