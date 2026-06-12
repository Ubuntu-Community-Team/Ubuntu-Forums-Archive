---
title: "Boot alternate root filesystem"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by HankB on 2011-10-15
At present my 10.04 LTS system is configured with the following file systems:

/ (/dev/md0)
/boot (/dev/md0)
/home (/dev/md3)

I have just installed another drive and have copied the root file system to it. (/dev/sdc1) With it mounted to /mnt/ssd I have run 'update-grub.' Grub correctly identifies the kernel on /dev/sdc1 and creates entries in /boot/grub/grub.cfg but the device and UUID are for /dev/md1.

For example a menuentry to boot with /dev/md1 as root:

```
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod raid
        insmod mdraid
        insmod ext2
        set root='([COLOR="Red"]md0[/COLOR])'
        search --no-floppy --fs-uuid --set [COLOR="Red"]6b74e77e-a0f8-4ce9-941e-0e7fba116b48[/COLOR]
        linux   /vmlinuz-2.6.38-12-generic root=UUID=a[COLOR="Red"]6fd80e6-e5a2-4f46-9f6e-2ca824da83f1[/COLOR] ro   quiet splash
        initrd  /initrd.img-2.6.38-12-generic
}

```


And the one for /dev/sdc1:
```
menuentry "Ubuntu, with Linux 2.6.38-12-generic (on [COLOR="Red"]/dev/sdc1[/COLOR])" {
        insmod raid
        insmod mdraid
        insmod ext2
        set root='([COLOR="Red"]md0[/COLOR])'
        search --no-floppy --fs-uuid --set [COLOR="Red"]6b74e77e-a0f8-4ce9-941e-0e7fba116b48[/COLOR]
        linux /vmlinuz-2.6.38-12-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro quiet splash
        initrd /initrd.img-2.6.38-12-generic
}

```

Is there a way to get grub to provide boot entries that will set either of /dev/md1 or /dev/sdc1 as the root partition? For now I'm happy to leave the /boot partition on /dev/md0 and leave those drives in the machine.

thanks,
hank

---

