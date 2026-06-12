---
title: "Update Manager Error: Not enough free disk space"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by dancingLoki on 2011-08-19
I am a beginner to Ubuntu & Linux.  Some months back I installed ubuntu on a somewhat aged & slowed down acer laptop running win XP.  Finally I tried running ubuntu a couple days ago & it's been pretty smooth, until this from update manager:
---------------------------------------------------------------
Not enough free disk space

The upgrade needs a total of 615M free space on disk '/'. Please free at least an additional 296M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
---------------------------------------------------------------
I guess I don't have to install these "important security updates", but it's probably best I do & learn how to use the file browser, terminal (Applications - Accessories - really, it's a little hidden), other important parts of ubuntu.

For downloading I have an external drive connected with 760 GB free - more than enough space for anything.  I can also move files to this disk - do I maybe need to reboot into win xp to move files?  I have no idea how to know which ubuntu files to remove for space - proc folder seems to have enough room, but should I just move it to the external drive?  I can't seem to access the rest of the hard Drive where I could simply move a 4GB movie.

---

### Post by fdrake on 2011-08-19
> **dancingLoki said:**
> I am a beginner to Ubuntu & Linux.  Some months back I installed ubuntu on a somewhat aged & slowed down acer laptop running win XP.  Finally I tried running ubuntu a couple days ago & it's been pretty smooth, until this from update manager:
---------------------------------------------------------------
Not enough free disk space

The upgrade needs a total of 615M free space on disk '/'. Please free at least an additional 296M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
---------------------------------------------------------------
I guess I don't have to install these "important security updates", but it's probably best I do & learn how to use the file browser, terminal (Applications - Accessories - really, it's a little hidden), other important parts of ubuntu.

For downloading I have an external drive connected with 760 GB free - more than enough space for anything.  I can also move files to this disk - do I maybe need to reboot into win xp to move files?  I have no idea how to know which ubuntu files to remove for space - proc folder seems to have enough room, but should I just move it to the external drive?  I can't seem to access the rest of the hard Drive where I could simply move a 4GB movie.

```
gksudo nautilus
```
now you can freely move data around. Suggestion format the 760 gb drive to ntfs or fat32 so you can use those files on both win and linux.

---

### Post by Hakunka-Matata on 2011-08-19
> **dancingLoki said:**
> I am a beginner to Ubuntu & Linux.  Some months back I installed ubuntu on a somewhat aged & slowed down acer laptop running win XP.  Finally I tried running ubuntu a couple days ago & it's been pretty smooth, until this from update manager:
---------------------------------------------------------------
Not enough free disk space

The upgrade needs a total of 615M free space on disk '/'. Please free at least an additional 296M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
---------------------------------------------------------------
I guess I don't have to install these "important security updates", but it's probably best I do & learn how to use the file browser, terminal (Applications - Accessories - really, it's a little hidden), other important parts of ubuntu.

For downloading I have an external drive connected with 760 GB free - more than enough space for anything.  I can also move files to this disk - do I maybe need to reboot into win xp to move files?  I have no idea how to know which ubuntu files to remove for space - proc folder seems to have enough room, but should I just move it to the external drive?  I can't seem to access the rest of the hard Drive where I could simply move a 4GB movie.
```

gksu nautilus

``` is dangerous if you're not sure which files to move around.  The command gksu gives you root privileges / super user privileges and that lets you change low level aspects of the system.  I would not use it if you don't know exactly what to move where yet.

---

### Post by Hakunka-Matata on 2011-08-19
> The upgrade needs a total of 615M free space on disk '/'. Please free at  least an additional 296M of disk space on '/'. Empty your trash and  remove temporary packages of former installations using 'sudo apt-get  clean'.

I would suggest doing as advised by the system:  sudo apt-get clean, and so forth.

Open a Terminal (Applications > Accessories > Terminal.)  You can 'drag' the Terminal selection out and stick a copy in your uppermost bar, because you'll use Terminal a lot in future.  Left Click on the Terminal program (or any other program/app), hold down the left button and drag the app to the uppermost bar, then release.  

Once in Terminal, type in (or copy) the command ```
sudo apt-get clean
```, you will then need to enter your password, you'll get no indication while you're typing it, then hit enter.

sudo makes you super user - root, temporarily, only.

---

### Post by dancingLoki on 2011-08-19
Thank you for the quick replies & that's my thoughts too - not to move or delete when I don't know what I'm doing.

XP has been particularly screwed up lately - this is why I'm trying ubuntu - but I managed to free up about 4 GB.  Unfortunately this didn't translate into more space for ubuntu - in Disk Utility I notice 2 volumes - 5.2 GB FAT & 155 GB NTFS.  Is this called a partition?  Is Ubuntu in the 5.2 GB FAT area?  What's it mean to mount a volume?  

most important - what do I do now?  I can probably go back to windows & even free up another 20 GB, but will it make a difference?

---

### Post by Elfy on 2011-08-19
Please open a terminal and run this command, then paste the results here.

```
sudo fdisk -l &&df -h
```

That's a lowercase L not a 1

---

### Post by Hakunka-Matata on 2011-08-19
no, don't go back to windows, it won't help.  Windows can't make changes on you linux partitions.  If we can get a look at your disk partition setup that's the first place to investigate, see what you have where, how big partitions are etc.  SO:
You probably don't have GParted installed yet, as it's not installed by default.  So first do that,

```
sudo apt-get install gparted
```

---

### Post by Elfy on 2011-08-19
Can't see any reason why gparted is needed - even if partitions need resizing they'll need to do so from a livecd.

---

### Post by fdrake on 2011-08-19
> **forestpiskie said:**
> Can't see any reason why gparted is needed - even if partitions need resizing they'll need to do so from a livecd.

well he can start resizing the win partition while he downloads/burns a live-cd

---

### Post by Elfy on 2011-08-19
I suppose so ... 

But I'd do all of that from a livecd, not half in a running system and then the rest later. It also appears that the reason to get it installed is to find out "your disk partition setup"

In addition to which the thread's about gaining space :)

---

### Post by Hakunka-Matata on 2011-08-19
> **forestpiskie said:**
> I suppose so ... 

But I'd do all of that from a livecd, not half in a running system and then the rest later. It also appears that the reason to get it installed is to [COLOR=Red]find out "your disk partition setup"
[/COLOR] 
In addition to which the thread's about gaining space :)

That is exactly why I suggested installing gparted now, the OP states in post # 1 "I am a beginner to Ubuntu & Linux".  I thought he might like to find out how to use a Terminal for instance first, and then maybe start an App like gparted, and see for the first time what a partition layout is for instance.  Before going ahead and making changes,

---

### Post by Elfy on 2011-08-19
> **Hakunka-Matata said:**
> That is exactly why I suggested installing gparted now, the OP states in post # 1 "I am a beginner to Ubuntu & Linux".  I thought he might like to find out how to use a Terminal for instance first, and then maybe start an App like gparted, and see for the first time what a partition layout is for instance.  Before going ahead and making changes,

I can understand that - I'd have done that with a screenshot :)

As it is I'm waiting for the fdisk output - I've got a wubi feeling in my bones, which will make the thread somewhat different :)

---

### Post by fdrake on 2011-08-19
> **forestpiskie said:**
> I can understand that - I'd have done that with a screenshot :)

As it is I'm waiting for the fdisk output - I've got a wubi feeling in my bones, which will make the thread somewhat different :)

:p:p:p  that would be funny. such a waste of time ....

---

### Post by Hakunka-Matata on 2011-08-19
> **forestpiskie said:**
> I can understand that - I'd have done that with a screenshot :)

As it is I'm waiting for the fdisk output - [COLOR=Red]I've got a wubi feeling in my bones[/COLOR], which will make the thread somewhat different :)

