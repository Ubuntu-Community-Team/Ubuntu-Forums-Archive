---
title: "&quot;ALERT! /dev/mapper/my-root does not exist&quot; for encrypted root partition"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by rothmans on 2011-06-29
Hi all,

I had a machine running Ubuntu 8.4 with 2 LUKS encrypted hard disk drives mounted as / and /home. After 2 years of good work I decided to upgrade the OS to 10.1. So I ran the upgrade which has succeeded over night (it is pretty old machine).
After upgrade the machine was restarted and after a splash screen I get now the error message
"ALERT! /dev/mapper/my-root does not exist. Dropping to a shell"

The /dev/mapper/my-root does not exist of course.
If I run
```

mkdir -p /mnt/root
cryptsetup luksOpen /dev/sda5 my-root
mount -t ext3 /dev/mapper/my-root /mnt/root

```
The /dev/mapper/my-root appears in place and I get my root partition perfectly opened and mounted to the /mnt/root. 

So I guess everything I need to boot my system now is simply to make above process happen automatically on boot.
As I can see in the /etc folder (being in the initramfs console) there are neither fstab nor crypttab files.

Do I understand correctly that in order to fix my machine I need to mount (natureally unencrypted) boot partition, extract initrd of the new Ubuntu version, add fstab and crypttab to the image, pack it back and edit grub's menu.lst to pick up my customized initrd image?

I am stuck at the moment actually with the fact that I cannot pack the initrd back since busybox's cpio apparently supports only unpacking (-o flag throws an error) so I need to get some Linux boot CD to do that from there. Until then I'd like to ask for an advise, whether I am on the right path or do I miss something very basic?

Thank you very much!

---

