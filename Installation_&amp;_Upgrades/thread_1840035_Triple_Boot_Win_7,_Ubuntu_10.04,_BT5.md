---
title: "Triple Boot: Win 7, Ubuntu 10.04, BT5"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by Eddieduce on 2011-09-06
I have created a Triple Boot environment using Win 7, Ubuntu 10.04, BT5 and it works very 'Awesomely.'  I have now one more task at hand I can not pin-point yet.

My last task at hand is to change the boot order so that Win 7 boots first.

I have attempted to modify the boot file but it makes no difference.

Below I have typed up the boot menu as shown on boot up:
<START OF BOOT MENU POST>

                     GNU GRUB version 1.98-1ubuntu12

Ubuntu, with Linux 2.6.38
Ubuntu, with Linux 2.6.38 (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)
Windows Vista (loader) (on /dev/sda3)
Ubuntu 10.04.2 LST, kernel 2.6.32-32-generic (on /dev/sda5)
Ubuntu 10.04.2 LST, kernel 2.6.32-32-generic (recovery mode) (on /dev/sda5)
Ubuntu 10.04.2 LST, kernel 2.6.24-23-generic (on /dev/sda5)
Ubuntu 10.04.2 LST, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda5)
Ubuntu 10.04.2 LST, memtest86+ (on /dev/sda5)
<END OF BOOT MENU POST>


My conclusion is that the very top ubuntu listing is the one for BT5 and that I would need to modify it to list Win 7 first but I have not gotten around to it yet.


Any thoughts?

---

### Post by Quackers on 2011-09-06
If BT5 boots up automatically if nothing is pressed from the boot menu then BT5's grub is in control of the menu (as opposed to Ubuntu 10.04's grub being in control).
I'm not sure whether BT5 used grub legacy (the older grub) or grub2.
What does it say right at the top of the boot menu? It should give the grub version.

---

### Post by Eddieduce on 2011-09-07
> **Quackers said:**
> .......What does it say right at the top of the boot menu? It should give the grub version.

It says GRUB version 1.98.

---

### Post by Quackers on 2011-09-07
What I would suggest is to boot into Ubuntu 10.04 and then run the following in the terminal ```
sudo grub-install /dev/sda
``` 
NOTE  obviously /dev/sda must be the drive your bios boots from for that command to be correct - change as necessary.

What that will do is to install grub to the mbr of the drive so that 10.04 will then have control of grub.
You can then download Startup Manager from the repos and select the system you wish to be the default option from there.

Alternatively you can edit /etc/default/grub in your BT5 system with ```
gksu gedit /etc/default/grub
``` so that the line ```
GRUB_DEFAULT=0
```
reflects the line number (minus 1) of the grub entry that you wish to be the default one.
For example if you want the "Windows 7 (loader) (on /dev/sda1)" to be default the line would become GRUB_DEFAULT=4.
Then save the file, quit the file and run ```
sudo update-grub
```

---

### Post by Eddieduce on 2011-09-07
Thanks Quakers,

I did both but it did not make a difference.

I did the sudo grub-install /dev/sda but it did not make a difference.

I tried modifying the bt5 grub file but it was empty. So, I assume it would have made no difference.

Consequently, Ubuntu gives me video errors when booting.

Thanks.

---

### Post by Blasphemist on 2011-09-07
I'm going to refer to information from this.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
This is the description of setting the default item to boot.
> /etc/default/grub (file)
The main configuration file for changing default settings. The following lines are available for alteration by the user.
GRUB_DEFAULT - Sets the default menu entry. Entries may be numeric, a complete menuentry quotation, or "saved"
GRUB_DEFAULT=0 Sets the default menu entry by menu position. Counting of entries is the same as in GRUB - the first "menuentry" in grub.cfg is 0, the second is 1, etc.
Note: Grub 1.99 introduces a submenu menu structure. For a menu item in a submenu, the entry becomes a two-digit entry. The first entry is the position of the submenu title in the main menu. The second entry is the position within the submenu. If the submenu is the 3rd entry in the main entry, and the user wishes to boot the first entry in the submenu, it would be designated as "2>0"
GRUB_DEFAULT="xxxx" An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"
In a Grub 1.99 submenu, the format would first include the submenu number, followed by the title. Example: "2>Ubuntu, Linux 2.6.38-8-generic"

Given what you've said, the ubuntu grub must already be in control. So let's assume the above solves the default issue, leaving the video errors issue. I don't know what those errors are but I can tell you of a great thread that helps troubleshoot that. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by YesWeCan on 2011-09-07
Hi there. What files are in your /etc/init.d/grub directory?

---

### Post by Eddieduce on 2012-03-27
Quick update...I got me a new machine. The old  machine was formatted and passed on to another person, (nothing to do with the shared issue).

---

