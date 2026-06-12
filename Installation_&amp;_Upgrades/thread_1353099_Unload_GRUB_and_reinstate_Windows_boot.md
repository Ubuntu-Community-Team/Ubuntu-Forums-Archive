---
title: "Unload GRUB and reinstate Windows boot"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by johnjacobt on 2009-12-12
Hi,
 
I had a laptop with a corporate Win XP OS running on its 120Gb HDD. Now I had an external 60 GB HDD as well with 2 NTFS partitions. I booted Ubuntu from Ubuntu 9.04 live CD and curious me installed Ubuntu on the first partition of the 60GB external USB HDD. (I manually created the / and swap partitions in the space I got free after deleteing one of the partitions). Now after installation when I rebooted the machine - neither ubuntu from external HDD nor Windows from the laptop's HDD are booting up.
 
If external USB disk is not plugged in - I get the Error 21 after "GRUB loading, please wait..." message.
 
If the external HDD is plugged in - GRUB loads the regular Ubuntu options and on loading Ubuntu I get a prompt (initramfs) and then an error - "Buffer I/O error on device sdb, logical block 0"
 
Now with the current situation the laptop cannot be used for anything. I need to restore Windows in the laptop as it was before.
 
Experts and gurus - Please help!!!
 
Thanks!

---

### Post by darkod on 2009-12-12
Restoring different bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by fancypiper on 2009-12-12
[How to Remove Linux and Install Windows XP on Your Computer]("http://support.microsoft.com/kb/314458/EN-US/)

---

### Post by johnjacobt on 2009-12-12
Thank you Darko and Fancy Piper. Let me try these.
 
The challenge here is - Data in the laptop's HDD was encrypted with Pointsec and reinstalling windows is not an option I can go for as it should have a corporate image.
 
I shall post the results here after trying the options. Thanks again for your pointers!

---

### Post by johnjacobt on 2009-12-15
Unfortunatley nothing worked out :(

_Darkod__,_ after fixboot and fixmbr, it started giving me the message NTLDR is missing. Press any key to restart.

Fancypiper, As I said reinstalling Windows completely was not an option for me.

Now I'm trying what I can do with the boot info script

---

### Post by darkod on 2009-12-15
First, unplug the ext hdd while doing the XP repair. Also set the XP disk as first in boot order in BIOS.
Then, to check out ntldr, boot with ubuntu cd, Try Ubuntu option, and open your int hdd and see if ntldr file is in it. That will give you some idea whether it really is missing.
Also I recommend repeating the XP bootloader restore process with the ext hdd unplugged, if it was plugged in last time.
Let us know...

---

### Post by johnjacobt on 2009-12-15
I had done the process without the external HDD plugged in and in the bootorder in BIOS Notebook HDD is the second option after Optical Drive.

BTW, I am not able to look into the Win XP partition as that is (or was) encrypted with Pointsec. After booting up using Ubuntu live CD, the internal HDD is just being shown as a 'Filesystem'. Additionally in the partition editor sda (which is the internal hDD) is shown as 100 % used. I did not edit anything using gParted, just went into see what is being shown.

---

### Post by darkod on 2009-12-15
> **johnjacobt said:**
> I had done the process without the external HDD plugged in and in the bootorder in BIOS Notebook HDD is the second option after Optical Drive.

BTW, I am not able to look into the Win XP partition as that is (or was) encrypted with Pointsec. After booting up using Ubuntu live CD, the internal HDD is just being shown as a 'Filesystem'. Additionally in the partition editor sda (which is the internal hDD) is shown as 100 % used. I did not edit anything using gParted, just went into see what is being shown.

Hmmm... yes, it would be shown just as Filesystem because you're on the LiveCD. But the encryption might prevent you from looking inside.

I have no other advice than to try the restore again. But you already did that once and I don't expect different outcome too. Sorry. :(
Not sure if the encryption can also prevent the MBR from "seeing" ntldr on C:.

---

### Post by johnjacobt on 2009-12-15
Let me give you some info about what used to happen before installing Ubuntu and then maybe something would strike a bell and I'd get lucky .. just maybe...

When the laptop is booted, Pointsec message would come up saying "Loading operating system" and then XP would boot up.

Does this mean that Pointsec gets loaded before Windows XP and MBR would have the location of Pointsec as the start of disc (This may be rubbish from my imagination)

BTW, I have another laptop which has Pointsec encryped HDD with XP installed on it. But this one is of a different corporate and pointsec requires a password before XP is loaded.

---

### Post by darkod on 2009-12-15
I haven't used encryption, but yes, it seems Pointsec is loading first and then booting XP. Not sure how would you fix this one.

---

