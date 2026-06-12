---
title: "yet another hal.dll problem"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by one_ro on 2007-07-10
Hello ubuntuers,

After a few hours of researching I finally have to ask for your help.
You know the usual, got a Win XP system, then installed Kubuntu and now I cannot boot in Windows anymore (although I use Linux as my main system, I have to boot Windows just this time to synchronize my Pocket PC).

OK, so I did my research, here's the facts:
```
$ sudo sfdisk -l

Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1       2598    3593     996    8000370   83  Linux
/dev/sda2        509    2597    2089   16779892+   c  W95 FAT32 (LBA)
/dev/sda3   *   3594    3842     249    2000092+  82  Linux swap / Solaris
/dev/sda4       3843   14592   10750   86349375   83  Linux

```So windows is in the second partition. Hal.dll does exists, now here is boot.ini:
```
  [boot loader]
  timeout=30
  default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
  [operating systems]  multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
```

I changed "partition(1)" with "partition(2)" but to no avail. At restart I get two Windows default, none of them works.

I played with various numbers, I even tried to change the partition numbers in menu.lst from the grub folder, but the stubborn Window$ partition won't boot.

Could you please advice further?
Thank you in advance,
Adrian

---

### Post by Pumalite on 2007-07-10
'Missing Files' is a known bug in Windows in dual boot. I'm not a Windows user, but as far as I know you could fix this sticking your Windows CD in, and at the appropiate time hit 'r' for Recovery, and then FIXBOOT

---

### Post by one_ro on 2007-07-10
Thanks for your reply. I know about this solution, but:
I've been using Kubuntu for three years now and (proud to say that) I don't even know where my former Windows CD is.
I would prefer a genuine Linux solution, given that writing on NTFS partitions is now possible.

Edit: plus, I wouldn't want to break my Grub; I know it can be rebuilt, but I would rather avoid that: Kubuntu is my main system now.

Cheers,
Adrian

---

### Post by Pumalite on 2007-07-10
The only Linux answer that I know to a Windows problem is: get rid of Windows. Maybe somebody with a better answer will jump in. I think you need to get a hold of a Windows CD.

---

### Post by one_ro on 2007-07-10
:lolflag:
Yeah, I agree. Unfortunately, my new Orange SPV M700 device is not that easy to synchronize with Linux... it has Windows Mobile 5.0.
I can only dream about a Linux version for Pocket PC that could deal with video-calling, GPS software, Internet with HSDPA speed and many of the features this device has...

Cheers,
Adrian

---

### Post by Pumalite on 2007-07-10
Glad you agree. Linux is the future, and the future is now. Good luck.
P.S. Linux is in all kinds of portable devices right now.

---

### Post by Odrodzona-Sarmacja on 2007-07-10
```
$ sudo sfdisk -l

Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1       2598    3593     996    8000370   83  Linux
/dev/sda2        509    2597    2089   16779892+   c  W95 FAT32 (LBA)
/dev/sda3   *   3594    3842     249    2000092+  82  Linux swap / Solaris
/dev/sda4       3843   14592   10750   86349375   83  Linux

```

Correct me if I am wrong, but shouldn't be the partition with windows (I guess it is sda2 with fat32) be bootable ("primary"), before any windows os will boot from it no matter other considerations?

---

### Post by Pimpn8ezy on 2007-07-10
Can we see the contents of your /boot/grub/menu.lst file?  I have recently had a similar problem and the solution was a simple off by one error.

My menu.lst file had a windows entry like the following

title   Windows
root  (hd0,0)
makeactive
chailoader +1

Fixing it was as simple as changing it to the following

title  Windows
root  (hd0,1)
mackeactive
chainloader +1


I'm not sure why I needed to make the change, but it fixed everything.

---

### Post by one_ro on 2007-07-11
> **Odrodzona-Sarmacja said:**
> Correct me if I am wrong, but shouldn't be the partition with windows (I guess it is sda2 with fat32) be bootable ("primary"), before any windows os will boot from it no matter other considerations?

Hi again,

You're probably right, but all my four partitions are primary: there can be no more than four primary partitions and this is exactly how I split my hard-disk:
- Windows
- Linux (root)
- Linux (swap)
- Linux (home)

I have no idea why the Windows partitions is sda2 instead of sda1, but it is surely primary.
Thanks
Adrian

---

### Post by one_ro on 2007-07-11
> **Pimpn8ezy said:**
> Can we see the contents of your /boot/grub/menu.lst file?  I have recently had a similar problem and the solution was a simple off by one error.

My menu.lst file had a windows entry like the following

title   Windows
root  (hd0,0)
makeactive
chailoader +1

Fixing it was as simple as changing it to the following

title  Windows
root  (hd0,1)
mackeactive
chainloader +1

I'm not sure why I needed to make the change, but it fixed everything.

Hi Pimpn8ezy,

Here's my Windows entry in the menu.lst:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP
root        (hd0,1)
savedefault
makeactive
chainloader    +1

