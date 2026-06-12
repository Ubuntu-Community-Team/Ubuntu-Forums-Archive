---
title: "Booting Linux from External Drive"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by AdamDunn on 2007-02-14
Hello, UbuntuForums.
The Setup:
My friend recently decided to try installing Linux (Edgy) for the first time onto his Dell Inspiron 6400. I shouldn't really say he installed it on his laptop, as he wanted to put it on his USB 2.0 external drive instead of on the internal drive. The install went along successfully, with no problems. He made the standard swap and ext3 partitions in some empty space on the external drive (the majority of the drive is fat32). He also installed grub into the master boot record of the drive that is internal to the laptop. His drive partitions look something like this:

Internal hard drive
  -Dell recovery partition
  -Another Dell recovery partition
  -NTFS Windows XP partition
External USB 2.0 drive
  -FAT32 Windows XP partition
  -ext3 linux partition
  -linux swap partition

Because he installed grub overwriting the Microsoft bootloader, when he first starts his computer he gets the menu to choose kernel version, or windows, and all that works. Nothing wrong so far.

The Problem:
Should my friend want to boot his computer without the external drive attached (like if he wants to take it somewhere, which is what laptops should do), then grub cannot find the /boot/grub/menu.lst and it fails. It won't even boot into Windows without having the external drive present. We also don't have a Windows disc, or else I would try reinstalling the microsoft bootloader.

The Solution?:
One possible solution I have found is to use a Preset Menu in grub (as per [http://www.gnu.org/software/grub/manual/html_node/Preset-Menu.html#Preset-Menu]("http://www.gnu.org/software/grub/manual/html_node/Preset-Menu.html#Preset-Menu")), so that it will boot Windows by default if it can't find /boot/grub/menu.lst, or will use the menu.lst if it is present. This of course requires recompiling and reinstalling grub, which I've never done before.

Does anybody have any other solutions? Are there any good guides to recompiling grub for Ubuntu with some custom compile options. Ubuntu has the whole booting process setup quite nicely, and I don't want to cause major breakage by recompiling grub and installing it without following some sort of Ubuntu method.

Thanks for your help.

---

### Post by cbhargava on 2007-02-14
Try to install grub on the external drive's MBR. Also restore the mbr on the internal drive using fdisk /mbr. In the system bios enable boot USB option and change the boot sequence accordingly.

Hope that this helps.

---

### Post by Macchi on 2007-02-14
My solution to this problem is to create a separate /boot partition (approx 256 MB that will contain the kernels , grub files etc.) 

Eventually I have to trim the /boot/grub/menu.lst manually to allow multibooot. It is possible to adjust the time out for the grub menu, provide a number of the default system to be booted, or even save the default for booting the latest system that was used.  

See also the book "Ubuntu Hacks" from Oreilly that has a "hack" number 10 describing how to boot ubuntu from external drive.

Many of my machines have that arrangement for multiboot since I like to create reserve systems on laptops, and also to booting different distributions or versions of Linux along with windows.

---

