---
title: "Problem with GRUB after upgrading to lynx"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Emowomble on 2010-05-11
After upgrading from 9.10 to 10.04 my windows install on my other hard drive no longer boots, it just sticks on a black screen with an unresponsive cursor.
I chose to update grub during the ubuntu upgrade and windows was working fine before it

I've tried running update-grub as root and it detects windows but it still wont boot up.

```
The relevent grub.cfg entry is:
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
        insmod ntfs
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 1eb49cd2b49cae31
        drivemap -s (hd0) ${root}
        chainloader +1
}
```

Any help would be much appreciated :)

---

