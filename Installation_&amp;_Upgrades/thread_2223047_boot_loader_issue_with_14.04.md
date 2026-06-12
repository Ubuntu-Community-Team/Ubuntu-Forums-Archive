---
title: "boot loader issue with 14.04"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by srikanth3 on 2014-05-09
I ran in to a silly problem when i installed Ubuntu 14.04 along with my existing windows 8.1. The problem is that when i boot my laptop it boots windows. when i restart it from windows it shows the grub menu and allows me to pick my OS, but when i reboot it from Ubuntu then it straight away boots windows again. so any ideas how i can get to grub menu when i first boot it up or reboot from Ubuntu?
thanks, help is much appreciated.

---

### Post by kc1di on 2014-05-09
with windows 8.1 and UEFI/secureboot every manufacturer seems to have there own spin on the boot process. there should be a setting in (What we used to call bios) now most machines i've dualbooted with call it something like boot settings.  that allows a menu to come up before boot.  What type of laptop is it? that may help getting an answer from some one.
I've have good luck with [Refind boot manage]("http://www.rodsbooks.com/refind/")r you may want to take a look at it.

---

### Post by srikanth3 on 2014-05-09
thanks for the reply. Mine is sony vaio svf14218snb, if that helps. yeah i've disabled the secure boot and boot type is still UEFI.

---

### Post by kc1di on 2014-05-09
you may also want to run boot-repair found [here]("https://help.ubuntu.com/community/Boot-Repair").
follow the instructions on the page and pay careful attention to the instruction given when you run boot-repair.

---

### Post by ubfan1 on 2014-05-09
From the Ubuntu side, you can run efibootmgr to list and alter the boot order in nvram.  Just move the "ubuntu" entry to the first slot in the boot order.
efibootmgr -v 
will list the existing boot entries and the boot order.

---

### Post by srikanth3 on 2014-05-10
thanks. my boot order from efibootmgr is as it shows here:
       $:  sudo efibootmgrBootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002,0000,0001,2001,2002,2003
Boot0000* Windows Boot Manager
Boot0001* Ubuntu
Boot0002* Ubuntu
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network



what does that ubuntu at the address Boot0001* refer to, can i delete it. how to delete the entry and also if the installation is active how do i delete it completely?

---

### Post by srikanth3 on 2014-05-10
I did run the boot repair and it generated this txt file saying an error occurred during the repair so here is the file i can't make any sense of that file, being a newbie myself. hope you can help me thanks

---

### Post by ubfan1 on 2014-05-10
It looks like boot-repair added the grub boot files to /EFI/ubuntu, and made an entry to boot it, placing it first.  Did you try to boot?  You should be in UEFI mode, not compatibility mode or legacy.  You have a grub installed in legacy/MBR mode, but now with the UEFI boot files, hopefully, the old grub will  just be ignored.  If the grub menu does not show, try typing a function key (varies by machine) to bring up a boot menu for devices/OSes and see if you can select ubuntu to bring up grub.

---

### Post by srikanth3 on 2014-05-11
I don't know how but my problem got solved. i ran the boot repair again and it said error got reported and gave me url which is  [http://paste2.org/Dd1mmpzt](http://paste2.org/Dd1mmpzt) and said i can reboot my laptop. so i did and voila  grub menu appeared. thank you people.

---

### Post by oldfred on 2014-05-11
BootInfo is showing no efi boot files in sda3??
You should have both Windows efi files in a Microsoft folder and Ubuntu's efi files in an ubuntu folder.

You still have a grub in the MBR for BIOS boot, just do not boot with BIOS as that will not work.

---

### Post by srikanth3 on 2014-05-13
Thanks oldfred, i used efibootmgr command and interestingly my laptop started showing grub menu at every boot up....

---

