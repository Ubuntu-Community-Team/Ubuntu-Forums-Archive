---
title: "Cannot Install Lubuntu: No Root File System is Defined (system crash)"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by m3yw0lf on 2013-07-19
I have used my linux laptop to create a bootable USB to install Lubuntu on my netbook (the specifications of which can be found [here]("http://www.asus.com/Notebooks_Ultrabooks/Eee_PC_1015P_Seashell/#specifications") )

However I keep getting a screen that says "No Root File System Defined." The problem is that I cannot define the root file because there are none available to me on the provided menu. 

Here is my process.

First, I format my USB using Gparted:

[ATTACH=CONFIG]244900[/ATTACH]

Then I use a downloaded lubuntu ISO (I have checked [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") and it passed)
I've created a bootable USB using two programs (wiping and formatting the USB before each attempt)

First using Startup Disk Creator (kde)

[ATTACH=CONFIG]244901[/ATTACH]

Second using UNebootin

[ATTACH=CONFIG]244902[/ATTACH]

Once I've completed the process for both, the result is the same.

I insert into my netbook (after going into the BIOS menu and setting it to boot from usb)

The install options appear.

I click Check disc for defects. > no defects.

I click Install Lubuntu. I choose my language. I choose my wifi.

And then I get this menu. I click Install now, and then I get this message:

[ATTACH=CONFIG]244903[/ATTACH]

When I click "-" "+" or "Change..." the system crashes:

[ATTACH=CONFIG]244904[/ATTACH]

I have tried this with two other USB sticks, and different versions of both Lubuntu and Ubuntu.:frown:

Can anyone help me with this? Thanks ahead of time!

---

### Post by sudodus on 2013-07-19
Can you try Lubuntu (not install, only run a live system from the install USB drive)?

1. If you can, open a terminal window, open the file browser and mount all partitions that can be mounted.

Run the following commands and post the output (cut and paste from the terminal window to 'this' editing window.

```
 sudo fdisk -lu
```
```
 sudo parted -l
```
```
df
```

I want you to do this because I think many of us can give much better advice after seeing the result. Maybe you have four primary partitions, and no possibility to create more partitions unless you delete one partition (that is big enough to give you enough space to install Lubuntu).

2. If you have Windows, boot into it, and check the partitions. If there are  dynamic partitions, linux will have problems. You need to convert  dynamic partitions to standard partitions.

*Edit*:
a. the second command was wrong, it is now changed to what it should be: [FONT=courier new]**sudo parted -l**[/FONT]
b. the descriptions of the tasks are more detailed and I hope easier to understand in my next post (Post #4)

---

### Post by m3yw0lf on 2013-07-19
I can do that! Here was the output:

[FONT=arial]align-check TYPE N                        check partition N for TYPE(min|opt)[/FONT]
[FONT=arial]        alignment[/FONT]
[FONT=arial]  check NUMBER                             do a simple check on the file system[/FONT]
[FONT=arial]  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition[/FONT]
[FONT=arial]  help [COMMAND]                           print general help, or help on[/FONT]
[FONT=arial]        COMMAND[/FONT]
[FONT=arial]  mklabel,mktable LABEL-TYPE               create a new disklabel (partition[/FONT]
[FONT=arial]        table)[/FONT]
[FONT=arial]  mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on[/FONT]
[FONT=arial]        partition NUMBER[/FONT]
[FONT=arial]  mkpart PART-TYPE [FS-TYPE] START END     make a partition[/FONT]
[FONT=arial]  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system[/FONT]
[FONT=arial]  move NUMBER START END                    move partition NUMBER[/FONT]
[FONT=arial]  name NUMBER NAME                         name partition NUMBER as NAME[/FONT]
[FONT=arial]  print [devices|free|list,all|NUMBER]     display the partition table,[/FONT]
[FONT=arial]        available devices, free space, all found partitions, or a particular[/FONT]
[FONT=arial]        partition[/FONT]
[FONT=arial]  quit                                     exit program[/FONT]
[FONT=arial]  rescue START END                         rescue a lost partition near START[/FONT]
[FONT=arial]        and END[/FONT]
[FONT=arial]  resize NUMBER START END                  resize partition NUMBER and its file[/FONT]
[FONT=arial]        system[/FONT]
[FONT=arial]  rm NUMBER                                delete partition NUMBER[/FONT]
[FONT=arial]  select DEVICE                            choose the device to edit[/FONT]
[FONT=arial]  set NUMBER FLAG STATE                    change the FLAG on partition NUMBER[/FONT]
[FONT=arial]  toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition[/FONT]
[FONT=arial]        NUMBER[/FONT]
[FONT=arial]  unit UNIT                                set the default unit to UNIT[/FONT]
[FONT=arial]  version                                  display the version number and[/FONT]
[FONT=arial]        copyright information of GNU Parted[/FONT]

---

### Post by sudodus on 2013-07-20
I'm very sorry! Bad communication from both of us. Two of my suggested commands were correct. You did not respond to them. One of my suggested commands (sudo parted) was missing the option -l. You responded to that (and you only got a help output).

We came a tiny step forward. We know that you can run parted, and you should be able to run all these three commands now. I want you to run these three commands because I think many of us can give much better  advice after seeing the result. Maybe you have four primary partitions,  and no possibility to create more partitions unless you delete one  partition (that is big enough to give you enough space to install  Lubuntu).

-o-

[SIZE=4]1. Lubuntu[/SIZE]

Try Lubuntu (not install, only run a live system from the install USB drive)

1a. If you can, ***open the file browser and mount all partitions*** that can be mounted. Simply click on the icons for the partitions in the left panel of the file browser. (The file browser corresponds to Explorer in Windows.)

1b. ***Open a terminal window***.

For the following commands please post the output between code tags like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

1c. ***Run the following commands and post the output*** (cut and paste from the terminal window to 'this' editing window).

```
 sudo fdisk -lu
```
```
 sudo parted -l
```
```
df
```

[SIZE=4]2. Windows[/SIZE]

 If you have Windows, boot into it, and check the partitions. If there  are  dynamic partitions, linux will have problems. You need to convert   dynamic partitions to standard partitions.

---

### Post by pixiq on 2013-07-20
I think your problem is that 

- either you have an msdos partition table with four partitions. So the Lubuntu installer can not create a new one

- or you have too little free space (you need 4.6 gigabyte free space in one partition, that can be used for Lubuntu).

---

### Post by Vormeph on 2013-07-20
Why did you format your USB through gparted? It's unnecessary since your USB is formated anyway through Startup Disk Creator. My USB is formated as NTFS but still works. What did you format your USB as?  Nvm, I realised that you formatted it as Fat32. Linux should support Fat32, but this file system is really used on Windows, not Linux. It's possible your Linux isn't recognising Fat32. Have you tried formatting your USB as NTFS?

---

### Post by m3yw0lf on 2013-07-20
> **sudodus said:**
> I'm very sorry! Bad communication from both of us. Two of my suggested commands were correct. You did not respond to them. One of my suggested commands (sudo parted) was missing the option -l. You responded to that (and you only got a help output).

We came a tiny step forward. We know that you can run parted, and you should be able to run all these three commands now. I want you to run these three commands because I think many of us can give much better  advice after seeing the result. Maybe you have four primary partitions,  and no possibility to create more partitions unless you delete one  partition (that is big enough to give you enough space to install  Lubuntu).

I'm sorry I misunderstood-  I'm am (quite obviously) new to Linux. Here is my second shot at answering your question:

**sudo fdisk -lu**
```
[FONT=arial]lubuntu@lubuntu:~$ sudo fdisk -lu[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Disk /dev/sda: 4112 MB, 4112515072 bytes[/FONT]
[FONT=arial]9 heads, 8 sectors/track, 111559 cylinders, total 8032256 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x000311cb[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sda1   *         680     8032255     4015788    b  W95 FAT32[/FONT]
```


**sudo parted -l**
```
[FONT=arial]lubuntu@lubuntu:~$ sudo parted -l[/FONT][FONT=arial]Model: Generic Flash Disk (scsi)[/FONT]
[FONT=arial]Disk /dev/sda: 4113MB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/512B[/FONT]
[FONT=arial]Partition Table: msdos[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Number  Start  End     Size    Type     File system  Flags[/FONT]
[FONT=arial] 1      348kB  4113MB  4112MB  primary  fat32        boot[/FONT]
```

**df**
```
[FONT=arial]lubuntu@lubuntu:~$ df[/FONT][FONT=arial]Filesystem     1K-blocks    Used Available Use% Mounted on[/FONT]
[FONT=arial]/cow             1032088   85820    893840   9% /[/FONT]
[FONT=arial]udev              497432       4    497428   1% /dev[/FONT]
[FONT=arial]tmpfs             101712     776    100936   1% /run[/FONT]
[FONT=arial]/dev/sda1        4007940 1755700   2252240  44% /cdrom[/FONT]
[FONT=arial]/dev/loop0        642560  642560         0 100% /rofs[/FONT]
[FONT=arial]none                   4       0         4   0% /sys/fs/cgroup[/FONT]
[FONT=arial]tmpfs             508560       4    508556   1% /tmp[/FONT]
[FONT=arial]none                5120       0      5120   0% /run/lock[/FONT]
[FONT=arial]none              508560     220    508340   1% /run/shm[/FONT]
[FONT=arial]none              102400       8    102392   1% /run/user[/FONT]
```

> **sudodus said:**
> 

[SIZE=4]2. Windows[/SIZE]

If you have Windows, boot into it, and check the partitions. If there are dynamic partitions, linux will have problems. You need to convert dynamic partitions to standard partitions.

To answer this question, I don't have windows on the netbook. The netbook used to have windows, but my friend put Lubuntu on it. He must have done it wrong because something went corrupt and it now won't load past the BIOS menu. This is why I am trying to get Lubuntu back on it.

---

### Post by m3yw0lf on 2013-07-20
> **Vormeph said:**
> Why did you format your USB through gparted? It's unnecessary since your USB is formated anyway through Startup Disk Creator. My USB is formated as NTFS but still works. What did you format your USB as?  Nvm, I realised that you formatted it as Fat32. Linux should support Fat32, but this file system is really used on Windows, not Linux. It's possible your Linux isn't recognising Fat32. Have you tried formatting your USB as NTFS?


Thanks for the suggestion. I will give that a shot.

---

