---
title: "Grub2 missing menu items"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by Snark1994 on 2010-09-01
Hiya

I thought I'd try my hand at a pure CLI distribution, so installed  Gentoo. However, when it got to the stage of installing a bootloader I  declined as I already had it working nicely in Ubuntu and I didn't want  to boot into Gentoo every time I wanted to change stuff... When I  rebooted, it didn't show Gentoo (as expected) so I went into Ubuntu as  per normal and ran "sudo update-grub", which gave me:
```

joshua@joshua-desktop:~$ sudo update-grub
[sudo] password for joshua: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows XP Professional x64 Edition on /dev/sda1
Found Gentoo Base System release 1.12.13 on /dev/sda8
done
joshua@joshua-desktop:~$ 

```However, when I rebooted again it didn't have any options for Gentoo (XP  was the last option on the list). I did a bit of research, and the  closest thing I could find to it was people missing the most recent  kernel, all of whom had done some messing with menu.lst (which doesn't  even exist under the new Grub). I finally found an article ([link]("http://computerdoctor-mitchel.blogspot.com/2010/07/adding-missing-menu-items-to-grub2.html")) which explained how to manually add a menu entry to Grub2, using the 40_custom file. The file's contents are currently:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Gentoo" {
    insmod ext4
    set root='(hd0,8)'
    drivemap -s (hd0) ${root}
    chainloader +1
}

```...which gives me 2 errors about "file not found"  and another which has  slipped my mind for the moment, and drops me to the grub prompt. I have  little idea exactly what the stuff in the 40_custom file is doing (I  guess "insmod" is giving the filesystem, and "set root" is telling it  which partition to boot from). Can anyone give me pointers either to  where I'm doing something stupid in order not to get the menu item to  appear, or to some info on how to fix the custom menu item?

Thanks,
Snark

---

### Post by Snark1994 on 2010-09-02
Ah, problem solved.

I had neglected to install grub onto the Gentoo partition. I ran "emerge grub", and then tinkered with the /boot/grub/grub.conf file (Gentoo doesn't use Grub2), and then re-ran "sudo update-grub" from Ubuntu, and it found both the default menu item and the custom one I added :)

---

