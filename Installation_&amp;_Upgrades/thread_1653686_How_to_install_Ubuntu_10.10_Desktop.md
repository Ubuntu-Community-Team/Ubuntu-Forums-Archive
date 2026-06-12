---
title: "How to install Ubuntu 10.10 Desktop?"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by HaHa Sandman on 2010-12-27
Okay, i'm totally new to Linux-based OSs and i don't know how to install Ubuntu on a different partition only on a tottally different drive or within windows and i don't want that, i want to install it on a different partition other then the one Windows XP SP2 is on (c).

So that everytime my computer boots prompts me if i want to use WinXP or Ubuntu, that way if someday something happens with WinXP or Ubuntu inbstead of imediately re-installing the OS, i can log on to the working one and save my files.

I have 2 HDD:

1x160GB HDD (Partition D)
1x80GB HDD (Splited in half Partition C & E) C (39GB), E (35.3GB)

The "Erase and use the entire disk" option didn't work for me since it couldn't see my partitions only my hard drives and i need help with how to use the "Specify partitions manually (advanced)" option, i got stuck not knowing witch partition is witch for sure, i asume the 37934 MB HDD may be the E partition i want to install Ubuntu on, but want to be sure before i continue.

[IMG]http://img257.imageshack.us/img257/9512/17971414.png[/IMG]
[IMG]http://img844.imageshack.us/img844/9973/14020322.png[/IMG]
[IMG]http://img109.imageshack.us/img109/152/61377210.png[/IMG]

---

### Post by jroa on 2010-12-27
Alright, you need to figure out where you want to free up space first.  You have sda1, sda5, and sdb1.  sda5 looks like it has the most available space.

It has been a while since I have done a fresh install next to Windows, but I personally would free up the space manually and then install to the free space.  But it should work fine if you let the installer do it.  Just select the partition that you want to take space from, select change, and then I believe that you just have to tell it how much space you want to give to Ubuntu.  It may give you other choices as far as /boot or /home locations or home many partitions Ubuntu will occupy, but it should be fairly straight forward.

---

### Post by HaHa Sandman on 2010-12-27
sda5 is Partition E exacly where i want to install Ubuntu, the partition is empty, i just didn't formated yet, i thought Ubuntu will do so before installing it in that location.

[IMG]http://img221.imageshack.us/img221/5467/20101227154333.png[/IMG]

I'll try that and come back with further info, thank you.

EDIT:

Okay tryed that but i get some sort of error.

[IMG]http://img442.imageshack.us/img442/7980/28792122.png[/IMG]
[IMG]http://img340.imageshack.us/img340/8105/53746460.png[/IMG]

There's a small unchecked square next to sdb5 can't seem to check it tough. I highlighted sdb5 and clicked "Install Now" and the error pop-ed up. Any suggestions? Sorry for beying a pain in the but and asking so many questions but the tutorial on ubuntu.com wasn't of too much help to me.

And btw what do i need to choose at "Boot Loader" ? Or do i leave it as it is? I want after installation to be able to chose at system boot witch OS to use.

---

### Post by ajgreeny on 2010-12-27
OK, let's talk in round figures here for the sda5 partition of 35 GB

Choose that after you click the "Specify partitions manually" choice.
Now having highlighted that partition, shrink it to about 33 GB leaving about 2GB at the far right hand end.

Now choose sda5 again and click the "Change" button and then in the table that appears use ext4 as the "Use as", and choose / as the mount point.  Click OK and after that has been done go to the small 2GB partition, click on it and choose to use as "linux swap".  You don't need to set a mount point for that.  Click OK again and all should go as planned.

Come back again if it does not make sense to you, or if I have any of the nomenclature wrong for the various choices I've suggested, but once you try it things may become clearer.

---

### Post by kansasnoob on 2010-12-27
Take a look here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

And especially here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by saptarshighosh on 2010-12-27
> **HaHa Sandman said:**
> sda5 is Partition E exacly where i want to install Ubuntu, the partition is empty, i just didn't formated yet, i thought Ubuntu will do so before installing it in that location.

[IMG]http://img221.imageshack.us/img221/5467/20101227154333.png[/IMG]

I'll try that and come back with further info, thank you.

EDIT:

Okay tryed that but i get some sort of error.

[IMG]http://img442.imageshack.us/img442/7980/28792122.png[/IMG]
[IMG]http://img340.imageshack.us/img340/8105/53746460.png[/IMG]

There's a small unchecked square next to sdb5 can't seem to check it tough. I highlighted sdb5 and clicked "Install Now" and the error pop-ed up. Any suggestions? Sorry for beying a pain in the but and asking so many questions but the tutorial on ubuntu.com wasn't of too much help to me.

And btw what do i need to choose at "Boot Loader" ? Or do i leave it as it is? I want after installation to be able to chose at system boot witch OS to use.
Well you need to select the mount point of the partition as root. Now the sda5 partition partition is ~35GB. When you click "Change" a window pop-ups where you need to select the mount point. If you want to install the os to sda5, then use the mount point as "/". Try it.

---

### Post by HaHa Sandman on 2010-12-29
Okay i've read some of kansasnoob's tutorials but i'm stil stuck or unsure in a few spots.

1. At "Preparing to install Ubuntu" my internet connexion is disabled, this must be because i'm using a network connexion that requires me to connect to the internet manually everytime i log into XP, so i asume i can download the updates after i install Ubuntu and configure my network connection.

2. Specify partitions manually (advanced)

These are my HDDs and partitions

C = /dev/sda1 (41940MB out of 80GB)
D = /dev/sdb1 (160GB out of 160GB)
E = /dev/sda5 (37934 out of 80GB)

Now this is what i understood i have to do:

1. Delete partition E (/dev/sda5)

2. Create a NEW partition E but with 2GB less on it then before. "Type of new partition" needs to be set as "Primary", and "Location for the new partition" needs to be set on "Beginning".

And "Mount Point" needs to be set on "/" so it can use the swap area thinggy. After this we go back to the 2000MB free space and create another partition witch is going to be used as a "swap area".
This one should have "Type of new partition" set to "Logical" and not "Primary" and "Location for the new partition" selected "End"

And the "Use as" set to "swap area"

Have i got it right so far?

3. Boot Loader (GNU/GRUB)

"The best choice for most people would be /dev/sda, the first hard disk."

On /dev/sda1 is installed Windows XP and read that you can't install it on a HDD/partition where you have Windows installed, that means my choise remains /dev/sda5 right? /dev/sdb1 is for storage (films,music etc.)

Have i got all of this right? (sorry for writing so much, i just wanted to be as precise as possible)

Info from one of kansasnoob's links:

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by kansasnoob on 2010-12-29
In order to be absolutely certain I'm providing proper specific instructions I'd first need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

And also the output from terminal of these two commands:

```
sudo parted -l
```

```
free
```

Alternate instructions for the Boot Info Script here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by kansasnoob on 2010-12-29
BTW I really appreciate you taking the proper time and caution to prepare in advance. I know it can at times seem a bit overwhelming but, if you end up loving Ubuntu as much as I do, you'll find that everything you learn is well worth the effort.

And a lot of what you learn here applies to many other Linux/Unix distros as well. There are lots and lots of distros:

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by HaHa Sandman on 2010-12-29
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdb2          81,915,435   156,007,214    74,091,780   f W95 Ext d (LBA)
/dev/sdb5          81,915,498   156,007,214    74,091,717   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B694A95094A913C1                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BEAC5042AC4FF385                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        2884FD4884FD18D0                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/B694A95094A913C1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  f7 c3 ef 28 73 99 2b 26  00 49 a9 b9 0b da a5 8e  |...(s.+&.I......|
00000010  ab 11 fe 40 78 e6 15 5c  cf a7 4a 68 37 57 98 87  |...@x..\..Jh7W..|
00000020  c2 c3 1d c2 ab 8a c2 8e  4a 54 15 5b 46 49 ff 38  |........JT.[FI.8|
00000030  15 8f 46 3e 6e 25 9a 89  0b e4 bf 1f 08 8d ce ba  |..F>n%..........|
00000040  7f bb b2 aa e3 9a c8 a8  e1 5f 8e f8 4d 59 e3 75  |........._..MY.u|
00000050  16 af 33 e8 07 35 2b 43  33 4a 55 da 4f 6d 6f 7d  |..3..5+C3JU.Omo}|
00000060  d8 7d e4 7b 8d 4b 08 f6  43 23 8e 6f 7d 6d 54 24  |.}.{.K..C#.o}mT$|
00000070  09 b4 19 c8 f5 7b aa b7  91 b8 aa 6d 14 c0 e4 bf  |.....{.....m....|
00000080  a0 65 11 f9 4e 89 3f 40  fa 64 c3 19 10 e9 20 16  |.e..N.?@.d.... .|
00000090  b3 bf 49 49 6b fd ce 4b  38 5f 9b d7 a5 ed 66 2e  |..IIk..K8_....f.|
000000a0  b5 9e ec c4 0c d3 a3 93  0c 07 15 da c4 9f 01 7f  |................|
000000b0  29 1e 87 8a 6b c3 fb 9d  12 08 88 a5 8c 2a 48 6a  |)...k........*Hj|
000000c0  4f 69 16 e4 3f f8 1c 63  ff 00 9b 59 7e f7 bb 19  |Oi..?..c...Y~...|
000000d0  8c e1 aa c3 e0 cf d8 6b  67 74 6f 59 df 8d d0 5d  |.......kgtoY...]|
000000e0  32 3b 83 ea d7 1d f7 83  dd bb 49 3c c5 88 24 85  |2;........I<..$.|
000000f0  00 c0 7a be bc 18 2f 3e  a5 46 26 09 5e 16 3e 25  |..z.../>.F&.^.>%|
00000100  aa fe f0 27 44 2e 2a f7  1e 7c 9c 26 7c 82 35 2a  |...'D.*..|.&|.5*|
00000110  08 69 b9 9c 27 7f 6c b2  52 b9 80 fc 69 14 71 cc  |.i..'.l.R...i.q.|
00000120  08 5d 6f ed 10 b0 b4 77  c0 23 de 7d a5 8e da be  |.]o....w.#.}....|
00000130  dc 3e 10 d6 4f dc 19 db  29 fd 66 af 56 f8 54 7d  |.>..O...).f.V.T}|
00000140  1d f7 9d 3d 95 9e 1e 07  23 34 ec 8a bc 03 be 4c  |...=....#4.....L|
00000150  d1 a5 43 74 d4 6b 1d 22  a8 2c 8d 6a 13 8f b7 90  |..Ct.k.".,.j....|
00000160  7a cd 28 91 59 5e bb 2e  05 68 d1 29 47 56 6a df  |z.(.Y^...h.)GVj.|
00000170  13 e7 7a 39 33 06 aa 05  ef 14 d0 0d 91 d7 a1 4c  |..z93..........L|
00000180  3a 8d 43 5e 1e 36 f6 2b  9d 86 27 b0 0c d3 c8 fa  |:.C^.6.+..'.....|
00000190  91 77 c9 93 d5 83 3f 4b  37 a3 87 55 c1 47 bd 79  |.w....?K7..U.G.y|
000001a0  7a 17 6e 61 68 78 ae c2  2d fb 47 db 4e b9 57 ac  |z.nahx..-.G.N.W.|
000001b0  5e 6d d9 e6 e2 90 cd 17  9f d2 37 1d fe e0 00 01  |^m........7.....|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 c5 8c 6a 04 00 00  |......?.....j...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Is this what you wanted my friend?

> BTW I really appreciate you taking the proper time and caution to prepare in advance. I know it can at times seem a bit overwhelming but, if you end up loving Ubuntu as much as I do, you'll find that everything you learn is well worth the effort.

And a lot of what you learn here applies to many other Linux/Unix distros as well. There are lots and lots of distros:

[http://distrowatch.com/](http://distrowatch.com/)

I like learning something new everyday :)

As for other Linux systems i've read about many of them, but the Linux titans i found praised were Ubuntu and openSUSE, so i chose Ubuntu, cause it's a little more compact and best to start off if you're new to Linux.

---

### Post by kansasnoob on 2010-12-29
I'd also like the output of those other two commands. Each has a reason, and I should tell you that you're helping Herman, Rubi1200, and I learn how to better help those needing a multi-boot solution. In fact I just posted about that:

