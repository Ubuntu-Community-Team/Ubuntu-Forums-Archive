---
title: "I have 10.10 but think I should have installed 10.04"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by technmom on 2011-01-12
I have 10.04 with dual boot Windows XP on one computer. Then I purchased a new computer on which I have Windows 7. I decided to install ubuntu and chose 10.10 but now that I have it installed I am rethinking. I think I would like to have 10.04 since it will be supported longer. I only have one hard drive. I started to install it but it only allows a side by side with 10.10 & windows 7. Should I get rid of 10.10 and redo the install? How would I go about doing that? 

I would like to do this before I get my work on the system. I have a lot of work to do in Ubuntu and some in Windows.
thanks,
technmom

---

### Post by LetsMugSanta on 2011-01-12
I'm not completely sure on this but I believe you would have to reformat the drive with Windows and then install 10.04. There might be other ways around this but I'm not sure.

---

### Post by elliotn on 2011-01-12
just format the ubuntu 10.10 partition and install 10.04 the normal way

---

### Post by technmom on 2011-01-12
Formatting the partition sounds doable since I don't want to mess up Windows. How do I do that?

---

### Post by marl30 on 2011-01-12
You could just do the formating of the 10.10 partition while installing 10.04. When you get to choosing your partition, just select to format and replace it with 10.04.

---

### Post by ErikNJ on 2011-01-12
Grab "Gparted" from the software center.  Resize your Windows 7 partition to a size you think you'll need in Windows.  Then run the 10.04 install and select the "custom" installation for the drives.  Delete the 10.10 portion of the partition.  Add new partitions as you see fit (or just "/" as your only mount point) and install.  BE CAREFUL NOT TO FORMAT THE NTFS PARTITION - you will lose Windows!

---

### Post by technmom on 2011-01-12
I am in the middle of doing this and am having probelms. Please help I had this

