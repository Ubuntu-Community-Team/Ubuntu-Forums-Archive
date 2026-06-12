---
title: "windows/lunux dual boot problem, &quot;Error 22&quot;"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by dnsfailure on 2007-10-14
In short:  After I've installed Ubuntu onto a separate (blank) drive, I'm getting "error 22: No such partition" when I select Windows as my boot OS. But the strange thing is that I only get this error when I plug in my photographs harddrive (that has no OS).  When the photographs harddrive is unplugged, windows boots just fine.  (linux boots just fine no matter what)


Details:

I have 4 separate physical drives, all connected via SATA cables.  They are as follows (as they are labeled in Windows)

C: Windows 2k and Windows applications only
F: Old backup files only, no applications or OS
I: Photograph files only, no applications or OS
J: Linux Ubuntu only (and I think there is a "swap"  partition in there somewhere, I'm not sure but whatever the case, it's all on this physical drive)

Windows was already installed on the C: drive before I started my Linux install.  When installing Linux, I unplugged my I: drive (Photographs) and my F: Drive (Backup files) to make sure that none of them got accidentally formatted or anything like that.  I left the C: (windows) drive plugged in, thinking that Linux would recognize the other OS and play nicely with it and I would get a nice dual boot using seperate harddrives for each OS.

So Linux Ubuntu installs just fine on the J: Drive, I shut the machine down, plug in the other two drives (I: photos, and F: backup files), I choose windows on the boot choice and I get "error 22: No such partition"


Not sure what happened, so I shut the machine down, unplug the F: and I: drives again (just as it was when I installed Linux).  Windows and Linux now boot and run just fine.  Ok, that was weird.  I plug back in my F: drive (leaving the I: drive the only drive unplugged), both Windows and Linux still boot up and run just fine.  The only drive left is the I: Photographs drive, I plug it in... and Windows won't boot, "error 22: No such partition", but Linux still boots just fine.  

Any ideas?  I installed Ubuntu with pretty much all the default options, running an AMD 64 bit machine, with Ubuntu 7.04 64 bit version.  Windows is the 2k version with the latest service packs.  I'm a new Linux user, I'm not quite sure what the problem is here, it's got to be a setting somewhere that is not set properly?  Because both OS run just fine when the Photographs drive is unplugged, but as soon as I plug in the Photographs drive, Windows won't boot.  Strange, no?

Thanks for any help or direction!

Daniel

---

### Post by Alan Stancliff on 2007-10-14
I'm really a beginner at this too. I have a dual boot system and installed Ubuntu only a few days ago, so take what I say with a grain of salt.

First of all, you are going to solve this problem. 

Error 22 means that the MBR (master boot record) is missing from the drive your machine tries to boot Windows from. The MBR is the little program that loads in the startup for the operating system. In your case, you have a MBR for your Ubuntu, an MBR for your windows, and an MBR for your GRUB (the little menu that lets you select which OS you want). When you select Windows, the GRUB tries to direct attention to the drive with the MBR for Windows at the beginning of what it surmises is the Windows drive.

When you unplug a couple of drives, the computer decides that the drive with Windows is the one that actually has the Windows  MBR . But for some reason, it sounds as if GRUB gets confused when you put a couple of other drives into the chain. 

You may have to configure GRUB somehow, or maybe you will have to go to your BIOS and set it up. You may even have to uninstall and then reinstall Linux, not a big deal as it is such a new install.

I hope I've got all the terms correct. If I don't, someone here will correct me. 

Somebody here can give you a more detailed explanation.

Best of luck. As I said, you will solve this problem. It's just going to be a bit irritating until you sort it out, but it won't be a big deal, I predict.

---

### Post by logos34 on 2007-10-14
Try switching the motherboard sata connectors for the windows and photograph drive.  

Any luck?

---

