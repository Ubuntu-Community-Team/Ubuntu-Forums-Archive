---
title: "Get Grub 2 Boot Sector"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by js71296 on 2011-04-27
Hi,

I need to get the boot sector of my grub installation, I tried using 'sudo  dd if=/dev/sda7 of=/mnt/floppy/linux.lnx bs=512 count=1' but when I hex-edited the file, it was all zeroes. SDA7 is my /boot partition. I'm trying to get the boot image so i can use ntldr to boot linux.

any help is appreciated,
js71296

---

### Post by dino99 on 2011-04-27
[http://ubuntuforums.org/showthread.php?p=9605758](http://ubuntuforums.org/showthread.php?p=9605758)

---

### Post by js71296 on 2011-04-27
So, will I have 2 reinstall Ubuntu to fix the problem? oh and my version of windows is windows 7 so i don't have a BOOT.INI :P

> **alienkid10 said:**
> Ok got it to work.

How:

Install Ubuntu to sdb2/hd1,1 formatted as ext3(4 would probably work)
at the final screen click advanced and have bootloader install to sdb
reboot to Windows and download GRUB4DOS place grldr at the root of C: make a menu.lst at the root of C: then add ```
timeout 0
default 0
title grub2
kernel (hd1,1)/boot/grub/core.img
boot
```add ```
C:\grldr="Ubuntu"
``` to the last line of boot.ini
reboot
at the NTLDR menu pick Ubuntu after a few seconds it will show GRUB then  boot Ubuntu. Only problem is I don't see boot splash or and boot info  it just stays black until GDM/desktop.

---

### Post by oldfred on 2011-04-27
Where did you install grub2's boot loader. Just haveing a boot partition for the rest of grub does not include the boot loader. It is normally installed to the MBR. Note that installing grub2 to a Partition boot sector is considered unreliable as it uses blocklists.

I like grub2, but I saved this from another post for those who insist on using windows. It is not the windows boot loader but another third party boot loader.

downloaded EasyBCD, which makes it very easy to add Ubuntu to Vista's boot loader menu.
I have a triple boot (vista, xp, ubuntu). What I did was install vista, then xp. Next repaired vista's bootloader with a repair 
disk. Then used easybcd (from Neosmart) and added xp bootloader files to vista's. Next installed ubuntu as per a 'normal' dual boot, where grub installed to the mbr where grubs root is (hdx,x) depending on your partition numbers and setup (hd0). Hope it helps. Easybcd should be able to handle vista/win7 bootloader files without issue.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---

### Post by js71296 on 2011-04-27
I used a program called "BACKUPMBR" for windows to backup my GRUB MBR **(Don't use it to restore the MBR though, or it will destroy your linux)** and then I rewrote my Windows MBR and now it works :D

Thanks Guys for ur Help :D

---

