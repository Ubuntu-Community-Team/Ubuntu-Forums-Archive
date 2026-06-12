---
title: "Problem with Dual boot on seperate drives"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by Mice4u on 2008-07-06
Hello,  I'm sure this isn't the first time this problem has been mentioned but I wasn't able to find an answer in the forums.  I'm still pretty new to using Ubuntu but it seems pretty easy to figure out, atleast it was on my laptop with Vista <shudder>.  Here's my problem though.  I added another hard drive to my frankenmachine desktop and installed the Ubuntu 8.?? off the live CD.  This is the same CD that I used to install it onto my laptop.  Problem is that I can't get the boot selector to come up. It will only install into XP.  Before I went off and started installing stuff onto the XP drive I wanted to get some info.  Should I install Grub onto the XP drive or not?  I'm kinda at a loose of what to do here so any advice is well welcomed.  Thankyou.

---

### Post by Herman on 2008-07-06
The short answer is, it won't hurt anything to install it to the MBR of the first hard disk regardless of which operating system the first hard disk contains.

For a more details, read on.
There are problems with terminology to watch out for here.

In the world of Microsoft and Windows, a lot of people call a partition a 'drive', and also use the terms 'Master Boot Record' and 'boot sector' interchangeably.
The widespread incorrect use of these terms, and the use of the expression 'the Windows MBR', is unfortunate as it lead to terrible confusion for anyone beginning to learn about computers. Windows does not actually own a hard disk's MBR, at least not in any of the hard disks I have.

What I (and I think most Linux users mean by a 'drive', is a hard drive.
A partition is part of a hard drive and a file system is created inside a partition.
The first sector of a partition is often a 'boot sector', as it may contain code that forms another stepping stone along the way to the boot loader.
There can be one boot sector per partition, Windows relies on the boot sector as a vital link in it's booting process, but in Linux it's optional to use the boot sector.

The MBR (Master Boot Record) is so named because it's the most important, and there's only one MBR per hard disk. The MBR is independant of any file system and doesn't belong to any operating system. Windows can boot with any boot manager installed in the MBR of a hard disk, as long as whatever boot manager is used is capable of chainloading Windows by the boot sector.

Another misleading expression is one that we Linux users like to use, 'install GRUB to MBR', that's not exactly true, but it's quicker than saying 'install the IPL for GRUB to MBR', which is all that really happens. The 'IPL' is just small piece of bootstrap code which acts as a stepping stone in the booting process and points to the boot sector or directly to a boot loader which is actually situated in the operating system somewhere.


Therefore, make sure you install GRUB to the MBR of the first hard disk if you want to boot with GRUB, because the BIOS normally only looks at the first hard disk for a boot sector to boot with.
Optionally, you can install GRUB to hard disk number 2's MBR, but then you need to direct the BIOS manually. You can do that in most computers by pressing an 'F' key during boot-up for a list of bootable devices and selecting the second hard disk. That's inconvenient to have to do very often though. The best thing to do is install GRUB to your first hard disk's MBR (hd0). It doesn't matter if the hard disk with Windows in it is (hd0) or if the Ubuntu hard disk is (hd0). 
What not to do is install GRUB to Windows boot sector, don't do that. It might be (hd0,0) or (hd1,0) or something else, depending on which hard disk contains your Windows partition and how your disks are partitioned.
You can tell by looking with Gnome Partition Editor in the Live CD.

If you choose to install GRUB to (hd0) and that's the hard disk that happens to have Windows in it, it's okay to do that because the hard disk's MBR isn't part of Windows at all, it doesn't even touch Windows.
Well, if you have Vista, Microsoft decided to tie Vista to the MBR's 'disk signature' for some reason, but GRUB doesn't touch that.

If you're the nervous type, you can make a backup of the first 466 bytes of your MBR, and I do recommend that for Vista users especially,  [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").

Regards, Herman :)

---

### Post by jw5801 on 2008-07-06
For an intermediary measure, the installer will have automatically installed grub to the MBR of the hard drive it was installed to. Therefore if you boot from the second hard drive by changing the bios boot order (or selecting it during boot) you should see the grub menu and be able to boot into Ubuntu.

---

### Post by leve4919 on 2008-07-06
Hi, ubuntians!

I want to install Ubuntu on a remote machine, running XP-PRO. This computer does not have I don't have monitor, keyboard and mouse attached and is accessed  over network using Windows Remote Desktop. I do not have physical accesses to this computer. I uploaded Ubuntu ISO image and using virtual CD in Windows installed Wubi and the rest of Ubuntu on a separate drive. Of course BOOT.INI was modified. But when computer was rebooted, I, naturally, could not connect during boot and select boot to Ubuntu option. Running Ubuntu in Virtual machine will not do. I need separate instalation.

Is it possible to solve this problem? What kind of software (if any) should I run on the connecting machine to see the PC during boot?

Thanks in advance.

PS. Actually I have one solution (maybe) but it's ugly :(

---

### Post by jw5801 on 2008-07-06
> **leve4919 said:**
> Hi, ubuntians!

I want to install Ubuntu on a remote machine, running XP-PRO. This computer does not have I don't have monitor, keyboard and mouse attached and is accessed  over network using Windows Remote Desktop. I do not have physical accesses to this computer. I uploaded Ubuntu ISO CD and using virtual drive in Windows installed Wubi and the rest of Ubuntu on a separate drive. Of course BOOT.INI was modified. But when computer was rebooted, I, naturally, could not connect during boot and select boot to Ubuntu option. Running Ubuntu in Virtual machine will not do. I need separate instalation.

Is it possible to solve this problem? What kind of software (if any) should I run on the connecting machine to see the PC during boot?

Thanks in advance.

I don't know of a way to do this. Any network access usually cannot be granted until an operating system has started. I'm sure there's a way to do it, but it probably won't be easy, and I strongly doubt you'll be able to do it without physical access to the server.

Regardless, this is almost certainly not an Ubuntu question, and is definitely completely unrelated to this thread! Please start a new thread for this question, probably in the hardware section.

---

### Post by akarmenia on 2008-07-06
If you would like to install XP and Ubuntu on the same computer, you can try my tutorial wiki at:

[http://aramk.wikispaces.com/Ubuntu+XP+Dual+Boot]("http://aramk.wikispaces.com/Ubuntu+XP+Dual+Boot")

I have step-by-step instructions and screenshots. Hope it helps!

---

