---
title: "after installing ubuntu on a different partition grub is not loaded at boot"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by waleemamun on 2008-11-29
hi
i am new at ubuntu .i have installed xp(sp2) on my C: drive (NTFS) and then installed ubuntu form the live cd on another partition after successfully installing ubuntu when i restarted my pc it showed boot loader not found and asked to insert a bootable disk . pls can anyone help me with that 
thnx in advance

---

### Post by Pumalite on 2008-11-29
Post:
sudo fdisk -lu
(boot your Live CD)

---

### Post by waleemamun on 2008-11-29
hi 
here what i got after sudo fdisk -lu
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x58435abb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2        81922048   143362047    30720000    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       143362048   204802047    30720000    c  W95 FAT32 (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4       204812685   312560639    53873977+   f  W95 Ext'd (LBA)
/dev/sda5       204812748   263626649    29406951    e  W95 FAT16 (LBA)
/dev/sda6       263626713   312560639    24466963+   b  W95 FAT32

ps: i have reinstalled windows so now can u tell me how i keep this windows on C: drive and also intall ubuntu on anther drive without having the problem of boot loader

---

### Post by theozzlives on 2008-11-29
Install Windows first using about half of your HD. Then install Ubuntu with the "use free space" option. GRUB should look for other Operating systems and setup a boot menu for you.

---

### Post by kadafi69 on 2008-11-29
I have the same problem, ( im not at my pc rite now so cant provide sudo fdisk -lu)

but i dont have the option of installing windows first. any other way around it?

---

### Post by caljohnsmith on 2008-11-29
kadafi69, fortunately you don't need to reinstall Windows and Ubuntu to fix booting problems related to Grub; but first, what exactly happens on start up? Do you get any errors? 

How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by waleemamun on 2008-11-29
hi caljohnsmith i provided the output of sudo fdisk -lu for my pc can u tell me now how i can keep the current xp an still install ubuntu on another partition, i created free space of size 23 gb where i want o install  ubuntu. i dont know about ubuntu at all but is this problem is due to not finding the grub in MBR ? pls i need help

---

### Post by caljohnsmith on 2008-11-29
> **waleemamun said:**
> hi caljohnsmith i provided the output of sudo fdisk -lu for my pc can u tell me now how i can keep the current xp an still install ubuntu on another partition, i created free space of size 23 gb where i want o install  ubuntu. i dont know about ubuntu at all but is this problem is due to not finding the grub in MBR ? pls i need help
In your second post you mentioned you wanted to install Ubuntu to another drive other than your Windows drive. So which drive do you want to install Ubuntu to? How about looking at this tutorial and seeing if it helps you install Ubuntu:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

---

### Post by waleemamun on 2008-11-29
hi caljohnsmith i read the link u gave i did those thing i created an free space for ubuntu and installed it their and it said the installation was successful but when i restart the pc after installation the grub is not loaded it says no boot loader found and asks to use a bootable disk

---

### Post by caljohnsmith on 2008-11-29
> **waleemamun said:**
> hi caljohnsmith i read the link u gave i did those thing i created an free space for ubuntu and installed it their and it said the installation was successful but when i restart the pc after installation the grub is not loaded it says no boot loader found and asks to use a bootable disk
So which drive did you install Ubuntu to? How about posting the output of all the commands I gave in post #6, including the fdisk command, so I can see what your setup is like now.

---

### Post by karthikCV on 2008-11-29
i am facing the same problem. i installed xpsp3 and then ubuntu7.10 and at the time of booting , i get the same message "PLEASE INSERT YOUR SYSTEM DISK....." of that sort when i try to use xp. 

i tried the code given above on the terminal. and this is the result

karthik@ParentsGift-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ffe660c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sda2        51199155   488375999   218588422+   f  W95 Ext'd (LBA)
/dev/sda5        51199218   215046089    81923436    7  HPFS/NTFS
/dev/sda6       215046153   378893024    81923436    7  HPFS/NTFS
/dev/sda7       378893088   430092179    25599546    7  HPFS/NTFS
/dev/sda8       430092243   488375999    29141878+   7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb88fb88

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39118274    19559106   83  Linux
/dev/hda2        39118275   150432659    55657192+   b  W95 FAT32
/dev/hda3       150432660   156296384     2931862+  82  Linux swap / Solaris
karthik@ParentsGift-desktop:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
karthik@ParentsGift-desktop:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
0000
karthik@ParentsGift-desktop:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
karthik@ParentsGift-desktop:~$ sudo xxd -s 1049 -l 2 -p /dev/sdb
xxd: /dev/sdb: No such file or directory
karthik@ParentsGift-desktop:~$

---

### Post by caljohnsmith on 2008-11-29
Can you set your BIOS to boot the Ubuntu hda drive on start up? If so, how about doing:
```
sudo grub
grub> device (hd0) /dev/hda
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And you should be able to boot your hda drive and at least get the Grub menu on start up if all goes well. If you have no way of booting your hda drive on start up, you could instead do:
```
sudo grub
grub> device (hd0) /dev/sda
grub> device (hd1) /dev/hda
grub> root (hd1,0)
grub> setup (hd0)
grub> quit
```
And then you should be able to get the Grub menu on start up when you boot the Windows sda drive. Please post the output of all the above commands, and let me know how it goes.

---

### Post by Pumalite on 2008-11-29
> **kadafi69 said:**
> I have the same problem, ( im not at my pc rite now so cant provide sudo fdisk -lu)

but i dont have the option of installing windows first. any other way around it?
You might want to try this:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by Pumalite on 2008-11-29
> **waleemamun said:**
> hi 
here what i got after sudo fdisk -lu
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x58435abb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2        81922048   143362047    30720000    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       143362048   204802047    30720000    c  W95 FAT32 (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4       204812685   312560639    53873977+   f  W95 Ext'd (LBA)
/dev/sda5       204812748   263626649    29406951    e  W95 FAT16 (LBA)
/dev/sda6       263626713   312560639    24466963+   b  W95 FAT32

ps: i have reinstalled windows so now can u tell me how i keep this windows on C: drive and also intall ubuntu on anther drive without having the problem of boot loader

Check your drive with TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

### Post by karthikCV on 2008-11-29
**To caljohnsmith**

This is the output:
grub> device (hd0) /dev/hda

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.l
st"... succeeded
Done.

grub> quit

---

### Post by kadafi69 on 2008-11-30
> **caljohnsmith said:**
> kadafi69, fortunately you don't need to reinstall Windows and Ubuntu to fix booting problems related to Grub; but first, what exactly happens on start up? Do you get any errors? 

How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

When I run sudo fdisk -lu i get this

> root@XPC:~# sudo fdisk -lu

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      192779       96358+  83  Linux
/dev/sda2          192780    72292499    36049860    5  Extended
/dev/sda5          192843     8000369     3903763+  82  Linux swap / Solaris
/dev/sda6         8000433    27535409     9767488+  83  Linux
/dev/sda7        27535473    54701324    13582926   83  Linux
/dev/sda8        54701388    60565049     2931831   83  Linux
/dev/sda9        60565113    66428774     2931831   83  Linux
/dev/sda10       66428838    72292499     2931831   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001c502

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001   83  Linux

then for each drive i run the other command I get

> sudo dd if=/dev/sda1 count=1 2>/dev/null | strings | grep -ie grub "missing operating system"
grep: missing operating system: No such file or directory

> sudo dd if=/dev/sda2 count=1 2>/dev/null | strings | grep -ie grub "missing operating system"
grep: missing operating system: No such file or directory

> sudo dd if=/dev/sd5 count=1 2>/dev/null | strings | grep -ie grub "missing operating system"
grep: missing operating system: No such file or directory

> sudo dd if=/dev/sda6 count=1 2>/dev/null | strings | grep -ie grub "missing operating system"
grep: missing operating system: No such file or directory

> sudo dd if=/dev/sda7 count=1 2>/dev/null | strings | grep -ie grub "missing operating system"
grep: missing operating system: No such file or directory

> sudo dd if=/dev/sda8 count=1 2>/dev/null | strings | grep -ie grub "missing operating system"
grep: missing operating system: No such file or directory

> sudo dd if=/dev/sda9 count=1 2>/dev/null | strings | grep -ie grub "missing operating system"
grep: missing operating system: No such file or directory

> sudo dd if=/dev/sda10 count=1 2>/dev/null | strings | grep -ie grub "missing operating system"
grep: missing operating system: No such file or directory

> sudo dd if=/dev/sdb1 count=1 2>/dev/null | strings | grep -ie grub "missing operating system"
grep: missing operating system: No such file or directory


In regards to Pumalite's link, I want nothing to do with windows on this system, so that rules that out!

EDIT:

I also have a problem with the /dev/sdb1 drive, this is a new drive i bought recently and since formatting it, ive not been able to put any files onto it, i just get a permissions denied error message. any ideas how to resolve this?

---

### Post by kadafi69 on 2008-12-01
bumpio I could do with this being sorted.

---

### Post by caljohnsmith on 2008-12-01
OK, according to the commands you ran in post #15, you should be able to boot your Ubuntu drive on start up and get the Grub menu. Have you been able to get the Grub menu yet? When you get that error booting Windows that you mentioned in your first post, is that when you boot the Windows drive, or if you boot Windows from the Grub menu? Also, have you ever been able to boot Windows before, or is it a fresh install?

---

### Post by kadafi69 on 2008-12-01
i dont have windows, not in a long time. but i did do a fresh install of ubuntu thats when the problems arose. when I run those grub commands I get this

> 
grub> device (hd0) /dev/sda

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/grub/stage2 /grub/menu
.lst"... succeeded
Done.

grub> 


---

