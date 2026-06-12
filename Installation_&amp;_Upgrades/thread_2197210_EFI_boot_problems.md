---
title: "EFI boot problems"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by droidadam on 2014-01-02
I'm having trouble getting the bootloader to install on my Thinkpad x120e.The installation fails at grub2. Boot-repair fails,I'm guessing because there's nothing to repair. i've done a lot of reading but can't seem to put it all together. My best guess is I need to install a bootloader then tell efi where to find it. I am not dual booting.  I'd rather have terminal commands than a gui solution. Please help, thanks.
Boot-repair output [http://paste.ubuntu.com/6680332/](http://paste.ubuntu.com/6680332/)

---

### Post by varunendra on 2014-01-04
Welcome to Ubuntu Forums droidadam !

I'm not a booting expert, but as you can see in the boot-info report yourself, there seem to be multiple filesystem errors on both the source (7 GB USB) and destination (320 GB hdd) drives.

As such, have you tried to start from scratch in this while? That is, recreate the Live USB (preferably after deleting -> recreating the partition on it, and using some recommended application like Unetbootin or Universal USB installer etc.) > boot with it > use GParted to delete the partitions on the hdd > recreate them (1 500MB FAT32 for EFI, 1 22-26 GB EXT4 for /, rest data partition) > retry installing with EFI support.

If possible, give us a screenshot of the error if it happens again.

Also, have you checked the integrity of the ISO you are using to create the Live USB? It seems you are trying Mint, but the method to check the integrity (MD5sum or SHA) should be similar to this : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Apart from MD5Sum, also check the Live USB itself ("Check for defects" or whatever similar option is available on the Mint Live USB).

---