*Touché* forestpiskie, very good point, I missed that possibility, hope it's not a probability.  I don't even participate in wubi discussions, they don't interest me.  Ok, i'm a snob, sorry.

---

### Post by dancingLoki on 2011-08-19
> **Hakunka-Matata said:**
> I would suggest doing as advised by the system:  sudo apt-get clean, and so forth.

Open a Terminal (Applications > Accessories > Terminal.)  You can 'drag' the Terminal selection out and stick a copy in your uppermost bar, because you'll use Terminal a lot in future.  Left Click on the Terminal program (or any other program/app), hold down the left button and drag the app to the uppermost bar, then release.  

Once in Terminal, type in (or copy) the command ```
sudo apt-get clean
```, you will then need to enter your password, you'll get no indication while you're typing it, then hit enter.

sudo makes you super user - root, temporarily, only.

I put the terminal in the bar, and ran sudo apt-get clean, but it didn't clear off space, or not enough anyway.

---

### Post by dancingLoki on 2011-08-19
[QUOTE=forestpiskie;11166177]Please open a terminal and run this command, then paste the results here.

```
sudo fdisk -l &&df -h

results:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638       19457   151171650    7  HPFS/NTFS

Disk /dev/mmcblk0: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders
Units = cylinders of 2352 * 512 = 1204224 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               4        3293     3868160    b  W95 FAT32

Disk /dev/mmcblk1: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders
Units = cylinders of 2352 * 512 = 1204224 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk1p1               4        3293     3868160    b  W95 FAT32

Disk /dev/sdb: 1000.2 GB, 1000204884992 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf5154add

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            2.7G  2.3G  279M  90% /
none                  491M  348K  491M   1% /dev
none                  496M  400K  495M   1% /dev/shm
none                  496M   92K  495M   1% /var/run
none                  496M     0  496M   0% /var/lock
none                  496M     0  496M   0% /lib/init/rw
/dev/sda2             145G  140G  5.2G  97% /host
/dev/mmcblk0p1        3.7G  3.7G   19M 100% /media/D8E5-F91A
/dev/mmcblk1p1        3.7G  1.6G  2.2G  43% /media/6361-3162
/dev/sdb1             932G  166G  766G  18% /media/FreeAgent Drive


```

