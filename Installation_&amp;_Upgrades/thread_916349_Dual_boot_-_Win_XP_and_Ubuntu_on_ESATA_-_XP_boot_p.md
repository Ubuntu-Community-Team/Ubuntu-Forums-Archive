---
title: "Dual boot - Win XP and Ubuntu on ESATA - XP boot problems"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by confusa on 2008-09-10
Originally I had Win XP installed on a raid mirror setup. I installed Ubuntu to an external ESATA drive and Grub to the ESATA. For awhile I could boot into either with no problem whatsoever, using grub to either boot Win XP or Ubuntu. If I unplugged the ESATA it would boot straight into XP which was great. Now, I can no longer get XP to boot from either grub or by removing the ESATA. Nothing changed, it just stopped working. Ubuntu from the ESATA works fine, XP will never boot, just cycles through the BIOS screen.

If I look at the partitions in Gparted, I see that all three drives, both members of the raid and the Ubuntu(ESATA) have the boot flag set on them. I assume this is incorrect?

Ideas?

---

### Post by caljohnsmith on 2008-09-10
> **confusa said:**
> Originally I had Win XP installed on a raid mirror setup. I installed Ubuntu to an external ESATA drive and Grub to the ESATA. For awhile I could boot into either with no problem whatsoever, using grub to either boot Win XP or Ubuntu. If I unplugged the ESATA it would boot straight into XP which was great. Now, I can no longer get XP to boot from either grub or by removing the ESATA. Nothing changed, it just stopped working. Ubuntu from the ESATA works fine, XP will never boot, just cycles through the BIOS screen.

If I look at the partitions in Gparted, I see that all three drives, both members of the raid and the Ubuntu(ESATA) have the boot flag set on them. I assume this is incorrect?

Ideas?
If nothing truly changed software-wise, then it sounds like you probably have some sort of hardware problem. You don't get any errors on start up? It just repeatedly goes back to the BIOS screen? Also, how about posting the output of:
```
sudo fdisk -lu
```

---

### Post by confusa on 2008-09-12
> **caljohnsmith said:**
> If nothing truly changed software-wise, then it sounds like you probably have some sort of hardware problem. You don't get any errors on start up? It just repeatedly goes back to the BIOS screen? Also, how about posting the output of:
```
sudo fdisk -lu
```

Yep, no errors on startup at all. I should add that sda1 and sdb1 are the RAID drives. sdc1 is the ESATA.

```
sudo fdisk -lu
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca5310ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16065   488375999   244179967+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca5310ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       16065   488375999   244179967+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00082eb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    41945714    20972826   83  Linux
/dev/sdc2       488392065   732580064   122094000    b  W95 FAT32
/dev/sdc3        41945715   488392064   223223175    5  Extended
/dev/sdc5        41945778    46138679     2096451   82  Linux swap / Solaris
/dev/sdc6        46138743   488392064   221126661   83  Linux

Partition table entries are not in disk order

```

---

### Post by caljohnsmith on 2008-09-12
Interesting--your sda and sdb HDDs look like they are exactly the same. Are they maybe the same drive? If that is true, it doesn't look like your RAID setup is working for some reason, as Ubuntu seems to see them as individual drives. Be sure to check all your HDD connections. Can you plug your RAID array into another computer to check if it will boot? Or if the computer recognizes it OK?

---

### Post by confusa on 2008-09-12
> **caljohnsmith said:**
> Interesting--your sda and sdb HDDs look like they are exactly the same. Are they maybe the same drive? If that is true, it doesn't look like your RAID setup is working for some reason, as Ubuntu seems to see them as individual drives. Be sure to check all your HDD connections. Can you plug your RAID array into another computer to check if it will boot? Or if the computer recognizes it OK?

It is a mirror raid, so they are essentially exactly the same. Ubuntu has always seen them as two drives, even when it worked correctly. Connections are fine. Unfortunately I can't plug it into another computer.

---

### Post by caljohnsmith on 2008-09-12
You mentioned earlier that you couldn't get the RAID array to boot even from Grub; what entry did you use in your Grub's menu.lst, and what errors did you get when trying to boot Windows?

Also, just to troubleshoot, you could try turning off the boot flag on one of your RAID drives and see if that makes any difference. When you are in Ubuntu, just do:
```
sudo fdisk /dev/sda
```
Press "a" to toggle boot flag, then enter the partition to toggle, which should be "1". And of course can then make sure the boot flag was toggled off with:
```
sudo fdisk -l
```
Let me know how it goes.

