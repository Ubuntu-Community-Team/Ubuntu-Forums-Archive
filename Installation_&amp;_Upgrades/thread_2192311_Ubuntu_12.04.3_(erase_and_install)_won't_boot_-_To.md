---
title: "Ubuntu 12.04.3 (erase and install) won't boot - Toshiba Z930"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by DaKellyFella on 2013-12-07
Hey guys/gals,

I've posted here previously about this issue (a couple of months ago) but the same fix hasn't seemed to work for me as it did back then.

Anyway my hard drive failed on my laptop so I sent it back off to Toshiba for repair. It came back with Windows 8 on it and so I thought I'd do the same as before and install Ubuntu on it.

I've installed Ubuntu (with erase and install entire disk) and ran boot repair (after turning if off and on again), I've done this twice with secure boot on and off with Intel Smart Response technology turned off in both cases.

Unforunately I don't have the pastebins from previous runs but I can gladly get them if needs be. Currently I've got Ubuntu installed with secure boot off but I can reinstall in any way people want to suggest.

Am I missing something obvious from what I've just described? Or am I really goosed?

Edit: I should say that when it won't boot I mean that it won't get passed the Bios splash of Toshiba. Basically I don't get any Grub and it hangs indefinitely.

Thanks in advance!

---

### Post by necromonger on 2013-12-07
is 12.04.3 installed?

---

### Post by DaKellyFella on 2013-12-07
Yep, I'm just not hitting grub. I've tried boot repair in multiple configurations (in terms of secure boot being on and off) with no joy.

---

### Post by ubfan1 on 2013-12-07
What do you have in the efi boot menu?  Hit F12 (maybe) to bring it up.  Or from live media, run sudo efibootmgr -v     to list the choices with their executables, so we can see what is failing to run.

---

### Post by necromonger on 2013-12-07
are you dual booting?

---

### Post by necromonger on 2013-12-07
either way here is a link
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by DaKellyFella on 2013-12-07
I'm not dual booting! Should I give it a read anyway?

---

### Post by oldfred on 2013-12-07
That was a link to Boot-Repair.
But you said you have tried Boot-Repair.
Best to post a link to the BootInfo report. You can just rerun it and post a new link.

---

### Post by DaKellyFella on 2013-12-07
Apologies for the delay. So anyway I've just done a fresh install of 12.04.3, secure boot on and just ran boot repair - [http://paste.ubuntu.com/6538230/](http://paste.ubuntu.com/6538230/)

I can try again with secure boot off if you think that'd make any difference!

---

### Post by DaKellyFella on 2013-12-07
> **ubfan1 said:**
> What do you have in the efi boot menu?  Hit F12 (maybe) to bring it up.  Or from live media, run sudo efibootmgr -v     to list the choices with their executables, so we can see what is failing to run.

Hey, I ran "sudo efibootmgr -v" and got the output:

BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0005,0000,0004,0003,0001
Boot0000* HDD/SSD    ACPI(a0341d0,0)PCI(1f,2)ATAPI(0,0,0)
Boot0001* LAN2    ACPI(a0341d0,0)PCI(19,0)MAC(e8e0b771b165,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0
Boot0002* LAN1    BIOS(80,0,50)........................A..............................................
Boot0003* LAN1    ACPI(a0341d0,0)PCI(19,0)MAC(e8e0b771b165,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000
Boot0004* USB Memory    ACPI(a0341d0,0)PCI(14,0)USB(0,0)
Boot0005* ubuntu    HD(1,800,2f000,fe8e70dd-d7cf-454a-bad9-fca1f1d9fa98)File(\EFI\ubuntu\shimx64.efi)

I apologise in advance if this looks like crap. Do I wrap them in code tags?

---

### Post by ubfan1 on 2013-12-07
Looks like you have a secure boot setup which should work.  Can you get to the efi boot menu (F12 ?) and select ubuntu?  I had no particular problems with a Toshiba S855.

---

### Post by DaKellyFella on 2013-12-07
Hmm OK. I'm trying to get into it. When I press F12 I get taken to a screen where I can chose the device to boot off (Hard-drive, USB...). The only 2 keys that appear to work are F2 (bios) and F12 (boot selection). I'll keep trying and search for my laptop's command.

---

### Post by necromonger on 2013-12-08
grub on a single boot system.
[http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time-on-a-single-boot-system-not-dual-boot](http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time-on-a-single-boot-system-not-dual-boot)

---

### Post by DaKellyFella on 2013-12-08
Just read that, it doesn't work. My problem is I don't even get to grub. I'm stuck on the Toshiba bios splash. It seems like there's nothing bootable present.

---

### Post by oldfred on 2013-12-08
Is your UEFI/BIOS the most current version from Toshiba?

I thought this was older models?
 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries

And some systems are hard coded in UEFI to only boot Windows. Some now have newer UEFI updates as a fix for that.
      
 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by DaKellyFella on 2013-12-10
Hey guys, sorry for the delay. I was in college being all busy etc! Anyway I took it to the local guru in my college, he changes the bios options so that it booted in legacy mode and not efi mode, booted it up with some recovery stick, changed grub so that it was the normal one rather than efi grub - done.

Then I did a full re-install in the legacy mode and everything worked fine (again). No efi partition and a normal vanilla install of Ubuntu.

Thanks for all your help.

---

