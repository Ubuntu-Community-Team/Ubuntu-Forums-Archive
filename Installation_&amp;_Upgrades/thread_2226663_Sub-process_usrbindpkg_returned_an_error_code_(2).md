---
title: "Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by herluf2 on 2014-05-28
Hey there, I hope someone can help me with this problem :) I can't update and upgrade, because ubuntu (14.04) says there is no disk space left.. also it will not boot

output of: sudo fdisk -l
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00034a70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   621008639   310504288+  83  Linux
/dev/sda2       621008640   625137344     2064352+   5  Extended
/dev/sda5       621008703   625137344     2064321   82  Linux swap / Solaris

Disk /dev/sdb: 3868 MB, 3868430336 bytes
32 heads, 63 sectors/track, 3747 cylinders, total 7555528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x082439ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7553951     3776944+   c  W95 FAT32 (LBA)


```

output of: df
```

Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             1007276   74560    932716   8% /
udev              995748       4    995744   1% /dev
tmpfs             201456    1152    200304   1% /run
/dev/sdb1        3762230 1014018   2748212  27% /cdrom
/dev/loop0        944256  944256         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            1007276    1028   1006248   1% /tmp
none                5120       4      5116   1% /run/lock
none             1007276      80   1007196   1% /run/shm
none              102400      60    102340   1% /run/user

```

And here are the last 4 lines when i run: sudo apt-get update and then upgrade.. 

Processing triggers for man-db (2.6.7.1-1) ...
debconf: DbDriver "templatedb": could not write /var/cache/debconf/templates.dat-new: No space left on device
No apport report written because MaxReports is reached already
                                                              E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by ian-weisser on 2014-05-28
Check inodes, too. df -i
Complex setups (yours looks complex) with lots of links can run out of inodes.

---

### Post by herluf2 on 2014-05-29
df -i :

```
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/cow           251819   1001 250818    1% /
udev           248937    521 248416    1% /dev
tmpfs          251819    541 251278    1% /run
/dev/sdb1           0      0      0     - /cdrom
/dev/loop0     179168 179168      0  100% /rofs
none           251819      2 251817    1% /sys/fs/cgroup
tmpfs          251819     18 251801    1% /tmp
none           251819      2 251817    1% /run/lock
none           251819      6 251813    1% /run/shm
none           251819     29 251790    1% /run/user

```

ok, but i didnt do anything to make it complex.. so maybe i should try another ubuntu or linux version..?

---

### Post by ian-weisser on 2014-05-29
> **herluf2 said:**
> /cow           251819   1001 250818    1% /
/dev/loop0     179168 179168      0  100% /rofs

cow means 'copy on write'
rofs means 'read only filesystem'

You seem to be either running off a Live media (which cannot be upgraded), or have set up a read-only (complex) system.
That's why the system cannot find space to install new package or upgrade existing packages.
The distro is irrelevant. You would have the same problem with any distro that you run read-only.

---

### Post by herluf2 on 2014-05-30
yes, i have installed lubuntu, but it cannot boot, so i start with the usb key.. and i assumed that when i try to update it would be what is already on the pc..
do you know how to fix it?

---

### Post by ian-weisser on 2014-05-30
Well, now we know that your update problem is the intended behavior when you try to update a Live image without persistence.

Lots of people here probably know how to fix your boot problem. There are thousands of "my-system-wont-boot" threads marked SOLVED here. Have you looked at any of those?

Describe, in painful detail, exactly what you see and hear when you try to boot.

Did it ever work in the past? Did something occur to make it stop working?

Does the system do it's Power On Self Test (POST?)
Do you get a manufacturer splash screen?
Do you get a grub screen?
Do you get a logon screen?
Do you get any error messages? Exactly when? And exactly what do they say?

---

### Post by herluf2 on 2014-05-31
I have tried searching for the solution, but without luck.
The installaion never worked.. i installed 2 weeks ago, and it would not boot..

When my pc starts, there is no power on self test, and then the grub menu apeears (version 2.02 beta2-9). Then, nomatter what i choose, the system stops or crashes almost right away.. like after 1 sec or so, no splash or logon screen, and this is what it looks like :

[   0.904678]        Call Trace:
[   0.904711]    [<c164b873>]     dump_stack + 0x41/0x52
[   0.904743]    [<c16469ac>]     panic +0x87/0x181
[   0.904744]    [<c1641cec>]     kernel_init+0xfc/0x100
[   0.904807]    [<c1659ab7>]     ret_from_kernel_thread+0x1b/0x28
[   0.904841]    [<c1641bf0>]      ? rest_init+0x70/0x70
_

---

### Post by mörgæs on 2014-05-31
Please use CODE tags. 
I have edited post #3, please edit #1 yourself.

---

### Post by herluf2 on 2014-05-31
Hey I tried to edit it the first time.. but it just slipped back into the state it is in now.. how do i save the change, and do i use any special keys apart from the spacekey?

---

### Post by bapoumba on 2014-05-31
> **herluf2 said:**
> Hey I tried to edit it the first time.. but it just slipped back into the state it is in now.. how do i save the change, and do i use any special keys apart from the spacekey?

When you edit a post, there is no editor button to auto-add code tags. You need to write them [noparse]```
Your text in between code tags
```[/noparse].
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by herluf2 on 2014-05-31
Ok thanks, thats a bit more easy than making all the spaces yourself and then it still looks way off. hehe

---

### Post by herluf2 on 2014-06-01
So my solution to this problem was to make a new installation of an older ubuntu version, 13.04...

---

### Post by mörgæs on 2014-06-01
I wouldn't call it a solution. 13.04 is out of support, so you are vulnerable to an attack now. 

14.04 is the way to go, always in a new install.

---

### Post by herluf2 on 2014-06-02
well, I was thinking to upgrade to 13.10,.. is it not possible?

---

### Post by mörgæs on 2014-06-02
Yes, it's possible but it's also risky. 
If this is a new install then I guess there's nothing worth saving on the hard disk.

---

### Post by herluf2 on 2014-06-02
yes, i have now upgraded from 13.04 to 13.10 and it seems to work fine.. it took me about ½ hour to download, and one hour to install..
I think its better to not upgrade to 14.04 for a long time.. since it didnt work on my pc at all.. there must be some kind of bug in it i guess.. anyway, thanks everyone for your reply's and help.. you are great!!

---

### Post by Vladlenin5000 on 2014-06-02
Not a solution either. 13.10 will be out of support in a couple of months.

---

### Post by mörgæs on 2014-06-02
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by herluf2 on 2014-08-24
Now i have upgraded to 14.04 and it works.. so now the problem is solved somehow :) for now..

---

### Post by mörgæs on 2014-08-24
Good, please mark the thread 'solved'.

---

