---
title: "Edgy Upgrade Problem:  Signal Timing"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by mbsasquatch on 2007-01-09
I tried upgrading to edgy and now the screen goes dead on reboot with the following message:  "Attention, Input signal is out of range.  Please change signal timing."  Can anyone tell me how to change the signal timing?

---

### Post by hal10000 on 2007-01-09
WHich graphic card do you use?
Maybe you have just to reconfigure your xserver.
You may boot in recovery mode to do that.

---

### Post by mbsasquatch on 2007-01-17
Ok, I've looked around to try to figure out how to reconfigure my xserver in recovery mode, but found nothing.  Could someone tell me how to try that?  If there's a way to undo my attempted upgrade instead that would be even better!

---

### Post by hal10000 on 2007-01-17
See my posting #4 here: [http://ubuntuforums.org/showthread.php?p=2015980#post2015980](http://ubuntuforums.org/showthread.php?p=2015980#post2015980)

---

### Post by mbsasquatch on 2007-01-17
Hal,  thanks for the info--very helpful.  I've now tried reconfiguring my xserver to a number of different values, but they don't help.  I don't know what to put in for the range.  My monitor manual isn't very helpful here.  I now know that I'm using an MGA 6400 AGP video card with a Winbook C1500 monitor.  How do I know what the ranges should be?  

Also, can anyone tell me a way to access files from my hard drive while booting from a CD?

---

### Post by hal10000 on 2007-01-17
If your monitor is autodetected, then there should be some values in the line.

You may select the "Medium" or "easy" option instead of "Advanced", the values chosen by the configure tool are usually correct.

I have found a manual for your monitor in the internet, and it says you have a LCD monitor. In the configuring tool you have to select an LCD monitor if you are asked.

If the autodetection does not work, and if th manual i found ([http://www.winbookcorp.com/support/lcd/ATLCD15.pdf](http://www.winbookcorp.com/support/lcd/ATLCD15.pdf)) is the right one for your monitor then you may choose the following settings, but be very careful when writing the values, because wrong values may be dangerous to the monitor:

Horzontal frequecies (KHz): 31.5-60
Vertical frequencies (Hz): 56.3-75.0
DON'T MUDDLE HORIZ. AND VERT. SYNC!!!!!!!!!!

To your other question: you can mount a harddrive with your ubuntu live cd by opening nautilus file browser and go to (i guess the name is) "places), there you will see your harddrives.

Another way wold be just to open a terminal and do: [COLOR="Red"]sudo mount /dev/yourpartition /mnt[/COLOR] (the partition which you want to get access to) and browse with a file manager to /mnt.

---

### Post by mbsasquatch on 2007-01-17
Hal, thanks again for your work on this.  As far as I can tell the reconfiguration of xserver as per the instructions above was rejected because somehow the file is "read only."  In addition, the last couple times I've tested the system by restarting it, it goes into a self-test and advises me that I need to check the disk for errors.  This leads me to believe that the problem goes beyond the xserver.  

The direction I'd really like to go at this point is to try to extract some files from the hard drive before wiping the system and starting over.  Unfortunately the instructions above for doing that aren't working yet either.  I should have mentioned that I'm currently booting on a 6.06 live CD (not edgy--that disk isn't working) and I don't seem to have the Nautilous Browser that was mentioned.  The browser I am using doesn't seem to have the files I need-- it shows a 9.1GB volume, but claims it is unable to mount it.  I tried mounting it in a terminal, but don't know what the partition is called.  How do I find out what the partition is called?  If It says it is unable to mount the volume, is there another way I can try to recover the files?  ](*,)

---

### Post by hal10000 on 2007-01-18
1. the /etc/X11/xorg.conf file MUST NOT be readonly for root
In the above posting i forgot to mention that the command for reconfiguring your xserver is [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR] MY posting #4 in [http://ubuntuforums.org/showthread.php?p=2015980#post2015980](http://ubuntuforums.org/showthread.php?p=2015980#post2015980)
is an advice how to deal with this command.

2. if you don't know the names of the partitions then the first thing to try is [COLOR="Red"]sudo fdisk -l[/COLOR] this shows your disks and the partitions on it Here's an example:
```

sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          19      152586   83  Linux
/dev/sda2              20         280     2096482+  83  Linux
/dev/sda3             281        1585    10482412+  83  Linux
/dev/sda4            1586        6546    39849232+   5  Extended
/dev/sda5            1586        2238     5245191   83  Linux
/dev/sda6            2239        2499     2096451   83  Linux
/dev/sda7            2500        2630     1052226   82  Linux swap / Solaris
/dev/sda8            2631        3935    10482381   83  Linux
/dev/sda9            3936        6546    20972826   83  Linux

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         892     7164958+   7  HPFS/NTFS
/dev/hda2             893        1866     7823655   83  Linux
/dev/hda3            1867        2840     7823655   83  Linux
/dev/hda4            2841        4865    16265812+   f  W95 Ext'd (LBA)
/dev/hda5            2841        4802    15759733+  83  Linux
/dev/hda6            4803        4865      506016   82  Linux swap / Solaris

Disk /dev/hdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        5222    41945683+  83  Linux
/dev/hdd2            5223       10011    38467642+   5  Extended
/dev/hdd5            5223       10011    38467611   83  Linux

```

Here you see three harddrives with some partition on each of them.
You have to looh to the last column for one or more entries titled "Linux" (NOT "Linux Swap") and in this line in the first column there is the name of your partition's device.
Let's say you found a "Linux" entry in /dev/hda2, then the command to mount would be [COLOR="Red"]sudo mount /dev/hda2 /mnt[/COLOR]
if you are on a command line you may use the [COLOR="Red"]mc[/COLOR] command and browse to the /mnt directory, where you find the content of your previously mounted partition.

The command to unmount a partition is [COLOR="Red"]sudo umount /mnt[/COLOR] NOTE:this is "umount" not "unmount".

---

