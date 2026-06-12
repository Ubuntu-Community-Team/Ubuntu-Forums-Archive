---
title: "Neither Windows 8 or Ubuntu 12.04 boots"
date: 2013-12-31
forum: Installation &amp; Upgrades
---

### Post by raphaelfv on 2013-12-31
Basically, I followed the steps from [here]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported") and [here]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html") to make dual boot with Windows 8 (with UEFI) and Ubuntu 12.04 64 bits. My result from boot-repair is [http://paste.ubuntu.com/6658704/](http://paste.ubuntu.com/6658704/) 
After restart, I went to Windows , which was "normal" (slow as always) but, after I restarted again, the only thing I got is the manufacter logo. After several tries, I could make the "BIOS" appear pressing F2 with the Windows 8 recovery DVD in the driver (not sure if the DVD had any influence) and I make it back to defaults. After saving, the laptop automatically shut down. I started it again and the list with Ubuntu and Windows (grub?) was there again and I choose Ubuntu, so that I can run the boot-repair again (and here I am). I am afraid of what is going to happen after another restart. 

PS: When I first ran the boot-repair, I got some warning messages, but I ignored then. Also, I answered Yes to the question "buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]?".

The machine: Chipset HM 67

---

### Post by oldfred on 2013-12-31
Please post screenshots as attachments not in line. Not everyone has high speed Internet.
You can use advanced editor and paperclip icon to attach screen shots.

What version did you install? Only 12.04.2 or later have secure boot capability and it looks like you have secure boot and UEFI has had major updates with each version, so if newer system 13.10 or wait for 12.04.4 may work better.

Never seen this error, so I assume you may have used 12.04 not 12.04.2?
>  GRUB too old for SecureBoot.

   You may want to retry after deactivating the [Backup and rename Windows EFI files] option.


The buggy UEFI renames Windows. Some systems only boot Windows and have hard coded UEFI to either boot only the Window efi file or boot the Windows description.
      
 Boot0000* Windows Boot Manager	
Boot0001* ubuntu

    With the rename the Windows entry is now grub also. So both entries should take you to grub menu and only from grub menu can you boot Windows backed up or renamed file.
If you can boot the ubuntu entry from your UEFI then undo rename.
If you turn secure boot off you may be able to boot without any other changes, but still should update to newer version as they have many improvements.

       And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. Then you also should be able to directly boot Windows from UEFI menu.

---

### Post by raphaelfv on 2013-12-31
I am with Ubuntu 12.04.3. I'll take a look in the link. At this moment, I am in Ubuntu and, when I run the boot-repair, it tells Secure Boot is ON, but I could move on by pressing Yes to question "Want to retry" or something like this. Again, I answered Yes to buggy-kenel question, and the log is on [http://paste.ubuntu.com/6670113/](http://paste.ubuntu.com/6670113/) . Is there something I need to do with gparted to stop the warning "The boot files of [The OS now in use - Ubuntu 12.04.3 LTS] are far from the start of the disk." ?

---

### Post by oldfred on 2013-12-31
I have yet to see a UEFI system need any revision due to far from start of disk. It is for some BIOS that will give a grub error on invalid UUID when it is correct. For whatever reason it does not see a partition beyond 100GB. So that is just a warning, that you can ignore.

If you can boot ubuntu from UEFI:
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Have you tried with Secure boot off in UEFI?

---

### Post by raphaelfv on 2013-12-31
I'm about to restart. The Secure boot is enabled because I restored the defaults in the setup. Is there something to do at Windows (besides desible Secure Boot)?

---

### Post by oldfred on 2013-12-31
You need to have fastboot or the always on hibernation off.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by raphaelfv on 2014-03-08
Sorry the long time to answer. You can mark as resolved, I think. I rarely use Windows, but when I do, if I ask to Shut Down, everything is OK (I didn't try Restart because it was by pressing Restart that I've got the problem reported, it might alter the Bios to force Win8, You can correct me if I'm wrong). Sometimes, when I start Ubuntu, I receive some messages from the log before the login screen, such as "Broken bios", but, except for once, the boot is always ok. This one exception was  when I had to wait full 2 hour to battery discharge, because the screen with that message was frozen. Besides, I advise who is about to try dual boot to record the Windows System Repair Disk. Thanks.

---

### Post by Iowan on 2014-03-08
> **raphaelfv said:**
> You can mark as resolved, I think. 
As can you... :)
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

