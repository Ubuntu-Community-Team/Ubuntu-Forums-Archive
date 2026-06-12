---
title: "WinXP Dualboot, &quot;A disk read error has occurred&quot;"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by vinneh on 2010-08-24
So I've been googling this nonsense for almost two days now.  Here's some drive info:

partition labels & uuid
```

Windows     /dev/sdb3     (hd0,3)     5450F91950F90312
/           /dev/sdb1     (hd0,1)     72c730c7-1aa5-46cb-8957-d309de430502
/boot       /dev/sdc1     (hd1,1)     3fe937cb-aa77-4516-a911-3da514d21aae

There's other partitions, but I don't think they're referenced in any of the boot files

```and my grub.cfg menu entries:
```

Ubuntu:
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 3fe937cb-aa77-4516-a911-3da514d21aae
    linux    /vmlinuz-2.6.32-24-generic root=UUID=72c730c7-1aa5-46cb-8957-d309de430502 ro   quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}

Windows:

menuentry "Microsoft Windows XP Professional (on /dev/sdb3)" {
    insmod ntfs
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 5450f91950f90312
    drivemap -s (hd0) ${root}
    chainloader +1
}

```My boot.ini:
```

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

```I don't know if boot.ini is relevant since I have grub2 installed on /dev/sdc, but there it is anyway. 
Ubuntu boots fine, windows returns "A disk read error has occurred, press ctrl-alt-del to restart".

This problem originated when I moved XP from sdc to sdb using clonezilla.  I installed Ubuntu after that, however, and I have since run update-grub, so the menu entries should reflect that move.  Also, all drives are set to IDE in BIOS.

However, I can mount the windows partition in Ubuntu and read all the files fine.  Please help? :(

---

### Post by qumah on 2010-08-26
I'm not sure if this will help you but I had the same problem yesterday when I installed windows and than ubuntu side-by side. After the linux install GRUB was put in and I had an option to choose xp or ubuntu. The linux distro worked but when I'd select Windows it wouldn't start. It would stop on  "A disk read error has occurred Pres alt ctrl del". However the partition would mount in linux.
[B]
The way I solved this is I re-installed ubuntu using exactly the same partition. [/B]The installer imported all the settings from the old system before erasing it so I didn't have to set everything up from scratch again.

Windows was working from grub after that.

---