/dve/sda1 Windows 7 41.1 MB
/Windows 7(loadr) /dev/sda2 15. G
/dev/sda3 153.4 GB
ubuntu (10.10  145.5GB

the next screen showed

I deleted the bottom two and went forward and it says 

No root file system is defined


> **ErikNJ said:**
> Grab "Gparted" from the software center.  Resize your Windows 7 partition to a size you think you'll need in Windows.  Then run the 10.04 install and select the "custom" installation for the drives.  Delete the 10.10 portion of the partition.  Add new partitions as you see fit (or just "/" as your only mount point) and install.  BE CAREFUL NOT TO FORMAT THE NTFS PARTITION - you will lose Windows!

---

### Post by kansasnoob on 2011-01-12
> **letsmugsanta said:**
> i'm not completely sure on this but i believe you would have to reformat the drive with windows and then install 10.04. There might be other ways around this but i'm not sure.

nonsense!

---

### Post by kansasnoob on 2011-01-13
> **technmom said:**
> I am in the middle of doing this and am having probelms. Please help I had this

/dve/sda1 Windows 7 41.1 MB
/Windows 7(loadr) /dev/sda2 15. G
/dev/sda3 153.4 GB
ubuntu (10.10  145.5GB

the next screen showed

I deleted the bottom two and went forward and it says 

No root file system is defined

You didn't know enough. You received poor advice!

You only needed to reinstall over the existing Ubuntu partitions!

At this point I'd suggest you stop manipulating the disc altogether and run only a Live CD! Then post the output of:

```
sudo parted -l
```

If you have only one hard drive also post a screenshot of that drive.

But I'll be gone until tomorrow.

Here's some very basic advice:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

People should not offer advice when they don't know what they're talking about!

---

### Post by technmom on 2011-01-13
thanks off to do that...

---

### Post by technmom on 2011-01-13
model: ATA WDC WD3200AAKS-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16
 2      41.9MB  15.0GB  15.0GB  primary   ntfs            boot
 3      15.0GB  168GB   153GB   primary   ntfs
 4      168GB   320GB   152GB   extended
 5      168GB   255GB   86.8GB  logical   ext4
 6      314GB   320GB   6199MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$

---

### Post by technmom on 2011-01-13
Sorry if this is a duplicate, it didn't seem to go through th first time


model: ATA WDC WD3200AAKS-7 (scsi)
  Disk /dev/sda: 320GB
  Sector size (logical/physical): 512B/512B
  Partition Table: msdos
   
  Number  Start   End     Size    Type      File system     Flags
   1      32.3kB  41.1MB  41.1MB  primary   fat16
   2      41.9MB  15.0GB  15.0GB  primary   ntfs            boot
   3      15.0GB  168GB   153GB   primary   ntfs
   4      168GB   320GB   152GB   extended
   5      168GB   255GB   86.8GB  logical   ext4
   6      314GB   320GB   6199MB  logical   linux-swap(v1)
   
   
  Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
  has been opened read-only.
  Error: /dev/sr0: unrecognised disk label                                  
   
  ubuntu@ubuntu:~$

---

### Post by technmom on 2011-01-13
THank you Kansasnoob. That site looks great. I won't be able to get to this computer until Tomorrow late or Friday, but I will have access to the internet and will read that info.

---

### Post by ErikNJ on 2011-01-13
> **technmom said:**
> model: ATA WDC WD3200AAKS-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16
 2      41.9MB  15.0GB  15.0GB  primary   ntfs            boot
 3      15.0GB  168GB   153GB   primary   ntfs
 4      168GB   320GB   152GB   extended
 5      168GB   255GB   86.8GB  logical   ext4
 6      314GB   320GB   6199MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$

It looks like you didn't overwrite anything yet (no need for any unnecessary panic).

When you install, you can delete what you see above in numbers 5 and 6 (provided you've backed up everything there you need first).

The "no root" error you saw is because you didn't select any mount point for root.  You need to select "/" (or more if you want to partition further - I usually put /home on a different partition).

Of course, if you are happy with your current windows partition size - there's no need to resize it with gparted.

And, if you are unsure about anything here, do not move beyond the disk partitioning - you can lose data at that point.

Additional note:

The only mount point you must have when you specify your partitions manually is "/" and everything else will reside within that partition.  You may want to manually create a partition for "swap."

---

### Post by kansasnoob on 2011-01-14
> **ErikNJ said:**
> It looks like you didn't overwrite anything yet **[COLOR="Red"](no need for any unnecessary panic).[/COLOR]**

When you install, you can delete what you see above in numbers 5 and 6 (provided you've backed up everything there you need first).

The "no root" error you saw is because you didn't select any mount point for root.  You need to select "/" (or more if you want to partition further - I usually put /home on a different partition).

Of course, if you are happy with your current windows partition size - there's no need to resize it with gparted.

And, if you are unsure about anything here, do not move beyond the disk partitioning - you can lose data at that point.

Additional note:

The only mount point you must have when you specify your partitions manually is "/" and everything else will reside within that partition.  You may want to manually create a partition for "swap."

Sorry about the panic, I'm old and I get cranky sometimes :frown:

---

### Post by kansasnoob on 2011-01-14
> **technmom said:**
> Sorry if this is a duplicate, it didn't seem to go through th first time


model: ATA WDC WD3200AAKS-7 (scsi)
  Disk **[COLOR="Red"]/dev/sda[/COLOR]**: 320GB
  Sector size (logical/physical): 512B/512B
  Partition Table: msdos
   
  Number  Start   End     Size    Type      File system     Flags
   **[COLOR="Red"]1[/COLOR]**      32.3kB  41.1MB  41.1MB  primary   fat16
   **[COLOR="Red"]2[/COLOR]**      41.9MB  15.0GB  15.0GB  primary   ntfs            boot
   **[COLOR="Red"]3[/COLOR]**      15.0GB  168GB   153GB   primary   ntfs
   **[COLOR="Red"]4[/COLOR]**      168GB   320GB   152GB   extended
   **[COLOR="Red"]5[/COLOR]**      168GB   255GB   86.8GB  logical   ext4
   **[COLOR="Red"]6[/COLOR]**      314GB   320GB   6199MB  logical   linux-swap(v1)
   
   
  Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
  has been opened read-only.
  Error: /dev/sr0: unrecognised disk label                                  
   
  ubuntu@ubuntu:~$

Just so you totally understand how to read that I highlighted the drive designation and partition designations in that quote. Just a bit about device designations:

The forward slashes are just "separators" and the "dev" just means device. The "sd" just indicates hard drive. The first character following "sd" indicates the drive "number" and the next character indicates the partition "number" as such:

Drives are designated as /dev/sda, /dev/sdb, /dev/sdc, etc. the last letter indicates the drive number, eg:
/dev/sda = drive #1
/dev/sdb = drive #2
/dev/sdc = drive #3

Partititions are designated with a number following the drive designations, eg:
/dev/sda1 = drive #1/partition #1
/dev/sda2 = drive #1/partition #2
/dev/sdb1 = drive #2/partition #1

You'll notice a lot of people request the output of "fdisk -l" rather than "parted -l". They can each be useful but fdisk tends not to list partitions in their actual order as you can see in this **[COLOR="Red"]example[/COLOR]**:

```
lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00082dba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9197    73872384   83  Linux
/dev/sdb2            9328        9730     3227649    5  Extended
/dev/sdb3            9197        9328     1048576    7  HPFS/NTFS
/dev/sdb5            9328        9730     3227648   82  Linux swap / Solaris

**[COLOR="Red"]Partition table entries are not in disk order[/COLOR]**

lance@lance-desktop:~$ sudo parted -l

Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  75.6GB  75.6GB  primary   ext4
 3      75.6GB  76.7GB  1074MB  primary   ntfs
 2      76.7GB  80.0GB  3305MB  extended
 5      76.7GB  80.0GB  3305MB  logical   linux-swap(v1)

```

Regardless both are useful but with parted you simply "add" the partition "number" to the end of the drive designation. Clear as mud?

Anyway, from your output we can see that /dev/sda1, /dev/sda2, and /dev/sda3 are all most likely Windows system partitions so you DO NOT want to make any changes to them!

Next comes /dev/sda4 which is an extended partition that is actually just a "shell" that can contain a large number of logical partitions so you can work beyond the four primary partition limit :)

I tend to carry that to extremes because I do a lot of testing:

[ATTACH]181073[/ATTACH]

Regardless, in your case the partition you'd want to reinstall over is /dev/sda5 so after selecting the Manual/Advanced partitioning option you'd select only /dev/sda5 from the list and click on "Change" which will display a window similar to this:

[ATTACH]181074[/ATTACH]

You need to complete all four of those fields before proceeding. Since you're reusing the same partition I'd assume that the size is appropriate, Ext4 is now the default filesystem, the root partition must be "formatted" to proceed, and "/" must be selected to indicate it's the root partition.

NOTE: Clicking on "Format the partition" will erase/destroy all data on that partition! If in doubt always create a backup. In fact things can go wrong with any installation/repartitioning operation so, if you just can't lose it, back it up!

OTOH if you wanted to create a new partition there, or delete the old one and then create a new one the window that opens looks a bit different:

[ATTACH]181075[/ATTACH]

Regarding existing SWAP partitions no change need be made. The Ubuntu installer "sniffs out" all existing SWAP partitions and will automatically use them unless told otherwise.

Have I helped, or only confused you :confused:

---

### Post by kansasnoob on 2011-01-14
Odd problem with the forums today. I reply but Firefox shows it's not done look:

[ATTACH]181083[/ATTACH]

Anyone else?

---

### Post by Pillars of Creation on 2011-01-14
Technmom,

What I recommend you do at this point is to boot into the Ubuntu install disc in live CD mode and run the GParted partition editor. It’s under system/administration. It’s either listed as simply GParted or GParted partition editor. Maximize to full screen. Note the sda number of the 86.8 GB partition. Reboot and start the installation of Ubuntu 10.04. No need to format the partition here as you’re going to do it later on in the install process.

Click on install Ubuntu 10.04 LTS. Click forward. Click forward. Under prepare disk, check the radio button for “specify partitions manually (advanced)”. Click forward. From the list of partitions select the partition with the sda number that you noted earlier. It should be approximately 86800 MB in size. Select the partition by left clicking on the arrow that it is in.

This is very important. In the little white box in the row under “format” left click twice. To the right of where it says “use as” click on the arrow down button. Select ext4 journaling file system. In a little white box to the right of “format the partition”, put a check box. Click the down arrow to the right of “mount point”. Select the foreword slash “/”. Click okay.

Click next. Enter your name or desired login name. Press the Num lock key. Enter a password. Click on the radio button for login automatically if you want automatic logon. Click forward. Click install.

That should do it. :D

Also note that is not much harder to run two Ubuntu’s side-by-side on the same partition. You simply need to make an extra logical partition in the extended partition. The GRUB-2 boot loader will pick up the second installation in the boot loader menu and display the second Ubuntu OS at the top of the list.

---

### Post by technmom on 2011-01-15
evice Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1827    14632960    7  HPFS/NTFS
/dev/sda3            1827       20370   148947968    7  HPFS/NTFS
/dev/sda4           20476       38914   148104193    5  Extended
/dev/sda5           20476       31023    84722552   83  Linux
/dev/sda6           38160       38914     6053888   82  Linux swap / Solaris
office@office-home:~$ 

I'm still somewhat confused......could be because it is very late. Why I don't get to this earlier I don't know. Old is relative. I also get cranky
anyway is there someway I can get more disc space by changing the extended partition to a smaller one before I attamt this. I think I messed that up before What I was hoping was to split the disc in approx two 1/2 for windows and 1/2 for ubuntu

---

### Post by kansasnoob on 2011-01-15
I didn't notice earlier:

> model: ATA WDC WD3200AAKS-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 41.1MB 41.1MB primary fat16
2 41.9MB 15.0GB 15.0GB primary ntfs boot
3 15.0GB 168GB 153GB primary ntfs
4 168GB 320GB **[COLOR="Red"]152GB[/COLOR]** extended
5 168GB 255GB **[COLOR="Red"]86.8GB[/COLOR]** logical ext4
6 314GB 320GB 6199MB logical linux-swap(v1)

You notice that the extended partition is the size you expected:  152GB (begins at 168, ends at 320)

But sda5 is only 86.8 GB (begins at 168, ends at 255) and sda6 begins at 314GB so if you look at Gparted I'm sure you'll find that the space between sda5 and sda6 is unallocated (approximately 59GB).

You can either fix that using Gparted from the Libve CD ahead of time or when you get to this screen just use the up toggle next to "new size":

[ATTACH]181146[/ATTACH]

Clear as mud?

---

### Post by kansasnoob on 2011-01-15
I guess this would have been a better way to show that:

> model: ATA WDC WD3200AAKS-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 41.1MB 41.1MB primary fat16
2 41.9MB 15.0GB 15.0GB primary ntfs boot
3 15.0GB 168GB 153GB primary ntfs
4 168GB 320GB 152GB extended
5 168GB **[COLOR="Red"]255GB[/COLOR]** 86.8GB logical ext4
6 **[COLOR="Red"]314GB[/COLOR]** 320GB 6199MB logical linux-swap(v1) 

The space between 255GB and 314GB will appear as "unallocated" and can be used by sda5 :)

---

### Post by technmom on 2011-01-16
Now I get it.  I am going to work on this today hopefully I'll have good news for you soon thanks for the help
 
> **kansasnoob said:**
> I didn't notice earlier:
 
 
 
You notice that the extended partition is the size you expected: 152GB (begins at 168, ends at 320)
 
But sda5 is only 86.8 GB (begins at 168, ends at 255) and sda6 begins at 314GB so if you look at Gparted I'm sure you'll find that the space between sda5 and sda6 is unallocated (approximately 59GB).
 
You can either fix that using Gparted from the Libve CD ahead of time or when you get to this screen just use the up toggle next to "new size":
 
[ATTACH]181146[/ATTACH]
 
Clear as mud?

---

### Post by technmom on 2011-01-17
I got it up and running although I'm not sure that I have the partition sizes they way I wanted. I would close this out, but its late and I want to read through and see if I have it all the way I would like it. Unfortunately, I have only been able to spend spotty time periods on this.....The life of a mom. Thanks for all the help.

---

### Post by technmom on 2011-01-18
I can only access approximately 200 G of my hard drive. How do I mount the other part. I'm also having trouble seeing my external drive

---

### Post by technmom on 2011-01-19
I'm not having problems with my external drive. I tried differnt usb ports etc. finally discovering it didn't boot in windows either. The cable to the back of it wasn't in. That is working, but I still don't seem to be able to access all of my hard drive.

---

### Post by kansasnoob on 2011-01-19
Please post a new output of:

```
sudo parted -l
```

You'd also be doing me a favor if you'd post the output in code tags by clicking on the **[COLOR="Red"]#[/COLOR]** in the upper right hand corner of the reply box then, with the cursor blinking between the code tags, right click and select paste. It just keeps things in tidy rows so it's easier to read :)

---

### Post by technmom on 2011-01-19
[CODE]/[Model: ATA WDC WD3200AAKS-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16
 2      41.9MB  15.0GB  15.0GB  primary   ntfs            boot
 3      15.0GB  168GB   153GB   primary   ntfs
 4      168GB   320GB   152GB   extended
 5      168GB   255GB   86.8GB  logical   ext4
 6      314GB   320GB   6199MB  logical   linux-swap(v1)

CODE]

hope I did that right

---

### Post by kansasnoob on 2011-01-19
You didn't get the code tag thing right but don't sweat it :)

I need to find a better way to explain that. Knowing how to do something and being able to explain it are often miles apart and I'm not that great at explaining things, anyway look at that:

sda5 ends on 255GB:

> 5 168GB **[COLOR="Red"]255GB[/COLOR]** 86.8GB logical ext4

and sda6 begins on 314GB:

> 6 **[COLOR="Red"]314GB[/COLOR]** 320GB 6199MB logical linux-swap(v1)

So, we're going to use Gparted to have a look, **[COLOR="Red"]but not to make any changes![/COLOR]**

You'll need to boot into Ubuntu and install 'gparted'. You can do that either using Synaptic, Ubuntu Software Center, or you could go to terminal and run:

```
sudo apt-get install gparted
```

You'll then find it in System > Administration > Gparted (aka: partition editor).

Time out for safety sake! I prefer never using Gparted to resize or otherwise edit any Windows 7 or Vista partition with the exception of creating a label or occasionally setting a boot flag if needed due to a boot problem! Your Windows partitions are sda1, sda2, and sda3! Leave them alone!

I'll almost bet that you see a "greyed out" area between sda5 and sda6 that shows up as "unallocated". That means it's unused or "free space".

It may be helpful to see a screenshot if you're at all in doubt. Ubuntu's screenshot tool is in Accessories and if you took a screenshot of Gparted you could save it to Desktop, then click on the paperclip thingy at the top of this reply box.

There you can click on Browse, select Desktop, then select the exact file (eg: Screenshot--dev-sda - GParted.png), then select Upload. Wait for the progress bar to show it's done, then minimize that window, click on the paperclip thingy again, and then attach the file.

If, as suspected, you have such an unallocated area between sda5 and sda6 you would then need to use the Ubuntu Live CD/USB to "add" that area to the Ubuntu root partition (sda5).

Typically you would boot the Live CD/USB choosing to "Try Ubuntu" and then once you're running the live desktop go to Gparted (it's already installed) and you'll likely see that there is a keyring emblem next to sda4 and sda6. That's because most Linux Live OS's will use all available swap when booting.

