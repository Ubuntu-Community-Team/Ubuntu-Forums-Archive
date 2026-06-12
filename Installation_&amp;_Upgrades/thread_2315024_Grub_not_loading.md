---
title: "Grub not loading"
date: 2016-02-25
forum: Installation &amp; Upgrades
---

### Post by van6 on 2016-02-25
http:://pastebin.ubuntu.com/15200794/ locked esp error even though esp is not locked. Surface pro 3 efi

---

### Post by oldfred on 2016-02-25
Are you running from live installer or from the install?

Boot-Repair makes this change in fstab, but it does not take effect until you reboot. 0077 means no permissions to do anything.
>  # /boot/efi was on /dev/sda1 during installation
#UUID=2C1C-5094  /boot/efi       vfat    umask=0077      0       1
UUID=2C1C-5094    /boot/efi    vfat    defaults    0    1



Have not seen recently but some ESP - efi system partitions had some sort of corruption. Some were fixed with chkdsk from Windows or a fsck from Ubuntu.
 sudo fsck.vfat -t -a /dev/sda1
Others had to fully backup partition, erase it with gparted. Then create new FAT32 partition with boot flag. You also then have to edit fstab with new UUID.

---

### Post by van6 on 2016-02-26
Hmmm... For some odd reason the **surface pro 3** doesn't seem to accept any of the common solutions. I'm going to list out the solutions I've tried in case anyone wants to save themselves some time.

1. DUAL BOOT WORKS plenty of resources for that. I have no idea why it works, but it is pretty well documented that it works.
2. wiping drive and installing X linux doesn't work regardless of UEFI compatibility. (specifically tried mint, ubuntu 15.10, 14.04, arch)
3. Boot repair doesn't work
4. Replacing efi/boot/*.efi bootloader doesn't work (makes your screen blink a lot though)
5. Unetbootin doesn't work (will give you grub shell)
6. Grub2win doesn't work (same as above)
7. Creating your own FAT32 partition with boot flag and running Boot repair using that partition.

best resource: [https://www.reddit.com/r/SurfaceLinux/](https://www.reddit.com/r/SurfaceLinux/)
Again this is for **surface pro 3**.

---

### Post by oldfred on 2016-02-26
Do not know if any of Surface Pro 2 comments may apply or not.

 Surface Pro Ubuntu install:
Surface Pro 3 - USB/MicroSD Only Install 
[http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798](http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798)
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)
Surface Pro2 mega thread:
[http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946)
[http://ubuntuforums.org/showthread.php?t=2209247](http://ubuntuforums.org/showthread.php?t=2209247)

---