---

### Post by confusa on 2008-09-12
> **caljohnsmith said:**
> You mentioned earlier that you couldn't get the RAID array to boot even from Grub; what entry did you use in your Grub's menu.lst, and what errors did you get when trying to boot Windows?

Also, just to troubleshoot, you could try turning off the boot flag on one of your RAID drives and see if that makes any difference. When you are in Ubuntu, just do:
```
sudo fdisk /dev/sda
```
Press "a" to toggle boot flag, then enter the partition to toggle, which should be "1". And of course can then make sure the boot flag was toggled off with:
```
sudo fdisk -l
```
Let me know how it goes.

Here is the windows entry in the menu.lst. No errors at all when I select Windows from Grub, it just boots back to the BIOS, then Grub again.

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

I will try turning off a flag and report back.

---

### Post by confusa on 2008-09-12
> **caljohnsmith said:**
> You mentioned earlier that you couldn't get the RAID array to boot even from Grub; what entry did you use in your Grub's menu.lst, and what errors did you get when trying to boot Windows?

Also, just to troubleshoot, you could try turning off the boot flag on one of your RAID drives and see if that makes any difference. When you are in Ubuntu, just do:
```
sudo fdisk /dev/sda
```
Press "a" to toggle boot flag, then enter the partition to toggle, which should be "1". And of course can then make sure the boot flag was toggled off with:
```
sudo fdisk -l
```
Let me know how it goes.

Tried turning the boot flag off on one, then the other windows partition and it made no difference. Even tried turning it off on the ESATA (Ubuntu) partition and leaving it on on the windows partition and it made no difference. I select windows from grub, it says loading... then back to the BIOS.

---

### Post by confusa on 2008-09-12
One thing I did do that may have caused this is I went into the BIOS and changed the boot order so that the ESATA was first. Then, I did unplug the ESATA so perhaps that screwed something up. I can get back into the BIOS and change it back to the internal drive, but it hasn't made a difference.

---

### Post by confusa on 2008-09-15
```

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
device.map 
```

```

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=5b8cef39-b615-4219-988
c-6506198f7f1e ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet


```
Not sure what to make of this. Even though selecting the above option for Ubuntu from Grub boots Ubuntu fine, that drive is actually shown as sdc in fdisk as can be seen in the post above. Totally confused!

---

### Post by caljohnsmith on 2008-09-15
When Grub boots on start up, it sees the order of HDDs the same as the BIOS boot order, not necessarily the same as the device order given in Ubuntu's /dev directory (i.e. sda, sdb, sdc, etc). So if Ubuntu is on the drive that boots on start up (which it is), then Grub considers it to be on (hd0), so (hd0,0) is correct for Ubuntu. 

Try adding the following to your menu.lst, and let me know the outcome:
```
title           Windows XP Professional (hd2)
root            (hd2,0)
savedefault
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1
```

---

### Post by confusa on 2008-09-16
> **caljohnsmith said:**
> When Grub boots on start up, it sees the order of HDDs the same as the BIOS boot order, not necessarily the same as the device order given in Ubuntu's /dev directory (i.e. sda, sdb, sdc, etc). So if Ubuntu is on the drive that boots on start up (which it is), then Grub considers it to be on (hd0), so (hd0,0) is correct for Ubuntu. 

Try adding the following to your menu.lst, and let me know the outcome:
```
title           Windows XP Professional (hd2)
root            (hd2,0)
savedefault
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1
```

Sadly still no joy. That edit of the menu.lst gives me:

Error 21: Selected disk does not exist. 

I am having a feeling that swapping the boot order in the BIOS is what killed my XP. Since I swapped it to the ESATA and then unplugged it, it hasn't worked so it must have freaked the BIOS out in some way. Thinking about resetting the BIOS to default but I am unsure what that will do. If it will kill my RAID, etc.

---

### Post by caljohnsmith on 2008-09-16
Since you can't even get your Windows drive to boot by itself at this point, then that means you most likely have a hardware problem that has nothing to do with Grub at this point. Can you plug your Windows RAID drive into some other computer to see if another computer can boot it? I suspect you won't be able to. I think your RAID drive is probably the culprit at this point.

---

