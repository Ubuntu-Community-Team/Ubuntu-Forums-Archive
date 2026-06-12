---
title: "Trying to install Ubuntu on Acer laptop (Grub2 freeze)"
date: 2018-12-01
forum: Installation &amp; Upgrades
---

### Post by sudsud on 2018-12-01
Hello all,

So I'm a Linux-noob and I'm trying to install Ubuntu 18.04 on an older Acer laptop for my mother.

Reason is that Windows 8/10 broke and is generally too slow. She only uses it for the internet.

I've created a bootable USB-stick, the installation program itself is working well. The only problem is that the installation hangs/freezes when its installing the grub2 package. 

I have tried it multiple times, even made the partitions myself (/, swap, home).

This is my boot-repair pastebin: [http://paste.ubuntu.com/p/YRx5ZdsMvQ/](http://paste.ubuntu.com/p/YRx5ZdsMvQ/)

Can someone help me? My goal is to just delete everything and make it an Ubuntu-only laptop.

---

### Post by yancek on 2018-12-01
You have both a BIOS boot partition and an EFI partition.  You only need one and since you have no boot code in the MBR, you should be booting in UEFI mode.

Boot the Ubuntu install media and when you do open gparted with:  sudo gparted  When it opens, highlight sdb5 in the main window, click the Partition tab at the top of the window and in the drop down menu click on Manage Flags and verify that the boxes to the left of boot and esp are checked.

Line 437 of boot repair shows:  No kernel in /boot  Don't know what happened there but the system will never boot without the kernel.  Boot repair shows a number of Grub files but not the grub.cfg file which contains the boot menu you see on boot on a working system.

You could try turning off Secure Boot in the BIOS if it is on.  Also, some Acer machines require you to set "Trust" in the BIOS before another OS can be installed and booted so you might investigate your BIOS options.

It's also a bit unusual to have your EFI partition on sdb5 as it is usually at the beginning of the drive.  I'm not sure that is part of the problem though.

---

### Post by oldfred on 2018-12-01
Many Acer need UEFI update from Acer.
       Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141

      [/URL]
 One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/) 
    [       ]("http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141")
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    [URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]
[/URL]

---