```

I did change to (hd0,0) then (hd0,2) and even (hd0,3) but this didn't solve it...
Adrian

---

### Post by Odrodzona-Sarmacja on 2007-07-11
> **one_ro said:**
> Hi again,

You're probably right, but all my four partitions are primary: there can be no more than four primary partitions and this is exactly how I split my hard-disk:
- Windows
- Linux (root)
- Linux (swap)
- Linux (home)

I have no idea why the Windows partitions is sda2 instead of sda1, but it is surely primary.
Thanks
Adrian

Oh really? For now, the only windows bootable partition I can see on your hd is... your linux-swap partition :D  :D :D
Linux do not need its primary partition to be bootable. Windows is an another story.

```
$ sudo sfdisk -l

Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1       2598    3593     996    8000370   83  Linux
/dev/sda2        509    2597    2089   16779892+   c  W95 FAT32 (LBA)
/dev/sda3   *   3594    3842     249    2000092+  82  Linux swap / Solaris
/dev/sda4       3843   14592   10750   86349375   83  Linux

```

Try moving that "*" in boot from sda3 to sda2 partition. I think this should fix your problem and make your "primary" partition with windows os also bootable.

---

### Post by one_ro on 2007-07-12
Guys, experts, Linux gurus... I'm sure there is a clever (Linux) solution to this problem, could you please advice?
Adrian

---

### Post by Odrodzona-Sarmacja on 2007-07-12
"gparted" - is partitioning program in linux. It can be used to set or unset flags of partitions (like "boot" flag for example).

"Synaptic Package Manager" - is a tool, which can be used to download programs from internet and then install them on ubuntu, so they are ready to be used from the "applications" menu on the desktop.

BUT I am no linux expert. :) I've been using ubuntu just for one month or so. :D How much can I know about linux? ;)

---

### Post by dabl on 2007-07-12
> **one_ro said:**
> I'm sure there is a clever (Linux) solution to this problem, could you please advice?
Adrian

Mr. Odrodzona-Sarmacja has provided the clever Linux solution.  GParted Live CD is Linux -- get it here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

And if you will boot your GParted Live CD, and change the asterisked partition to the FAT32 partition where Windows is, it might just boot.  It certainly will not boot until its partition is marked "bootable". :)

---

### Post by one_ro on 2007-07-12
> **dabl said:**
> Mr. Odrodzona-Sarmacja has provided the clever Linux solution.  GParted Live CD is Linux -- get it here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

And if you will boot your GParted Live CD, and change the asterisked partition to the FAT32 partition where Windows is, it might just boot.  It certainly will not boot until its partition is marked "bootable". :)

Oops, I don't know how did I miss Mr. Odrodzona-Sarmacja's post... sorry.
OK, I made that partition bootable (with gparted right inside Kubuntu, it can do that)... but to no avail.

**sudo fdisk -l **showed that the partitions were not in the disk order (Windows is the first partition on the disk, but it was labeled **sda2**). So I fixed that, using
[B]sudo fdisk sda
[/B]then hitting "x" to enter in the expert menu
then "f" to fix the order
and finally "w" to write the changes.

The next step was a nightmare, I forgot to change the order in /boot/grub/menu.lst
(hd0,0) where Linux was should have been changed to (hd0,1)

So I forgot to do that and grub wasn't working anymore. So I cooked a SGD - Super Grub Disk, repaired it, force boot the partition using SGD's menu.lst and change that. Now I can boot Linux again, only Windows doesn't want to boot.

EDIT: before SGD I used the Windows boot cd and issued the FIXMBR command in the repair mode... to no result. Luckily I could restore my GRUB...

Here's the output from **sudo fdisk -l**:
```
Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *    509    2597    2089   16779892+   c  W95 FAT32 (LBA)
/dev/sda2       2598    3593     996    8000370   83  Linux
/dev/sda3       3594    3842     249    2000092+  82  Linux swap / Solaris
/dev/sda4       3843   14592   10750   86349375   83  Linux

```The Windows section from **menu.lst**:
```
title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```As you can see, I changed it to **(hd0,0)**. AFAIK, the bloody windows partition should boot, but it throws again an error, this time not related to hal.dll anymore, but complaining about not finding any dll.

EDIT: this is the error it throws:
> Windows could not start because of an error in the software.
Please report this problem as :
load needed DLLs for the kernel
Please contact your support person to report this problem.

So... here I am, stucked again... waiting for more suggestions...
TIA,
Adrian

---

### Post by Odrodzona-Sarmacja on 2007-07-12
> **one_ro said:**
> 
OK, I made that partition bootable (with gparted right inside Kubuntu, it can do that)... but to no avail.


So your windows xp partition didn't boot after that change of flag with gparted? It lacks as it seems something that was on your original vista partition... something like part of its windows vista boot manager software. Something alike "/boot/grub/" on your linux and you don't wish to erase it together with your linux partition either.

I think your choices now are

a) to reformat that partition

b) to use "a windows solution" and reformat header of that partition, so winxp boots without any windows vista boot manager software.

Just don't forget in the "a)" case to first copy your entire "c:\" to "/home/"your home"/copy_of_c/" and after the operation to copy the stuff back on "c:" . Unless of course you love installing again winxp and then love fixing broken grub again. ;)

---

### Post by one_ro on 2007-07-14
Hello again,

Well, I solved it using the brute force approach: reinstalling Windows on that partition; no other method worked.
I just don't understand why Windows stops responding following a partitioning process; it really is a too dumb OS for such a smart Linux computer hahhaa :))
Cheers,
Adrian

---

