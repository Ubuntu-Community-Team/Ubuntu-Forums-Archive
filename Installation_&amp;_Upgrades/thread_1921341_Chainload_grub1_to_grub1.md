---
title: "Chainload grub1 to grub1"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by Frank64 on 2012-02-06
Hi,

I know I still use grub-legacy, long story behind that.
I am on Kubuntu 11.10 with grub-legacy.

I want to chainload from disk1 to disk2 (2 identical disks with same MBRs and EBRs).

I come from openSUSE and I have tried the following 3 methods for Kubuntu:

1-
title Linux test -- External drive Chainload
root (hd1,0)
chainloader +1

2-
title Linux test -- External drive Chainload Core.img
root (hd1,0)
kernel /boot/grub/core.img
boot

3-
title Linux test -- External drive Chainload Old method
root (hd1,0)
chainload +1
boot


1 gives me ERROR 13, 2 boots GRUB2 directly and 3 gives me ERROR 8. Interestingly method #3 used to work no problem on grub 0.97 and openSUSE.

How can I chainload 2 identical grub-legacy on 2 identical disks with 2 identical Kubuntu installed (same data on both disks)?


tnx

---

### Post by oldfred on 2012-02-06
I used to chainload from/to MBR & PBR as I used a grub only partition for booting. I did not originally like grub2 as it did not like to be installed to a partition. But now that I understand grub2 I consider it much better.

One issue can be that your boot drive will always be hd0. So you cannot copy a chainload entry from one to another drive without editing it, or sometimes you just have to edit the grub entry as you boot to get the correct drive number.

These are all entries from my old grub legacy that worked. I had three drives and often booted sdc, these entries now look like I was booting sda.

```
title       Ubuntu 9.04 Jaunty 64 bit @ sdc5
root        (hd2,4)
chainloader +1


title    Most Current Ubuntu on sdc5
root    (hd2,4)
kernel   /vmlinuz root=/dev/sdc5 ro quiet splash
initrd  /initrd.img

title       Ubuntu 9.04 Jaunty 32 bit @ sdb
root        (hd1)
chainloader +1

title       Ubuntu 9.10 Karmic 64 bit @ sdc
root        (hd2)
chainloader +1

title       Ubuntu 10.04 Lucid alpha/beta @ sda
root        (hd0)
chainloader +1

```

---

### Post by Frank64 on 2012-02-06
Wow quick answer, thought I wouldn't get one for many days, thanks for that. :)

It's possible *buntu works differently with grub than suse, it seems at least to do it with the gfxmenu, which is working out of the box in suse but not *buntu.

I'll try using hd1 instead of hd0 or try your second option.
If that doesn't work, I'll go to grub2. Indeed grub2 requires some time to get used to and some reading to understand and get comfortable. I think I've done most of it, only need to know how to chainload grub2 to grub2 and use themes. Maybe I should just move on with grub2 as grub developers told me the legacy is almost not supported anymore.

tnx :)

---

### Post by oldfred on 2012-02-06
I do not use themes:

Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

I some of the same chainload entries in grub2 but using grub2's somewhat different boot stanza format & different partition numbering (sda1 is hd0,1 not grub legacy's hd0,0).

openSUSE
[http://ubuntuforums.org/showthread.php?t=1740690](http://ubuntuforums.org/showthread.php?t=1740690)

```
menuentry "Lucid Lynx on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

menuentry "9.04 on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}
```

grub2 also boots other kernels or in Debian the links to kernels in root.

```
menuentry "Latest Kernel in sda1" {
insmod ext2
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
}

```

---

