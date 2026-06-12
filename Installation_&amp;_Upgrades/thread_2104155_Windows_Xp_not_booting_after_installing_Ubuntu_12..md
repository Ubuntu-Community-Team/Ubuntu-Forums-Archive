---
title: "Windows Xp not booting after installing Ubuntu 12.10"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by cool_thing76 on 2013-01-12
Hi,

I had a dual boot Kububtu and windowsXP. Then I installed Ubuntu 12.10 which boots fine and I can see the Windows partition inside ubuntu but I can't boot to Windows. Here is my boot info created by boot auto repair [http://paste.ubuntu.com/1519635/](http://paste.ubuntu.com/1519635/)

Thanx

---

### Post by oldfred on 2013-01-12
I do not see anything obviously wrong. What happens when you choose XP from grub menu?

Did you resize XP as part of the install? It may just need chkdsk from a Windows XP disk.

---

### Post by cool_thing76 on 2013-01-13
When I choose to boot to windows nothing happens. The grub menu disappeares and then only a blank screen showing the little dash cursor on the top left is there. Nothing else happens although I waited long enough.

As for your second question, no I didn't resize the Windows partition. I just formatted the Linux root partition and the /home partition then installed Ubuntu 12.10.

Thanks for your help.

---

### Post by oldfred on 2013-01-13
It almost for sure is a Windows issue. try chkdsk first.

---

### Post by cool_thing76 on 2013-01-13
I followed the instructions here to run chkdsk form the Windows XP CD
[https://kb.wisc.edu/helpdesk/page.php?id=5097](https://kb.wisc.edu/helpdesk/page.php?id=5097)

Restarted after chskdsk finished and now I don't even get the grub loader list?!

---

### Post by oldfred on 2013-01-13
Did you also run fixMBR as that writes the Windows boot loader to the MBR. Then you are directly booting Windows. That way you know it is not a grub/ubuntu issue. 

If chkdsk had any errors it may need to be rerun as it does not fix everything on one pass.

You can use Boot-Repair to restore the grub boot loader after you fix Windows.

---

### Post by cool_thing76 on 2013-01-13
Hi,

I didn't run FIXMBR.  chkdsk didn't report any errors but I will try to run it again and run fixMBR too.

---

### Post by cool_thing76 on 2013-01-13
I run chkdsk again and then fixMBR. After I restarted, it still won't boot.

---

### Post by oldfred on 2013-01-13
If you have gone thru the Windows repairs I do not know what else to try.
       XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

    

It is an older install of XP as it is in a FAT32 partition. Newer installs all used NTFS.

---

### Post by cool_thing76 on 2013-01-13
Thanks for your help. I'll these tools or maybe make a fresh installation again.

---

