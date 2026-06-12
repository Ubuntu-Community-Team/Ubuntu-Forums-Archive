---
title: "Nuke win8, now that Ubuntu installed via wubi"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by Ltar on 2012-12-04
I recently upgraded from Xp to Windows 8 on my desktop and, long story short, I sent windows 8 back to Microsoft for a refund.

Now, of course, I have to uninstall my copy of Win 8. Hardmode: my DVD drive crapped out during the month I was using windows 8, and I don't have a USB fob handy.

I've installed Ubuntu 12.10 via Wubi, and it seems to be installed in a strange sort of virtual drive. Dual-boot and all that work just fine, but I want to nuke windows 8 and use ubuntu exclusively.

Can this be done from within the linux environment? I'd like to do it pretty soon (sooner than it takes to order a DVD drive or USB fob), as my copy of (and license to) Win8 are currently En-Route to the Money-Back Guarantee processing center, and I don't want a WGA-type ping to fudge my refund.

My DVD drive is broken, and I don't have another machine for a network install. I want to use ubuntu exclusively, and I have nothing of value on the physical drive that holds Ubuntu and Windows8. Can it be done?

---

### Post by sudodus on 2012-12-04
This is described in the following link

[[COLOR="Red"]https://help.ubuntu.com/community/MigrateWubi[/COLOR]]("https://help.ubuntu.com/community/MigrateWubi")

You need to boot the computer into Ubuntu, so do it before you remove Windows, because its file system resides inside a file in the NTFS file system of Windows.

But before migrating, you need to create the partitions for the Ubuntu file system and for the swap. This should be done booted from another drive, so you need a CD/DVD or USB drive to boot from. Maybe the best idea is to buy a USB pendrive and install Ubuntu into it (make a live USB drive).

---

### Post by sudodus on 2012-12-04
I should also add, that it is risky to edit partitions. So I recommend, that you ***backup your whole internal HDD*** before you make the partitions and migrate Ubuntu. At least you should backup your ***personal files*** (documents, pictures, video clips etc).

Use ***gparted*** in Ubuntu booted from CD/DVD/USB to edit the partitions.

---

### Post by oldfred on 2012-12-04
Windows only boots from one primary NTFS partition or the active partition which in Linux we see as having the boot flag.

So if you installed Windows 8 after XP, your Windows 8 boot files are in your XP install, not in the Windows 8 partition. You can only do the full repair from a Windows repairCD or USB, but can do most of the restore with testdisk as it creates a XP type boot sector or PBR (partition boot record/sector) and making sure you have all the XP boot files.

There are two types of NTFS PBRs. One is XP and says to use ntldr to continue to boot and uses boot.ini and the other says to use bootmgr to continue to boot and then wants the BCD to know what systems are installed.

You can just install Boot-Repair into your current Ubuntu. Not sure if it runs ok from wubi or not?
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Ltar on 2012-12-04
As it turns out, I am completely blind. 

My DVD drive has been fine for 3 years, but suddenly goes on the fritz after installing windows 8. Obviously, the drive suffered an unfortunate fatal malfunction, right?

My drive works fine under Ubuntu, but I hadn't thought to try it until this morning when I noticed it was mounted in my sidebar. Burning 12.04 live CD right now. 

@Sudodus - Migrate is the word I was looking for. Thank you, sir. Your help would have fixed my up right, if only I had understood my problem correctly to begin with.

---

