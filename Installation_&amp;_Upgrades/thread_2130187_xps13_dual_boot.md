---
title: "xps13 dual boot"
date: 2013-03-28
forum: Installation &amp; Upgrades
---

### Post by belano on 2013-03-28
Hi,

I've been trying all day to setup a dual boot installation on a dell xps 13 (bios ao7) with windows 8 (preinstalled) and ubuntu (12.04 sputnik iso).

I've only managed to install ubuntu booting from usb stick in legacy option rom mode and uefi boot, after that I've run boot-repair which gave me the following info

[http://paste.ubuntu.com/5655997/](http://paste.ubuntu.com/5655997/)

Sadly grub does not show up, laptop boots straight away into windows.

Can anyone please help me to understand the above boot-repair output?

Thanks

---

### Post by oldfred on 2013-03-28
Have you tried going into UEFI and selecting ubuntu entry from the UEFI menu?

It looks like Boot-Repair converted install to UEFI and installed the efi version of grub. But you have to choose that in UEFI like changing which drive's MBR to boot from when you have multiple disks. You have multiple boot loaders in the efi partition.

       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)

Other issues:

 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

---

### Post by belano on 2013-03-29
Hi oldfred,

I gave up with 12.04 sputnik image as it seems it can't boot on uefi mode. I tried instead with 12.10, managed to install but after running [boot-repair]("http://paste.ubuntu.com/5658624/"), windows entry in grub gave me 'invalid EFI file path'.

Manually added the following entry to 40_custom grub config file and run update-grub

menuentry "Windows 8 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

This entry seems to do the trick and manages to boot windows okay.

PS: how can I mark this thread as solved?

---

### Post by oldfred on 2013-03-29
Glad you got it resolved. 

Was your 12.04 not 12.04.2 as you needed that or 12.10 to have secure boot capability.

See my signature below for current work around on Solved.

---

### Post by belano on 2013-03-29
I was trying to install [this]("http://hwe.ubuntu.com/uds-q/dellxps/amd64/sputnik-precise-amd64.iso") image from dell.

Thanks

---

### Post by oldfred on 2013-03-29
It looks like that may have been based on 12.04. Only 12.04.2 or 12.10 has the updates to grub and kernel to support secure boot and the new XPS all are now Windows 8 with secure boot.

May be better to be bleeding edge?

> ALL FIXES HAVE BEEN INCORPORATED INTO Ubuntu Raring (13.04) as of  Raring kernel version 3.8.0-7.15.  This PPA is no longer necessary for  Ubuntu Raring!



---

