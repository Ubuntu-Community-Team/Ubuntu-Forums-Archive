---
title: "Ubuntu 16.10 new installation hangs on Grub Boot Menu ..."
date: 2017-02-28
forum: Installation &amp; Upgrades
---

### Post by cwmoser2 on 2017-02-28
Wanting to replace my PC with an HP 8200 Elite.
Its an i7-2600 CPU.
I can boot off the thumb drive I have created and Ubuntu runs just fine.
BUT, when I try to install from the thumb drive, the install goes though OK but
on restart without the thumb drive it hangs on the Grub Boot Menu.

Anyone have an idea?  Any boot flags I need to add?

Thanks

Carl

---

### Post by gdesilva on 2017-03-01
When you say, 'hangs on the Grub Boot Menu' does that mean the Grub Menu appears but nothing happens when you press enter key or does Grub present you with 'grub_rescue>' prompt?

---

### Post by cwmoser2 on 2017-03-01
What happens is part of the Grub Menu is on the screen.
Its like a black box appeared over the the middle of the menu
and it just hangs up.  No errors, nothing more.

What I did do was create a Linux Mint 18.1 stick and it installed and worked perfectly.
Much rather have Ubuntu.  BTW, also tried a stick with Ubuntu 16.04 but it didn't work either.

To sum us, Mint will install but not Ubuntu.

---

### Post by slickymaster on 2017-03-01
*Thread moved to **Installation & Upgrades**.*

---

### Post by yancek on 2017-03-01
Is Ubuntu the only OS on the computer?  You don't mention any other OS?  Did you use the 'Erase disk and install Ubuntu" option?  Did you do an EFI install or the older MBR?  Did you do an md5 checksum on the downloaded Ubuntu iso before putting it on the flash drive?  Did you leave the bootloader installation as the default?  When you see the 'black box' in the middle of the screen, is part of the menu visible?  Have you tried hitting the Enter key at this point?  You might try booting either the Ubuntu or Mint usb and downloading and running the boot repair software as explained at the site below to get more details to post here.  If you select the "Create BootInfo summary" option, you should have a link you can post here for member to reivew. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cwmoser2 on 2017-03-02
No, I had partitions with a backup copy of Ubuntu 16.04 and Win10 on a separate drive.
I did the install checking to reformat the boot partition too.
I did disable EFI.

I was later able to get Linux Mint Mate 18.1 Serena to work beautifully.
Used the same method as I tried with Ubuntu - used Unetbootin on a thumb drive.
With Mint, no problems with Grub and even the dual monitor Radeon card was 
set up properly along with detecting my Compiz settings I had used with an
nVidia video card on my old PC.
This copy of Linux Mint really was a pleasant and easy install..

---

### Post by gdesilva on 2017-03-05
Check whether you have disabled Fastboot in BIOS as well. If it still fails, I would boot the system with a LiveCD and mount the Ubuntu partition on your hard disk. Then edit the /etc/default/grub file on your HDD and add 'nomodeset' to the end of the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" - should now read as GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset". Save and boot the HDD installation.

---

