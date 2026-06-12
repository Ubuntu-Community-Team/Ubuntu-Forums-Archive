---
title: "Windows bootloader, GRUB Geom Error"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by CIAduck on 2008-05-05
Hello,

I am new and experimenting with Ubuntu (Hardy 8.04).

Nevermind the reason, but I need my Windows XP bootloader to be the main thing in the MBR.



Here is my problem. I have 3 internal harddrives (all IDE), and the 3rd one is dedicated to linux.

I used Super GRUB Disk to make it so that Windows is in the MBR and that it chainloads Ubuntu (this ran GRUB setup on (hd2)). I loaded up Ubuntu and went in to the terminal, here is what I did:

df:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1             38147944   2314868  33910500   7% /
varrun                 1548748       100   1548648   1% /var/run
varlock                1548748         0   1548748   0% /var/lock
udev                   1548748        68   1548680   1% /dev
devshm                 1548748        48   1548700   1% /dev/shm
lrm                    1548748     43044   1505704   3% /lib/modules/2.6.24-16-generic/volatile
/dev/sdd1            488384000 344951580 143432420  71% /media/My Book
/dev/scd0                 4086      4086         0 100% /media/cdrom0
```

Then I made a copy of the boot sector:
```
dd if=/dev/sdc1 of="/media/My Book/sdc1.lnx" bs=512 count=1
```

"My Book" is an external USB WD HDD.

Then I loaded up Windows XP and copied the file to my 'C:' drive.
I modified my boot.ini file to include:
```
C:\sdc1.lnx="Linux - Ubuntu"
```

When I click on my new option in the loader it returns the error: GRUB Geom Error

Here is what my "fdisk -l" looks like:
```

Disk /dev/sda: 20.4 GB, 20416757760 bytes
240 heads, 63 sectors/track, 2637 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x69737369

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2637    19935688+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8eedf44e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1ce0553

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4787    38451546   83  Linux
/dev/sdc2            4788        4998     1694857+   5  Extended
/dev/sdc5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf49c60bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS
```

The strange thing is, when I do this process but use GRUB in the MBR instead: I can get to the Windows bootloader, then I can use the Linux option, and it takes me back to the GRUB, and I could go back and forth all day.

Thanks in advance!
CIAduck

---

### Post by daengbo on 2008-05-05
> **CIAduck said:**
> Hello,

I used Super GRUB Disk to make it so that Windows is in the MBR and that it chainloads Ubuntu (this ran GRUB setup on (hd2)). 
Then I made a copy of the boot sector:

```
dd if=/dev/sdc1 of="/media/My Book/sdc1.lnx" bs=512 count=1
```

From what you've written, it looks like you installed Grub to /dev/sdc, but you've taken the first 512 blocks from /dev/sdc1. Is this accurate? They're not the same.

Try this how-to:
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)
You'll need to adjust some of the parameters, but it should work otherwise.

---

### Post by CIAduck on 2008-05-05
I have actually tried both.

The sdc entry will give me a blank screen and then go back to the Windows bootloader, and the sdc1 screen gives me the GRUB Error. So naturally I assumed that it was the sdc1 entry that I needed.

Is it possible that GRUB needs to be installed on the boot drive? How would I go about doing that when it is NTFS format? The only way I know is to have GRUB on the linux drive and make a copy like this to the windows bootloader.

What am I doing wrong? From what I've read a Geom Error deals in drive orders and physical locations, but I'm sure I have everything in the correct place.

---

### Post by daengbo on 2008-05-05
Did you try following the advice in the howto I linked to?

---

### Post by CIAduck on 2008-05-06
Thanks daengbo!

It worked, you were right. It wasn't loading GRUB from the Windows bootloader because it was on a different physical disk.

That is why I was able to have GRUB in the MBR and it would work, because windows is on the same physical boot disk. But having GRUB on a different disk than the one that was booting the MBR made it not work.

Thanks for the link, it was very helpful!

~CIAduck

---

### Post by xzero1 on 2008-05-06
> Did you try following the advice in the howto I linked to?Maybe Ubuntu Screencasts would host your videos. They have nothing on 8.04.
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

---

### Post by daengbo on 2008-05-06
CIAduck: No problem.
xzero1: The videos really need to be redone.

---

### Post by adrian15 on 2008-05-07
> **CIAduck said:**
> Thanks daengbo!

It worked, you were right. It wasn't loading GRUB from the Windows bootloader because it was on a different physical disk.


It worked? It should not work because that howto does not take in account the 2nd hard disk problem.

This howto takes the problem into account:

[http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows).

**What CIAduck did you do? What was explained on that howto or more things?**

Thank you.

adrian15

---

