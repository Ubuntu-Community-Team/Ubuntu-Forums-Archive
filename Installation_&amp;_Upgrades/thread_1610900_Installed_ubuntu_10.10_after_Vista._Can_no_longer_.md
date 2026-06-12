---
title: "Installed ubuntu 10.10 after Vista. Can no longer access Vista"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by ubifree on 2010-11-01
Hi. I already have Windows Vista installed on my desktop and wanted to add Unbuntu 10.10 to it to make it a dual-bootable machine.  I downloaded the ububtu 10.10 iso image, burnt a CD, and installed ubuntu from that. The installer shrank the Windows partition for me and installed ubuntu in the remaining space.  When I restarted the GRUB loader menu appeared and I could boot into Ubuntu fine. However, although Vista is listed as one of the options on the GRUB menu, when I select it, the screen goes blank with the cursor blinking in the top-left corner for a few seconds, and then simply returns to the GRUB loader menu!

Has anybody else seen this and could help me boot into Vista please?  I don't mind reinstalling Ubuntu because it's got no user data yet.  But I don't want to lose my Windows data!

I tried booting from the Vista install cd and selecting the startup recovery option. However it reports that no problems were detected and so doesn't change anything.

The C: drive has Vista in a partition at the beginning, then a 40 GB space I want to use for Unbuntu, then a partition for Windows recovery. I also have an external drive connected by USB but don't want that to be used by Linux or the bootloader.

In the GRUB menu I notice it has "(loader)" at the end of the Vista option in case that helps.

---

### Post by Quackers on 2010-11-01
Welcome to UF.
The Windows MBR needs repairing. Boot from the Windows repair disc and select other options and select the command prompt option. 
In the command prompt enter
```
bootrec.exe /fixmbr
``` 
then type
```
bootrec.exe /fixboot
```
and reboot

---

### Post by ubifree on 2010-11-01
Thanks very much - that worked! I could then boot into Vista fine.

However I no longer had the GRUB boot menu. But when I followed [these instructions ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record")I was able to recover the GRUB menu and hence boot into Ubuntu or Vista as required. At last!  Thanks very much for your help.

BTW I did try running the wubi installer initially but lost patience waiting for the download - it looked like it would take more than 24 hours to complete! If that's typical for most people then I bet many won't bother using it and hence maybe not try ubuntu at all:(.

---

### Post by Quackers on 2010-11-01
You're welcome. Glad to hear you're back up and running.

---

### Post by donghnoslo on 2010-11-01
Hello all UF'ers,

I'm a newbie and would appreciate your help with a similar problem:

Though I chose "Install Ubuntu alongside another OS", defined a partition of app. 5GB for Ubuntu under the installation, now I cannot boot Windows Vista anymore.

This is what it looks like in Disk Utilities:

[CENTER][IMG]http://img.photobucket.com/albums/v248/linhtinh/Screenshot.png[/IMG]
[/CENTER]
 
and in Gparted
[CENTER][IMG]http://img.photobucket.com/albums/v248/linhtinh/Screenshot2.png[/IMG]
[/CENTER]
 
When I tried Quacker's suggestion, it said:  

> bootrec.exe /fixboot
  The volume does not contain a recognised  file system. Please make sure that all required file system drivers are loaded and that the volume is not corrupted.In Ubuntu, I can't access the folders that used to be on my harddrive anymore.

Have Ubuntu formatted my HDD? I can live without Vista, but I really need some files that I forgot to back up.

Thanks in advance for your help!

---