---

### Post by dancingLoki on 2011-08-19
> **Hakunka-Matata said:**
> no, don't go back to windows, it won't help.  Windows can't make changes on you linux partitions.  If we can get a look at your disk partition setup that's the first place to investigate, see what you have where, how big partitions are etc.  SO:
You probably don't have GParted installed yet, as it's not installed by default.  So first do that,

```
sudo apt-get install gparted
```

I installed gparted as written here.  don't know what to do with it.

---

### Post by Elfy on 2011-08-19
Hi - you are running wubi it appears. There are no linux file systems on any of your drives. This is a different kettle of fish indeed.

This thread should help you to resize the wubi file. As it stands the file is 2.7Gb - this is very small. If that was all the space you had available then you might need to think about that a bit more.

[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by dancingLoki on 2011-08-19
> **forestpiskie said:**
> Hi - you are running wubi it appears. There are no linux file systems on any of your drives. This is a different kettle of fish indeed.

This thread should help you to resize the wubi file. As it stands the file is 2.7Gb - this is very small. If that was all the space you had available then you might need to think about that a bit more.

[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)
wubi - windows installer - makes sense.  Are there drawbacks to running linux this way?  I basically have nothing saved in Linux right now, very little customization... is it better for performance that I do a different install?

---

### Post by Elfy on 2011-08-19
It's only designed to be a way to look at ubuntu - there might be performance issues but as I only looked at it once I'm not the person to ask ;)

There are people who look for wubi prefixes - I'd wait for someone more able to answer you :)

---

### Post by bcbc on 2011-08-19
I wouldn't resize the virtual disk... you only have 5 GB free on the /host ntfs partition. If you try and use that you'll likely grind windows to a standstill.

---

### Post by Elfy on 2011-08-19
thanks bcbc - I can unsubscribe now ... :)

---

