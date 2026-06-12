---
title: "How to add grub boot item to installation usb when it's read-only?"
date: 2019-05-10
forum: Installation &amp; Upgrades
---

### Post by left4taco on 2019-05-10
I need to install ubuntu on multiple machines so preseed would be very useful. 
Here's the grub item that I would like to add,
```

[COLOR=#000000][FONT=Menlo]   menuentry "DANGER! This will reprovision you machine" {        set gfxpayload=keep
        echo "Please enter your device type(desktop, spectra):"
        read device
        echo ""
        echo "Please enter the hosename of the new machine:"
        read hn
        linux /casper/vmlinuz url=http://x.x.x.x:5000/preseed/$device/$hn boot=casper debian-installer/locale=en_US keyboard-configuration/layoutcode=us ubiquity/reboot=true languagechooser/language-name=English countrychooser/shortlist=US localechooser/supported-locales=en_US.UTF-8 automatic-ubiquity quiet splash noprompt noshell ---
        initrd /casper/initrd
[/FONT]
[FONT=Menlo]    }[/FONT][/COLOR][COLOR=#B5B3AA][FONT=Menlo]
[/FONT][/COLOR]
```

However, after I followed the official tutorial of creating bootable usb stick, it's always write protected which means I can only mount it as readonly. The partition table is like:

```

sdb      8:16   1  29.3G  0 disk
&#9500;&#9472;sdb2   8:18   1   2.4M  0 part
&#9492;&#9472;sdb1   8:17   1   1.6G  0 part

```

[COLOR=#8959A8][FONT=Consolas]So in this case, how can I create a bootable usb stick while being able to copy files to it?


[/FONT][/COLOR][SIZE=3][FONT=Consolas]========
Solved. Format the disk to FAT and copy everything from ISO. It's now both bootable and writable. [/FONT][/SIZE]

---

### Post by yancek on 2019-05-11
Is that a typo and you meant "NOW" both bootable and writable rather than not?

Loop mounting the iso and then copying it to a partition on the usb should work to modify and it doesn't need to be a FAT filesystem.
Another method would be to create a boot directory on the usb and then install Grub to the usb and manually modify grub.cfg.  This method allows you to simply copy the iso to a partition on the usb.

---

### Post by C.S.Cameron on 2019-05-11
@left4taco
Your system works on UEFI boot but not on older BIOS boot computers.
Mkusb builds a nice grub2 drive that boots both BIOS and UEFI.
Sdx4, the ISO9660 OS partition can be replaced with anything from ISO files to a clone of your desktop system.
The grub.cfg file in sdx2 can be edited to boot them.

---

### Post by left4taco on 2019-05-14
Yes `not` is a type and has been fixed. I'll look into your second solution. Thanks.

---

