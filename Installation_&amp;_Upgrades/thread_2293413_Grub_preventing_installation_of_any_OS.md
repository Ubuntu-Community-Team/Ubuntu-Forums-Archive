---
title: "Grub preventing installation of any OS"
date: 2015-09-04
forum: Installation &amp; Upgrades
---

### Post by bullywug on 2015-09-04
I somehow managed to mess up my system today.  When I rebooted grub wouldn't let me in so I reinstalled Ubuntu but grub was still saying there was no OS.  Then I tried to install Windows and grub wouldn't allow that either.  I've tried playing with the various settings in CMOS and running the grub repair tool and I think I've only made things worse.
Is there a way to completely remove grub so I can install either Windows or Ubuntu?

---

### Post by oldfred on 2015-09-04
Grub does not prevent anything. And No OS is usually from UEFI/BIOS.

But it sounds like it is installed into the MBR, if BIOS or ESP if UEFI and your reinstall is not correctly overwriting the old install. Or if UEFI hardware, you may have switched install from UEFI to BIOS or vice-versa.

Best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by bullywug on 2015-09-05
I appreciate your response.  I'm sorry if my inexperience with grub is causing me difficulties communicating my problem.   The link to the file you requested is [http://paste.ubuntu.com/12277644/](http://paste.ubuntu.com/12277644/).  I'll try to be more specific:
1) Installed Ubuntu 14.04 on main hard drive of Lenovo Horizon 27
2) Set up the software on the computer
3) Rebooted
4) Got error 1962 - No operating system found.
5) Tried reinstalling Ubuntu - didn't help
6) Tried deleting all partitions and reinstalling Ubuntu - didn't help
7) Tried running grub boot repair - first the basic scan and when that failed I tried other combinations of check boxes.
8) Tried switching bios from uefi to legacy - no help
9) Tried installing Windows - Won't even see the drive Windows is on, even if I remove every other device from the boot order.

Well, I think that covers what I did with my Friday.  Anyhow, I'm at my wits end.  I've had a lot of problems with grub.  Every time I've installed Ubuntu, grub was why I gave up.  Is there something I should know about it (like don't let it eat after midnight) or a good book on Ubuntu and grub that will tell me what not to do?

---

### Post by bullywug on 2015-09-05
Okay, I was tired last night.  When I made the Windows install disc I didn't notice the default was to make a linux disc so that's why I kept ending up in grub.  I've got Windows installer up and running and I'm going to try installing it and then if that works I will reinstall Ubuntu.  I'll post my results later today.

---

### Post by oldfred on 2015-09-05
You now show this boot entry in UEFI.
Can you go into UEFI or one time boot key, often f10 or f12 and choose it.

Boot0000* ubuntu	HD(1,800,100000,80931dda-881b-49b8-a3a8-46b550601ca5)File(EFIubuntushimx64.efi)

---

### Post by bullywug on 2015-09-05
I've made some progress.. kinda.  I got Windows to reinstall and it did get rid of grub.  I installed Ubuntu again with the delete Windows option and on reboot Windows boot loader wanted to run a repair.  ARGH!  So, I ran the grub repair tool again.  It said success and told me to select sda1/EFI/ubuntu/shimx64.efi but there is no option for that.  I only had the Windows boot loader and another string of letters and numbers but when I selected it, it just loaded the Windows boot loader.  The report is paste.ubuntu.com/122816741.

---

### Post by bullywug on 2015-09-05
Okay, so it looks like Windows has finally managed to wrestle control of my system back from grub.  I've tried Ubuntu in the past and problems with grub have always been the reason I gave up on it.  As much as I love Ubuntu this has to be the last time I try it.  I was hoping it had evolved into a reliable alternative to Windows and Mac but it's clear that it is still not ready for prime time.  I hope one day that Ubuntu becomes a viable option but after the hours and headaches and data loss I've experienced every time I've given Ubuntu a go, it would be reckless and foolish of me to ever try it again.
I don't really want to sound like I'm complaining.  I knew Ubuntu and grub were touchy and I should have come to the forum for help before trying to fix grub myself but that's no longer relevant.  I'm here now and I have to get on with my school work.  I've just lost a project that I had been working on for over a month because the backup was made with Ubuntu's backup tool and for some reason it skipped the project files that were in my home directory even though it said it was backing it up.  So it stinks, but I'm taking this as a positive learning experience and saying goodbye to Ubuntu forever.
Thank you for taking the time to offer your help with my system.  I really greatly appreciate it.

---

### Post by oldfred on 2015-09-05
It not as much grub & Ubuntu as just the extra complications of UEFI, UEFI with secure boot and Windows settings that make it difficult to configure anything other than Windows. Even if you want to dual boot two versions of Windows it is more difficult.

And then many vendors now are modifying UEFI to use description as part of boot and only allowed description is "Windows". That is not per UEFI standard (maybe a Microsoft suggestion to make it more difficult to install anything other than Windows).
But then you have to do a work around to make it work.

---

