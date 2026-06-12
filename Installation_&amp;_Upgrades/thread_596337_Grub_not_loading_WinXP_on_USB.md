---
title: "Grub not loading WinXP on USB"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by salariua on 2007-10-29
I have searched and searched with no success. Links are welcomed.

I have a laptop with win home one first partition (/dev/hda1) and ubuntu on another partition (/dev/hd4).
I have also installed windows on an usb disk made with this tutorial :

[http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)

I see and access the usb disk from ubuntu but can't make grub to boot from it
when I manually edit the line in grub and test the detected disks with "root (tab" it only sees fd0 and hd0 but no hd1 (that should be sda ).

It has worked fine till now with both windows and after installing ubuntu (grub) I can't have access to the usb drive anymore.

I have seen there is a way of delaying the grub with "rootdelay=10"(10 or whatever seconds I want) but how do I make grub to detect my usb drive to boot from it?

---

### Post by It_Was_Luck on 2007-10-29
You might want to look into burning yourself a SuperGrub Disk... I have one myself, they are very very powerful and can usually solve most Grub related problems.

Heres the site in case you want to read up on it...
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)
and heres the download link...
[http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2](http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2)


hth

---

### Post by salariua on 2007-10-29
I am downloading the image now.
10x ... I will let you know what's the result.

---

### Post by salariua on 2007-11-25
I really need you help guys! for I am out of solutions.

I have read a lot of stuff from all possible sites and I am clueless. It seems that Grub can't see my usb drive, tried SuperGrub Disk as It_Was_Luck's suggested and still no luck. My BIOS sees the drive ( I have disable splash screen and I see it detects the usb storage device) and before Ubuntu, when I had win on internal drive and win on external drive it worked ok but I think it's a problem with GRUB.
When it gives me the error of not finding drive (usb) I manually try to edit the boot line of win in GRUB , but when I do : "root (" tab it only shows me hd0 and fd0. Altrough my drive is sda I see in /boot/grub/device.map that /dev/sda is mapped as (hd1). I have tried hd1, sd0, sd1 ..... You name it!! and still no success.

Please give me some help. I usually read a lot and try to find solution on net before posting but it's beed a week and it's holding me down.

Here is the line of win xp in /boot/grub/menu.lst:

title     XP
root              (hd1,0)
unhide          (hd1,0)
hide              (hd0,0)
rootnoverify (hd1,0)
makeactive
map               (hd1,0)  (hd0)
map               (hd0) (hd1,0)
chainloader +1

Any suggestions ?

---

### Post by salariua on 2007-11-25
After one month of intense searching I had to give up. 

I have installed GAG and everything is ok now.

I am just posting this so that others will learn from it.

GAG did it for me now. I am in win (as much as I hate it) I need CAD software that on Linux is still on early ages.

---

### Post by meierfra on 2007-11-25
Did your try

title XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


If this did not work, post the output of

sudo fdisk -l

and 

cat /boot/grub/menu.lst


Edit: Never mind: Somehow  didn't realize that you solved your problem.

---

### Post by salariua on 2007-11-26
meierfra,

You are welcomed to help. We are here to understand what happen and as you can see I haven't fixed the problem but found a way around it.

This is the menu.lst contents. I have cut the beginning of the file because I haven't changed anything and I don't think you will need it.

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3de1991f-888b-467c-81fe-d1868a6ed285 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3de1991f-888b-467c-81fe-d1868a6ed285 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

#this are meierfra's guiding .. my own old inputs can be seen above in the previous posts
# this is the XP Pro settings
title XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


I am going to reboot now and see if your changes are helping grub.

---

### Post by salariua on 2007-11-26
> **meierfra said:**
>  Never mind: Somehow  didn't realize that you solved your problem.

I have rebooted to grub and it still gives me the error 21 disk not found.

The sole purpose of this thread is to see how this can be solved without the help of GAG or other boot mangers than GRUB.

Any more ideas?

Maybe I should mention that I am having this problem on a laptop with pata and usb drive.

---

### Post by meierfra on 2007-11-26
Could you post the output of  "sudo fdisk -l".
 If you have more than two hard drives, what is the boot order?,

---

### Post by salariua on 2007-12-04
Sorry for not posting sooner but I was caught in other problems.

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf91c9e14

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1       10249    82325061    f  W95 Ext'd (LBA)
/dev/hda3           10250       10371      979965   82  Linux swap / Solaris
/dev/hda4   *       10372       12161    14378175   83  Linux
/dev/hda5               2        3188    25599577+  83  Linux
/dev/hda6            3189        6376    25607578+   c  W95 FAT32 (LBA)
/dev/hda7            6377       10249    31109841    c  W95 FAT32 (LBA)

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28f12a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4569    36700461    7  HPFS/NTFS
/dev/sdb2            4570       14593    80517780    c  W95 FAT32 (LBA)

---

### Post by meierfra on 2007-12-04
I don't really have any good suggestion. But you might try

title XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

