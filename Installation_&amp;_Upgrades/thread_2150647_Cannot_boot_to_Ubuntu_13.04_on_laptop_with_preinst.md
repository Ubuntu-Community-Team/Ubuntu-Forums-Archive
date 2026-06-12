---
title: "Cannot boot to Ubuntu 13.04 on laptop with preinstalled Win8 (UEFI)"
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by nicosc on 2013-06-01
Hello,

I have been trying to install Ubuntu 13.04 on a laptop that came with  Windows 8 pre-installed (UEFI; I am a veteran Linux user, but completely  new to UEFI).

I have been unable to get the laptop to boot Ubuntu (I have installed  Ubuntu on a separate partition, using a newly created UEFI partition to  boot from).

I tried to repair the boot using boot-repair ([http://paste.ubuntu.com/5723354](http://paste.ubuntu.com/5723354)).

Boot-repair indicated that I should tell my BIOS to set the boot to the  /sda8/EFI/ubuntu/shimx64.efi, but unfortunately I have no clue how to do  this (I can get into the BIOS, but AFAICS I can only disable UEFI, not  change a bootpath).

I would really appreciate any help!

Thanks,

Nico

---

### Post by thefirstwolfman on 2013-06-02
Try booting your machine then hitting F2 to bring up the BIOS options. You will need to go to the security section to disable secure boot. This should work but you may need to alter the boot option order.

---

### Post by nicosc on 2013-06-02
I can get into the BIOS and disable UEFI, however, I cannot disable secureboot separately: the only option is to switch to legacy mode. I could get Ubuntu to work in legacy mode I guess, but as far as I understand UEFI, I would not be able to boot to Windows anymore (which is installed under UEFI)?

---

### Post by arpanaut on 2013-06-02
Hopefully this post will help you get things sorted.
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

EDIT: did you disable the quick boot/ fast boot in win8 with all the errors of not allowing mounting of the windows parts.
I would suspect this is the case... but I am just guessing.  You may need to disable this in bios/uefi too.
A lot of good information in the link above.

---

### Post by nicosc on 2013-06-02
Hi,

thanks for your replies. I have been able to fix one problem (and am left with another):

1. The problem was that my EFI partition was corrupted (could boot from it, but not add files to it). I managed to fix that with fdisk -r.
2. Now I get the boot menu, and can successfully boot Ubuntu. Booting Windows now is no longer working (still looking into this).

-Nico

---

