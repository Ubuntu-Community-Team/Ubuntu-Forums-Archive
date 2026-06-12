---
title: "Booting 2 XP Installs."
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Trapper on 2010-05-01
I have Lucid installed on a hard drive that dual boots with XP on the same drive. I am in need of adding a secondry drive that also has an XP install. Is there any way I can add the secondary drive to my grub2 menu to boot it and is there a way of tricking the XP install on the secondary drive into thinking it's on drive c: of the primary hard drive so it will boot?

---

### Post by Trapper on 2010-05-02
As part of planning ahead I asked this question prior to actually connecting the second drive. Once I connected it I ran update-grub. It found the 2nd drive and gave me a new entry in grub to boot from it. Below are both of my entrys for my primary and secondary drives:

```
menuentry "Microsoft Windows XP (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 404d-221d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP (on /dev/sdb1)" {
    insmod fat
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6834-fc6b
    drivemap -s (hd0) ${root}
    chainloader +1
} 
```

I also had figured out an entry I could boot from using the 40_custom file. That code is:

```
menuentry "Microsoft Windows XP on /dev/sdb1" {
drivemap (hdo) (hd1)
drivemap (hd1) (hd0)
set root=(hd0)
chainloader (hd1,1)+1
}

```Either method boots okay for me.

---