So the first thing you'd need to do is click on the swap partition to highlight it, then right-click and select Swapoff. Then click on the green checkmark to apply. That should only take a few moments and when it's complete you should now see no more keyrings.

Now, if as suspected, you see a gray unallocated area between sda5 and sda6 you'd click on sda5 to highlight it, then right-click and select Resize/Move. Then a new window will open similar to this:

[ATTACH]181517[/ATTACH]

**[COLOR="Red"]NOTE:[/COLOR]** When I say similar I mean just that! The device designation is wrong, the sizes are not the same! It's only "representative"!

Now, if you hover the mouse pointer over the colored part of that graphic you'll notice that at either end it turns to a double arrow which indicates you can "drag" that end to resize the partition. Alternately if you hover in the center it turns to a fist which indicates "move".

If, as suspected, you have a gray area to the right simply "drag" the right end all the way to the right, click on Resize/Move in the lower right hand corner, then if things look right on the next screen click on the green checkmark to apply.

I'd expect that procedure to take anywhere from 10 to 30 minutes. **[COLOR="Red"]Do not abort or quit during that process![/COLOR]** Be patient and when it's done that should be it.

I hope I did a good job of explaining this.

---

### Post by technmom on 2011-01-30
Thanks for all the help. I used Gparted after booting from the CD and everything looks great! Thanks for all the help over the last few weeks. it takes me forever to get to things but now I have everything up and running well.........I haven't checked Windows much because i don't use it much. Some day i might even get rid of it.

---

