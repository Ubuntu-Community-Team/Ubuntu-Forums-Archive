---
title: "[UEFI] Loosing hdd bootable partition when trying to temporary boot on usb key"
date: 2016-01-30
forum: Installation &amp; Upgrades
---

### Post by SwanMougnoz on 2016-01-30
Hello everyone,

 I'm requesting your help on a problem that struggle me for day now...
 Here is the story : I installed a ubuntu mate 15.04 on my desktop in uefi mode, it was the first time I had to deal with this it was a pain. Nothing was correctly working, first the installation succeed and then I was unable to boot. I tried several things like recommended install on the whole hdd after properly formated it : fail. Manually create an efi partition on a new gpt partition table and then configure my install "manually" : fail a couple of time and magically work without doing anything more (yay!). 

But the problem is : Recently, I had to install some Windows on a laptop so a created a bootable usb for it (uefi mode too), I simply plug this on my desktop with the intent to make sure it was working. It worked so I removed it and try to reboot on my ubuntu and then : my BIOS seems to have lose the bootable partition and display me the same message I had when my previous install failed.

I'm confused... I tried to use boot-repair software to this but it didn't change anything. Could someone help me on this please ?

Here is the boot-repair pastebin I got : [http://paste.ubuntu.com/14696653/](http://paste.ubuntu.com/14696653/)

I'm not expert but I read line 20-21 that there is microsoft entry on the efi partition ?! Is this normal ?

Thank in advance for your help and sorry for the english, I'm french, I try to do my best^^

---

### Post by oldfred on 2016-01-31
Did you have Windows on this system before?
If so the old Windows entry in the ESP - efi system partition would not have been erased with an Ubuntu install unless you manually erased the ESP. Ubuntu normally reuses the existing ESP.

And you show a Windows UEFI boot entry in UEFI boot. That also is not erased from UEFI's NVRAM unless you disconnect drive or manually erase it with efibootmgr.

I would be a bit surprised if just booting the Windows installed added those entries. But Windows does make itself first in boot order with just about any maintenance or update. So you have to regularly reset that.

First delete the /EFI/Microsoft folder in the ESP, or else UEFI may add it back on a reboot. Then use efibootmgr to remove NVRAM entry.
 Check entry is there.
sudo efibootmgr -v 

   Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

### Post by SwanMougnoz on 2016-02-20
Thanks you, it worked ! :)
I had to additionnaly use boot-repair with the "remove hard coded microsoft efi entry" option to get it right but now everything is fine.
Marked a solved.

---

