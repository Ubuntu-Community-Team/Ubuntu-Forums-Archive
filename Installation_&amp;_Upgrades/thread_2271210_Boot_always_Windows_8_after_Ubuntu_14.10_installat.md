---
title: "Boot always Windows 8 after Ubuntu 14.10 installation"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by TWEESTY on 2015-03-28
Hello all!

I installed Ubuntu 14.10 in UEFI Mode, but after installation my computer always starts on Windows 8 and don't let me choose between Ubutun and Windows 8.
I tried to solve the problem with boot-repair, but I have the same issue, herebelow the url : [http://paste.ubuntu.com/10695221/](http://paste.ubuntu.com/10695221/)

Thanks for your help :=)

---

### Post by googleorganico on 2015-03-28
May be you have to go in to the windows 8 and ***disable fast boot when having dual boot***! Look this :  [http://askubuntu.com/questions/452071/why-disable-fast-boot-on-windows-8-when-having-dual-booting](http://askubuntu.com/questions/452071/why-disable-fast-boot-on-windows-8-when-having-dual-booting)

---

### Post by TWEESTY on 2015-03-28
My SecureBoot was disabled, but thanks to your follow thread, I found the solution :

bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

Thanks

---

### Post by Vignesh_S on 2015-03-28
I think boot loader _**gurb**_ was not installed or installed properly.

---

### Post by oldfred on 2015-03-28
At some point grub was installed in BIOS boot mode to gpt's protective MBR. 

But Summary report shows grub in efi partition and loading efi partition in fstab, so it is currently in UEFI boot mode.

---

