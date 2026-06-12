---
title: "grub2 question"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by skotos on 2009-12-09
I have 2 hard disks:

[LIST=1]
[*]/dev/sda - Ubuntu
[*]/dev/sdb - Arch
[/LIST]
I already have an entry like
```

menuentry "Arch" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 709592da-ef0b-4c11-ad51-68f7973b771a
    linux /vmlinuz26 root=/dev/disk/by-uuid/76f62da8-dd20-4ae3-a3e7-50f9b7c90c66 ro
    initrd /kernel26.img
}

```but what about a non Arch / UUID specific entry similar to
```

menuentry "MBR (sdb)" {
    set root to sdb MBR
    just leave the control to sdb
}

```I would simply like to pass the control to the MBR instead of to a partition, so that, for instance, another GRUB/whatever might do its job.
I do not want to reinstall/update any partition info either UUID concerning the other distro.
I would just like to switch to the other MBR and let it do its job: going to see what its boot partition is is not necessary, it should not be compulsory.
GRUB2 on /dev/sda should not known anything on /dev/sdb. I do not want to run any [/dev/sda1]/etc/grub.d/30_os-prober every time something has changed on /dev/sdb and I know a boot partition is already there.

Thx in advance.

---

### Post by darkod on 2009-12-09
I'm not sure you can jump to the MBR of /dev/sdb but chainloading to the part of the boot process on /dev/sdb1 should be possible. The MBR holds very small part of grub anyway, and it just tells it where to "jump".
So your entry might look something like
insmod ext2
set root=(hd1,1)
chainloader +1

The chainloader command is used for jumping to windows boot process and basically it just says continue with what ever is booting from here.
I'm not too used to grub2 yet so you might need few modifications to the above commands.

---

### Post by darkod on 2009-12-09
PS. You might need the search command too, here is sample windows manual entry:
menuentry "Windows Vista 43_custom" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader +1
}

from here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