[http://ubuntuforums.org/showpost.php?p=10292809&postcount=82](http://ubuntuforums.org/showpost.php?p=10292809&postcount=82)

Our goal is to provide the most informative and yet concise info possible for anyone to install Ubuntu using the manual/advanced option.

The reason I need the output of both 'sudo parted -l' and 'free' are to determine the proper size for SWAP and to get a more human readable look at partitions.

Just as an example, on my machine if I run 'free':

```
lance@lance-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2050396     639620    1410776          0      16212     332248
-/+ buffers/cache:     291160    1759236
Swap:      2457908          0    2457908

```

There I can see exactly how much RAM my system has, of course I already have SWAP because I have Linux already.

The reason I want the output of 'sudo parted -l' is that the Boot Info Script uses 'fdisk -l'. Look at the difference:

```
lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00052a50

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          79      625664   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              79        1121     8372224   83  Linux
/dev/sdb3            1121        9730    69151744    5  Extended
/dev/sdb5            1121        9592    68045824   83  Linux
/dev/sdb6            9592        9730     1103872   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2610    20964793+  83  Linux
/dev/sda2            2611        5219    20956792+  83  Linux
/dev/sda3            5220       18363   105579180   83  Linux
/dev/sda4           18364       60801   340883173    5  Extended
/dev/sda5           39292       45992    53825751   83  Linux
/dev/sda6           45993       52514    52387933+  83  Linux
/dev/sda7           52515       59192    53641003+  83  Linux
/dev/sda8           59193       60495    10466316   83  Linux
/dev/sda9           60496       60801     2457913+  82  Linux swap / Solaris
/dev/sda10          36642       39291    21286093+  83  Linux
/dev/sda11          33998       36641    21237898+  83  Linux
/dev/sda12          31366       33997    21141508+  83  Linux
/dev/sda13          28691       31365    21486906   83  Linux
/dev/sda14          18364       20924    20571169+  83  Linux
/dev/sda15          20925       23487    20587266   83  Linux
/dev/sda16          23488       26089    20900533+  83  Linux
/dev/sda17          26090       28690    20892501   83  Linux

Partition table entries are not in disk order
lance@lance-desktop:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary   ext3            boot
 2      21.5GB  42.9GB  21.5GB  primary   ext3
 3      42.9GB  151GB   108GB   primary   ext3
 4      151GB   500GB   349GB   extended
14      151GB   172GB   21.1GB  logical   ext4
15      172GB   193GB   21.1GB  logical   ext4
16      193GB   215GB   21.4GB  logical   ext4
17      215GB   236GB   21.4GB  logical   ext4
13      236GB   258GB   22.0GB  logical   ext4
12      258GB   280GB   21.6GB  logical   ext4
11      280GB   301GB   21.7GB  logical   ext3
10      301GB   323GB   21.8GB  logical   ext4
 5      323GB   378GB   55.1GB  logical   ext3
 6      378GB   432GB   53.6GB  logical   ext3
 7      432GB   487GB   54.9GB  logical   ext3
 8      487GB   498GB   10.7GB  logical   ext3
 9      498GB   500GB   2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  642MB   641MB   primary   ext3
 2      642MB   9215MB  8573MB  primary   ext3
 3      9215MB  80.0GB  70.8GB  extended
 5      9216MB  78.9GB  69.7GB  logical   ext3
 6      78.9GB  80.0GB  1130MB  logical   linux-swap(v1)

```

I need a bit of a break to care for my goats and hopefully I'll be back very soon.

---

### Post by HaHa Sandman on 2010-12-30
The reason i didn't give you the result of those values you gave me it's because i didn't know how to enter them in the terminal, i tried something today hope this is at least a part of what you want to know.

If not let me know how else can i enter them (btw i know the lance@lance must have been you're computers user name but i ran out of ideas and tried it just in case...)

[IMG]http://img233.imageshack.us/img233/8029/screenshotwi.png[/IMG]
[IMG]http://img209.imageshack.us/img209/9681/screenshot1mm.png[/IMG]
[IMG]http://img41.imageshack.us/img41/7913/screenshot2mf.png[/IMG]

---

### Post by kansasnoob on 2010-12-30
I should have mentioned that's a lower case L at the end of "sudo parted -l", but regardless I have enough to work with now, although I'd still like to see that if you happen to read this before I get back.

I want to do some testing so I can answer this:

> 1. At "Preparing to install Ubuntu" my internet connexion is disabled, this must be because i'm using a network connexion that requires me to connect to the internet manually everytime i log into XP, so i asume i can download the updates after i install Ubuntu and configure my network connection.

I'm not doing it just for you, I need to know a couple of things regarding that. Sorry for the delay but I'll be back.

---

### Post by HaHa Sandman on 2010-12-30
> **kansasnoob said:**
> I should have mentioned that's a lower case L at the end of "sudo parted -l", but regardless I have enough to work with now, although I'd still like to see that if you happen to read this before I get back.

I want to do some testing so I can answer this:



I'm not doing it just for you, I need to know a couple of things regarding that. Sorry for the delay but I'll be back.

If the internet problem is the thing that worries you, i should probably tell you that i need a username and password in order to connect to the internet, so i connect everytime i log in Windows and click "connect" in my internet setup shortcut icon. 

I think i found a setup just like that in Ubuntu in the top right it appears a Network icon, if i click it a window pop-s up witch makes me chose witch connexion i have, i think it's DSL.

I didn't set-it up since i was running Ubuntu through Live CD.

Maybe the reason it does not detct my internet connexion when i try to install Ubuntu it's because it can't detect it, until i install it and set up my username and password.

Tough, awaiting you're opinion/suggestions.

And btw thank you for taking to the time to help me and others witch may encounter the same problem.

Cheers to you and all the other people that try to make noobs life easier (y)

---

### Post by kansasnoob on 2010-12-30
**[COLOR="Red"]Do not proceed with this until we've answered my questions in post #20![/COLOR]**

OK, now I can answer you, thanks for being patient. Going back to post #7 I'll try my best to answer your questions. If any of this is still confusing please ask for clarification. We need to start with where to install grub.

Since you have a Windows MBR on both drives (sda and sdb) you should find out which drive is the boot drive in BIOS. Do you know how to access your system BIOS? If so you should see a Hard Disc boot priority option.

If you want to be able to boot using grub (which I recommend) you should install grub to the MBR of the boot drive, and remember that drives are designated like /dev/sda and /dev/sdb. Devices ending with numbers are partitions! Your 160GB drive is /dev/sda and your 80GB drive is /dev/sdb.

You should absolutely **NOT** install grub to /dev/sdb1 under any circumstance!!!

In case Ubuntu ends up not working out for you, you should know how to restore the Windows MBR:

[http://www.ehow.com/how_5095077_recover-mbr-windows-xp.html](http://www.ehow.com/how_5095077_recover-mbr-windows-xp.html)

> 1. At "Preparing to install Ubuntu" my internet connexion is disabled, this must be because i'm using a network connexion that requires me to connect to the internet manually everytime i log into XP, so i asume i can download the updates after i install Ubuntu and configure my network connection.

Yes, I just performed a test to be certain, but **be sure to "tick" the box next to "Install third party software"**. Failing to do so appears to result in "missing" software repositories. So just leave the box next to "Download updates" unchecked, **but DO check the box next to "Install third party software"**!

> 2. Specify partitions manually (advanced)

These are my HDDs and partitions

C = /dev/sda1 (41940MB out of 80GB)
D = /dev/sdb1 (160GB out of 160GB)
E = /dev/sda5 (37934 out of 80GB)

You're a little mixed up there. While installing Ubuntu basically forget about C, D, E, etc. Don't get me wrong you did an excellent job of figuring out that Windows drive E was the space you wanted to use but that designation means nothing to Ubuntu.

I can't overly stress the importance of understanding the Ubuntu device designations for drives and partitions. The Windows designations mean nothing to the Ubuntu installer. What you actually have is:

> Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdb2          81,915,435   156,007,214    74,091,780   f W95 Ext d (LBA)
/dev/sdb5          81,915,498   156,007,214    74,091,717   7 HPFS/NTFS

So we can see that /dev/sda is a 160GB drive with only one partition (/dev/sda1), and it appears to be data only.

And /dev/sdb is an 80GB drive with three partitions and /dev/sdb1 is your Windows XP OS which is using slightly more than half of the drive. The other two partitions are an extended partition (/dev/sdb2) and one logical partition (/dev/sdb5).

So, you see where you were wrong was referring to sdb5 as sda5:

> E = /dev/sd**[COLOR="Red"]a[/COLOR]**5 (37934 out of 80GB)

Now this is what i understood i have to do:

1. Delete partition E (/dev/sd**[COLOR="Red"]a[/COLOR]**5)

**You absolutely want to leave partitions sda1 and sdb1 alone, as well as sda and sdb which are drive designations!**

Partition /dev/sdb2 is an extended partition which is basically a "shell" that can contain a large number of logical partitions, and /dev/sdb5 is a logical partition which is just fine.

So, I'd recommend selecting the &#8220;Specify partitions manually (advanced)&#8221; option and clicking on forward.

On the next screen be absolutely certain to click on /dev/sdb5 which will highlight that line, then click on "Change" and you'll see another window open like this:

[ATTACH]179694[/ATTACH]

You'll notice that my sdb5 is 39530MB and yours will be slightly different, but the output of "free" shows that you have about 1GB of RAM so I suggest about 2GB of SWAP. Anyway you should see four choices that need to be made there:

(1) New partition size
(2) Use as
(3) Format the partition
(4) Mount point

You'll see in the next screenshot I "shrunk" the size of sdb5 from 39530MB to 37500MB to free up a bit more than 2GB for SWAP. Then in "Use as" I selected "ext4 journaling fs". You must also check "Format", and set the Mount point as "/" just as shown here:

[ATTACH]179695[/ATTACH]

After making all the proper selections there just click on OK and then you'll be asked to confirm those changes. After doing so you'll have to wait a bit for that to complete. When that's complete you should now see "free space" displayed as shown in the next screenshot, so click on "free space" to highlight it and select Add and you'll see a new window open:

[ATTACH]179696[/ATTACH]

Notice there are 5 decisions to make there:

1- Type for the new partition: should be "Logical"
2- New partition size: should require no change
3- Location for new partition: should be "End"
4- Use as: should be "swap area"
5- Mount point: will be grayed out because it's SWAP

Once you've made all the proper choices there just click on OK. That will take a few moments to complete, then you can click on Install now.

---

### Post by kansasnoob on 2010-12-30
> **HaHa Sandman said:**
> If the internet problem is the thing that worries you, i should probably tell you that i need a username and password in order to connect to the internet, so i connect everytime i log in Windows and click "connect" in my internet setup shortcut icon. 

I think i found a setup just like that in Ubuntu in the top right it appears a Network icon, if i click it a window pop-s up witch makes me chose witch connexion i have, i think it's DSL.

I didn't set-it up since i was running Ubuntu through Live CD.

Maybe the reason it does not detct my internet connexion when i try to install Ubuntu it's because it can't detect it, until i install it and set up my username and password.

Tough, awaiting you're opinion/suggestions.

And btw thank you for taking to the time to help me and others witch may encounter the same problem.

Cheers to you and all the other people that try to make noobs life easier (y)

I know almost nothing about setting up internet connections just because I've always been lucky in that regard. Ubuntu's just always automatically detected my DSL.

---

### Post by HaHa Sandman on 2010-12-30
> **kansasnoob said:**
> We need to start with where to install grub.

Since you have a Windows MBR on both drives (sda and sdb) you should find out which drive is the boot drive in BIOS. Do you know how to access your system BIOS? If so you should see a Hard Disc boot priority option.

If you want to be able to boot using grub (which I recommend) you should install grub to the MBR of the boot drive, and remember that drives are designated like /dev/sda and /dev/sdb. Devices ending with numbers are partitions! Your 160GB drive is /dev/sda and your 80GB drive is /dev/sdb.


Disc boot priority:

PCI SLOT - INACTIVE
ONBOARD - INACTIVE
PEG X - ACTIVE

1st Booting Device: CD-ROM
2nd Booting Device: HDD
3rd Booting Device: Floppy

Yes i do want to replace the windows boot with GRUB, that leaves just to find out where to install GRUB.

> You should absolutely NOT install grub to /dev/sdb1 under any circumstance!!!

/dev/sdb5 ? Sorry for beying such a hard head but there are ALOT of options in "Boot Loader" multiple options to single partitions, so i just want to be sure.

And i'm sorry for not getting the names to the HDD right, im stil new to this and need time to get used to it. I've bin using Windows for almost 10 years it's hard to "forget" all that and start over.

---

### Post by gordintoronto on 2010-12-30
Just to highlight an earlier comment: sda5 is a logical partition, not a primary partition. Ubuntu can use this just fine.

Don't worry about the internet connection until after you complete the installation, unless you just want to prove that your network hardware works.

---

### Post by kansasnoob on 2010-12-31
**[COLOR="Red"]I'm going to go ahead and post this but I just noticed something I'd overlooked yesterday, so hold off, be patient and wait for my next post before beginning to install![/COLOR]**

**Please read this all before beginning.**

I wasn't aware how much you already new about BIOS and/or boot priorities, so thanks for taking the time to find out :)

Since /dev/sdb5 will be Ubuntu's "/" (aka: root) partition, if you installed grub to that partition you would have to use another bootloader like Easy-BCD to boot both Windows and Ubuntu. I prefer just using grub.

As far as "hard disc boot priority", well, it may or may not show up in the BIOS. Many things can effect that such as whether the drives are IDE or SATA, or a mix of the two. Quite often, if both drives are IDE, and they share the same cable as master and slave, the option won't even exist in BIOS. Some people might recommend mucking about with cables, flashing the BIOS, etc. **[COLOR="Red"]but I don't recommend that![/COLOR]** You know Windows runs OK so why take a chance on messing things up, eh?

So the answer is, grub should be installed to either /dev/sda or /dev/sdb and I'd personally try /dev/sda. If that's wrong nothing will be broken, you'll simply boot directly into Windows as though Ubuntu weren't even there but that's very easy to fix with the Ubuntu Live CD.

*Time out here for some off-topic discussion. I remember when you got the "sudo parted -l" typed wrong. It's generally expected when someone suggests running a command and it's in code tags that you'll copy-n-paste the command by double-clicking with the mouse pointer inside the code box, then right-click & select copy, then with the mouse pointer inside the terminal right-click again and select paste. It's important to know how to do that because you'll see some commands are quite long and it's too darn easy to get a typo.*

So. lets say you install grub to /dev/sda and, once the installation completes, you reboot and rather than the grub menu appearing you boot straight into Windows - no worries! If that happens just boot the Live CD, choosing Try Ubuntu, and install grub to /dev/sdb from the live desktop by copy-n-pasting these commands in terminal:

```
sudo mount /dev/sdb5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sdb
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

*Note: I'm assuming that you'll follow the installation procedure in post #15 and sdb5 will be Ubuntu's root partition! Also, it doesn't happen often but occasionally the "grub-install /dev/sdX" command will spit out errors. If that happens you should also run "grub-install --recheck /dev/sdX" where X is the proper drive designation.*

Now, **I do have one concern** related to the lack of internet. I know I already posted a link about how to restore a Windows MBR using an XP recovery CD, but I like to always be prepared for the worst just in case! I'm not sure how you've been posting info w/o internet? Using a second computer? Transferring data with a flash drive?

I'm just thinking about what you should do, if after installing Ubuntu, you find that you can't boot either XP or Ubuntu. It doesn't happen often but it's great to have a Live CD that can connect to the internet for troubleshooting and fixing things :)

For instance the Ubuntu package "lilo" can be used to create a Windows readable MBR but it's not included in the Live CD. Of course if you have a second computer there are ways to work around that (eg: downloading .debs) but it's certainly easier if you can get a network connection with the Live CD.

As I said previously I'm blissfully ignorant regarding network problems but I wonder if it might be worth asking here:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

If any of this is still confusing to you please take a bit more time to ask more questions. I will be out again from time to time today, not as much because it's cold again.

---

### Post by kansasnoob on 2010-12-31
As I mentioned above I noticed something that explains why you were probably confused about sda5 vs sdb5 :confused:

Looking at post #1 it clearly shows that sda is the 80GB drive and sdb is the 160GB drive.

But in post #3 and post #10 they've traded places.

**That could possibly cause problems!**

So, I'd assumed that both hard drives are internal drives. Is that correct?

Or is one a USB drive?

We should figure out what's up with that before proceeding!

---

### Post by HaHa Sandman on 2010-12-31
> Since /dev/sdb5 will be Ubuntu's "/" (aka: root) partition, if you installed grub to that partition you would have to use another bootloader like Easy-BCD to boot both Windows and Ubuntu. I prefer just using grub.

As far as "hard disc boot priority", well, it may or may not show up in the BIOS. Many things can effect that such as whether the drives are IDE or SATA, or a mix of the two. Quite often, if both drives are IDE, and they share the same cable as master and slave, the option won't even exist in BIOS. Some people might recommend mucking about with cables, flashing the BIOS, etc. but I don't recommend that! You know Windows runs OK so why take a chance on messing things up, eh?

They're both SATA as far as i know.

> So the answer is, grub should be installed to either /dev/sda or /dev/sdb and I'd personally try /dev/sda. If that's wrong nothing will be broken, you'll simply boot directly into Windows as though Ubuntu weren't even there but that's very easy to fix with the Ubuntu Live CD.

I have one last question about GRUB and partitions but my head is blowing up from all this, i'll post it later tonight or most probably tomorrow morning.

> Time out here for some off-topic discussion. I remember when you got the "sudo parted -l" typed wrong. It's generally expected when someone suggests running a command and it's in code tags that you'll copy-n-paste the command by double-clicking with the mouse pointer inside the code box, then right-click & select copy, then with the mouse pointer inside the terminal right-click again and select paste. It's important to know how to do that because you'll see some commands are quite long and it's too darn easy to get a typo.

I know the short Copy & Paste technique ;)

But i couldn't do that, since if you look closer in post #12 you'll see that the "codes" are in fact images not text documets, pics taken by me from this site, or another, and the values you gave me as well. Made screenshots of them since i had no internet on Ubuntu Live CD, saved them to a partition, and "picked" them up with ULCD.

> So. lets say you install grub to /dev/sda and, once the installation completes, you reboot and rather than the grub menu appearing you boot straight into Windows - no worries! If that happens just boot the Live CD, choosing Try Ubuntu, and install grub to /dev/sdb from the live desktop by copy-n-pasting these commands in terminal:

As i said i'll try/discuss this tomorrow, i need a timeout atm.

> Now, I do have one concern related to the lack of internet. I know I already posted a link about how to restore a Windows MBR using an XP recovery CD, but I like to always be prepared for the worst just in case! I'm not sure how you've been posting info w/o internet? Using a second computer? Transferring data with a flash drive?

I'm using WinXP also, remember? :P  I haven't installed Ubuntu yet, everything i got, i got through the internet connexion i set-ed up on Windows. I was just transfering data from one HDD to another, everything i was doing on Ubuntu i was saving on /dev/sdb1. I have a USB Stick but didn't need to use it.

> I'm just thinking about what you should do, if after installing Ubuntu, you find that you can't boot either XP or Ubuntu. It doesn't happen often but it's great to have a Live CD that can connect to the internet for troubleshooting and fixing things

I just made a run through ULCD and set-ed up my internet connexion in Ubuntu, i have to do this everytime i boot from the CD, until i install it, thats why i didn't do it the first time, but thats okay, now i have internet connexion on both WinXP & ULCD. The connexion i set-ed up was DSL.

> As I mentioned above I noticed something that explains why you were probably confused about sda5 vs sdb5 

Looking at post #1 it clearly shows that sda is the 80GB drive and sdb is the 160GB drive.

But in post #3 and post #10 they've traded places.

I didn't even see that. How can it be possible?

> That could possibly cause problems!

So, I'd assumed that both hard drives are internal drives. Is that correct?

Or is one a USB drive?

We should figure out what's up with that before proceeding!

Both are internal.

Here's some more detailed info on them:

```
HWiNFO32 Version 3.43-623

85BFA5D1E5254CA -----------------------------------------------------------

 [Current Computer]
 [Operating System]

Central Processor(s) ------------------------------------------------------

 [CPU Unit Count]
  Number Of Processor Packages (Physical): 1
  Number Of Processors Cores:             1
  Number Of Logical Processors:           2

Intel Pentium 4 631 -------------------------------------------------------

 [General Information]
  Processor Name:                         Intel Pentium 4 631
  Original Processor Freqency:            3000.0 MHz
  Original Processor Freqency [MHz]:      3000
  CPU ID:                                 00000F65
  CPU Brand Name:                         Intel(R) Pentium(R) 4 CPU 3.00GHz
  CPU Vendor:                             GenuineIntel
  CPU Stepping:                           D0
  CPU Code Name:                          Cedar Mill
  CPU S-Spec:                             SL9KG, SL9KR
  CPU Thermal Design Power (TDP):         65 W
  CPU Max. Case Temperature (Tcase_max):  64.4 °C
  CPU Type:                               Production Unit
  CPU Platform:                           LGA775 (FC-LGA4)
  Microcode Update Revision:              7
  Number of CPU Cores:                    1
  Number of Logical CPUs:                 2
 [Operating Points]
  CPU LFM (Minimum):                      2400.0 MHz = 12.00 x 200.0 MHz @ 1.2000 V
  CPU HFM (Maximum):                      3000.0 MHz = 15.00 x 200.0 MHz @ 1.3125 V [Locked]
  CPU Current:                            2991.4 MHz = 15.00 x 199.4 MHz @ 1.3125 V
  CPU Bus Type:                           FSB (QDR)
 [Cache and TLB]
  L1 Cache:                               Instruction Trace: 12K uOps, Data: 16 KBytes
  L2 Cache:                               Integrated: 2 MBytes
  Instruction TLB:                        4KB/2MB/4MB Pages, Fully associative, 64 entries
  Data TLB:                               4KB/4MB Pages, Fully associative, 64 entries
 [Standard Feature Flags]
  FPU on Chip                             Present
  Enhanced Virtual-86 Mode                Present
  I/O Breakpoints                         Present
  Page Size Extensions                    Present
  Time Stamp Counter                      Present
  Pentium-style Model Specific Registers  Present
  Physical Address Extension              Present
  Machine Check Exception                 Present
  CMPXCHG8B Instruction                   Present
  APIC On Chip / PGE (AMD)                Present
  Fast System Call                        Present
  Memory Type Range Registers             Present
  Page Global Feature                     Present
  Machine Check Architecture              Present
  CMOV Instruction                        Present
  Page Attribute Table                    Present
  36-bit Page Size Extensions             Present
  Processor Number                        Not Present
  CLFLUSH Instruction                     Present
  Debug Trace and EMON Store              Present
  Internal ACPI Support                   Present
  MMX Technology                          Present
  Fast FP Save/Restore (IA MMX-2)         Present
  Streaming SIMD Extensions               Present
  Streaming SIMD Extensions 2             Present
  Self-Snoop                              Present
  Multi-Threading Capable                 Present
  Automatic Clock Control                 Present
  IA-64 Processor                         Not Present
  Signal Break on FERR                    Present
  Streaming SIMD Extensions 3             Present
  Carryless Multiplication (PCLMULQDQ)/GFMUL Not Present
  64-Bit Debug Store                      Present
  MONITOR/MWAIT Support                   Present
  CPL Qualified Debug Store               Present
  Virtual Machine Extensions              Not Present
  Safer Mode Extensions (Intel TXT)       Not Present
  Thermal Monitor 2                       Present
  Supplemental Streaming SIMD Extensions 3 Not Present
  Enhanced SpeedStep Technology           Present
  L1 Context ID                           Present
  CMPXCHG16B Support                      Present
  Send Task Priority Messages Disabling   Present
  Performance/Debug Capability MSR        Present
  Processor Context ID                    Not Present
  Direct Cache Access                     Not Present
  Streaming SIMD Extensions 4.1           Not Present
  Streaming SIMD Extensions 4.2           Not Present
  Extended xAPIC                          Not Present
  MOVBE Instruction                       Not Present
  POPCNT Instruction                      Not Present
  AES Cryptography Support                Not Present
  XSAVE/XRSTOR/XSETBV/XGETBV Instructions Not Present
  XGETBV/XSETBV OS Enabled                Not Present
  AVX Support                             Not Present
 [Extended Feature Flags]
  64-bit Extensions                       Present
  No Execute                              Present
  SYSCALL/SYSRET Support                  Not Present
  RDTSCP and TSC_AUX Support              Not Present
 [Enhanced Features]
  Thermal Monitor 1:                      Supported, Enabled
  Thermal Monitor 2:                      Supported, Enabled
  Enhanced Intel SpeedStep (GV3):         Supported, Enabled
  Bi-directional PROCHOT#:                Enabled
  Extended Auto-HALT State C1E:           Enabled
  Extended Stop Grant State C2E:          N/A
  Enhanced Halt State C3E:                N/A
  Enhanced Halt State C4E:                N/A
  Enhanced Halt State Hard C4E:           N/A
  Hardware Prefetcher:                    Supported, Enabled
  DCU Prefetcher:                         Not Supported
  IP Prefetcher:                          Not Supported
  Adjacent Cache Line Prefetch:           Supported, Enabled
  MLC Streamer Prefetcher                 Not Supported
  MLC Spatial Prefetcher                  Not Supported
  DCU Streamer Prefetcher                 Not Supported
  DCU IP Prefetcher                       Not Supported
  Intel Dynamic Acceleration (IDA) Technology: Not Supported
  Intel Dynamic FSB Switching:            Not Supported
  Enhanced Multi Threaded Thermal Management: N/A
  Intel Turbo Boost Technology:           Not Supported
  Programmabe Ratio Limits:               Not Supported
  Programmabe TDC/TDP Limits:             Not Supported
 [Platform]
  Platform Requirement:                   No (VR_CONFIG_06)
  Platform Conformance:                   No
 [Memory Ranges]
  Maximum Pysical Address Size:           36-bit (64 GBytes)
  Maximum Virtual Address Size:           48-bit (256 TBytes)
 [MTRRs]
  Range 0-40000000 (0MB-1024MB) Type:     Write Back (WB)
  Range D0000000-D8000000 (3328MB-3456MB) Type: Write Combining (WC)
 [P.I.ROM]
  P.I.ROM Status:                         Not Present

Motherboard ---------------------------------------------------------------

 [Computer]
  Computer Brand Name:                    Unknown on Noname
 [Motherboard]
  Motherboard Model:                      Giga-Byte GA-VM900M
  Motherboard Chipset:                    VIA P4M900 + VT8237A
  Motherboard Slots:                      2xPCI, 1xAGP v3.5 , 1xPCI Express x1, 1xPCI Express x16
 [BIOS]
  BIOS Manufacturer:                      Award Modular BIOS v6.00PG
  BIOS Date:                              11/03/06
  BIOS Version:                           F2
  Super-IO/LPC Chip:                      Winbond/Nuvoton W83627DHG

Plug-and-Play System Nodes ------------------------------------------------


Programmable Interrupt Controller -----------------------------------------

 [General Information]
  Node Number:                            0
  Device ID:                              PNP0000
  Device Name:                            Programmable Interrupt Controller
  Device Type Code:                       080000
 [System Resources]
  IRQ:                                    2
  I/O Port:                               0020
  I/O Port:                               00A0
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

DMA Controller ------------------------------------------------------------

 [General Information]
  Node Number:                            1
  Device ID:                              PNP0200
  Device Name:                            DMA Controller
  Device Type Code:                       080100
 [System Resources]
  DMA:                                    4
  I/O Port:                               0000
  I/O Port:                               0081
  I/O Port:                               0087
  I/O Port:                               0089
  I/O Port:                               008F
  I/O Port:                               00C0
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

System Timer --------------------------------------------------------------

 [General Information]
  Node Number:                            2
  Device ID:                              PNP0100
  Device Name:                            System Timer
  Device Type Code:                       080201
 [System Resources]
  IRQ:                                    0
  I/O Port:                               0040
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

RealTime Clock ------------------------------------------------------------

 [General Information]
  Node Number:                            3
  Device ID:                              PNP0B00
  Device Name:                            RealTime Clock
  Device Type Code:                       080300
 [System Resources]
  IRQ:                                    8
  I/O Port:                               0070
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

101/102-Key or MS Natural Keyboard ----------------------------------------

 [General Information]
  Node Number:                            4
  Device ID:                              PNP0303
  Device Name:                            101/102-Key or MS Natural Keyboard
  Device Type Code:                       090000
 [System Resources]
  IRQ:                                    1
  I/O Port:                               0060
  I/O Port:                               0064
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

PC Speaker ----------------------------------------------------------------

 [General Information]
  Node Number:                            5
  Device ID:                              PNP0800
  Device Name:                            PC Speaker
  Device Type Code:                       088000
 [System Resources]
  I/O Port:                               0061
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

Numeric Data Processor ----------------------------------------------------

 [General Information]
  Node Number:                            6
  Device ID:                              PNP0C04
  Device Name:                            Numeric Data Processor
  Device Type Code:                       0B0100
 [System Resources]
  IRQ:                                    13
  I/O Port:                               00F0
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

System Board Extension ----------------------------------------------------

 [General Information]
  Node Number:                            7
  Device ID:                              PNP0C01
  Device Name:                            System Board Extension
  Device Type Code:                       050000
 [System Resources]
  Memory Location:                        00000000-0009FFFF
  Memory Location:                        FFFE0000-FFFFFFFF
  Memory Location:                        FEC00000-FEC0FFFF
  Memory Location:                        FEE00000-FEE0FFFF
  Memory Location:                        00100000-3FFFFFFF
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

Motherboard Resources -----------------------------------------------------

 [General Information]
  Node Number:                            8
  Device ID:                              PNP0C02
  Device Name:                            Motherboard Resources
  Device Type Code:                       088000
 [System Resources]
  Memory Location:                        000F0000-000F3FFF
  Memory Location:                        000F4000-000F7FFF
  Memory Location:                        000F8000-000FFFFF
  Memory Location:                        000CEE00-000CFFFF
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

PCI Bus -------------------------------------------------------------------

 [General Information]
  Node Number:                            9
  Device ID:                              PNP0A03
  Device Name:                            PCI Bus
  Device Type Code:                       060400
 [System Resources]
  I/O Port:                               0290
  I/O Port:                               04D0
  I/O Port:                               0CF8
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

Logitech PS/2 Port Mouse --------------------------------------------------

 [General Information]
  Node Number:                            10
  Device ID:                              PNP0F13
  Device Name:                            Logitech PS/2 Port Mouse
  Device Type Code:                       090200
 [System Resources]
  IRQ:                                    12
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Supported
  Disableable Device:                     Supported

16550A-compatible UART Serial Port ----------------------------------------

 [General Information]
  Node Number:                            11
  Device ID:                              PNP0501
  Device Name:                            16550A-compatible UART Serial Port
  Device Type Code:                       070002
 [System Resources]
  IRQ:                                    4
  I/O Port:                               03F8
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Supported
  Disableable Device:                     Supported

Floppy Controller ---------------------------------------------------------

 [General Information]
  Node Number:                            12
  Device ID:                              PNP0700
  Device Name:                            Floppy Controller
  Device Type Code:                       010200
 [System Resources]
  IRQ:                                    6
  DMA:                                    2
  I/O Port:                               03F0
  I/O Port:                               03F7
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Not Supported
  Disableable Device:                     Not Supported

Parallel Port -------------------------------------------------------------

 [General Information]
  Node Number:                            13
  Device ID:                              PNP0400
  Device Name:                            Parallel Port
  Device Type Code:                       070100
 [System Resources]
  IRQ:                                    7
  I/O Port:                               0378
  I/O Port:                               0778
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Supported
  Disableable Device:                     Supported

16550A-compatible UART Serial Port ----------------------------------------

 [General Information]
  Node Number:                            15
  Device ID:                              PNP0501
  Device Name:                            16550A-compatible UART Serial Port
  Device Type Code:                       070002
 [System Resources]
  IRQ:                                    3
  I/O Port:                               02F8
 [Flags]
  Removable Device:                       Not Present
  Docking:                                Not Supported
  IPL:                                    Not Supported
  Primary Input Device:                   Not Capable
  Primary Output Device:                  Not Capable
  Configurable Device:                    Supported
  Disableable Device:                     Supported

ACPI Devices --------------------------------------------------------------


ACPI Fixed Feature Button -------------------------------------------------

  Device Name:                            ACPI Fixed Feature Button

Intel Processor -----------------------------------------------------------

  Device Name:                            Intel Processor

Intel Processor -----------------------------------------------------------

  Device Name:                            Intel Processor

Programmable interrupt controller -----------------------------------------

  Device Name:                            Programmable interrupt controller
 [Assigned Resources]
  I/O Port:                               0020 - 0021
  I/O Port:                               00A0 - 00A1
 [Alternative 1]
  I/O Port:                               0020 - 0021
  I/O Port:                               00A0 - 00A1

System timer --------------------------------------------------------------

  Device Name:                            System timer
 [Assigned Resources]
  I/O Port:                               0040 - 0043
  IRQ:                                    0
 [Alternative 1]
  I/O Port:                               0040 - 0043
  IRQ:                                    0

Direct memory access controller -------------------------------------------

  Device Name:                            Direct memory access controller
 [Assigned Resources]
  I/O Port:                               0000 - 000F
  I/O Port:                               0080 - 0090
  I/O Port:                               0094 - 009F
  I/O Port:                               00C0 - 00DF
  DMA:                                    4
 [Alternative 1]
  I/O Port:                               0000 - 000F
  I/O Port:                               0080 - 0090
  I/O Port:                               0094 - 009F
  I/O Port:                               00C0 - 00DF
  DMA:                                    4

Standard 101/102-Key or Microsoft Natural PS/2 Keyboard -------------------

  Device Name:                            Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
 [Assigned Resources]
  I/O Port:                               0060
  I/O Port:                               0064
  IRQ:                                    1
 [Alternative 1]
  I/O Port:                               0060
  I/O Port:                               0064
  IRQ:                                    1

Printer Port --------------------------------------------------------------

  Device Name:                            Printer Port
 [Assigned Resources]
  I/O Port:                               0378 - 037F
  I/O Port:                               0778 - 077B
  IRQ:                                    7
 [Alternative 1]
  I/O Port:                               0378 - 037F
  I/O Port:                               0778 - 077B
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12
 [Alternative 2]
  I/O Port:                               0278 - 027F
  I/O Port:                               0678 - 067B
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12
 [Alternative 3]
  I/O Port:                               03BC - 03BF
  I/O Port:                               07BC - 07BF
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12

Communications Port -------------------------------------------------------

  Device Name:                            Communications Port
 [Assigned Resources]
  I/O Port:                               03F8 - 03FF
  IRQ:                                    4
 [Alternative 1]
  I/O Port:                               03F8 - 03FF
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12
 [Alternative 2]
  I/O Port:                               02F8 - 02FF
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12
 [Alternative 3]
  I/O Port:                               03E8 - 03EF
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12
 [Alternative 4]
  I/O Port:                               02E8 - 02EF
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12

Communications Port -------------------------------------------------------

  Device Name:                            Communications Port
 [Assigned Resources]
  I/O Port:                               02F8 - 02FF
  IRQ:                                    3
 [Alternative 1]
  I/O Port:                               03F8 - 03FF
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12
 [Alternative 2]
  I/O Port:                               02F8 - 02FF
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12
 [Alternative 3]
  I/O Port:                               03E8 - 03EF
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12
 [Alternative 4]
  I/O Port:                               02E8 - 02EF
  IRQ:                                    3
  IRQ:                                    4
  IRQ:                                    5
  IRQ:                                    7
  IRQ:                                    9
  IRQ:                                    10
  IRQ:                                    11
  IRQ:                                    12

Standard floppy disk controller -------------------------------------------

  Device Name:                            Standard floppy disk controller
 [Assigned Resources]
  I/O Port:                               03F0 - 03F5
  I/O Port:                               03F7
  IRQ:                                    6
  DMA:                                    2
 [Alternative 1]
  I/O Port:                               03F0 - 03F5
  I/O Port:                               03F7
  IRQ:                                    6
  DMA:                                    2

System speaker ------------------------------------------------------------

  Device Name:                            System speaker
 [Assigned Resources]
  I/O Port:                               0061
 [Alternative 1]
  I/O Port:                               0061

Extended IO Bus -----------------------------------------------------------

  Device Name:                            Extended IO Bus

PCI bus -------------------------------------------------------------------

  Device Name:                            PCI bus
 [Assigned Resources]
  I/O Port:                               0000 - 0CF7
  I/O Port:                               0D00 - FFFF
  Memory Location:                        000A0000 - 000BFFFF
  Memory Location:                        000C0000 - 000DFFFF
  Memory Location:                        40000000 - BFEFFFFF
  Memory Location:                        C0000000 - FEBFFFFF
 [Alternative 1]
  I/O Port:                               0000 - 0CF7
  I/O Port:                               0D00 - FFFF
  Memory Location:                        000A0000 - 000BFFFF
  Memory Location:                        000C0000 - 000DFFFF
  Memory Location:                        40000000 - BFEFFFFF
  Memory Location:                        C0000000 - FEBFFFFF

PCI bus -------------------------------------------------------------------

  Device Name:                            PCI bus
 [Assigned Resources]
  I/O Port:                               0000 - 0CF7
  I/O Port:                               0D00 - FFFF
  Memory Location:                        000A0000 - 000BFFFF
  Memory Location:                        BFF00000 - BFFFFFFF
 [Alternative 1]
  I/O Port:                               0000 - 0CF7
  I/O Port:                               0D00 - FFFF
  Memory Location:                        000A0000 - 000BFFFF
  Memory Location:                        BFF00000 - BFFFFFFF

System CMOS/real time clock -----------------------------------------------

  Device Name:                            System CMOS/real time clock
 [Assigned Resources]
  I/O Port:                               0070 - 0073
  IRQ:                                    8
 [Alternative 1]
  I/O Port:                               0070 - 0073
  IRQ:                                    8

System board --------------------------------------------------------------

  Device Name:                            System board
 [Assigned Resources]
  Memory Location:                        000CEE00 - 000CFFFF
  Memory Location:                        000F0000 - 000F7FFF
  Memory Location:                        000F8000 - 000FBFFF
  Memory Location:                        000FC000 - 000FFFFF
  Memory Location:                        3FFF0000 - 3FFFFFFF
  Memory Location:                        FFFF0000 - FFFFFFFF
  Memory Location:                        00000000 - 0009FFFF
  Memory Location:                        00100000 - 3FFEFFFF
  Memory Location:                        FEC00000 - FEC00FFF
  Memory Location:                        FEE00000 - FEE00FFF
  Memory Location:                        FFF80000 - FFFEFFFF
 [Alternative 1]
  Memory Location:                        000CEE00 - 000CFFFF
  Memory Location:                        000F0000 - 000F7FFF
  Memory Location:                        000F8000 - 000FBFFF
  Memory Location:                        000FC000 - 000FFFFF
  Memory Location:                        3FFF0000 - 3FFFFFFF
  Memory Location:                        FFFF0000 - FFFFFFFF
  Memory Location:                        00000000 - 0009FFFF
  Memory Location:                        00100000 - 3FFEFFFF
  Memory Location:                        FEC00000 - FEC00FFF
  Memory Location:                        FEE00000 - FEE00FFF
  Memory Location:                        FFF80000 - FFFEFFFF

Motherboard resources -----------------------------------------------------

  Device Name:                            Motherboard resources
 [Assigned Resources]
  I/O Port:                               0010 - 001F
  I/O Port:                               0022 - 003F
  I/O Port:                               0044 - 005F
  I/O Port:                               0062 - 0063
  I/O Port:                               0065 - 006F
  I/O Port:                               0074 - 007F
  I/O Port:                               0091 - 0093
  I/O Port:                               00A2 - 00BF
  I/O Port:                               00E0 - 00EF
  I/O Port:                               04D0 - 04D1
  I/O Port:                               0290 - 0294
  I/O Port:                               0880 - 088F
 [Alternative 1]
  I/O Port:                               0010 - 001F
  I/O Port:                               0022 - 003F
  I/O Port:                               0044 - 005F
  I/O Port:                               0062 - 0063
  I/O Port:                               0065 - 006F
  I/O Port:                               0074 - 007F
  I/O Port:                               0091 - 0093
  I/O Port:                               00A2 - 00BF
  I/O Port:                               00E0 - 00EF
  I/O Port:                               04D0 - 04D1
  I/O Port:                               0290 - 0294
  I/O Port:                               0880 - 088F

Motherboard resources -----------------------------------------------------

  Device Name:                            Motherboard resources
 [Assigned Resources]
  I/O Port:                               4000 - 407F
  I/O Port:                               0500 - 050F
 [Alternative 1]
  I/O Port:                               4000 - 407F
  I/O Port:                               0500 - 050F

Motherboard resources -----------------------------------------------------

  Device Name:                            Motherboard resources
 [Assigned Resources]
  Memory Location:                        E0000000 - EFFFFFFF
 [Alternative 1]
  Memory Location:                        E0000000 - EFFFFFFF

Motherboard resources -----------------------------------------------------

  Device Name:                            Motherboard resources
 [Assigned Resources]
  Memory Location:                        F0001000 - F0001FFF
 [Alternative 1]
  Memory Location:                        F0001000 - F0001FFF

Motherboard resources -----------------------------------------------------

  Device Name:                            Motherboard resources
 [Assigned Resources]
  Memory Location:                        F0002000 - F0002FFF
 [Alternative 1]
  Memory Location:                        F0002000 - F0002FFF

Motherboard resources -----------------------------------------------------

  Device Name:                            Motherboard resources
 [Assigned Resources]
  Memory Location:                        F0000000 - F0000FFF
 [Alternative 1]
  Memory Location:                        F0000000 - F0000FFF

Numeric data processor ----------------------------------------------------

  Device Name:                            Numeric data processor
 [Assigned Resources]
  I/O Port:                               00F0 - 00FF
  IRQ:                                    13
 [Alternative 1]
  I/O Port:                               00F0 - 00FF
  IRQ:                                    13

ACPI Power Button ---------------------------------------------------------

  Device Name:                            ACPI Power Button

PS/2 Compatible Mouse -----------------------------------------------------

  Device Name:                            PS/2 Compatible Mouse
 [Assigned Resources]
  IRQ:                                    12
 [Alternative 1]
  IRQ:                                    12

A17YRMTE IDE Controller ---------------------------------------------------

  Device Name:                            A17YRMTE IDE Controller
 [Alternative 1]
  I/O Port:                               0010 - FFF0
  IRQ:                                    0 - -1

SMBIOS DMI ----------------------------------------------------------------


BIOS ----------------------------------------------------------------------

  BIOS Vendor:                            Award Software International, Inc.
  BIOS Version:                           F2
  BIOS Release Date:                      11/03/2006
  BIOS Start Segment:                     E000
  BIOS Size:                              512 KBytes
  ISA Support:                            Present
  MCA Support:                            Not Present
  EISA Support:                           Not Present
  PCI Support:                            Present
  PC Card (PCMCIA) Support:               Not Present
  Plug-and-Play Support:                  Present
  APM Support:                            Present
  Flash BIOS:                             Present
  BIOS Shadow:                            Present
  VL-VESA Support:                        Not Present
  ESCD Support:                           Not Present
  Boot from CD:                           Present
  Selectable Boot:                        Present
  BIOS ROM Socketed:                      Present
  Boot from PC Card:                      Not Present
  EDD Support:                            Present
  NEC PC-98 Support:                      Not Present
  ACPI Support:                           Present
  USB Legacy Support:                     Present
  AGP Support:                            Present
  I2O Boot Support:                       Not Present
  LS-120 Boot Support:                    Present
  ATAPI ZIP Drive Boot Support:           Present
  IEE1394 Boot Support:                   Not Present
  Smart Battery Support:                  Not Present

System --------------------------------------------------------------------

  System Manufacturer:                    
  Product Name:                           
  Product Version:                        
  Product Serial Number:                  

Mainboard -----------------------------------------------------------------

  Mainboard Manufacturer:                 Gigabyte Technology Co., Ltd.
  Mainboard Name:                         VM900M
  Mainboard Version:                      x.x
  Mainboard Serial Number:                Wed Mar 28 08:33:40 2007

System Enclosure ----------------------------------------------------------

  Manufacturer:                            
  Case Type:                              Desktop
  Version:                                 
  Serial Number:                           
  Asset Tag Number:                        

Processor -----------------------------------------------------------------

  Processor Manufacturer:                 Intel
  Processor Version:                      Intel(R) Pentium(R) 4 CPU
  External Clock:                         200 MHz
  Maximum Clock Supported:                3600 MHz
  Current Clock:                          3000 MHz
  CPU Socket:                             Populated
  CPU Status:                             Enabled
  Processor Type:                         Central Processor
  Processor Voltage:                      1.3 V
  Processor Upgrade:                      ZIF
  Socket Designation:                     Socket 775

Memory Devices ------------------------------------------------------------


Memory Controller ---------------------------------------------------------

  Error Detecting Method:                 None
  Error Correction:                       None
  Supported Interleave:                   1-Way
  Current Interleave:                     4-Way
  Max. Memory Module Size:                1024 MBytes
  Supported Memory Speed:                 70 ns, 60 ns
  Supported Memory Type:                  SPM, EDO
  Supported Memory Voltage:               3.3 V
  Associated Memory Slots:                2

A0 ------------------------------------------------------------------------

  Socket Designation:                     A0
  Memory Type:                            EDO
  Memory Speed:                           30 ns
  Installed size:                         8192 MBytes
  Enabled size:                           8192 MBytes

A1 ------------------------------------------------------------------------

  Socket Designation:                     A1
  Memory Type:                            EDO
  Memory Speed:                           30 ns
  Installed size:                         8192 MBytes
  Enabled size:                           8192 MBytes

Internal Cache ------------------------------------------------------------

  Socket Designation:                     Internal Cache
  Cache State:                            Enabled
  Cache Type:                             Internal
  Cache Scheme:                           Write-Back
  Supported SRAM Type:                    Synchronous
  Current SRAM Type:                      Synchronous
  Cache Speed:                            Unknown
  Error Correction Type:                  Unknown
  Maximum Cache Size:                     16 KBytes
  Installed Cache Size:                   16 KBytes
  Cache Associativity:                    Unknown

External Cache ------------------------------------------------------------

  Socket Designation:                     External Cache
  Cache State:                            Enabled
  Cache Type:                             Internal
  Cache Scheme:                           Write-Back
  Supported SRAM Type:                    Synchronous
  Current SRAM Type:                      Synchronous
  Cache Speed:                            Unknown
  Error Correction Type:                  Unknown
  Maximum Cache Size:                     1024 KBytes
  Installed Cache Size:                   2048 KBytes
  Cache Associativity:                    Unknown

Port Connectors -----------------------------------------------------------


Port Connector ------------------------------------------------------------

  Port Type:                              Unknown
  Internal Reference:                     PRIMARY IDE
  Internal Connector Type:                On Board IDE
  External Reference:                      
  External Connector Type:                None

Port Connector ------------------------------------------------------------

  Port Type:                              Unknown
  Internal Reference:                     SECONDARY IDE
  Internal Connector Type:                On Board IDE
  External Reference:                      
  External Connector Type:                None

8251 FIFO Compatible ------------------------------------------------------

  Port Type:                              8251 FIFO Compatible
  Internal Reference:                     FDD
  Internal Connector Type:                On Board Floppy
  External Reference:                      
  External Connector Type:                None

Serial Port 16450 Compatible ----------------------------------------------

  Port Type:                              Serial Port 16450 Compatible
  Internal Reference:                     COM1
  Internal Connector Type:                9 Pin Dual Inline (pin 10 cut)
  External Reference:                      
  External Connector Type:                DB-9 pin male

Serial Port 16450 Compatible ----------------------------------------------

  Port Type:                              Serial Port 16450 Compatible
  Internal Reference:                     COM2
  Internal Connector Type:                9 Pin Dual Inline (pin 10 cut)
  External Reference:                      
  External Connector Type:                DB-9 pin male

Parallel Port ECP/EPP -----------------------------------------------------

  Port Type:                              Parallel Port ECP/EPP
  Internal Reference:                     LPT1
  Internal Connector Type:                DB25 pin female
  External Reference:                      
  External Connector Type:                DB25 pin female

Keyboard Port -------------------------------------------------------------

  Port Type:                              Keyboard Port
  Internal Reference:                     Keyboard
  Internal Connector Type:                Unknown
  External Reference:                      
  External Connector Type:                PS/2

Mouse Port ----------------------------------------------------------------

  Port Type:                              Mouse Port
  Internal Reference:                     PS/2 Mouse
  Internal Connector Type:                PS/2
  External Reference:                     Detected
  External Connector Type:                PS/2

USB -----------------------------------------------------------------------

  Port Type:                              USB
  Internal Reference:                     USB
  Internal Connector Type:                None
  External Reference:                      
  External Connector Type:                Access Bus (USB)

System Slots --------------------------------------------------------------


PCI -----------------------------------------------------------------------

  Slot Designation:                       PCI
  Slot Type:                              PCI
  Slot Usage:                             In use
  Slot Data Bus Width:                    32-bit
  Slot Length:                            Long

PCI -----------------------------------------------------------------------

  Slot Designation:                       PCI
  Slot Type:                              PCI
  Slot Usage:                             In use
  Slot Data Bus Width:                    32-bit
  Slot Length:                            Long

BIOS Language -------------------------------------------------------------





Physical Memory Array -----------------------------------------------------

  Array Location:                         System board
  Array Use:                              System memory
  Error Detecting Method:                 None
  Memory Capacity:                        1048576 KBytes
  Memory Devices:                         2

Memory Device -------------------------------------------------------------

  Total Width:                            Unknown
  Data Width:                             Unknown
  Device Size:                            512 MBytes
  Device Form Factor:                     DIMM
  Device Locator:                         A0
  Bank Locator:                           Bank0/1
  Device Type:                            Unknown
  Device Type Detail:                     
  Memory Speed:                           41632 MHz
  Manufacturer:                            
  Serial Number:                           
  Part Number:                             
  Asset Tag:                               

Memory Device -------------------------------------------------------------

  Total Width:                            Unknown
  Data Width:                             Unknown
  Device Size:                            512 MBytes
  Device Form Factor:                     DIMM
  Device Locator:                         A1
  Bank Locator:                           Bank2/3
  Device Type:                            Unknown
  Device Type Detail:                     
  Memory Speed:                           41632 MHz
  Manufacturer:                            
  Serial Number:                           
  Part Number:                             
  Asset Tag:                               

Memory Array Mapped Address -----------------------------------------------

  Starting Address:                       00000000
  Ending Address:                         000FFFFF
  Partition Width:                        1

Memory Device Mapped Address ----------------------------------------------

  Starting Address:                       00000000
  Ending Address:                         0007FFFF
  Partition Row Position:                 1
  Interleave Position:                    Non-interleaved
  Interleave Data Depth:                  0

Memory Device Mapped Address ----------------------------------------------

  Starting Address:                       00080000
  Ending Address:                         000FFFFF
  Partition Row Position:                 1
  Interleave Position:                    Non-interleaved
  Interleave Data Depth:                  0

System Boot Information ---------------------------------------------------

  Boot Status:                            No error occured

Memory --------------------------------------------------------------------

 [General information]
  Total Memory Size:                      1 GBytes
  Total Memory Size [MB]:                 1024
 [Current Performance Settings]
  Current Memory Clock:                   332.4 MHz (5 : 3 ratio)
  Current Timing (tCAS-tRCD-tRP-tRAS):    5.0-5-5-15
  Command Rate:                           2T
  Write to Read Delay (tWR_RD) Same Rank (tWTR): 2T
  Read to Precharge Delay (tRTP):         3T
  Write to Precharge Delay (tWTP/tWR):    3T
  RAS# to RAS# Delay (tRRD):              3T
  Refresh Cycle Time (tRFC):              35T

Row: 0 - 512 MB PC2-5300 DDR2-SDRAM Nanya Technology M2Y51H64TU8HB0B-3C ---

 [General Module Information]
  Module Number:                          0
  Module Size:                            512 MBytes
  Memory Type:                            DDR2-SDRAM
  DIMM Type:                              Regular Unbuffered (UDIMM) 
  Error Check/Correction:                 None
  Memory Speed:                           333.3 MHz (PC2-5300)
  Module Manufacturer:                    Nanya Technology
  Module Model:                           M2Y51H64TU8HB0B-3C
  Serial Number:                          319489695
  Manufacturing Date:                     Year: 2007, Week: 24
 [Module characteristics]
  Module Width:                           64-bits
  Module Voltage:                         SSTL 1.8V
  SPD Revision:                           1.2
  Number Of Ranks:                        2
  Row Address Bits:                       13
  Column Address Bits:                    10
  Number Of Banks:                        4
 [Module timing]
  Supported Burst Lengths:                4, 8
  Refresh Rate:                           Reduced 0.5x (7.8 us)
  Supported CAS Latencies (tCAS):         5.0, 4.0, 3.0
  Min. RAS-to-CAS Delay (tRCD):           15.00 ns
  Min. Row Precharge Time (tRP):          15.00 ns
  Min. RAS Pulse Width (tRAS):            45 ns
  Supported Module Timing at 333.3 MHz:   5.0-5-5-15
  Supported Module Timing at 266.7 MHz:   4.0-4-4-12
  Supported Module Timing at 200.0 MHz:   3.0-3-3-9
  Min. Row-Activate To Row-Activate Delay (tRRD): 7.50 ns
  Write Recovery Time (tWR):              15.00 ns
  Internal write to read command delay (tWTR): 7.50 ns
  Internal read to precharge command delay (tRTP): 7.50 ns
  Address and Command Setup Time Before Clock (tIS): 0.20 ns
  Address and Command Setup Time After Clock (tIH): 0.27 ns
  Data Input Setup Time Before Strobe (tDS): 0.10 ns
  Data Input Setup Time After Strobe (tDH): 0.17 ns

Row: 1 - 512 MB PC2-5300 DDR2-SDRAM Nanya Technology M2Y51H64TU8HB0B-3C ---

 [General Module Information]
  Module Number:                          1
  Module Size:                            512 MBytes
  Memory Type:                            DDR2-SDRAM
  DIMM Type:                              Regular Unbuffered (UDIMM) 
  Error Check/Correction:                 None
  Memory Speed:                           333.3 MHz (PC2-5300)
  Module Manufacturer:                    Nanya Technology
  Module Model:                           M2Y51H64TU8HB0B-3C
  Serial Number:                          302713289
  Manufacturing Date:                     Year: 2007, Week: 24
 [Module characteristics]
  Module Width:                           64-bits
  Module Voltage:                         SSTL 1.8V
  SPD Revision:                           1.2
  Number Of Ranks:                        2
  Row Address Bits:                       13
  Column Address Bits:                    10
  Number Of Banks:                        4
 [Module timing]
  Supported Burst Lengths:                4, 8
  Refresh Rate:                           Reduced 0.5x (7.8 us)
  Supported CAS Latencies (tCAS):         5.0, 4.0, 3.0
  Min. RAS-to-CAS Delay (tRCD):           15.00 ns
  Min. Row Precharge Time (tRP):          15.00 ns
  Min. RAS Pulse Width (tRAS):            45 ns
  Supported Module Timing at 333.3 MHz:   5.0-5-5-15
  Supported Module Timing at 266.7 MHz:   4.0-4-4-12
  Supported Module Timing at 200.0 MHz:   3.0-3-3-9
  Min. Row-Activate To Row-Activate Delay (tRRD): 7.50 ns
  Write Recovery Time (tWR):              15.00 ns
  Internal write to read command delay (tWTR): 7.50 ns
  Internal read to precharge command delay (tRTP): 7.50 ns
  Address and Command Setup Time Before Clock (tIS): 0.20 ns
  Address and Command Setup Time After Clock (tIH): 0.27 ns
  Data Input Setup Time Before Strobe (tDS): 0.10 ns
  Data Input Setup Time After Strobe (tDH): 0.17 ns

Bus -----------------------------------------------------------------------


PCI Bus #0 ----------------------------------------------------------------


VIA P4M900/CN896/VN896 Chipset - System Controller ------------------------

 [General Information]
  Original Device Name:                   VIA P4M900/CN896/VN896 Chipset - System Controller
  Device Class:                           Host-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          0
  Function Number:                        0
  PCI Latency Timer:                      8
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
  Memory Base Address 0                   D0000000
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA P4M900/CN896/VN896 Chipset - Error Reporting --------------------------

 [General Information]
  Original Device Name:                   VIA P4M900/CN896/VN896 Chipset - Error Reporting
  Device Class:                           Host-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          0
  Function Number:                        1
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA P4M900/CN896/VN896 Chipset - Host Bus Interface -----------------------

 [General Information]
  Original Device Name:                   VIA P4M900/CN896/VN896 Chipset - Host Bus Interface
  Device Class:                           Host-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          0
  Function Number:                        2
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA P4M900/CN896/VN896 Chipset - DRAM Controller --------------------------

 [General Information]
  Original Device Name:                   VIA P4M900/CN896/VN896 Chipset - DRAM Controller
  Device Class:                           Host-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          0
  Function Number:                        3
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA P4M900/CN896/VN896 Chipset - Power Management -------------------------

 [General Information]
  Original Device Name:                   VIA P4M900/CN896/VN896 Chipset - Power Management
  Device Class:                           Host-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          0
  Function Number:                        4
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA P4M900/CN896/VN896 Chipset - APIC and Central Traffic Controller ------

 [General Information]
  Original Device Name:                   VIA P4M900/CN896/VN896 Chipset - APIC and Central Traffic Controller
  Device Class:                           8259-Compatible PIC
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          0
  Function Number:                        5
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA P4M900/CN896/VN896 Chipset - Security Device --------------------------

 [General Information]
  Original Device Name:                   VIA P4M900/CN896/VN896 Chipset - Security Device
  Device Class:                           Host-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          0
  Function Number:                        6
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA P4M900/CN896/VN896 Chipset - V-Link Bus Interface ---------------------

 [General Information]
  Original Device Name:                   VIA P4M900/CN896/VN896 Chipset - V-Link Bus Interface
  Device Class:                           Host-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          0
  Function Number:                        7
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA P4 A.G.P. Controller --------------------------------------------------

 [General Information]
  Original Device Name:                   VIA P4 A.G.P. Controller
  Device Class:                           PCI-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          1
  Function Number:                        0
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Capable
  Fast Back-to-Back Transactions:         Not Capable
 [CPU-to-AGP Flow Control 1]
  CPU-AGP Post Write:                     Enabled
  CPU-AGP One Wait State Burst Write:     Disabled
  Read Prefetch Control:                  Always prefetch
  MDA on AGP:                             Forward to AGP
  AGP Master Read Caching:                Disabled
  AGP Delay Transaction:                  Enabled
 [CPU-to-AGP Flow Control 2]
  Retry Timeout Action:                   Flush buffer
  Retry Count And Backoff:                2x, back off CPU
  CPU-to-AGP Burst Timeout:               Disabled
  CPU-to-PCI/AGP Cycles Invalidate PCI/AGP Buffered Read Data: Enabled
 [AGP Master Control]
  AGP Master One Wait State Write:        Disabled
  AGP Master One Wait State Read:         Disabled
  Break Consecutive PCI Master Accesses:  Disabled
  Claim I/O R/W and Memory Read Cycles:   Disabled
  Claim Local APIC FEEx xxxx Cycles:      Enabled
  Snoop Write Enable 2T Rate, Support Host Side Snoop Cycles at 2T Rate: Disabled
 [AGP Master Latency Timer]
  Host to AGP Time slot:                  64 GCLKs
  AGP Master Time slot:                   64 GCLKs
 [Fast Write Control]
  Force Fast Write Cycle to be QW Aligned: Disabled
  Merge Multiple CPU Transactions Into One Fast Write Burst Transaction: Enabled
  Merge Multiple CPU Write Cycles To Memory Offset 23-20 Into Fast Write Burst Cycles: Enabled
  Merge Multiple CPU Write Cycles To Prefetchable Memory Offset 27-24 Into Fast Write Burst Cycles: Enabled
  Fast Write Burst 4T Max (No Slave Flow Control): Disabled
  Fast Write Fast Back to Back:           Enabled
  Fast Write Initial Block 1 Wait State:  Disabled

PCI Bus #1 ----------------------------------------------------------------


VIA P4M900/CN896/VN896 Chipset - PCI Express Graphics Root Port -----------

 [General Information]
  Original Device Name:                   VIA P4M900/CN896/VN896 Chipset - PCI Express Graphics Root Port
  Device Class:                           PCI-to-PCI Bridge
  Revision ID:                            80
  Bus Number:                             0
  Device Number:                          2
  Function Number:                        0
  PCI Latency Timer:                      0
 [PCI Express]
  Version:                                1.0
  Maximum Link Width:                     16x
  Current Link Width:                     16x
  Maximum Link Speed:                     2.5 Gb/s
  Current Link Speed:                     2.5 Gb/s
  Device/Port Type:                       Root Port of PCI Express Root Complex
  Slot Implemented:                       Yes
  Hot-Plug:                               Capable
  Hot-Plug Surprise:                      Capable
  Slot Power Limit:                       150.000 W
  Active State Power Management (ASPM) Support: L0s and L1 Entry
  Active State Power Management (ASPM) Status: Disabled
 [System Resources]
  Interrupt Line:                         IRQ27
  Interrupt Pin:                          INTA#
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

PCI Express x16 Bus #2 ----------------------------------------------------


ASUS EN6200TC -------------------------------------------------------------

 [General Information]
  Original Device Name:                   nVIDIA GeForce 6200SE TurboCache
  Device Class:                           VGA Compatible Adapter
  Revision ID:                            A1
  Bus Number:                             2
  Device Number:                          0
  Function Number:                        0
  PCI Latency Timer:                      0
 [PCI Express]
  Version:                                1.0
  Maximum Link Width:                     16x
  Current Link Width:                     16x
  Maximum Link Speed:                     2.5 Gb/s
  Current Link Speed:                     2.5 Gb/s
  Device/Port Type:                       PCI Express Endpoint
  Slot Implemented:                       No
  Active State Power Management (ASPM) Support: L0s and L1 Entry
  Active State Power Management (ASPM) Status: Disabled
 [System Resources]
  Interrupt Line:                         IRQ24
  Interrupt Pin:                          INTA#
  Memory Base Address 0                   DC000000
  Memory Base Address 1                   C0000000
  Memory Base Address 3                   DD000000
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA P4M900/CN896/VN896 Chipset - PCI Express Root Port 1 ------------------

 [General Information]
  Original Device Name:                   VIA P4M900/CN896/VN896 Chipset - PCI Express Root Port 1
  Device Class:                           PCI-to-PCI Bridge
  Revision ID:                            80
  Bus Number:                             0
  Device Number:                          3
  Function Number:                        0
  PCI Latency Timer:                      0
 [PCI Express]
  Version:                                1.0
  Maximum Link Width:                     1x
  Current Link Width:                     Not negotiated
  Maximum Link Speed:                     2.5 Gb/s
  Current Link Speed:                     2.5 Gb/s
  Device/Port Type:                       Root Port of PCI Express Root Complex
  Slot Implemented:                       Yes
  Hot-Plug:                               Capable
  Hot-Plug Surprise:                      Capable
  Slot Power Limit:                       150.000 W
  Active State Power Management (ASPM) Support: L0s and L1 Entry
  Active State Power Management (ASPM) Status: Disabled
 [System Resources]
  Interrupt Line:                         IRQ31
  Interrupt Pin:                          INTA#
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

PCI Express x1 Bus #3 -----------------------------------------------------


VIA VT8237A SATA RAID Controller ------------------------------------------

 [General Information]
  Original Device Name:                   VIA VT8237A SATA RAID Controller
  Device Class:                           IDE Controller
  Revision ID:                            80
  Bus Number:                             0
  Device Number:                          15
  Function Number:                        0
  PCI Latency Timer:                      32
 [System Resources]
  Interrupt Line:                         IRQ21
  Interrupt Pin:                          INTB#
  I/O Base Address 0                      FC00
  I/O Base Address 1                      F800
  I/O Base Address 2                      F400
  I/O Base Address 3                      F000
  I/O Base Address 4                      EC00
  I/O Base Address 5                      E800
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Capable

VIA VT82C571 Integrated IDE Controller ------------------------------------

 [General Information]
  Original Device Name:                   VIA VT82C571 Integrated IDE Controller
  Device Class:                           IDE Controller
  Revision ID:                            7
  Bus Number:                             0
  Device Number:                          15
  Function Number:                        1
  PCI Latency Timer:                      32
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
  I/O Base Address 4                      E400
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Capable
 [Chip Enable]
  Primary IDE Channel:                    Enabled
  Secondary IDE Channel:                  Enabled
 [IDE Configuration I]
  Primary IDE Read Prefetch Buffer:       Enabled
  Primary IDE Post Write Buffer:          Enabled
  Secondary IDE Read Prefetch Buffer:     Enabled
  Secondary IDE Post Write Buffer:        Enabled
 [IDE Configuration II]
  PIO Operating Mode - Primary Channel:   Compatibility Mode
  PIO Operating Mode - Secondary Channel: Compatibility Mode
 [FIFO Configuration]
  FIFO Configuration:                     PRI = 16, SEC = 0
  Primary Channel FIFO Threshold:         1/2
  Secondary Channel FIFO Threshold:       1/2
 [Miscellaneous Control 1]
  Master Read Cycle IRDY# Wait State:     0 WS
  Master Write Cycle IRDY# Wait State:    0 WS
  FIFO Output Data 1/2 Clock Advance/PIO Read Pre-Fetch Byte Counter: Enabled
  Bus-Master IDE Status Register Read Retry: Enabled
  Packet Command Prefetching:             Disabled
  UltraDMA Host Must Wait for First Transfer Before Termination: Enabled
 [Miscellaneous Control 2]
  Interrupt Steering Swap Between Channels: Disabled
  Rx3C Write Protect:                     Disabled
  Memory-Read-Multiple Command:           Enabled
  Memory-Write-and-Invalidate Command:    Enabled
 [Miscellaneous Control 3]
  Read DMA FIFO Flush (PRI):              Enabled
  Read DMA FIFO Flush (SEC):              Enabled
  End-of-Sector FIFO Flush (PRI):         Disabled
  End-of-Sector FIFO Flush (SEC):         Disabled
  Maximum DRDY# Pulse Width:              Unlimited
 [Drive Timing Control]
  Primary Drive 0 Active Pulse Width:     3 clocks
  Primary Drive 0 Recovery Time:          1 PCICLKs
  Primary Drive 1 Active Pulse Width:     3 PCICLKs
  Primary Drive 1 Recovery Time:          1 clocks
  Secondary Drive 0 Active Pulse Width:   3 clocks
  Secondary Drive 0 Recovery Time:        1 PCICLKs
  Secondary Drive 1 Active Pulse Width:   3 PCICLKs
  Secondary Drive 1 Recovery Time:        1 clocks
 [Address Setup Time]
  Primary Drive 0 Address Setup Time:     4T
  Primary Drive 1 Address Setup Time:     4T
  Secondary Drive 0 Address Setup Time:   4T
  Secondary Drive 1 Address Setup Time:   4T
 [Secondary Non-01F0h Port Access Timing]
  DIOR#/DIOW# Active Pulse Width:         12 PCICLKs
  DIOR#/DIOW# Recovery Time:              7 PCICLKs
 [Primary Non-01F0h Port Access Timing]
  DIOR#/DIOW# Active Pulse Width:         12 PCICLKs
  DIOR#/DIOW# Recovery Time:              7 PCICLKs
 [Ultra-DMA Extended Timing Control (SEC DRV 1)]
  Ultra-DMA Mode Enable Method:           Using Set Feature Cmd.
  Ultra-DMA Mode:                         Disabled
  Transfer Mode:                          DMA or PIO
  Cable Type Reporting:                   40-pin
  Drive Cycle Time:                       9T
 [Ultra-DMA Extended Timing Control (SEC DRV 0)]
  Ultra-DMA Mode Enable Method:           Using this reg.
  Ultra-DMA Mode:                         Enabled
  Transfer Mode:                          Ultra-DMA
  Cable Type Reporting:                   40-pin
  Drive Cycle Time:                       8T
 [Ultra-DMA Extended Timing Control (PRI DRV 1)]
  Ultra-DMA Mode Enable Method:           Using Set Feature Cmd.
  Ultra-DMA Mode:                         Disabled
  Transfer Mode:                          DMA or PIO
  Cable Type Reporting:                   80-pin
  Drive Cycle Time:                       9T
 [Ultra-DMA Extended Timing Control (PRI DRV 0)]
  Ultra-DMA Mode Enable Method:           Using this reg.
  Ultra-DMA Mode:                         Enabled
  Transfer Mode:                          Ultra-DMA
  Cable Type Reporting:                   80-pin
  Drive Cycle Time:                       3T
 [Ultra-DMA FIFO Control]
  Lower ISA Request Priority When Write Device Packet Command is Issued: Disabled
  Clear Native Mode Interrupt on Falling Edge of Gated Interrupt: Disabled
  Improve PIO Prefetch and Post-Write Performance: Enabled
  Memory Prefetch Size:                   2 lines
  Change Drive Clears All FIFO & Internal States: Enabled
  Complete DMA Cycle with Transfer Size Less Than FIFO Size: Enabled
 [IDE Clock Gating]
  Dynamic 100/133 MHz Clock Gating:       Enabled
  Dynamic 66 MHz Clock Gating:            Enabled
 [Primary Sector Size]
  Sector Size:                            512 Bytes/Sector
 [Secondary Sector Size]
  Sector Size:                            512 Bytes/Sector

VIA VT8237A USB Universal Host Controller ---------------------------------

 [General Information]
  Original Device Name:                   VIA VT8237A USB Universal Host Controller
  Device Class:                           Universal Serial Bus (USB)
  Revision ID:                            A0
  Bus Number:                             0
  Device Number:                          16
  Function Number:                        0
  PCI Latency Timer:                      32
 [System Resources]
  Interrupt Line:                         IRQ20
  Interrupt Pin:                          INTA#
  I/O Base Address 4                      E000
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable
 [Miscellaneous Control 1]
  PCI Memory Commands Support:            MRL, MRM, and MWAI
  Babbled Port of EOF:                    Disabled
  PCI Parity Checking:                    Disabled PERR#
  Frame Interval Select:                  1 msec
  USB Data Length Limit:                  1280 bytes
  USB Power Management/Improved FIFO Latency: Disabled
  DMA Limited To:                         16-DW Burst
  PCI Wait States:                        0 WS
 [Miscellaneous Control 2]
  USB 1.1 Improvement for EOP:            Disabled (USB 1.0)
  Trap Status Bits Override:              Disabled
  A20GATE Pass Through Option:            Don't Pass
 [Miscellaneous Control 4]
  Continue Transmission of Erroneous Data on FIFO Underrun: Enabled
  Issue CRC Error Instead of Stuffing Error on FIFO Underrun: Enabled
 [Miscellaneous Control 5]
  Issue Bad CRC5 in SOF After FIFO Underrun: Enabled
  Lengthen PreSOF Time:                   Enabled
  Issue Nonzero Bad CRC Code on FIFO Underrun: Non zero CRC
 [Miscellaneous Control 6]
  EHCI Supports PME Assertion in D3 Cold State: Supported
  UHCI Supports PME Assertion in D3 Cold State: Supported
 [Miscellaneous Control 7]
  Use External 60 MHz Clock:              Disabled
 [USB Release Number]
  USB Release Number:                     1.0
 [USB Legacy Support]
  UHCI v1.1 Compliant:                    2000

VIA VT8237A USB Universal Host Controller ---------------------------------

 [General Information]
  Original Device Name:                   VIA VT8237A USB Universal Host Controller
  Device Class:                           Universal Serial Bus (USB)
  Revision ID:                            A0
  Bus Number:                             0
  Device Number:                          16
  Function Number:                        1
  PCI Latency Timer:                      32
 [System Resources]
  Interrupt Line:                         IRQ22
  Interrupt Pin:                          INTB#
  I/O Base Address 4                      DC00
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable
 [Miscellaneous Control 1]
  PCI Memory Commands Support:            MRL, MRM, and MWAI
  Babbled Port of EOF:                    Disabled
  PCI Parity Checking:                    Disabled PERR#
  Frame Interval Select:                  1 msec
  USB Data Length Limit:                  1280 bytes
  USB Power Management/Improved FIFO Latency: Disabled
  DMA Limited To:                         16-DW Burst
  PCI Wait States:                        0 WS
 [Miscellaneous Control 2]
  USB 1.1 Improvement for EOP:            Disabled (USB 1.0)
  Trap Status Bits Override:              Disabled
  A20GATE Pass Through Option:            Don't Pass
 [Miscellaneous Control 4]
  Continue Transmission of Erroneous Data on FIFO Underrun: Enabled
  Issue CRC Error Instead of Stuffing Error on FIFO Underrun: Enabled
 [Miscellaneous Control 5]
  Issue Bad CRC5 in SOF After FIFO Underrun: Enabled
  Lengthen PreSOF Time:                   Enabled
  Issue Nonzero Bad CRC Code on FIFO Underrun: Non zero CRC
 [Miscellaneous Control 6]
  EHCI Supports PME Assertion in D3 Cold State: Supported
  UHCI Supports PME Assertion in D3 Cold State: Supported
 [Miscellaneous Control 7]
  Use External 60 MHz Clock:              Disabled
 [USB Release Number]
  USB Release Number:                     1.0
 [USB Legacy Support]
  UHCI v1.1 Compliant:                    2000

VIA VT8237A USB Universal Host Controller ---------------------------------

 [General Information]
  Original Device Name:                   VIA VT8237A USB Universal Host Controller
  Device Class:                           Universal Serial Bus (USB)
  Revision ID:                            A0
  Bus Number:                             0
  Device Number:                          16
  Function Number:                        2
  PCI Latency Timer:                      32
 [System Resources]
  Interrupt Line:                         IRQ21
  Interrupt Pin:                          INTC#
  I/O Base Address 4                      D800
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable
 [Miscellaneous Control 1]
  PCI Memory Commands Support:            MRL, MRM, and MWAI
  Babbled Port of EOF:                    Disabled
  PCI Parity Checking:                    Disabled PERR#
  Frame Interval Select:                  1 msec
  USB Data Length Limit:                  1280 bytes
  USB Power Management/Improved FIFO Latency: Disabled
  DMA Limited To:                         16-DW Burst
  PCI Wait States:                        0 WS
 [Miscellaneous Control 2]
  USB 1.1 Improvement for EOP:            Disabled (USB 1.0)
  Trap Status Bits Override:              Disabled
  A20GATE Pass Through Option:            Don't Pass
 [Miscellaneous Control 4]
  Continue Transmission of Erroneous Data on FIFO Underrun: Enabled
  Issue CRC Error Instead of Stuffing Error on FIFO Underrun: Enabled
 [Miscellaneous Control 5]
  Issue Bad CRC5 in SOF After FIFO Underrun: Enabled
  Lengthen PreSOF Time:                   Enabled
  Issue Nonzero Bad CRC Code on FIFO Underrun: Non zero CRC
 [Miscellaneous Control 6]
  EHCI Supports PME Assertion in D3 Cold State: Supported
  UHCI Supports PME Assertion in D3 Cold State: Supported
 [Miscellaneous Control 7]
  Use External 60 MHz Clock:              Disabled
 [USB Release Number]
  USB Release Number:                     1.0
 [USB Legacy Support]
  UHCI v1.1 Compliant:                    2000

VIA VT8237A USB Universal Host Controller ---------------------------------

 [General Information]
  Original Device Name:                   VIA VT8237A USB Universal Host Controller
  Device Class:                           Universal Serial Bus (USB)
  Revision ID:                            A0
  Bus Number:                             0
  Device Number:                          16
  Function Number:                        3
  PCI Latency Timer:                      32
 [System Resources]
  Interrupt Line:                         IRQ23
  Interrupt Pin:                          INTD#
  I/O Base Address 4                      D400
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable
 [Miscellaneous Control 1]
  PCI Memory Commands Support:            MRL, MRM, and MWAI
  Babbled Port of EOF:                    Disabled
  PCI Parity Checking:                    Disabled PERR#
  Frame Interval Select:                  1 msec
  USB Data Length Limit:                  1280 bytes
  USB Power Management/Improved FIFO Latency: Disabled
  DMA Limited To:                         16-DW Burst
  PCI Wait States:                        0 WS
 [Miscellaneous Control 2]
  USB 1.1 Improvement for EOP:            Disabled (USB 1.0)
  Trap Status Bits Override:              Disabled
  A20GATE Pass Through Option:            Don't Pass
 [Miscellaneous Control 4]
  Continue Transmission of Erroneous Data on FIFO Underrun: Enabled
  Issue CRC Error Instead of Stuffing Error on FIFO Underrun: Enabled
 [Miscellaneous Control 5]
  Issue Bad CRC5 in SOF After FIFO Underrun: Enabled
  Lengthen PreSOF Time:                   Enabled
  Issue Nonzero Bad CRC Code on FIFO Underrun: Non zero CRC
 [Miscellaneous Control 6]
  EHCI Supports PME Assertion in D3 Cold State: Supported
  UHCI Supports PME Assertion in D3 Cold State: Supported
 [Miscellaneous Control 7]
  Use External 60 MHz Clock:              Disabled
 [USB Release Number]
  USB Release Number:                     1.0
 [USB Legacy Support]
  UHCI v1.1 Compliant:                    2000

VIA VT8237(A) USB 2.0 Enhanced Host Controller ----------------------------

 [General Information]
  Original Device Name:                   VIA VT8237(A) USB 2.0 Enhanced Host Controller
  Device Class:                           Universal Serial Bus (USB)
  Revision ID:                            86
  Bus Number:                             0
  Device Number:                          16
  Function Number:                        4
  PCI Latency Timer:                      32
 [System Resources]
  Interrupt Line:                         IRQ21
  Interrupt Pin:                          INTC#
  Memory Base Address 0                   DFFFF000
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable
 [Miscellaneous Control 1]
  Babbled Port of EOF:                    Enabled
  PCI Parity Checking:                    Disabled PERR#
  DMA Limited To:                         16-DW Burst
 [Miscellaneous Control 5]
  CCA Burst Access:                       Disabled
 [Miscellaneous Control 6]
  Clock Auto Stop:                        Enabled
  Auto Power Down Receiver Squelch Detector: Auto Power Down
 [USB Release Number]
  USB Release Number:                     2.0
 [Frame Length Adjust]
  Frame Length Adjust:                    32

VIA VT8237A PCI-to-ISA Bridge ---------------------------------------------

 [General Information]
  Original Device Name:                   VIA VT8237A PCI-to-ISA Bridge
  Device Class:                           PCI-to-ISA Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          17
  Function Number:                        0
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Disabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA VT8251/VT8261 Ultra V-Link Controller ---------------------------------

 [General Information]
  Original Device Name:                   VIA VT8251/VT8261 Ultra V-Link Controller
  Device Class:                           Host-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          17
  Function Number:                        7
  PCI Latency Timer:                      32
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA VT6102 Rhine II Fast Ethernet Adapter ---------------------------------

 [General Information]
  Original Device Name:                   VIA VT6102 Rhine II Fast Ethernet Adapter
  Device Class:                           Ethernet Adapter
  Revision ID:                            7C
  Bus Number:                             0
  Device Number:                          18
  Function Number:                        0
  PCI Latency Timer:                      32
 [System Resources]
  Interrupt Line:                         IRQ23
  Interrupt Pin:                          INTA#
  I/O Base Address 0                      D000
  Memory Base Address 1                   DFFFE000
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA VT8237A PCI-to-PCI Express Bridge -------------------------------------

 [General Information]
  Original Device Name:                   VIA VT8237A PCI-to-PCI Express Bridge
  Device Class:                           Host-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          19
  Function Number:                        0
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Disabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

VIA VT8237A/VT8261 PCI-to-PCI Bridge --------------------------------------

 [General Information]
  Original Device Name:                   VIA VT8237A/VT8261 PCI-to-PCI Bridge
  Device Class:                           PCI-to-PCI Bridge
  Revision ID:                            0
  Bus Number:                             0
  Device Number:                          19
  Function Number:                        1
  PCI Latency Timer:                      0
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          N/A
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

PCI Bus #4 ----------------------------------------------------------------


Philips/NXP SAA7130HL Multimedia Capture Device ---------------------------

 [General Information]
  Original Device Name:                   Philips/NXP SAA7130HL Multimedia Capture Device
  Device Class:                           Unknown Multimedia Adapter
  Revision ID:                            1
  Bus Number:                             4
  Device Number:                          4
  Function Number:                        0
  PCI Latency Timer:                      32
 [System Resources]
  Interrupt Line:                         IRQ11
  Interrupt Pin:                          INTA#
  Memory Base Address 0                   DFAFF000
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Capable

PCI Bus #128 --------------------------------------------------------------


VIA VT8237A/8251/8261 - High Definition Audio Controller ------------------

 [General Information]
  Original Device Name:                   VIA VT8237A/8251/8261 - High Definition Audio Controller
  Device Class:                           Mixed mode device
  Revision ID:                            10
  Bus Number:                             128
  Device Number:                          1
  Function Number:                        0
  PCI Latency Timer:                      0
 [PCI Express]
  Version:                                1.0
  Current Link Width:                     Not negotiated
  Device/Port Type:                       Root Complex Integrated Endpoint
  Slot Implemented:                       No
  Active State Power Management (ASPM) Support: Unknown
  Active State Power Management (ASPM) Status: Disabled
 [System Resources]
  Interrupt Line:                         IRQ17
  Interrupt Pin:                          INTA#
  Memory Base Address 0                   BFFFC000
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable

Video Adapter -------------------------------------------------------------


nVIDIA GeForce 6200SE TurboCache (NV44) -----------------------------------

 [Video chipset]
  Video Chipset:                          nVIDIA GeForce 6200SE TurboCache (NV44)
  Video Memory:                           64 MBytes of DDR SDRAM
 [Video Card]
  Video Card:                             ASUS EN6200TC
  Video Bus:                              PCIe v1.0 x16 (2.5 Gb/s) @ x16 (2.5 Gb/s)
  Video RAMDAC:                           Integrated RAMDAC
  Video BIOS Version:                     5.44.02.37.10
  Video Chipset Revision:                 A1
 [Performance]
  Processor Clock:                        351.0 MHz
  Memory Clock:                           250.6 MHz (Effective 501.2 MHz)
  Memory Bus Width:                       32-bit
  Number Of Pixel Pipelines:              4
  Number Of Vertex Shaders:               3

Monitor -------------------------------------------------------------------


DELL M782p ----------------------------------------------------------------

 [General information]
  Monitor Name:                           DELL M782p
  Serial Number:                          1M978292G0H3 
  Date Of Manufacture:                    Week: 36, Year: 2002
  Max. Vertical Size:                     23 cm
  Max. Horizontal Size:                   31 cm
  Horizontal Frequency:                   30 - 85 kHz
  Vertical Frequency:                     50 - 160 Hz
  Maximum Pixel Clock:                    160 MHz
 [Advanced parameters]
  Input Signal:                           Analog: 0.700 V / 0.300 V (1.000 V p-p)
  Display Type:                           RGB color
  Gamma Factor:                           2.87
 [DPMS Modes]
  Standby:                                Supported
  Suspend:                                Supported
  Active Off:                             Supported
  Standard Colour Space:                  Supported
  Preferred Timing Mode:                  Supported
  Default GTF Supported:                  Not Supported
 [DPMS Input Signal]
  Serration VSync:                        Not Supported
  Sync On Green:                          Not Supported
  Composite Sync:                         Not Supported
  Separate Syncs:                         Supported
  Blank-to-black Setup:                   Not Supported
 [Supported Video Modes]
  1024 x 768                              85 Hz
  800 x 600                               85 Hz
  640 x 480                               85 Hz
  1024 x 768                              306 x 230 mm, Pixel Clock 94.50 MHz

Drives --------------------------------------------------------------------


Floppy Drives -------------------------------------------------------------


1.44 MB 3½" ---------------------------------------------------------------


(S)ATA/ATAPI Drives -------------------------------------------------------


WDC WD1600AAJS-00L7A0 -----------------------------------------------------

 [General Information]
  Drive Controller:                       Serial ATA 1.5Gb/s
  Drive Model:                            WDC WD1600AAJS-00L7A0
  Drive Revision:                         01.03E01
  Drive Serial Number:                    WD-WCAV26356695
  Drive Capacity:                         152,627 MBytes (160 GB)
  Drive Capacity [MB]:                    152627
 [Drive Geometry]
  Number of Cylinders:                    16383
  Number of Heads:                        16
  Sectors Per Track:                      63
  Bytes Per Sector:                       Unknown
  Bytes Per Track:                        Unknown
  Number Of ECC Bytes:                    50
  Number of Sectors:                      16514064
  Total 32-bit LBA Sectors:               268435455
  Total 48-bit LBA Sectors:               312581808
  Cache Buffer Size:                      8192 KBytes
  Controller Type:                        Not Specified
 [Transfer Modes]
  Sectors Per Interrupt:                  Total: 16, Active: 16
  Max. PIO Transfer Mode:                 4
  Multiword DMA Mode:                     Total: 2, Active: -
  Singleword DMA Mode:                    Total: -, Active: -
  Ultra-DMA Mode:                         Total: 6 (ATA-133), Active: 6 (ATA-133)
  Max. Multiword DMA Transfer Rate:       16.7 MBytes/s
  Max. PIO with IORDY Transfer Rate:      16.7 MBytes/s
  Max. PIO w/o IORDY Transfer Rate:       16.7 MBytes/s
  Transfer Width:                         16-bit
  Native Command Queuing:                 Supported, Max. Depth: 32
  TRIM Command:                           Not Supported
 [Device flags]
  Fixed Drive:                            Present
  Removable Drive:                        Not Present
  Magnetic Storage:                       Present
  LBA Mode:                               Supported
  DMA Mode:                               Supported
  IORDY:                                  Supported
  IORDY Disableable:                      Supported
 [Features]
  Write Cache:                            Present, Active
  S.M.A.R.T. Feature:                     Present, Inactive
  Security Feature:                       Present, Inactive
  Removable Media Feature:                Not Present, Disabled
  Power Management:                       Present, Active
  Advanced Power Management:              Not Present, Inactive
  Packet Interface:                       Not Present, Disabled
  Look-Ahead Buffer:                      Present, Active
  Host Protected Area:                    Present, Enabled
  Power-Up In Standby:                    Supported, Inactive
  Automatic Acoustic Management:          Supported, Inactive
  48-bit LBA:                             Supported, Active
 [Self-Monitoring, Analysis and Reporting Technology]
  Raw Read Error Rate:                    200/51, Worst: 200 (Data = 1786)
  Spin Up Time:                           132/21, Worst: 132 (Data = 4358)
  Start/Stop Count:                       99/Always OK, Worst: 99 (Data = 1182)
  Reallocated Sector Count:               200/140, Worst: 200
  Seek Error Rate:                        100/Always OK, Worst: 253
  Power-On Time Count:                    95/Always OK, Worst: 95 (Data = 4039)
  Spin Retry Count:                       100/Always OK, Worst: 100
  Calibration Retry Count:                100/Always OK, Worst: 100
  Power Cycle Count:                      99/Always OK, Worst: 99 (Data = 1180)
  Power-Off Retract Count:                200/Always OK, Worst: 200 (Data = 28)
  Load/Unload Cycle Count:                200/Always OK, Worst: 200 (Data = 1182)
  Temperature                             113/Always OK, Worst: 89 (Data = 30.0 °C)
  Reallocation Event Count:               200/Always OK, Worst: 200
  Current Pending Sector Count:           200/Always OK, Worst: 193 (Data = 10)
  Off-Line Uncorrectable Sector Count:    200/Always OK, Worst: 200
  Ultra ATA CRC Error Rate:               200/Always OK, Worst: 200
  Write Error Rate:                       200/Always OK, Worst: 200

WDC WD800BB-00JHC0 --------------------------------------------------------

 [General Information]
  Drive Controller:                       E-IDE (ATA-6)
  Drive Channel:                          Primary, Slave
  Drive Model:                            WDC WD800BB-00JHC0
  Drive Revision:                         05.01C05
  Drive Serial Number:                    WD-WMAM9LX92345
  Drive Capacity:                         76,189 MBytes (79 GB)
  Drive Capacity [MB]:                    76189
 [Drive Geometry]
  Number of Cylinders:                    16383
  Number of Heads:                        16
  Sectors Per Track:                      63
  Bytes Per Sector:                       Unknown
  Bytes Per Track:                        Unknown
  Number Of ECC Bytes:                    66
  Number of Sectors:                      16514064
  Total 32-bit LBA Sectors:               156035242
  Cache Buffer Size:                      2048 KBytes
  Controller Type:                        Not Specified
 [Transfer Modes]
  Sectors Per Interrupt:                  Total: 16, Active: 16
  Max. PIO Transfer Mode:                 4
  Multiword DMA Mode:                     Total: 2, Active: -
  Singleword DMA Mode:                    Total: -, Active: -
  Ultra-DMA Mode:                         Total: 5 (ATA-100), Active: 5 (ATA-100)
  Max. Multiword DMA Transfer Rate:       16.7 MBytes/s
  Max. PIO with IORDY Transfer Rate:      16.7 MBytes/s
  Max. PIO w/o IORDY Transfer Rate:       16.7 MBytes/s
  Transfer Width:                         16-bit
  Native Command Queuing:                 Not Supported
  TRIM Command:                           Not Supported
 [Device flags]
  Fixed Drive:                            Present
  Removable Drive:                        Not Present
  Magnetic Storage:                       Present
  LBA Mode:                               Supported
  DMA Mode:                               Supported
  IORDY:                                  Supported
  IORDY Disableable:                      Supported
 [Features]
  Write Cache:                            Present, Active
  S.M.A.R.T. Feature:                     Present, Inactive
  Security Feature:                       Present, Inactive
  Removable Media Feature:                Not Present, Disabled
  Power Management:                       Present, Active
  Advanced Power Management:              Not Present, Inactive
  Packet Interface:                       Not Present, Disabled
  Look-Ahead Buffer:                      Present, Active
  Host Protected Area:                    Present, Enabled
  Power-Up In Standby:                    Not Suppported, Inactive
  Automatic Acoustic Management:          Supported, Inactive
  48-bit LBA:                             Not Suppported, Inactive
 [Self-Monitoring, Analysis and Reporting Technology]
  Raw Read Error Rate:                    200/51, Worst: 200
  Spin Up Time:                           165/21, Worst: 164 (Data = 2733)
  Start/Stop Count:                       97/Always OK, Worst: 97 (Data = 3311)
  Reallocated Sector Count:               200/140, Worst: 200
  Seek Error Rate:                        200/51, Worst: 200
  Power-On Time Count:                    80/Always OK, Worst: 80 (Data = 15296)
  Spin Retry Count:                       100/51, Worst: 100
  Calibration Retry Count:                100/51, Worst: 100
  Power Cycle Count:                      97/Always OK, Worst: 97 (Data = 3240)
  Temperature                             107/Always OK, Worst: 82 (Data = 36.0 °C)
  Reallocation Event Count:               200/Always OK, Worst: 200
  Current Pending Sector Count:           200/Always OK, Worst: 200
  Off-Line Uncorrectable Sector Count:    200/Always OK, Worst: 200
  Ultra ATA CRC Error Rate:               200/Always OK, Worst: 200
  Write Error Rate:                       200/51, Worst: 200

HL-DT-ST DVDRAM GSA-H42N --------------------------------------------------

 [General information]
  Drive Model:                            HL-DT-ST DVDRAM GSA-H42N
  Drive Revision:                         RL00
  Firmware Date:                          2006-11-21 12:34:56
  Serial Number:                          K0C6CEC2147 
  Device Type:                            DVD+R DL
 [Device capabilities]
  Drive can read:                         CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD-RAM, DVD+R DL
  Drive can write:                        CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD-RAM, DVD+R DL

LAP 56JO9QNKPM ------------------------------------------------------------

 [General information]
  Drive Model:                            LAP 56JO9QNKPM
  Drive Revision:                         1.03
  Device Type:                            BD-ROM
 [Device capabilities]
  Drive can read:                         CD-R, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL, DVD+RW DL, BD

LAP 56JO9QNKPM ------------------------------------------------------------

 [General information]
  Drive Model:                            LAP 56JO9QNKPM
  Drive Revision:                         1.03
  Device Type:                            BD-ROM
 [Device capabilities]
  Drive can read:                         CD-R, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL, DVD+RW DL, BD

Audio ---------------------------------------------------------------------


VIA VT8237A/8251/8261 - High Definition Audio Controller ------------------


Network -------------------------------------------------------------------


VIA Rhine II Fast Ethernet Adapter ----------------------------------------

 [General information]
 [Capabilities]

Ports ---------------------------------------------------------------------


Serial Ports --------------------------------------------------------------


COM1 ----------------------------------------------------------------------


COM2 ----------------------------------------------------------------------


Parallel Ports ------------------------------------------------------------


LPT1 ----------------------------------------------------------------------


USB -----------------------------------------------------------------------


VIA Rev 5 or later USB Universal Host Controller --------------------------


USB Hub -------------------------------------------------------------------


[Port1] : No Device Connected ---------------------------------------------


[Port2] : No Device Connected ---------------------------------------------


VIA Rev 5 or later USB Universal Host Controller --------------------------


USB Hub -------------------------------------------------------------------


[Port1] : No Device Connected ---------------------------------------------


[Port2] : No Device Connected ---------------------------------------------


VIA Rev 5 or later USB Universal Host Controller --------------------------


USB Hub -------------------------------------------------------------------


[Port1] : No Device Connected ---------------------------------------------


[Port2] : No Device Connected ---------------------------------------------


VIA Rev 5 or later USB Universal Host Controller --------------------------


USB Hub -------------------------------------------------------------------


[Port1] : No Device Connected ---------------------------------------------


[Port2] : No Device Connected ---------------------------------------------


VIA USB Enhanced Host Controller ------------------------------------------


USB Hub -------------------------------------------------------------------


[Port1] : No Device Connected ---------------------------------------------


[Port2] : No Device Connected ---------------------------------------------


[Port3] : No Device Connected ---------------------------------------------


[Port4] : No Device Connected ---------------------------------------------


[Port5] : No Device Connected ---------------------------------------------


[Port6] : No Device Connected ---------------------------------------------


[Port7] : No Device Connected ---------------------------------------------


[Port8] : No Device Connected ---------------------------------------------


```

---

### Post by kansasnoob on 2010-12-31
Since they're both internal it's odd that Ubuntu recognized them in a different order at different times :confused:

If Ubuntu does that after being installed I'd expect both it and Windows to become un-bootable, so let me pick a few other folks' brains. I'm glad I noticed that before you installed.

Being able to copy-n-paste is only one of many reasons why you should be sure to have some live Linux media that can connect to the internet before installing. Otherwise it could be very tedious to work on if something goes haywire.

---

### Post by HaHa Sandman on 2011-01-04
> **kansasnoob said:**
> Since they're both internal it's odd that Ubuntu recognized them in a different order at different times :confused:

If Ubuntu does that after being installed I'd expect both it and Windows to become un-bootable, so let me pick a few other folks' brains. I'm glad I noticed that before you installed.

Being able to copy-n-paste is only one of many reasons why you should be sure to have some live Linux media that can connect to the internet before installing. Otherwise it could be very tedious to work on if something goes haywire.

Any news?

Could the random reading order be affected by a bad Ubuntu iso?

---

### Post by kansasnoob on 2011-01-04
You can test the Live CD/USB by booting it, and you first see the purple screen with two small emblems at the bottom. You have 3 seconds at that moment to press any key which should then display all the boot options.

On that screen you can then select "Check disc for defects". It takes a few minutes to complete and will tell you if any errors are found.

Were you able to figure out your networking issue?

---

### Post by kansasnoob on 2011-01-04
I posted a query here:

[http://ubuntuforums.org/showthread.php?p=10315164#post10315164](http://ubuntuforums.org/showthread.php?p=10315164#post10315164)

I've never seen that happen before with 2 or more internal drives.

---

### Post by HaHa Sandman on 2011-01-04
> **kansasnoob said:**
> You can test the Live CD/USB by booting it, and you first see the purple screen with two small emblems at the bottom. You have 3 seconds at that moment to press any key which should then display all the boot options.

On that screen you can then select "Check disc for defects". It takes a few minutes to complete and will tell you if any errors are found.

Were you able to figure out your networking issue?

Check complete: No errors found

> Were you able to figure out your networking issue?

If you're talking about if i can connect through the internet through ULCD yes i can, i wrote that in post 21, as for detecting my internet connexion before installing Ubuntu, no.

But that does not worry me, i can manually install the updates, what worries me is what you said with "unable to boot neither operating systems".

---

### Post by kansasnoob on 2011-01-04
> what worries me is what you said with "unable to boot neither operating systems".

Me too :(

I see at that query I posted others have seen this, I hadn't. Some seem to indicate that it's not a problem, but others indicate that it can be a problem.

I'm just not sure ATM.

---

### Post by HaHa Sandman on 2011-01-04
> **kansasnoob said:**
> Me too :(

I see at that query I posted others have seen this, I hadn't. Some seem to indicate that it's not a problem, but others indicate that it can be a problem.

I'm just not sure ATM.

Okay...

You said that you think if the hard drives will swap both operating systems will be unbootable.

But, if i would proceed and install it anyways, could i undo this by deleting drive E (sda5 whatever letter it is)

And re-installing windows in it's main partition, sda1

and then making a new partition, a new sda5?

I mean theoretically after deleting drive sda5 and reinstalling windows, the windows boot program (if it has any) should be reinstalled right? Or everything return to it's default booting process. It would be like nothing ever happened before.

If you aprove what i wrote, i can risk it and install it, what i have on sda1 and sdb5 is expendable, only the 160GB HD is important to me.

Either ways whatever happens i won't hold you responsible, you only tried to help me, and besides this is free support after all ;)

---

### Post by kansasnoob on 2011-01-04
First of all just know I've not abandoned you, if you follow this thread I'm trying to learn myself:

[http://ubuntuforums.org/showthread.php?t=1659542](http://ubuntuforums.org/showthread.php?t=1659542)

Almost needless to say, it's quite hard to figure some things out if I can't reproduce the behavior on one of my own machines. Regardless I have a new testing strategy that should answer at least one question. I hope you'll be patient.

Regardless let me answer a few questions:

> You said that you think if the hard drives will swap both operating systems will be unbootable.

But, if i would proceed and install it anyways, could i undo this by deleting drive E (sda5 whatever letter it is)

And re-installing windows in it's main partition, sda1

and then making a new partition, a new sda5?

There would be no need to remove or reinstall any OS! You'd simply need to "fix" grub. Since Karmic, Ubuntu has used grub2 (aka: grub-pc), and it's puzzled some people but it's actually much simpler than the old legacy-grub in many regards. But let's begin with understanding installing again.

Before beginning the installation go to terminal and run the command:

```
sudo parted -l
```

Remember, that's a lower case L.

You'll need to know if Ubuntu is recognizing the 80GB drive as sda or sdb. Remember this:

> Drives are designated as /dev/sda, /dev/sdb, /dev/sdc, etc. the last letter indicates the drive number, eg:
/dev/sda = drive #1
/dev/sdb = drive #2
/dev/sdc = drive #3

Partititions are designated with a number following the drive designations, eg:
/dev/sda1 = drive #1/partition #1
/dev/sda2 = drive #1/partition #2
/dev/sdb1 = drive #2/partition #1

I think you understand that so far, eh :confused:

I hate that these device designations change like that, but I think you understand what's up so far. BTW I'm not a developer, just an end-user that does testing and tries to get bugs fixed, so don't shoot me if something goes wrong.

Anyway, back to "what to do if you try to boot and it won't"! **No need to panic!**

This is where you need to have the ability to copy-n-paste certain commands so you can fix grub. IMHO in order to properly restore **and update** grub2 one should basically follow the **METHOD 3 - CHROOT** procedure here because it's the only procedure that also allows you to "update-grub" while reinstalling grub:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

But I've tweaked things. Certainly you'll still want to use either "fdisk -l" or "parted -l" to determine the proper designation for your Ubuntu root partition, but you'll notice that's a lot of commands, I condensed it to one:

```
sudo mount /dev/sdXY /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

The "space && space" simply allows one command to directly follow another, and obviously the X needs to be replaced by the drive designation and the Y needs to be replaced by the partition designation.

Look back at post #19 or my semi-condensed version:

*****************************

```
sudo mount /dev/sdXY /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sdX
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

**Only if "grub-install /dev/sdX" fails you should also run "grub-install --recheck /dev/sdX"**!

**********************************************

Well, I'm tired :p

Have I totally confused you?

The short answer is that you can always fix grub much faster than you can reinstall an OS!

By this time tomorrow I should know more about how grub2 in Maverick is effected by device designation changes, but it requires time and I'm attending some tax prep classes right now :D

One last thing, if you establish an internet connection on an Ubuntu Live CD you can also restore a Windows MBR by simply running two commands:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sdX mbr
```

Again the X must be replaced with the proper drive designation (eg: a or b).

Now you can shoot me :lolflag:

---

### Post by HaHa Sandman on 2011-01-05
> **kansasnoob said:**
> First of all just know I've not abandoned you

I know, I've bin following that link and read everything in it since post 25 ;)

I'll still wait a few days before proceeding, just to be sure no "negative" posts will pop up.

Besides i need to understand what tgm4883 meant in post 20. Overall i understood pretty much whats this swapping thing and that it might not be such a big dilemma as we thought. I just need to find out what do those "short words" stand for. "UDEV / UUID" and other. I'll try google.

BTW

All that testing you're doing on you're PC that i've read in the other thread, i hope it's not just for me, i feel bad now for giving you such a hard time figuring why this is happening...

---

### Post by kansasnoob on 2011-01-05
Well, I completed my test:

[http://ubuntuforums.org/showpost.php?p=10319652&postcount=23](http://ubuntuforums.org/showpost.php?p=10319652&postcount=23)

I'm now fairly confident that your ability to boot will not be effected by those drive designations changing after installation.

So, where to install grub? As previously mentioned, since both of your drives have a Windows MBR I can't be certain whether you should install to sda or sdb. And remember here that those designations may change so you always need to run either "sudo fdisk -l" or "sudo parted -l" to be certain which drive is recognized as which.

Anyway, do you know how to access your BIOS? I don't want you to make any changes there, but you should be able to see in BIOS whether the 80GB or 160GB drive is set as the boot drive. It's usually in a section named "Hard disc boot priority".

As I said, make no changes, just look and see. Then when you boot the Live CD see what that drives designation is (either /dev/sda or /dev/sdb). Whichever it is that's where you want to install grub.

Based on my own testing that should be it :)

---

### Post by HaHa Sandman on 2011-01-05
> **kansasnoob said:**
> Well, I completed my test:

[http://ubuntuforums.org/showpost.php?p=10319652&postcount=23](http://ubuntuforums.org/showpost.php?p=10319652&postcount=23)

I'm now fairly confident that your ability to boot will not be effected by those drive designations changing after installation.

So, where to install grub? As previously mentioned, since both of your drives have a Windows MBR I can't be certain whether you should install to sda or sdb. And remember here that those designations may change so you always need to run either "sudo fdisk -l" or "sudo parted -l" to be certain which drive is recognized as which.

Anyway, do you know how to access your BIOS? I don't want you to make any changes there, but you should be able to see in BIOS whether the 80GB or 160GB drive is set as the boot drive. It's usually in a section named "Hard disc boot priority".

As I said, make no changes, just look and see. Then when you boot the Live CD see what that drives designation is (either /dev/sda or /dev/sdb). Whichever it is that's where you want to install grub.

Based on my own testing that should be it :)

First drive that boots is th 80GB one parted in sda/b1 and sda/b5
therefore it should be okay to install Ubuntu & GRUB on the same partition in sda/b5 right?

sda/b1 & sda/b5 (80GB:2)

---------------------------------------------------------------------------

BTW in post #15 you sayd that i shouldn't delete sda/b5 but resize it instead, is that correct? Shouldn't i delete it and make a new one less then 2 GB instead?

> **kansasnoob said:**
> So, where to install grub? As previously mentioned, since both of your drives have a Windows MBR I can't be certain whether you should install to sda or sdb. And remember here that those designations may change so you always need to run either "sudo fdisk -l" or "sudo parted -l" to be certain which drive is recognized as which.

Why do i need to enter those commands when i know witch partition is witch even if the letters swap again i know where to install Ubuntu and GRUB.

The 37GB partition either sda5 or sdb5 i'll always know its the partition with 37GB on it, and the partition Ubuntu and GRUB are installed in.

I think i understood all so far, only want to make sure if it's okay to install GRUB on the same partition where Ubuntu is installed (sda/b5).

I'm sorry for repeating myself like some idiot that cant understand what you write, but i'm used to being a control freak, i don't like things going wild withowt my consent, hope you understand 8-[

---

### Post by kansasnoob on 2011-01-05
> therefore it should be okay to install Ubuntu & GRUB on the same partition in sda/b5 right?

You do NOT want to install grub to a partition. It needs to be installed to the drive itself (either sda or sdb, depending on how the Live CD recognizes the 80GB drive).

> BTW in post #15 you sayd that i shouldn't delete sda/b5 but resize it instead, is that correct? Shouldn't i delete it and make a new one less then 2 GB instead?

You could do that. You should know though that the "installer" screens differ a bit depending on whether you're "changing" or "adding" a partition.

This is typical if you select a partition and click on "change":

[ATTACH]180242[/ATTACH]

This is typical if you select a "free space" and click on "add":

[ATTACH]180243[/ATTACH]

But you should also know that if you delete sdX5 and create a new primary partition rather than a logical partition it'll probably end up being sdX2.

Note: I'm using an X just because I don't know if it should be an "a" or a "b".

> Why do i need to enter those commands when i know witch partition is witch even if the letters swap again

You don't. I'm just kind of anal retentive :p

It's much easier for me to just do things than it is to explain how to do things. Just to recap, and in this example I'll assume that the 80GB shows up as sdb, either delete/create new or resize sdb5, then create a logical SWAP, then **install grub to sdb**.

---

### Post by HaHa Sandman on 2011-01-06
Okay tried installing Ubuntu, had a problem at the beginning since i setted both partitions boot as "/" after it told me that i changed the swaping partitions boot to "swap area" no problem so far.

Problem is tough, i had to install Ubuntu twice, since the first time i think i accidently installed GRUB on the 160GB HDD, how could i be so dumb? It seems after i clicked on sda2 to install it suddenly changed the location to the 160GB HDD or somewhere else...i installed ubuntu, had an error, it worked, rebooted, Ubuntu was undetected, so as GRUB.


Second try - Installed Ubuntu, this time sda became sdb, and after i clicked sdb2 where i wanted to install Ubuntu, GRUB's location changed again to the 160GB HDD, tough this time i was aware and fast changed it to the entire 80GB HDD, installed Ubuntu succesfully, internet connexion seted up succesfully but after installling it and sayd that a reboot is necesarry i got an error, but passed over it with a simple enter, could it have bin because the ULCD was stil in the DVD-RW?

Either ways this is one of the last line of the error i got:

end_request: I/0 error, DEVSR0, sector 537392

Ia this a problem? And is there a way to check where GRUB is installed and if it's installed on multiple hard drives?

BTW a folder called ".Trash-999" appeared on my 160GB HDD, a few pics a INFO folder with some data with the name of the pics. Can i delete this?

At boot The Ubuntu Generic is the one i always should use right? Not the recovery one. I asume the recovery one is something similar to Windows' Safe Mode Recovery.

EDIT:

This OS is INCREDIBLE! It's soooooooooooooo awesome! I can't believe i've wasted 10 years of my life using Windows instead of Linux.

---

### Post by kansasnoob on 2011-01-06
> after installling it and sayd that a reboot is necesarry i got an error, but passed over it with a simple enter, could it have bin because the ULCD was stil in the DVD-RW?

Either ways this is one of the last line of the error i got:

end_request: I/0 error, DEVSR0, sector 537392

That sounds like this known bug (from the release notes):

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

> *I/O error after CD is ejected at end of install. In some cases, ejecting the CD at the end of installation will leave errors on the screen such as: 

end_request: I/O error, dev sr0, sector 437628

these error messages indicate that the system is still trying to access some files on the CD, and are harmless except that they obscure the message asking the user to press Enter to reboot. You can safely remove the CD from the tray and press Enter at this point to reboot to your new Ubuntu system.

Here's the actual bug report:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/539027](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/539027)

> is there a way to check where GRUB is installed and if it's installed on multiple hard drives?


A fresh output from the Boot Info Script would tell us. It would do no harm at all to have grub installed to both sda and sdb, just DO NOT install grub to a partition!

So, you could boot into your installed Ubuntu and run these three commands:

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdb
```

```
sudo update-grub
```

> BTW a folder called ".Trash-999" appeared on my 160GB HDD, a few pics a INFO folder with some data with the name of the pics. Can i delete this?

I don't know, I've never seen that. Does that have something to do with where you saved those screenshots?

> At boot The Ubuntu Generic is the one i always should use right?

Yes. After updating you'll see another new kernel appear, so you'll have both standard and recovery boot options for both kernels 2.6.35-22 and 2.6.35-24 (if I remember the numbers correctly).

It's normally suggested to keep at least one older kernel after a kernel update so you can boot into an older kernel in case of breakage.

I always remove the "memtest" option by running:

```
sudo chmod -x /etc/grub.d/20_memtest86+
```

This is my favorite grub2 guide:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I'd really like to see the output of:

```
sudo parted -l
```

Just to see what you ended up with :D

---

### Post by HaHa Sandman on 2011-01-06
> So, you could boot into your installed Ubuntu and run these three commands:

```
sudo grub-install /dev/sda
``````
sudo grub-install /dev/sdb
``````
sudo update-grub
``` 

[IMG]http://img412.imageshack.us/img412/5813/screenshot2ml.png[/IMG]

> I don't know, I've never seen that. Does that have something to do with where you saved those screenshots?I made some screenshots witch i have not copied from Ubuntu Desktop LCD to another HDD maybe it moved them on /dev/sda automatically so they won't be lost.

> I'd really like to see the output of:

```
sudo parted -l
```Just to see what you ended up with :D

[IMG]http://img810.imageshack.us/img810/6083/screenshot3b.png[/IMG]

BTW

After instalation there's no moe Drive E on Windows and the 37GB /dev/sdb2 (previously sdb5) had disipeared in Ubuntu as well, i can stil find it on ubuntu somewhere under a name like "System File" or something like that, is that a problem?

---

### Post by kansasnoob on 2011-01-06
> After instalation there's no moe Drive E on Windows

That's typical. Windows can't read most Linux file systems.

My only worry is that warning you saw after installing grub to /dev/sda (the 80GB drive) regarding FlexNet using sector 32 of that drive. The warning is very apparent!

Now, since Ubuntu is installed and you can connect to the internet why so many screenshots?

That's a needless use of bandwidth and It's a real pain for those who'd like to help you. It's much better to post info using copy-n-paste and, depending on what you're pasting, using either quote tags or code tags.

I'd have liked to copy-n-pasted that FlexNet error rather than having to type it (because I'm lazy) :p

It appears that may bite you in the a$$:

[http://ubuntuforums.org/showthread.php?t=1643935](http://ubuntuforums.org/showthread.php?t=1643935)

---

### Post by HaHa Sandman on 2011-01-06
> **kansasnoob said:**
> My only worry is that warning you saw after installing grub to /dev/sda (the 80GB drive) regarding FlexNet using sector 32 of that drive. The warning is very apparent!

I have no problems with Ubuntu so far, except with Transmission, it worked until i loaded a torrent in it since then it stopped opening. Uninstalled it and then reinstalled it but same thing, think i'll try Deluge or something else and see if it's just from Transmission or has a connexion with the error i had.

The error, might be ebcause it asked me for my password at first, maybe not, idk.

> Now, since Ubuntu is installed and you can connect to the internet why so many screenshots?

That's a needless use of bandwidth and It's a real pain for those who'd like to help you. It's much better to post info using copy-n-paste and, depending on what you're pasting, using either quote tags or code tags.

I'd have liked to copy-n-pasted that FlexNet error rather than having to type it (because I'm lazy) :p

It appears that may bite you in the a$$:

[http://ubuntuforums.org/showthread.php?t=1643935](http://ubuntuforums.org/showthread.php?t=1643935) 

As far as i know you can't copy & paste from windows command to a text file/browser or vice versa. Tried to copy & paste the commands you gave me in the Terminal but it didn't work, so i had to enter them manually.

You know the problem you keept telling me about lower case l and not capital L? Well the reason it didn't work for me in the past it's because i entered 1 (number) not l (letter), it seems that if you put the command in a ```
 small case l and 1 look the same, go figure :confused:

BTW

Thank you for all you're guidance, time and patience to help me set up my first Linux OS :)

2 questions tough:

1. How do i enter Windows Safe Mode? Before installing GRUB it was just by constantly pressing F8. I don't want to intentionately make errors in windows to have access to SM in windows.

and 2. If i reinstall windows it, will it override GRUB and will i have to re-install it again?

And how about Ubuntu? If i need to re-install it will i have to delete the 2GB swapping partition everytime i do this or just simply re0install to the same partition as before but check to format it first?

Sorry for so many questions.[CODE]
```

---

### Post by kansasnoob on 2011-01-06
> I have no problems with Ubuntu so far, except with Transmission

The focus of this thread is installing/booting Ubuntu. If you have other problems you need to start a new thread in the appropriate section of the forums.

> As far as i know you can't copy & paste from **[COLOR="Red"]windows[/COLOR]** command to a text file/browser or vice versa. Tried to copy & paste the commands you gave me in the Terminal but it didn't work, so i had to enter them manually.

When you say windows do you mean the OS, or "a" window?

Now that you're running Ubuntu you can easily copy-n-paste text from almost anywhere to anywhere. You did it once in post #10 with the Boot Info Script output.

> 1. How do i enter Windows Safe Mode? Before installing GRUB it was just by constantly pressing F8. I don't want to intentionately make errors in windows to have access to SM in windows.

You should be able to enter XP safe mode the same way you always did! The one caveat is that warning regarding "FlexNet using sector 32" of the 80GB drive. I've already posted a link regarding that.

> If i reinstall windows it, will it override GRUB and will i have to re-install it again?

Look back at post #29. It's never necessary to reinstall an entire OS just to fix the MBR! Again that error you saw regarding FlexNet should be your greatest concern!

> If i reinstall windows it, will it override GRUB and will i have to re-install it again?


Again, look at post #29! Yes, if you reinstall Windows you will mess up grub!

> And how about Ubuntu? If i need to re-install it will i have to delete the 2GB swapping partition everytime i do this or just simply re0install to the same partition as before but check to format it first?


Very early on I referenced this:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

In my post #1 there it says:

> Of course SWAP will be used as swap area, but if you already assigned the SWAP using Gparted you’ll find that the installer will use any and all existing SWAP partitions. I multi-boot a lot and quite often have a SWAP on each of two or more drives, so if I don’t want the SWAP on a certain drive to be used with a new installation I simply choose the “do not use this partition” option.

So, no! A default Ubuntu install will use all available SWAP space.

I'm now removing this thread from my subscriptions. At some point you need to do a bit of work on your own ):P

---

