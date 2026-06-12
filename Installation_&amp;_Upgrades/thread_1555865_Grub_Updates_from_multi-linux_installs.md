---
title: "Grub Updates from multi-linux installs"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by trogbot on 2010-08-18
Advice Needed.  I now run 2 versions of Ubuntu on my computer, each loaded to a different disk.  32 bit version which I installed, pointing grub to my first hard drive.  Later installed 64 bit version to another drive & grub installed to that drive.  When I updated 64 bit version, had to go into 32 bit version & run update grub for updated grub menu to appear correct.  I now want to install 64 bit Kbuntu to the disk where 64 bit Ubuntu is installed.  Can I point the Kbuntu grub to my first hard disk also & then when updates occur on either install, grub is updated automatically.  The fact that one is 32 bit & the other 64 bit have any consequences?  Will the way grub updates be affected by the order it finds things in if the other install was the last to update & visa versa?  Any advice or help is greatly appreciated.

---

### Post by oldfred on 2010-08-18
No.

Your system only can boot from one MBR and that MBR can only point to one copy of grub2. You can have either install in either MBR but I prefer to have each drive be able to boot in case on drive fails. You have to use the advanced button to make sure grub2 installs to the correct drive.

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

You can add to 40_custom a boot stanza that boots the most current version. You can also chainboot from one to another which I do. But the chainboot entries are a little confusing as the boot drive is hd0 in grub regardless of whether in Ubuntu it is sda or sdb.  

If you add this (with your drive & partition) to 40_custom then you will automatically boot the most current version.
from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

Or you can chainload to hd1:

menuentry "Lucid Lynx on sdb (When from sda) Chainboot" {
set root=(hd1)
chainloader +1
}

I think the above actually will work in either grub as the boot drive will be hd0. It is more confusing for me as I have 3 drives and drive numbers vary.

---

### Post by trogbot on 2010-08-18
Thanks for the 40_common info.  Will take that approach & mark this puppy solved.  Thanks again for the help.

---

