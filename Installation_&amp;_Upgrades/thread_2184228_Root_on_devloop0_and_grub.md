---
title: "Root on /dev/loop0 and grub"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by mystrangeusername on 2013-10-28
Hi,
my Ubuntu has /dev/loop0 mounted as root. I wonder what that means: maybe it is a partition hosted in a windows file?
I would like to have a three boot with Windows, Ubuntu and Gentoo but I will not know how to set the grub bootloader to boot using /dev/loop0, would it be able to see it?

---

### Post by oldfred on 2013-10-28
That is a wubi install inside the Windows NTFS partition and uses the Windows boot loader. You then boot from Windows boot option if you have another install that uses grub2.

You may be able to direct boot it, but will have to manually add an entry to 40_custom. Example is with install in sda2.
       wubi direct boot
```
menuentry "Wubi" {
insmod ntfs
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
initrd /initrd.img
}
```

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
    
wubi is being discontinued as it does not work with new systems
 Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)

---

