---
title: "Re-Order grub2 order?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by woodbj on 2009-10-04
I'm wondering how to re-order the grub menu so that it goes 1. Karmic 2. Windows Vista then the rest ie recovery, memtest

---

### Post by tsger on 2009-10-04
You need to change the numbering of the files in /etc/grub.d.  Make sure to read the README file in that directory, too.  Be careful, there are certain limitations on how the files are numbered and which numbers they can be.

I have found the following link to be very helpful in understanding the new Grub2:
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

Here is a quote from that page:

Quick reference
The (standard) files in /etc/grub.d (each is a script) are:
00_header
05_debian_theme: Set background, text colors, themes
10_hurd Locates Hurd kernels
10_linux Locates Linux kernels based on results of the lsb_release command.
20_memtest86+: If the file /boot/memtest86+.bin exists, it is included in the boot menu.
30_os-prober: Searches for Linux and other OS's on all partitions; includes them in the boot menu.
40_custom: A template for adding custom boot menu entries.

---

### Post by ikisham on 2009-10-04
A much simpler guide is [here]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=edit+grub2").
I imagine that basically you should rename 30_os-prober to a number between 5 and 9, like 06_os-prober
This way Windows will be detected before the Linux entries.
After renaming the file run ```
sudo update-grub
```

EDIT- sorry, I misread your question. To put Windows before the Linux (recovery mode) entry I think it's more complex since grub2 runs a script to detect the o.s. and build the menu. What you could do is the change above so Windows will be the first in the list and then edit /etc/default/grub to make Karmic the default (even being second on the list - change GRUB_DEFAULT=0 to GRUB_DEFAULT=1).

---

### Post by ranch hand on 2009-10-05
The simplest way to do what you want is to create a custom entry in /etc/grub.d.  Do this by opening 40_custom in your favorite text editor (I like gedit).

Make sure that you go to preferences and turn OFF line wrapping.

You can do an entry like this;
```

echo "Adding DailyB on sda7" >&2 
cat << EOF
menuentry "DailyB on sda7" {
        set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 so quiet splash
        initrd /initrd.img
}
EOF

``` 
for Karmic and you should be able to boot from it with out any updates to the entry.  As we are still getting a lot of updates to grub I would also put in an entry like this (suitably edited to your box);
```

echo "Adding NoUpdateA4 on sda12 (2.6.31-10-generic)" >&2 
cat << EOF
menuentry "NoUpdate on sda12 2.6.31-10-generic" {
    set quiet=1
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set 0944b738-832a-4d1a-8822-fd5f7a2f65a1
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=0944b738-832a-4d1a-8822-fd5f7a2f65a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-10-generic
}
EOF

```
and then add your Windows menu entry.

It should follow the same pattern as the above entries.  The part of the entries that ends up in your /boot/grub/grub.cfg file (and thus on your screen) is this;
```

menuentry "NoUpdate on sda12 2.6.31-10-generic" {
    set quiet=1
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set 0944b738-832a-4d1a-8822-fd5f7a2f65a1
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=0944b738-832a-4d1a-8822-fd5f7a2f65a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-10-generic
}

```
Make sure that All of the stuff before and after the above is there too.

Save your new custom file as 06-custom.  This puts it after the instructions for the operation of grub.d and before the stuff that generates your other menu entries.  This will put your custom entries at the top of your menu that you see on the screen.  If it all works and that is all you are going to have on your box, you can cange the permissions for 10_linux, 20_memtest86+, and 30_os-prober so that they are not executable and then your custom entries will be the only menu that you get.

---

