---
title: "cannot chainload LinuxMint"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by codemaniac on 2010-02-26
Hello Ubuntuites,
i am having a wierd problem chainloading Linux mint 8...
let me first describe my story..I have installed Ubuntu karmic,Suse 11.2 ,Fedora 12, Mint halena in my box.
Ubuntu's bootloader(grub2) is at the MBR.other operating systems respective grubs are at their root partitions..Now i have edited 40_custom and added all the entries needed to chainload the operating systems..this way i am able to chainload suse and fedora....
BUT the problem is when i tried chainload Linux MINT...with the commands
menuentry "Mint@[sda9]"{
set root=(hd0,9)
chainloader +1
boot
}

i got invalid signature erro..cant chainload linux mint..although linux mint's grub2 is at /dev/sda9...
my 40_custom file is attached below..Thanks in advance..

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu 9.10" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set aeaf6f71-8b36-4669-8b48-0e04066f6ff1
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=aeaf6f71-8b36-4669-8b48-0e04066f6ff1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10 (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set aeaf6f71-8b36-4669-8b48-0e04066f6ff1
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=aeaf6f71-8b36-4669-8b48-0e04066f6ff1 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8614c4ff14c4f36b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Suse 11.2[@sda10]"{
set root=(hd0,10)
chainloader +1
boot
}
menuentry "Fedora 12[@sda5]"{
set root=(hd0,5)
chainloader +1
boot
}
menuentry "Mint[@sda9]"{
set root=(hd0,9)
chainloader +1
boot
}

---

### Post by codemaniac on 2010-02-26
no one  have any idea where i am going wrong???

---

### Post by oldfred on 2010-02-26
This script will tell us if the boot loaders are in the correct places and other info required for booting:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by recluce on 2010-02-26
Sorry, I cannot help you there. I find GRUB2 to complex for a simple chainloading task.

In your situation, I would create a dedicated GRUB partition (Legacy GRUB from an EXT4 aware distribution like Jaunty) and chainload into the individual bootloaders (including Ubuntu's GRUB2) from there. This also has the advantage of not loosing GRUB settings when you reinstall Ubuntu - and you will not have to maintain the other distribution's kernel entries manually, in case they are not detected after an update.

Check out this guide:

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

### Post by codemaniac on 2010-02-26
Thanks Friends for your replies...
@oldfred : i have tried to download the script from sourceforge.net but in vain..seems like the link doesn't work..can you please upload the script here...

---

### Post by codemaniac on 2010-02-26
@reluce:: thanks 4 ur reply pal...The problem is that i cannot chainload any GRUB2 from ubuntu's grub2(MBR)....but i can chainload distros which use legacy grub...
your idea of separate partition looks cool..i 'll check that out...

---

### Post by oldfred on 2010-02-27
I just downloaded script to see if download works with no problem, what was your problem? Perhaps the site was being updated.

---

### Post by codemaniac on 2010-02-27
i m still not able to download that script...Can't figure out where in fell the problem lies!!!!

---

### Post by oldfred on 2010-02-27
Are you not clicking thru to the download page (purple download boot_info_script line or the title that also is purple) with the big green button. I like to link to the instructions page as most do not know how to run it. 

linked download page.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

