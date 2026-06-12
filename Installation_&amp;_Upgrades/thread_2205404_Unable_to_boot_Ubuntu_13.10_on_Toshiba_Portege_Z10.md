---
title: "Unable to boot Ubuntu 13.10 on Toshiba Portege Z10-A"
date: 2014-02-13
forum: Installation &amp; Upgrades
---

### Post by sbrookfield on 2014-02-13
Just tried installing Ubuntu 13.10 from USBkey on laptop as above
Installing goes fine, tried various partitioning setups - from windows and ubuntu
Have tried both CSM(legacy) and UEFI boot
Have tried secureboot disabled and enabled
Have tried easyBCD
Neither work, it just boots windows
Then I tried boot-repair - [http://paste.ubuntu.com/6927373/](http://paste.ubuntu.com/6927373/)
Now it doesn't boot either - it just sits at bios
I would update my UEFI firmware but Toshiba website doesn't let it download...

Any ideas?
If anyones looking to buy Toshiba Portege z10-a for linux - I wouldn't recommend it!

---

### Post by Bucky Ball on 2014-02-13
Welcome. First thing's first. What was Windows installed in, EFI or Legacy? I'm presuming that was installed first. Whichever it was you MUST install Ubuntu in the same and you CAN'T change the disk from, say, EFI to Legacy if Win was installed in EFI. That will prevent Win from booting. If both were installed in one and you change it to the other, neither will boot.

So, whatever Windows was installed in, change the disk back to that, cross your fingers and see if you can boot at least Windows. The Ubuntu part should be relatively easy to fix.

Failing all else, boot from the Ubuntu install media, try ubuntu and get to a desktop and run Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can also burn a bootable CD of it and run from that.

---

### Post by sbrookfield on 2014-02-14
Thanks

So windows appears to be installed as a uefi boot - windows doesn't boot when I select legacy/csm boot in uefi bios. Windows was preinstalled on a gpt partition system. 

I've tried installing Ubuntu from USB booted as uefi, does not work. It puts all the necessary files in the uefi partition, but when booting it just hangs at the Toshiba screen and flashes occasionally something too fast to see. Holding shift etc doesn't get me into a grub console.

I've tried installing grub onto a separate uefi partition and also using the windows uefi bios, still either doesn't boot or just boots windows. I've tried using boot-repair to hard code grub over windows boot, it doesn't boot until you replace it with windows file.

The uefi firmware/bios doesn't really have any options for selecting boot choices - all I can chose is HDD vs USB vs lan. I think the UEFI Firmware may be the source of my problems but the update is unavailable on the Toshiba site... Ideal.

Anyone any other ideas?

Thanks for your help

Sam

---

### Post by sbrookfield on 2014-02-14
Solved it...

Managed to get hold of a bios update from a third party - no use, bios still no options and only boots Windows

Switched back to legacy boot
Reinstalled ubuntu from legacy boot with grub installed on sda and it just worked - not quite sure what I did wrong last time
Can't boot windows from grub but at least I can switch to windows by changing back from legacy to uefi boot

---

### Post by Bucky Ball on 2014-02-14
> **sbrookfield said:**
> ... at least I can switch to windows by changing back from legacy to uefi boot

And that is how it will remain as you have Ubuntu in legacy and Win in UEFI. Boot Repair can change the Ubuntu install to UEFI (as far as I know) and then you won't have this problem.

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Use BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

