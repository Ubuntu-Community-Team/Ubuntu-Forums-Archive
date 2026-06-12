---
title: "Ubuntu 14.04 not booting (Alert, dropping to shell (initramfs))"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by captaingraviton on 2014-06-12
Hello Ladies & Gents,

Found myself in a soggy quagmire, I wonder if anyone would be kind enough to throw me a line?

My Ubuntu 14.04 64bit system has been working perfectly well until yesterday morning when I tried to boot it up and these lines of horror greeted me..

```

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/efe24220-9569-4e7b-8fof does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a lost of built-in commands.
(initramfs)
```

I tried the trick wherein one holds down the shift key and tries to boot into another kernel, but I tried them all and they don't work.
There are two SATA hard drives, the second data drive just has user files on it, the first main one has Ubuntu. 
I tried unplugging the second data drive - no difference.

I'm currently dancing naked around the machine trying to evoke the Gods Of Ubuntu, if that doesn't work, can you suggest anything?

---

### Post by Bashing-om on 2014-06-12
captaingraviton; Hi ! Welcome to the forum .

Most likely that the boot code has become corrupted - for who knows why or how. I have high doubts that any dance or incantations will prove effective to lead to a resolution; does not hurt to try, and a better frame of mind could result.

Rather than relying on 'faith' let's do the 'scientific' method.
Let's prepare to (re-)install grub, 1st let's make sure that all points to the correct places and designations. We want to look at what the files system is directing to be mounted. 
Boot the liveDVD and;
Post back the outputs - between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
once these are known we will take a look at the File System TABle ( /etc/fstab) file from that liveDVD and if all looks proper will proceed to (re-)install grub.

We could take a wild stab at the heart of the matter, but I would, in this instance, make sure the file system knows what it is talking about.

Booting, from point a to point b to point d
[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-12
This is good. I prefer the scientific method too!

I had to go download and burn a current Ubuntu 14.04 LiveDVD because I had previously (about five weeks ago) upgraded from Ubuntu 11 to 12 to 14 via the terminal. Might this be why I'm having issues? Even still, it's been working just fine until now. 

Anyway, here's the output from the code you suggested...


```

 sudo fdisk -lu

(nothing)


```

```

sudo parted -l

Warning: Unable to open /dev/sr0 (Read-only file system). /dev/sr0 has been opened read-only.
Error: Can't have a partition outside the disk!

```

```

sudo blkid

/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Ubuntu 14.04 LTS amd64" TYPE="iso9660"

```

What does that lot tell you?

---

### Post by Bucky Ball on 2014-06-12
Welcome. It tells us, quite eerily, nothing. There appears to be something drastically wrong if you have two hard drives in there ...

The first command Bashing-om gave you to try should have listed all your partitions on both drives.

* This might give some clues as it sounds similar to what's happening.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

I suggest booting from a LiveDisk/USB, get to a desktop and launch Gparted. If it shows 'unallocated space' then your issue is pretty close to the one on that thread, or at least in the ball park.

---

### Post by captaingraviton on 2014-06-12
Gparted, via the liveDVD, had a little scan and says "No devices detected" at the bottom. 

Gulp. I've got that cold feeling creeping up to my neck from the back of my underpants...

---

### Post by Bashing-om on 2014-06-12
captaingraviton; Yuk !

That tells me that there is no file system on those hard drives ! Which I find very hard to believe ( a total lack of faith ).
Something along these lines should have been the result:
```

sysop@1310mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux
sysop@1310mini:~$ 

``` where I have 3 disks and 4 'buntus installed.

Humm .. OK, So what is going on here ?

Boot the liveDVD, as soon as the bios screen clears depress and hold the right shift key -> language screen; escape key to accept the defaults -> boot options screen;

Choose "check disk for defects", will take a while to make the checks and prompt for a re-boot.
Upon that return from the re-boot -> boot options screen -> "try ubuntu" -> desk top
ctl+alt+t to get a terminal. What now results from:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
still with no output ? Houston we have a problem !...
from the dash ( top icon on the launcher at the left side of screen -> enter the term gparted -> partition editor. Provide us a screen shot of both the hard drives ( top right of the GParted screen to select) to have a picture of what is.

[INDENT][INDENT]boy oh boy
[INDENT][INDENT][INDENT]what do we not have here 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-06-12
I suggest following the fix on the link I provided and using fixparts to realign the partitions. It is a few scroll rolls down the page.

---

### Post by Bashing-om on 2014-06-12
@ Bucky Ball; Great resource - had completely slipped my mind !
( see that is why you get paid the big bucks ).

@ captaingraviton; When you get done with all the aboves and "fixparts" as well... do not write anything to those disks - if you have data that needs to be saved !- 
Next in line is 'testdisk' to try and salvage the data.

We are awaiting an update on your status/situation.

[INDENT][INDENT][INDENT]Oh Boy, Time and effort !
[/INDENT][/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-12
@Bashing-om: Okay, well I rebooted the LiveDVD and held the right shift key, chose "Check disks for defects" and after a while it said "No errors found" (!?) then, pressed a key to reboot again into the LiveDVD Ubuntu Desktop, opened terminal, same commands, same outputs as before, opened Gparted, same as before "no devices found".*screenshot below*

@Bucky Ball: I'll see what Bashing-om has to say and I'l start reading through your link. Frankly all those words terrify me. I'll try and be brave...

[IMG]http://i62.tinypic.com/2it0siv.png[/IMG]

---

### Post by Bashing-om on 2014-06-12
captaingraviton; UnGood for the home team.

OK, time to read Bucky Ball's link -> fixparts, see what it relates.
Then IF there is data to be salvaged.. consider 'testdisk'......
Else: see what results with a clean (RE-)install of ubuntu 14.04 in the default install - let the install wizard do it's thing.
IF that default install goes well, we can think about getting creative with the disk(s) partitioning -> and (RE-)(RE-)install.

Your call, only you know what was on those disk(s), and what needs salvaging.

(re-)install: Windows prefers to be the 1st operating system installed - IF this is to be a dual boot with Windows situation on the same hard drive. Sure saves some effort and grieve with the boot code.
I do recommend, though, as there are 2 hard disks; Windows only on the 1st hard drive, and ubuntu 14.04 on that second hard drive, boot to that second hard drive, and chainload Windows onto grub ( GRand Unified Bootloader).

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-12
The machine is a dedicated Ubuntu machine (I'm sick of Windows). 

I'll delve into all this tomorrow and update you both with how I get along. You've been really really helpful, thanks a tonne!

---

### Post by Bashing-om on 2014-06-12
k
\0/ ........

---

### Post by captaingraviton on 2014-06-13
Sorry, I'm trapped at the very first hurdle. With regard to the page: [http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html) it reccommends that I first back up my current partitions. 

So, I've got an Ubuntu destop via the Ubuntu LiveDVD and in a terminal I type in:

```

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sdc > parts.txt

```

and the response is..

```

/dev/sdc No such file or directory

sfdisk: Cannot open dev/sdc for reading

```

I'm guessing that (a) my drive can't been seen and so there's no point in trying the fdisk backup thing? and (b) I probably wrote down the wrong address for it and it's called dev/*something else*?

I'll just add one bit of information that I don't *think* will make a difference; I've unplugged the second SATA drive in my machine, the one I just used for data, not the main one that had ubuntu on it. 

What am I doing wrong (besides e-v-e-r-y-t-h-i-n-g!)?

---

### Post by captaingraviton on 2014-06-13
Oh, also, I went to the download page for FixParts at [Sourceforge]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.8/fixparts-binaries/") and clicked on the file "fixparts_0.8.8-1_amd64.deb" and tried to open that. I'm still in the Ubuntu LiveDVD. The Ubuntu Software Center opens up with an option to "upgrade" (as opposed to install) but then it tells me off by warning me that the "Package is of bad quality". I cancelled the install. 

Obviously I'm fumbling around like a blind man at a landmine testing facility.

---

### Post by Bucky Ball on 2014-06-13
So how many drives have you got in there now? If you're running from the Live boot, open Gparted and see what the name of the partition you're trying to fixpart. Once you know that, try the commands again. If there's only one drive in there, it's probably sda. Check with Gparted.

---

### Post by captaingraviton on 2014-06-13
I'm just running the single main SATA HDD that [is supposed to/did have] Ubuntu 14.04 on. I unplugged the second drive I was using just for data storage to try to keep things simple. But because Ubuntu won't boot from the main HDD I'm having to boot from a LiveDVD. In the liveDVD Ubuntu, Gparted tells me that "No devices detected" (but there is one plugged in).

A friend lent me her Spinrite 6.0 disk and we let it perform a maintainance scan (3 hours!) It didn't find any errors. Interestingly it did identify some specifics of the HDD that is plugged in. 

These are:

```


Drive 0 Add On / Master
 - Gap - unpartitioned space
Part 1 Linux native
 - Gap - unpartitioned space
Part 2 Linux swap
 - Gap - unpartitioned space

```

and 

```

bios support: extended "int13"
bios drive num: 80h
cyls/hds/secs: 1,024 / 255 / 63
sector count: 160,086,528
total bytes: 81,964,302,336

hardware addrs: C480=C487, C402
hardware irq: 5
address style: lba-assist trans
drive sectors: unknown
determined by: bios extentions

32-bit xfers: yes, now in use
dma channel: no, fast PIO mode

```

Does that tell you anything?

---

### Post by Bashing-om on 2014-06-13
captaingraviton; Hey,, 

In my role as "teacher": We are in that realm 'beyond the point click arena" and the learning curve is steep.
Hard disk nomenclature in linux:
1st hard drive that the system recognizes is 'sd[color=blue]a[/color]'
2nd disk is sd[color=blue]b[/color]
3rd disk is sdc :
On these hard disk are slices called "partitions" that are identified by number:
sda1 is that 1st hard drive and the 1st partition
sda5 is that 1st hard drive and the 5th partition
sdc8 would be that 3rd hard drive and the 8th partition on that disk

So how do we know what the system has assigned as the nomenclatures ?
The 2 primary commands to know are:
```

sudo fdisk -lu
sudo blkid

``` It is left as an exercise for the student to see the relationship of UUIDs to device names (sda, sda1, sdc5 ).

In this instance the requirement is to copy some data from a hard disk. We need to know what the device name is as the system knows it:
```

sudo fdisk -lu ## yeah yeah, the partition table is all hosed up and you get no output #

```
but, all we want to know is the identifier - as it is also possible that the usb thumb drive got recognized first by the system and got the name 'sda'. However, generally speaking, with no exterior devices connected to the system that 'sda' is the 1st interior hard drive . - with no other hard drives connected this then 'sda' becomes the drive we are working to pull the data off of (if possible).
At this point I do not know that the 1st hard drive will need to be explicitly mounted ( attached to the file system) .

OK, back to the subject at hand: 'sfdisk'
Let's presume that you have positively identified the hard drive as "sda", thus the command would be:
```

sudo sfdisk -d /dev/sda > parts.txt

```
I would not be amazed if the system can not comply, because, the target device is not mounted .. then again these utilities are real smart and may figure it out on their own.
The command will output the info to a text file "parts.txt" at the location of your "Present Working Directory" (PWD) which in this case is the /home directory of the liveDVD. This file will not persist a reboot as the medium is not write-able. copy/save that file to an external medium ( thumb drive).

OH, how do you do that in ubuntu, you ask ...???
Back to square 1, what is the identifier of the thumb drive, again one way to know is terminal command "sudo fdisk -lu";
OK.let's attach the thumb drive to the system's file structure > Let presume the thumb drive has the identifier 'sdb' and that the "data storage" is the 1st partition. then:
```

sudo mkdir /mnt/work ## to make us a place to attach to the file system
sudo mount /dev/sdb1 /mnt/work ##the file system (partition # 1) is attached
cp -p parts.txt /mnt/work ##to copy that file from the PWD to the destination
ls -la /mnt/work/parts.txt ## to verify that the job is done, the file exist where expected
sudo umount /mnt/work ## we manually attached that partition, we MUST tell the system we are all done so the system clears all resources
## devoted to an open file and closes things out gracefully. Real bad things "could" happen if you do not tell the system what you are doing
## ( umount - all done !).##

```
Else, hey there is the GUI way, that does all this for you ,,, open 2 instances of the file manager and drag and drop the file .. still when done tell the system you are done by clicking on "unmount" or maybe the label is "eject".

In any event you now have the file parts.txt safely tucked away.

Proceed on to the next .. and let's see what is.

---

### Post by captaingraviton on 2014-06-14
Thanks Bashing-om,

I read through all that and it was nice to get some clarity where before I only *thought* I knew what I was refering to. 

However, once again, I boot into my Ubuntu LiveDVD and try the commands you suggest in a terminal. Once again the responses are thus:

```

ubuntu@ubuntu:~$ sudo fdisk -lu

(*nothing happens*)

```


```

ubuntu@ubuntu:~$ sudo sfdisk -d dev/sda > parts.txt
/dev/sda: No such file or directory

```

^^Note, I tried the above on /dev/sda1, /dev/sdb and /dev/sdb1 with the same results.

```

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" /dev/sr0: LABEL="Ubuntu 14.04 LTS amd64" TYPE="iso9660"

```

*******************

I had a snoop around in my BIOS settings and I noticed that my BIOS does see the HDD drive plugged in "Maxtor SATA" (I forget the rest) so that might serve as another clue Sherlock?

*******************

---

### Post by Bucky Ball on 2014-06-14
Your BIOS will see the drive fine, but that has nothing to do with this. Things are in a bad way if that is all 'sudo blkid' has to say. You should be getting something like this:

```
/dev/sda1: LABEL="System" UUID="3E10BBBF10BB7C89" TYPE="ntfs" 
/dev/sda2: LABEL="S3A8406D004" UUID="7060EA3E60EA0B24" TYPE="ntfs" 
/dev/sda4: LABEL="HDDRECOVERY" UUID="8AD8245BD82447B1" TYPE="ntfs" 
/dev/sda5: LABEL="10.10" UUID="93f00b46-2cf5-4b46-83be-f708cf831675" TYPE="ext4" 
/dev/sda6: LABEL="home" UUID="0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1" TYPE="ext4" 
/dev/sda7: UUID="63d86782-bff4-41c1-924f-37d093fbe371" TYPE="swap" 
/dev/sda8: LABEL="12.04" UUID="7343d254-e594-4593-8258-3ecebdb376ef" TYPE="ext4" 
/dev/sda9: LABEL="Misc" UUID="6B8E2F2A62CEE191" TYPE="ntfs" 
/dev/sda10: LABEL="TrustyMini" UUID="40c1d59b-20a7-4096-8cc4-fd65e0a1fb93" TYPE="ext4" 
/dev/sda11: LABEL="LFS" UUID="8d597f7e-8c90-4b59-8ab5-862dec0593bd" TYPE="ext4" 
/dev/sda12: LABEL="Mini" UUID="865e6caa-b7bf-49b5-8d41-bf7e8d03be32" TYPE="ext4" 
/dev/zram0: UUID="ecf1b91f-1c55-4c96-88ff-ae40aef1e38d" TYPE="swap" 
```

That is the output of 'sudo blkid' on my machine, listing all partitions. In other words, I'd be tempted to start again. Something is well screwed up. Gparted sees nothing and neither does blkid. You're getting no results when trying to work with sda or sdb, so ...

Things look grim ...

---

### Post by captaingraviton on 2014-06-14
Even though I'm accessing a terminal in a LiveDVD? 

What if I tried those commands in the GRUB shell? (I think that's what comes up when it tries to boot normally)

---

### Post by Bucky Ball on 2014-06-14
> **captaingraviton said:**
> Even though I'm accessing a terminal in a LiveDVD? 

What if I tried those commands in the GRUB shell? (I think that's what comes up when it tries to boot normally)

Yea, right. Forgot ... again! Yes, boot normally to the grub shell and try it. ;)

---

### Post by captaingraviton on 2014-06-14
Okay, right. No, I see, that doesn't work either.

Oh hello Square One old friend...

---

### Post by captaingraviton on 2014-06-14
In my desperation, I'm looking at this page [Linux: How to Rescue a Non-booting GRUB2 On Linux]("http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux") 

It suggests trying the following code (in the GRUB shell) and it returns the following result:

```

grub> ls
(hd0) (hd0,msdos5) (hd0,msdos1)
```

So then I try:

```

grub> ls (hd0)
error: disk 'hd0' not found

```

Balls! So then I try..

```

grub> ls (hd0,msdos5)
partition hdo,msdos5: No known filesystem detected - Partition start at 71656448KiB - Total size 8386560KiB 

```

Oh? Sort of bad news, but then again, it's reading *something* there, isn't it? Let's try:


```

grub> ls (hd0,msdos1)
partition hdo,msdos: Filesystem type ext* - Last modification time 2014-06-08 08:45:14 Sunday, UUID efe24220-9569-4e7b-8f0f-ce6e0342a1be - Partition start at 1024KiB - Total size 71654400KiB

```

So, does *that* tell us anything helpful?

***********************
Two other questions:


[LIST=1]
[*]Could my problem be related to this [bug in grub]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1292628")? 
[*]In your opinion(s) do you think that [Boot-Repair]("http://sourceforge.net/projects/boot-repair/") will be worth trying? 
[/LIST]

---

### Post by Bucky Ball on 2014-06-14
> **captaingraviton said:**
> 
[*]In your opinion(s) do you think that [Boot-Repair]("http://sourceforge.net/projects/boot-repair/") will be worth trying? 
[/LIST]

I was just about to suggest it, but see here first:

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

There are two ways of going about it. If you can get an internet connection when booting from the LiveDVD/USB then you can install it and run it there rather than having to create a Boot Repair CD.

---

### Post by Bashing-om on 2014-06-14
captaingraviton; Yukkie some more.

It is good to see that you are doing your homework.

Well, there is "something" there, but from the indications so far - not enough to work with. It is my thought that trying to repair the file system will only compound the problem.
If there is data to be salvaged it is now time for 'testdisk':
From the liveDVD ( that will not survive a reboot ):
```

sudo apt-get install testdisk

```

A better option might be to down load and burn the testdisk CD:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

Loads of tutorials on how to apply 'testdisk' - Google search term "testfisk ubuntu". I have had no complaints from these tutorials:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

A "somewhat" similar situation for reference:
[http://ubuntuforums.org/showthread.php?t=2112112](http://ubuntuforums.org/showthread.php?t=2112112)

Else: Well, if the data is not worth the trouble to try and save. Start all over from scratch and format the hard drive. Install ubuntu and be done with it.

[INDENT][INDENT]if when you do not succeed 
[INDENT][INDENT][INDENT]try something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-14
*salutes*

Leave it with me, I'll report back tomorrow.
(and THANKS!)

---

### Post by captaingraviton on 2014-06-15
So, we are due an update, although I'm not finished, this is Part One:

So I made myself a Boot-Recovery LiveCD and booted that, just to look at it before I did the testdisk thing (which will be Part Two). I had a little click around and made a report on my drive. It told me to post this link:

[http://paste.ubuntu.com/7648256](http://paste.ubuntu.com/7648256)

Interesting in that it seems to see my devices and partitions? WHen I clicked back to the desktop, the program had vanished, so I looked for it from the "start" menu, found it, but also noted there was a copy of gparted on it too, so I fired that sucker up and, surprisingly, I saw my devices and partitions. I took a photo with my phone (see attachment).

I've left it at that and I'm making a BootMed LiveCD (I've used BootMed before and it's on the list you recommended as having testdisk facility on it) so testdisk is next.

Just keeping you updated.

---

### Post by Bashing-om on 2014-06-15
captaingraviton; Hey, Hey ...

That last outputs are encouraging ! .. 
Bet now ( change in heart ) that 'testdisk' can recover the partitions...
Might also be quicker and easier to take a look and see what the "backup" partition tables look like .. and perhaps - if they look good - roll one of the backups into place [superblock that is ] (??).
[http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756)
That link, as there is no point in re-inventing the wheel and slickymaster has done a good job of it.

[INDENT][INDENT]a better light shines
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-06-15
Please attach large pics rather than inserting them in the body of your post (see post #27 for example). This can be done using 'Adv Reply' and then the paperclip icon. Thanks.

---

### Post by captaingraviton on 2014-06-16
Update Part Two:


I'll spare you exactly all of  the gory details because, frankly, yesterday I went down a lot of  cul-de-sacs, but I've ended up booting into a Debian Rescue Disk (Debian  Wheezy?). For one reason or another, the solution I was going for ended  up fruitless again, but I did check the terminal and tried all the  previous tricks like before (all to no avail). I then thought I'd have a  look for gparted to see if it could see any goodies, but this distro  doesn't have it, it has "Disk Utility" and in it, it sees all! 


Now at this point I should have made a post, but I took a  gamble and used the ap to mount my drive, then I tried those recommended  commands in a terminal again. Look what happened!


 ```


user@debian:~$ sudo fdisk -lu

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000112f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   143310847    71654400   83  Linux
/dev/sda2       143312894   160086015     8386561    5  Extended
/dev/sda5       143312896   160086015     8386560   82  Linux swap / Solaris
user@debian:~$ sudo parted -l
sudo: parted: command not found
user@debian:~$ sudo blkid
/dev/sda1: UUID="efe24220-9569-4e7b-8f0f-ce6e0342a1be" TYPE="ext4" 
/dev/sda5: UUID="026b3f08-6d17-4249-9d32-26fa84b940c1" TYPE="swap" 
/dev/sr0: LABEL="Debian wheezy 20140505-04:14" TYPE="iso9660" 
/dev/loop0: TYPE="squashfs" 
user@debian:~$ 


```


I'm on a roll! Straight to tesdisk.  I have to install it. Then I realise I have to use it as root (and I  saw a 'root terminal' as an option in the applications menu) lo and  behold, it shows my Hard Disk sda! So I run a deep scan and this is what  it tells me...


```

Disk /dev/sda - 81 GB / 76 GiB - CHS 9965 255 63

     Partition                  Start        End    Size in sectors

 1 * Linux                    0  32 33  8920 175 23  143308800
 2 P Linux Swap            8920 207 56  9964 227 39   16773104


```


I then do a deeper search...


```

Disk /dev/sda - 81 GB / 76 GiB - CHS 9965 255 63

The harddisk (81 GB / 76 GiB) seems too small! (< 110 GB / 102 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
   Linux                 4460 217 46 13381 105 36  143308800
   Linux                 4462  65 20 13382 208 10  143308800
   Linux                 4467  25 39 13387 168 29  143308800
>  Linux                 4468 160 45 13389  48 35  143308800
   Linux                 4470 138 21 13391  26 11  143308800
   Linux                 4471  13 23 13391 156 13  143308800


```


Hmmm?


I'll now look into that link you sent regarding superblocks. <gulp>


 CG

---

### Post by Bashing-om on 2014-06-16
captaingraviton; Hey;

For sure no longer looks hopeless... I bet if the partition table were restored .. either from 'testdisk' of with 'e2fsck', all will be better in our world.

Looks like the data is still there, just need some pointers established to get to the data ! huh ?

We are in this deep, may as well do some reading to fully understand the situation and a good means to reach a solution:
[http://linux.sys-con.com/node/117909?page=0,0](http://linux.sys-con.com/node/117909?page=0,0)

[INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-16
Thanks, I'll read up and update.

*heart swells with hope*

---

### Post by captaingraviton on 2014-06-23
Sorry for the delay, problems building up, been away for the weekend etc.

Okay, this is all equally confusing, frustrating and exciting at the same time.
I've managed to get a stable set-up with a Debian liveCD, I can see in GParted
 my HDD and the way it's set up..

[ATTACH=CONFIG]254182[/ATTACH]

I open up a terminal, I install testdisk, run as a root user (otherwise it doesn't see
 my drive /sda) and there it sees my drive..

[ATTACH=CONFIG]254178[/ATTACH]

I do a quick search, then a 'deeper search' by pressing 'continue'...

[ATTACH=CONFIG]254179[/ATTACH]

It chugs along for ten minutes or so and then this screen shows..

[ATTACH=CONFIG]254180[/ATTACH] 

...at this point, I'm at a fork in the road and don't know what to do
 for the best, so I'll take any advice?

CG

---

### Post by Bashing-om on 2014-06-23
captaingraviton; Hey,

I presently do not know what to advise as GParted sees the extended partition and the contained swap partition just fine; but, I see that test disk sees that swap partition as a primary partition (??).  Test disk is not even seeing the extended partition and is looking at the swap partition as 'sda2'. I have no idea as to how that can be.
I do perceive a partition alignment situation .. I expect the 1st partition to begin at sector 2048 and not at sector 0 - some one correct me if I am in error, but is not the start of the hard drive reserved for system usage ?

Let's see if we can get a look at 'sda1' and what files are on that partition. Looking can not hurt a thing so long as we do not write anything to that disk.
look'n:
From the liveDVD -> terminal commands:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -la /mnt/work
ls -la /mnt/work/home
ls -la /mnt/work/home/<your_user_name>

```
When all done looking around, seeing what might be possible to copy off directly, the mounted file system must be unmounted:
```

sudo umount /mnt/work

```

As to testdisk recovery, It is advised never to work from that original disk, rather work off of a copy of the disk that has been imaged from that original. I do not have the experience myself to advise on the procedure to re-align the partition boundries; so we are flying here by the seat of our pants.

Stranger and stranger --- what to believe ?
[INDENT]what I would do in this situation
[/INDENT]

---

### Post by captaingraviton on 2014-06-23
Thanks for the help again Bashing-om,

Here's the results of the commands you suggested..

```

user@debian:~$ sudo mkdir /mnt/work
user@debian:~$ 
user@debian:~$ sudo mount /dev/sda1 /mnt/work
user@debian:~$ ls -la /mnt/work
total 148
drwxr-xr-x  25 root root  4096 Jun  8 08:37 .
drwxr-xr-x   3 root root    60 Jun 23 20:59 ..
drwxr-xr-x   2 root root  4096 May 17 14:27 bin
drwxr-xr-x   4 root root 12288 Jun  8 08:40 boot
drwxr-xr-x   2 root root  4096 Mar 29  2012 cdrom
drwxr-xr-x   5 root root  4096 Oct 12  2011 dev
drwxr-xr-x 174 root root 12288 Jun  8 20:49 etc
drwxr-xr-x   3 root root  4096 Mar 29  2012 home
lrwxrwxrwx   1 root root    33 Jun  8 08:37 initrd.img -> boot/initrd.img-3.13.0-29-generic
lrwxrwxrwx   1 root root    33 May 27 11:35 initrd.img.old -> boot/initrd.img-3.13.0-27-generic
drwxr-xr-x  26 root root  4096 May 17 14:27 lib
drwxr-xr-x   2 root root 12288 May 17 13:20 lib32
drwxr-xr-x   2 root root  4096 May 17 14:27 lib64
lrwxrwxrwx   1 root root    36 May 16 21:40 libnss3.so -> /usr/lib/x86_64-linux-gnu/libnss3.so
drwx------   2 root root 16384 Mar 29  2012 lost+found
drwxr-xr-x   4 root root  4096 May 17 15:04 media
drwxr-xr-x   2 root root  4096 Oct  9  2011 mnt
drwxr-xr-x   5 root root  4096 Feb  1  2013 opt
drwxr-xr-x   2 root root  4096 Oct  9  2011 proc
drwx------  20 root root  4096 Jun  4 11:27 root
drwxr-xr-x   2 root root  4096 May 27 11:35 .rpmdb
drwxr-xr-x   7 root root  4096 Oct 12  2011 run
drwxr-xr-x   2 root root 12288 May 22 12:51 sbin
drwxr-xr-x   2 root root  4096 Oct 12  2011 srv
drwxr-xr-x   2 root root  4096 Jul 14  2011 sys
drwxrwxrwt   9 root root 12288 Jun 15 18:54 tmp
drwxr-xr-x  11 root root  4096 Mar 29  2012 usr
drwxr-xr-x  14 root root  4096 May 17 08:38 var
lrwxrwxrwx   1 root root    30 Jun  8 08:37 vmlinuz -> boot/vmlinuz-3.13.0-29-generic
lrwxrwxrwx   1 root root    30 May 27 11:35 vmlinuz.old -> boot/vmlinuz-3.13.0-27-generic
user@debian:~$ ls -la /mnt/work/home
total 32
drwxr-xr-x  3 root root  4096 Mar 29  2012 .
drwxr-xr-x 25 root root  4096 Jun  8 08:37 ..
drwxr-xr-x 94 user user 20480 Jun  8 08:46 stu
user@debian:~$ ls -la /mnt/work/home/stu
total 8596
drwxr-xr-x 94 user user   20480 Jun  8 08:46 .
drwxr-xr-x  3 root root    4096 Mar 29  2012 ..
drwxrwxr-x  2 user user    4096 Dec 29  2012 .acetoneiso
drwx------  3 user user    4096 Mar 29  2012 .adobe
drwxrwxr-x 11 user user    4096 May 28 14:12 apps
drwxrwxr-x  3 user user    4096 Dec 24  2012 .appwork
drwx------  2 user user    4096 Apr 23 16:42 .aptitude
drwxrwxr-x  2 user user    4096 Apr 21 16:19 .armory
-rw-rw-r--  1 user user     183 May  9  2013 .asunder
drwxrwxr-x  4 user user    4096 May  8 12:27 .audacity-data
drwxr-xr-x  2 user user    4096 May  8 13:33 Audio
drwxrwxr-x  2 user user    4096 Dec 29  2012 Audiobooks
-rw-------  1 user user    9493 Jun  4 12:28 .bash_history
-rw-r--r--  1 user user     220 Mar 29  2012 .bash_logout
-rw-r--r--  1 user user    3353 Mar 29  2012 .bashrc
drwxrwxr-x  5 user user    4096 Nov 15  2012 .bitpim-files
drwx------ 50 user user    4096 Jun  8 20:41 .cache
drwxr-xr-x 13 user user    4096 Aug 28  2012 .cddbslave
drwxrwxr-x  6 user user    4096 Mar 29  2013 .clamtk
drwx------  3 user user    4096 May 17 13:09 .compiz
drwxrwxr-x  3 user user    4096 Mar 29  2012 .compiz-1
drwx------ 58 user user    4096 Jun  4 12:35 .config
drwx------  3 user user    4096 Mar 29  2012 .dbus
drwxr-xr-x  4 user user    4096 Jun  7 20:04 Desktop
-rw-rw-r--  1 user user     165 Aug  8  2013 .devede
drwxr-xr-x  3 root root    4096 Apr 24 14:37 .distlib
-rw-r--r--  1 user user      26 May 17 13:09 .dmrc
drwxr-xr-x  2 user user    4096 May 29 13:52 Documents
drwxrwxrwx  2 user user   12288 May 28 15:23 Downloads
drwx------  4 user user    4096 Jun  8 16:09 .dropbox
drwx------ 10 user user    4096 Jun  8 08:47 Dropbox
drwxr-xr-x  7 user user    4096 May 20 00:40 .dropbox-dist
drwx------  2 user user    4096 May 17 08:40 .dropbox-master
drwxr-xr-x  2 user user    4096 Aug 10  2012 .eBook-speaker
-rw-rw-r--  1 user user     481 Aug 10  2012 .eBook-speaker.rc
-rw-------  1 user user      16 Mar 29  2012 .esd_auth
-rw-r--r--  1 user user     179 Mar 29  2012 examples.desktop
-rw-r--r--  1 root root   15140 Mar 29  2012 .face
-rw-rw-r--  1 user user 7970835 Apr 11  2013 Firefox_wallpaper.png
drwxr-xr-x  2 user user    4096 May 17 00:40 fontconfig
drwxr-xr-x  2 user user   12288 May 17 00:40 .fontconfig
drwxrwxr-x  5 user user    4096 Jul 30  2013 FrostWire
drwxrwxr-x  8 user user    4096 Aug  2  2013 .frostwire5
drwx------  5 user user    4096 Jun  8 08:46 .gconf
drwx------  4 user user    4096 Mar 29  2012 .gegl-0.0
drwxr-xr-x 22 user user    4096 Jul  9  2012 .gimp-2.6
drwxr-xr-x 24 user user    4096 Mar  8 14:18 .gimp-2.8
-rw-r-----  1 user user       0 Jun  8 09:14 .gksu.lock
drwx------  4 user user    4096 Jun  8 08:44 .gnome2
drwx------  2 user user    4096 Mar 30  2012 .gnome2_private
drwx------  3 user user    4096 May 18 10:02 .gnupg
drwxrwxr-x  3 user user    4096 Feb 26  2013 .goldendict
drwx------  5 user user    4096 Mar 10 12:31 .googleearth
-rw-------  1 user user       0 Oct 23  2013 .goutputstream-007M5W
-rw-------  1 user user       0 Sep 16  2013 .goutputstream-07BK3W
-rw-------  1 user user       0 Sep  4  2013 .goutputstream-0NF42W
-rw-------  1 user user       0 Oct 28  2012 .goutputstream-0T5XMW
-rw-------  1 user user       0 May  2  2013 .goutputstream-0WMUWW
-rw-------  1 user user       0 Oct 11  2013 .goutputstream-0X1Z4W
-rw-------  1 user user       0 Jun 18  2013 .goutputstream-14M4YW
-rw-------  1 user user       0 Mar  4 21:52 .goutputstream-1B80BX
-rw-------  1 user user       0 Jun 29  2013 .goutputstream-1C05YW
-rw-------  1 user user       0 Nov 16  2012 .goutputstream-1CDZNW
-rw-------  1 user user       0 Jan 20  2013 .goutputstream-1CI9QW
-rw-------  1 user user       0 Aug 14  2013 .goutputstream-1Q4Q1W
-rw-------  1 user user       0 Mar  1 22:30 .goutputstream-1YWZBX
-rw-------  1 user user       0 Mar  5  2013 .goutputstream-1Z9ITW
-rw-------  1 user user       0 Aug 24  2012 .goutputstream-2CQTJW
-rw-------  1 user user       0 Jul  8  2013 .goutputstream-2H8QZW
-rw-------  1 user user       0 Feb 15 21:32 .goutputstream-2JOZAX
-rw-------  1 user user       0 Sep  2  2012 .goutputstream-2O73JW
-rw-------  1 user user       0 Aug 14  2012 .goutputstream-2XF7IW
-rw-------  1 user user       0 Dec  1  2012 .goutputstream-2XVBOW
-rw-------  1 user user       0 Mar  6 21:44 .goutputstream-2XWBCX
-rw-------  1 user user       0 Jan 27 21:06 .goutputstream-2YEMAX
-rw-------  1 user user       0 Apr 23 21:00 .goutputstream-385OEX
-rw-------  1 user user       0 Jan 30 20:31 .goutputstream-3EZ39W
-rw-------  1 user user       0 Aug 19  2012 .goutputstream-3IXIJW
-rw-------  1 user user       0 May 19  2013 .goutputstream-3MSJXW
-rw-------  1 user user       0 Sep  8  2013 .goutputstream-3QD22W
-rw-------  1 user user       0 May 24  2013 .goutputstream-3QEDXW
-rw-------  1 user user       0 May 20  2013 .goutputstream-3S00WW
-rw-------  1 user user       0 Nov 30  2012 .goutputstream-3ZQFOW
-rw-------  1 user user       0 Nov 23  2012 .goutputstream-40P6NW
-rw-------  1 user user       0 May 11  2012 .goutputstream-4FJ6DW
-rw-------  1 user user       0 Oct 26  2013 .goutputstream-4GAM5W
-rw-------  1 user user       0 May 17  2013 .goutputstream-4WXIXW
-rw-------  1 user user       0 Apr 25  2013 .goutputstream-4XKRVW
-rw-------  1 user user       0 Oct 13  2013 .goutputstream-52DV4W
-rw-------  1 user user       0 Oct 26  2012 .goutputstream-52ZVMW
-rw-------  1 user user       0 May 14 22:59 .goutputstream-5BK2FX
-rw-------  1 user user       0 Aug 23  2013 .goutputstream-5D8B2W
-rw-------  1 user user       0 Sep 11  2013 .goutputstream-6B182W
-rw-------  1 user user       0 May 27  2013 .goutputstream-6GPZXW
-rw-------  1 user user       0 May 17  2012 .goutputstream-6H5QEW
-rw-------  1 user user       0 Oct  4  2012 .goutputstream-6KVDLW
-rw-------  1 user user       0 Jul 31  2013 .goutputstream-6PCC1W
-rw-------  1 user user       0 Nov 12  2013 .goutputstream-6QYY6W
-rw-------  1 user user       0 Jun 20  2013 .goutputstream-6UJ7YW
-rw-------  1 user user       0 Jun 22  2012 .goutputstream-713AGW
-rw-------  1 user user       0 May  6  2012 .goutputstream-7CUYDW
-rw-------  1 user user       0 Apr  7 20:34 .goutputstream-7GZYDX
-rw-------  1 user user       0 Dec 17  2012 .goutputstream-7LE3OW
-rw-------  1 user user       0 Feb  3 17:35 .goutputstream-7LPHAX
-rw-------  1 user user       0 Mar 17  2013 .goutputstream-7P0BUW
-rw-------  1 user user       0 Mar 27 12:02 .goutputstream-7VQPDX
-rw-------  1 user user       0 Oct  8  2013 .goutputstream-8AAP4W
-rw-------  1 user user       0 Feb 23  2013 .goutputstream-8HUNSW
-rw-------  1 user user       0 Dec 31 20:27 .goutputstream-8SKW8W
-rw-------  1 user user       0 Nov 19  2012 .goutputstream-8WS3NW
-rw-------  1 user user       0 May  9 19:31 .goutputstream-8WYMFX
-rw-------  1 user user       0 Feb 14 22:11 .goutputstream-91VBBX
-rw-------  1 user user       0 Nov 22  2013 .goutputstream-92LK6W
-rw-------  1 user user       0 Mar 26  2013 .goutputstream-96ARUW
-rw-------  1 user user       0 Aug 29  2012 .goutputstream-99LRJW
-rw-------  1 user user       0 Jun 14  2013 .goutputstream-9GFJYW
-rw-------  1 user user       0 Jun 21  2012 .goutputstream-9HG5FW
-rw-------  1 user user       0 Jun 13  2012 .goutputstream-9M8XFW
-rw-------  1 user user       0 Sep 26  2013 .goutputstream-9PRF4W
-rw-------  1 user user       0 Oct 20  2013 .goutputstream-9XXN5W
-rw-------  1 user user       0 Feb  9  2013 .goutputstream-A1O2RW
-rw-------  1 user user       0 Jun 11  2012 .goutputstream-AEFYFW
-rw-------  1 user user       0 Apr 13 20:07 .goutputstream-AFH1DX
-rw-------  1 user user       0 Mar 22 22:53 .goutputstream-AONYCX
-rw-------  1 user user       0 Jul  5  2013 .goutputstream-AQSLZW
-rw-------  1 user user       0 Apr 26  2013 .goutputstream-AUWSVW
-rw-------  1 user user       0 Jan 28 22:32 .goutputstream-AW239W
-rw-------  1 user user       0 May 18  2013 .goutputstream-B1A4WW
-rw-------  1 user user       0 May  9  2012 .goutputstream-B3UODW
-rw-------  1 user user       0 Sep 17  2012 .goutputstream-B8TOKW
-rw-------  1 user user       0 Feb  7 11:09 .goutputstream-BBK8AX
-rw-------  1 user user       0 Jul  7  2012 .goutputstream-BEG6GW
-rw-------  1 user user       0 Feb  6 22:13 .goutputstream-BQN4AX
-rw-------  1 user user       0 Apr  9 20:06 .goutputstream-BRIXDX
-rw-------  1 user user       0 Jun  6  2013 .goutputstream-BU4AYW
-rw-------  1 user user       0 Jul 14  2012 .goutputstream-BW9EHW
-rw-------  1 user user       0 Feb 11 21:29 .goutputstream-BYP2AX
-rw-------  1 user user       0 Jul  6  2013 .goutputstream-C5ZXZW
-rw-------  1 user user       0 Jul 18  2013 .goutputstream-C8BO0W
-rw-------  1 user user       0 Apr 17  2013 .goutputstream-C8JDVW
-rw-------  1 user user       0 May  8  2013 .goutputstream-CBVMWW
-rw-------  1 user user       0 Oct 25  2012 .goutputstream-CL6YMW
-rw-------  1 user user       0 May  3 23:11 .goutputstream-CNWCFX
-rw-------  1 user user       0 Jun 10  2012 .goutputstream-CO1OFW
-rw-------  1 user user       0 Oct 29  2012 .goutputstream-COMXMW
-rw-------  1 user user       0 Jan  3 21:17 .goutputstream-CY2V8W
-rw-------  1 user user       0 Nov  5  2012 .goutputstream-D5QINW
-rw-------  1 user user       0 Nov 10  2013 .goutputstream-D79F6W
-rw-------  1 user user       0 Jan 20 22:10 .goutputstream-D91Y9W
-rw-------  1 user user       0 Mar  3 21:23 .goutputstream-D9QDCX
-rw-------  1 user user       0 Jun  1  2013 .goutputstream-DBMXXW
-rw-------  1 user user       0 Sep  7  2013 .goutputstream-DLMP2W
-rw-------  1 user user       0 Dec 16  2012 .goutputstream-DM56OW
-rw-------  1 user user       0 Jun  1  2013 .goutputstream-DN2MXW
-rw-------  1 user user       0 Mar 15  2013 .goutputstream-DQCHUW
-rw-------  1 user user       0 May 29  2012 .goutputstream-DULBFW
-rw-------  1 user user       0 Mar 30 21:49 .goutputstream-DX6SDX
-rw-------  1 user user       0 Jul 26  2013 .goutputstream-DYCB1W
-rw-------  1 user user       0 Jun 15  2013 .goutputstream-DZOBYW
-rw-------  1 user user       0 Jan  3 14:06 .goutputstream-E1MA9W
-rw-------  1 user user       0 May 10 20:16 .goutputstream-EC49EX
-rw-------  1 user user       0 Aug 20  2013 .goutputstream-EM311W
-rw-------  1 user user       0 Aug 24  2012 .goutputstream-EV6DJW
-rw-------  1 user user       0 May 21  2012 .goutputstream-EZGJEW
-rw-------  1 user user       0 Nov  2  2012 .goutputstream-F33ENW
-rw-------  1 user user       0 Jun 10  2013 .goutputstream-F6RJYW
-rw-------  1 user user       0 Mar 28 20:47 .goutputstream-F7CQDX
-rw-------  1 user user       0 Jul 29  2013 .goutputstream-FDD80W
-rw-------  1 user user       0 Apr 22 21:28 .goutputstream-FFWYEX
-rw-------  1 user user       0 Mar 26 21:02 .goutputstream-FH4CDX
-rw-------  1 user user       0 Jun  7  2012 .goutputstream-FINIFW
-rw-------  1 user user       0 Mar 10 21:35 .goutputstream-FLAGCX
-rw-------  1 user user       0 Feb 22 23:44 .goutputstream-FMOJBX
-rw-------  1 user user       0 Apr 20 19:47 .goutputstream-FRRHEX
-rw-------  1 user user       0 Mar 19  2013 .goutputstream-FYBEUW
-rw-------  1 user user       0 Jun  5  2013 .goutputstream-G270XW
-rw-------  1 user user       0 Jul 11  2013 .goutputstream-G5DKZW
-rw-------  1 user user       0 Oct 27  2013 .goutputstream-G7EO5W
-rw-------  1 user user       0 Mar 17 22:31 .goutputstream-GECYCX
-rw-------  1 user user       0 Oct 31  2012 .goutputstream-GEDMNW
-rw-------  1 user user       0 Nov 15  2013 .goutputstream-GENV6W
-rw-------  1 user user       0 Aug  3  2012 .goutputstream-GI53HW
-rw-------  1 user user       0 Aug 11  2012 .goutputstream-GNHXIW
-rw-------  1 user user       0 Jun 12  2013 .goutputstream-GO0HYW
-rw-------  1 user user       0 Dec 28  2012 .goutputstream-GOB1PW
-rw-------  1 user user       0 Sep 21  2012 .goutputstream-GTOQKW
-rw-------  1 user user       0 Jul 12  2013 .goutputstream-GTPL0W
-rw-------  1 user user       0 Jun  8  2012 .goutputstream-GWNJFW
-rw-------  1 user user       0 Mar 25 22:17 .goutputstream-HF4EDX
-rw-------  1 user user       0 Dec 15  2013 .goutputstream-HNKY7W
-rw-------  1 user user       0 Apr 12 21:31 .goutputstream-HOHVDX
-rw-------  1 user user       0 Oct 19  2013 .goutputstream-HTFN5W
-rw-------  1 user user       0 Jan 28 22:02 .goutputstream-HZBOAX
-rw-------  1 user user       0 Aug  6  2012 .goutputstream-HZT6IW
-rw-------  1 user user       0 Jan 22  2013 .goutputstream-IQO9QW
-rw-------  1 user user       0 Jan 12  2013 .goutputstream-IU2BRW
-rw-------  1 user user       0 Aug  6  2012 .goutputstream-JOWDIW
-rw-------  1 user user       0 Oct 22  2013 .goutputstream-JQ094W
-rw-------  1 user user       0 Oct 31  2013 .goutputstream-JTAA6W
-rw-------  1 user user       0 May  5  2012 .goutputstream-K4AUDW
-rw-------  1 user user       0 Jan 21  2013 .goutputstream-K5ZYQW
-rw-------  1 user user       0 Nov 11  2013 .goutputstream-KD0H6W
-rw-------  1 user user       0 May 25  2012 .goutputstream-KE7DEW
-rw-------  1 user user       0 Dec  3  2013 .goutputstream-KJN96W
-rw-------  1 user user       0 Apr 11  2013 .goutputstream-KPZEVW
-rw-------  1 user user       0 Nov  7  2013 .goutputstream-KWMX5W
-rw-------  1 user user       0 Sep 12  2012 .goutputstream-KX52KW
-rw-------  1 user user       0 Jan 21 21:42 .goutputstream-KYVQ9W
-rw-------  1 user user       0 Aug  2  2013 .goutputstream-KZDA1W
-rw-------  1 user user       0 Sep 13  2013 .goutputstream-L54J3W
-rw-------  1 user user       0 Dec  5  2013 .goutputstream-LTSK7W
-rw-------  1 user user       0 Sep 18  2012 .goutputstream-LUUXKW
-rw-------  1 user user       0 Jun  1  2013 .goutputstream-LX46XW
-rw-------  1 user user       0 Jul 15  2012 .goutputstream-M0MGHW
-rw-------  1 user user       0 Dec 28 00:35 .goutputstream-M18D8W
-rw-------  1 user user       0 May 17 08:38 .goutputstream-MB4YFX
-rw-------  1 user user       0 May  4 12:22 .goutputstream-MQ0MFX
-rw-------  1 user user       0 Nov 11  2012 .goutputstream-MTK6MW
-rw-------  1 user user       0 Apr  5  2013 .goutputstream-MVAUUW
-rw-------  1 user user       0 Jul 11  2012 .goutputstream-MXE4GW
-rw-------  1 user user       0 Jun  3  2012 .goutputstream-MY1ZEW
-rw-------  1 user user       0 Oct  7  2012 .goutputstream-N430LW
-rw-------  1 user user       0 Jul 15  2013 .goutputstream-N8SB0W
-rw-------  1 user user       0 Jun 30  2012 .goutputstream-NJPBGW
-rw-------  1 user user       0 Nov 15  2013 .goutputstream-NNBE6W
-rw-------  1 user user       0 Sep  8  2012 .goutputstream-NPA9JW
-rw-------  1 user user       0 Jul  4  2012 .goutputstream-NPYVGW
-rw-------  1 user user       0 Mar 29 12:20 .goutputstream-NRBADX
-rw-------  1 user user       0 Aug 11  2013 .goutputstream-O16K1W
-rw-------  1 user user       0 Aug 23  2012 .goutputstream-O2LHJW
-rw-------  1 user user       0 Aug 17  2013 .goutputstream-O4JI1W
-rw-------  1 user user       0 Jul 30  2013 .goutputstream-O4MZ0W
-rw-------  1 user user       0 Aug  8  2012 .goutputstream-OFMRIW
-rw-------  1 user user       0 Jan  1 15:41 .goutputstream-OGLB9W
-rw-------  1 user user       0 May  4  2013 .goutputstream-OKBDWW
-rw-------  1 user user       0 Mar 19  2013 .goutputstream-OX0DUW
-rw-------  1 user user       0 Oct 28  2013 .goutputstream-P0FG5W
-rw-------  1 user user       0 May 15 21:47 .goutputstream-PBNRFX
-rw-------  1 user user       0 Apr 16  2013 .goutputstream-PMDOVW
-rw-------  1 user user       0 Dec  9  2012 .goutputstream-PP1GPW
-rw-------  1 user user       0 Aug 12  2012 .goutputstream-PP75IW
-rw-------  1 user user       0 Sep  2  2012 .goutputstream-PR3BKW
-rw-------  1 user user       0 Jul  8  2012 .goutputstream-QLG7GW
-rw-------  1 user user       0 Jul 28  2012 .goutputstream-QPDIIW
-rw-------  1 user user       0 Aug 22  2013 .goutputstream-QS211W
-rw-------  1 user user       0 Sep  9  2012 .goutputstream-QW81JW
-rw-------  1 user user       0 Jul 24  2012 .goutputstream-RBKIHW
-rw-------  1 user user       0 Dec 14  2013 .goutputstream-RGYV7W
-rw-------  1 user user       0 Jul  1  2013 .goutputstream-RJO2ZW
-rw-------  1 user user       0 Sep 19  2012 .goutputstream-RMXVKW
-rw-------  1 user user       0 Nov 19  2013 .goutputstream-RYYX6W
-rw-------  1 user user       0 Apr 16 19:51 .goutputstream-S84DEX
-rw-------  1 user user       0 Oct 22  2013 .goutputstream-SLLK5W
-rw-------  1 user user       0 Apr 27 12:18 .goutputstream-SVRPEX
-rw-------  1 user user       0 May 25  2013 .goutputstream-SXYXXW
-rw-------  1 user user       0 Feb  8  2013 .goutputstream-T0VISW
-rw-------  1 user user       0 May 12  2012 .goutputstream-TATUDW
-rw-------  1 user user       0 Jun 20  2012 .goutputstream-TINEGW
-rw-------  1 user user       0 Feb 20 20:20 .goutputstream-TNTWBX
-rw-------  1 user user       0 Jan 15 17:05 .goutputstream-TOYN9W
-rw-------  1 user user       0 Oct 18  2013 .goutputstream-TY1K5W
-rw-------  1 user user       0 Aug  6  2012 .goutputstream-U00SIW
-rw-------  1 user user       0 Sep 15  2013 .goutputstream-UEAO3W
-rw-------  1 user user       0 Mar 12  2013 .goutputstream-UIRMTW
-rw-------  1 user user       0 Feb 11  2013 .goutputstream-UN7ISW
-rw-------  1 user user       0 Jun 12  2012 .goutputstream-UYAVFW
-rw-------  1 user user       0 Mar 31 20:08 .goutputstream-V52CDX
-rw-------  1 user user       0 Aug 13  2013 .goutputstream-V7EG1W
-rw-------  1 user user       0 Nov  8  2013 .goutputstream-VDDY5W
-rw-------  1 user user       0 Sep 27  2012 .goutputstream-VHAFLW
-rw-------  1 user user       0 Dec  7  2013 .goutputstream-VHLX7W
-rw-------  1 user user       0 May  3  2013 .goutputstream-VOHDWW
-rw-------  1 user user       0 Sep 20  2013 .goutputstream-VOWH3W
-rw-------  1 user user       0 Jul 29  2013 .goutputstream-W2Y10W
-rw-------  1 user user       0 Jun  7  2012 .goutputstream-W4NQFW
-rw-------  1 user user       0 Jul 22  2013 .goutputstream-WBL9ZW
-rw-------  1 user user       0 Dec 13  2013 .goutputstream-WIY27W
-rw-------  1 user user       0 Sep 25  2012 .goutputstream-WK8JLW
-rw-------  1 user user       0 May 28  2012 .goutputstream-WP05EW
-rw-------  1 user user       0 May 15  2012 .goutputstream-WRDNEW
-rw-------  1 user user       0 Aug 27  2013 .goutputstream-WTWA2W
-rw-------  1 user user       0 Apr 15 22:52 .goutputstream-WUGWDX
-rw-------  1 user user       0 Jul 19  2013 .goutputstream-WWOH0W
-rw-------  1 user user       0 Nov 10  2012 .goutputstream-X41HNW
-rw-------  1 user user       0 Jun 26  2013 .goutputstream-X9ABZW
-rw-------  1 user user       0 Aug 24  2013 .goutputstream-XH8K2W
-rw-------  1 user user       0 Sep 29  2013 .goutputstream-XKAD4W
-rw-------  1 user user       0 May 13  2013 .goutputstream-XN63WW
-rw-------  1 user user       0 Nov 27  2012 .goutputstream-XOWJOW
-rw-------  1 user user       0 Jun 19  2012 .goutputstream-YLYOGW
-rw-------  1 user user       0 Aug  1  2013 .goutputstream-YMOR0W
-rw-------  1 user user       0 May  7  2012 .goutputstream-YR27DW
-rw-------  1 user user       0 Oct  3  2013 .goutputstream-YT883W
-rw-------  1 user user       0 Jan  8  2013 .goutputstream-YTXDQW
-rw-------  1 user user       0 Jun 15  2013 .goutputstream-Z07LYW
-rw-------  1 user user       0 Feb  5  2013 .goutputstream-Z4D8RW
-rw-------  1 user user       0 Mar 15 14:52 .goutputstream-Z87UCX
-rw-------  1 user user       0 Aug  7  2012 .goutputstream-Z9N0IW
-rw-------  1 user user       0 Nov 30  2013 .goutputstream-ZGG96W
-rw-------  1 user user       0 Sep 20  2012 .goutputstream-ZN4UKW
-rw-------  1 user user       0 Mar 23 22:47 .goutputstream-ZPR3CX
drwx------  2 user user    4096 Dec  7  2013 .gphoto
drwx------ 27 user user    4096 Oct 16  2013 gpodder-downloads
drwxrwxr-x  2 user user    4096 Dec 12  2012 .gsharkdown
drwxrwxr-x  3 user user    4096 May 17 14:53 .gstreamer-0.10
-rw-rw-r--  1 user user     142 May 17 14:52 .gtk-bookmarks
drwx------  2 user user    4096 Mar 29  2012 .gvfs
drwxr-xr-x  2 user user    4096 Jun  8 08:46 .hplip
-rw-------  1 user user  139866 Jun  8 08:46 .ICEauthority
drwxrwxr-x  7 user user    4096 Aug 19  2012 .icedtea
drwx------  2 user user    4096 May 17 12:29 .icons
-rw-rw-r--  1 user user      44 Jul  1  2012 .install4j
drwxrwxr-x  4 user user    4096 Jul 30  2013 .java
drwx------  3 user user    4096 Mar 13  2013 .kde
drwx------  3 user user    4096 Aug 13  2012 .launchpadlib
-rw-rw-r--  1 user user    9636 May  1  2012 libnautilus-gksu.so
-rw-rw-r--  1 user user    9636 Aug 28  2012 libnautilus-gksu.so.1
drwxr-xr-x  3 user user    4096 Mar 29  2012 .local
drwx------  3 user user    4096 Mar 29  2012 .macromedia
drwxr-xr-x  7 user user    4096 Aug 14  2013 .mandelbulber
-rw-rw-r--  1 user user   74842 Aug 20  2013 .mandelbulber_log.txt
drwx------  3 user user    4096 Mar 29  2012 .mission-control
drwxrwxr-x  2 user user    4096 Apr  3  2013 movie
drwx------  4 user user    4096 Mar 29  2012 .mozilla
drwxrwxr-x  2 user user    4096 Apr  3  2013 .mplayer
-rw-rw-r--  1 user user       0 Dec 30  2012 .mtab.fuseiso
drwxr-xr-x  5 user user    4096 Mar  9 11:05 Music
drwxrwxr-x  5 user user    4096 Sep  2  2012 .mypaint
drwxrwxr-x  2 user user    4096 Jul 12  2012 NewFolder
drwx------  4 user user    4096 Mar 25 16:51 .nv
drwxrwxr-x  2 user user    4096 Jun 21  2013 .nvidia
-rw-rw-r--  1 user user    1153 Feb 27  2013 .nvidia-settings-rc
drwxr-xr-x  6 user user    4096 May  2 11:26 Pictures
drwx------  3 user user    4096 Mar 29  2012 .pki
drwxrwxr-x  2 user user    4096 Dec 29  2012 Podcasts
drwx--x--x  5 user user    4096 Mar 14  2013 .pokerth
-rw-r--r--  1 user user     797 Mar 30  2012 .profile
drwxr-xr-x  2 user user    4096 Mar 29  2012 Public
drwx------  2 user user    4096 May 17 08:40 .pulse
-rw-------  1 user user     256 Mar 29  2012 .pulse-cookie
drwx------  6 user user    4096 Apr  6  2013 .purple
drwxr-xr-x  6 user user    4096 Jun 19  2013 PyBitmessage
drwxrwxr-x  2 user user    4096 Feb  9 16:15 .PyBitmessage
drwxr-xr-x  2 root root    4096 May 16 21:45 .rpmdb
drwxrwxr-x  5 user user    4096 Nov 13  2013 .rs
drwxrwxr-x  4 user user    4096 Feb 15  2013 .sabnzbd
drwx------  3 user user    4096 Jun  4 12:26 .sane
drwxrwxr-x  4 user user    4096 May  1  2012 .shotwell
drwx------  6 user user    4096 Apr 26 16:13 .Skype
drwx------  4 user user    4096 Mar 13  2013 .speech-dispatcher
drwxrwxr-x  2 user user    4096 Apr  3  2013 .spumux
drwx------  2 user user    4096 Aug 13  2012 .stardict
-rw-r--r--  1 user user       0 Mar 30  2012 .sudo_as_admin_successful
drwxrwxrwx  2 user user    4096 Jan 19  2013 Sync Folder
drwxrwxr-x  3 user user    4096 Jun  6  2012 .teamviewer
drwxr-xr-x  2 user user    4096 Mar 29  2012 Templates
drwx------  5 user user    4096 Mar 29  2012 .thumbnails
drwxrwxr-x  2 user user    4096 Aug 13  2012 Ubuntu One
drwxr-xr-x  3 user user    4096 May 28 16:03 Videos
drwxrwxr-x  2 user user    4096 Mar  3  2013 .VirtualBox
drwxrwxr-x  4 user user    4096 Dec 13  2012 VirtualBox VMs
drwxrwxr-x  3 user user    4096 Dec 29  2012 virtual-drives
-rw-------  1 user user      53 Jun  8 08:46 .Xauthority
-rw-------  1 user user     868 Jun  8 20:49 .xsession-errors
-rw-------  1 user user    1431 Jun  8 08:44 .xsession-errors.old
user@debian:~$ 

```

What does that lot tell you?

CG

---

### Post by Bashing-om on 2014-06-23
captaingraviton; Well well well !

That tells me that the file system is now intact .. !!

Ya want to try and copy off your data files OR ya want to try and fix the permissions on/in your /home directory, see if ya can then boot, and no booty try and (re-)install grub and see if then you can boot ??

Your system, your data, your time, your call as to what you want to do ...

But sure looks like it is a doable situation . And who knows, I may even learn a thing or 2.

See my outputs for reference:
```

sysop@1310mini:~$ ls -la /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 Jun 13 00:07 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 24 sysop sysop  4096 Jun 23 09:59 sysop
sysop@1310mini:~$

sysop@1310mini:~$ ls -la /home/sysop
total 4284
drwxr-xr-x 24 sysop sysop    4096 Jun 23 09:59 .
drwxr-xr-x  4 root  root     4096 May 19  2013 ..
drwx------  2 sysop sysop    4096 May  7 11:50 .aptitude
-rw-------  1 sysop sysop   57005 Jun 23 01:26 .bash_history
-rw-r--r--  1 sysop sysop     309 Jul  8  2013 .bash_logout
-rw-r--r--  1 sysop sysop     220 May 19  2013 .bash_logout~
-rw-r--r--  1 sysop sysop     220 Jul  8  2013 .bash_logout-orig
-rw-r--r--  1 sysop sysop    3726 May 19 14:44 .bashrc
-rw-r--r--  1 sysop sysop    3721 May 18 13:51 .bashrc~
-rw-rw-r--  1 sysop sysop    4036 Apr 22 12:40 booting_issue
-rw-rw-r--  1 sysop sysop    3890 Apr 22 12:14 booting_issue~
drwx------ 21 sysop sysop    4096 Jun  5 17:02 .cache
-rwxr-xr-x  1 sysop sysop    2297 May 21 22:14 chglog
-rwxr-xr-x  1 sysop sysop    2132 May 10 17:16 chglog~
-rwxr-xr-x  1 sysop sysop   15975 Jun 17 13:10 cli_cmds
-rwxr-xr-x  1 sysop sysop   15900 Jun  8 17:14 cli_cmds~
drwxrwxr-x 15 sysop sysop    4096 Mar 19 12:51 .config
-rw-rw-r--  1 sysop sysop    6070 Aug  6  2013 cron-rotatelogs
-rw-rw-r--  1 sysop sysop    5242 Aug  3  2013 cron-rotatelogs~
drwx------  3 sysop sysop    4096 May 19  2013 .dbus
-rw-r--r--  1 root  root   142763 May 27  2013 DejaVuSansMono.pf2
drwxr-xr-x  2 sysop sysop    4096 May 19  2013 Desktop
-rw-rw-r--  1 sysop sysop     192 Sep  1  2013 device.map
-rw-rw-r--  1 sysop sysop     982 Dec  9  2013 docpgp.txt
drwxr-xr-x  2 sysop sysop    4096 May 19  2013 Documents
drwxr-xr-x  2 sysop sysop    4096 Jun  9 15:22 Downloads
-rw-rw-r--  1 sysop sysop    2767 Jun 23 13:29 errors-boot.txt
drwx------  4 sysop sysop    4096 Jun 22 12:24 .gconf
-rw-r-----  1 sysop sysop       0 May 22 13:46 .gksu.lock
drwx------  3 sysop sysop    4096 May 19  2013 .gnome2
drwx------  2 sysop sysop    4096 Jun  1 13:42 .gnupg
-rw-r--r--  1 root  root     1482 Mar 30 10:40 grub-30mar2014
drwxrwxr-x  2 sysop sysop    4096 Apr 21 13:26 grubing
-rw-rw-r--  1 sysop sysop    2833 Apr  3 23:07 grub-txt
-rw-rw-r--  1 sysop sysop    2089 Apr  3 18:55 grub-txt~
drwx------  2 sysop sysop    4096 May 19  2013 .gvfs
-rw-rw-r--  1 sysop sysop  345119 Jan  6 12:22 hwinfo.txt
-rw-------  1 sysop sysop   12714 Jun 23 09:59 .ICEauthority
-rw-r--r--  1 root  root  2477387 Mar 31 16:59 ini <snip>
<snip>

```
Where the directory and it's contents are owned by me "sysop". In your case rather then being owned by you 'stu' they are possessed by 'user'.

I would like to do this slowly, carefully and a lot of looking at what happened and looking to see what we are going to do next and next.

[INDENT][INDENT]looks doable to me
[/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-24
I was particularly eager to back up an extension I had in my Chrome browser, pretty much everything else was already backed up. I'm assuming that if this all goes wrong and I have to reinstall Chrome on a fresh Ubuntu, I'll just be able to replace the folder with it in it (~/.config/google-chrome/Default/Extensions/) and resume as before? 

So, I'm ready to try to prepare to fix grub and reboot this old dog...what's first?

CG

---

### Post by Bashing-om on 2014-06-24
captaingraviton; Morning;

Sounds good to me .. 
1st up to to correct the permissions on the /home directory. Let me get caught up here on the forum to the point I can RE-boot so I can verify what I have in mind. I will boot into the liveDVD of 12.04 and check/verify  my process of thought. And then get rid of all those ".goutputstream-XXX" (known bug) files.

Then take a gander and see where we stand.

[INDENT][INDENT]I will be Bacckkkk
[/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-24
Brilliant. Thank you...

---

### Post by Bashing-om on 2014-06-24
captaingraviton; Here I am,

And hey, there you are !

OK, I did my check, and while my checks did not result in what you have, they were not what I expected. I have a whole new plan.
Let's change root into the install and then have a looksee at what is.
Boot the liveDVD in try ubuntu mode -> terminal;
Terminal commands:
```

sudo mount /dev/sda1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo chroot /mnt/ /bin/bash

```
Notice that your prompt has changed ..You are now root ! as well we are in that install.. Exercise extreme caution and be very certain of all we do from this point on. There is no forgiveness of any mistake or error. You are ROOT ! Do not hit the enter key until double checked that what is, is what we want.

Presently we want to verify those /home access and permissions:
so:
```

ls -la

```
all files are owned by 'root' and all are in the group 'root' as for example:
```

drwxr-xr-x   4 [color=red]root root[/color]  4096 May 19  2013 home

```
next we want to look at /home
```

ls -la /home

``` 'root' should own it .

Now the biggy:
```

ls -la /home/stu

```
all but this one:
> 
drwxr-xr-x  4 root  root     4096 May 19  2013 ..
 - notice the 2 "dots' at the end for your differentiation - should be owned by you and in "your' group .. maybe less any "special" files you have made and copied and left as other access permissions on purpose ( as I have done in that previous example).
In particular I want to know the permissions on the files .ICEauthority and .Xauthority. That they too are 'stu stu' .

OK, all done looking about, and we know the general lay of things -  maybe all good ! .. just need to make sure.

Now let's back out of that full CHange Root and back into the liveDVD and un-do our mounts - practice save hex ! - :
```

exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

Depending on these results is what we are going to do next. A successful CHange Root is a real good indicator that all is well with the file system, next we want to be able to boot into it ! And I got a plan.

[INDENT][INDENT]gets any brighter
[INDENT][INDENT][INDENT]we gonna have to put on sunglasses
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-24
Sorry for my lengthy absences, I'm all of a tizzy over here with work, craziness, and I suspect time differentials, or spacetime continuums.

Anyway, I'm trying to follow along, here's the output after your commands Supreme Leader..

```

user@debian:~$ sudo mount /dev/sda1 /mnt/
user@debian:~$ sudo mount --bind /dev /mnt/dev
user@debian:~$ sudo mount --bind /proc /mnt/proc
user@debian:~$ sudo mount --bind /sys /mnt/sys
user@debian:~$ sudo mount --bind /dev/pts /mnt/dev/pts
user@debian:~$ sudo chroot /mnt/ /bin/bash
root@debian:/# ls -la
total 140
drwxr-xr-x  25 root root  4096 Jun  8 09:37 .
drwxr-xr-x  25 root root  4096 Jun  8 09:37 ..
drwxr-xr-x   2 root root  4096 May 17 15:27 bin
drwxr-xr-x   4 root root 12288 Jun  8 09:40 boot
drwxr-xr-x   2 root root  4096 Mar 29  2012 cdrom
drwxr-xr-x  13 root root  3200 Jun 24 17:47 dev
drwxr-xr-x 174 root root 12288 Jun  8 21:49 etc
drwxr-xr-x   3 root root  4096 Mar 29  2012 home
lrwxrwxrwx   1 root root    33 Jun  8 09:37 initrd.img -> boot/initrd.img-3.13.0-29-generic
lrwxrwxrwx   1 root root    33 May 27 12:35 initrd.img.old -> boot/initrd.img-3.13.0-27-generic
drwxr-xr-x  26 root root  4096 May 17 15:27 lib
drwxr-xr-x   2 root root 12288 May 17 14:20 lib32
drwxr-xr-x   2 root root  4096 May 17 15:27 lib64
lrwxrwxrwx   1 root root    36 May 16 22:40 libnss3.so -> /usr/lib/x86_64-linux-gnu/libnss3.so
drwx------   2 root root 16384 Mar 29  2012 lost+found
drwxr-xr-x   4 root root  4096 May 17 16:04 media
drwxr-xr-x   2 root root  4096 Oct  9  2011 mnt
drwxr-xr-x   5 root root  4096 Feb  1  2013 opt
dr-xr-xr-x 146 root root     0 Jun 24 15:52 proc
drwx------  20 root root  4096 Jun  4 12:27 root
drwxr-xr-x   2 root root  4096 May 27 12:35 .rpmdb
drwxr-xr-x   7 root root  4096 Oct 12  2011 run
drwxr-xr-x   2 root root 12288 May 22 13:51 sbin
drwxr-xr-x   2 root root  4096 Oct 12  2011 srv
drwxr-xr-x  13 root root     0 Jun 24 15:52 sys
drwxrwxrwt   9 root root 12288 Jun 15 19:54 tmp
drwxr-xr-x  11 root root  4096 Mar 29  2012 usr
drwxr-xr-x  14 root root  4096 May 17 09:38 var
lrwxrwxrwx   1 root root    30 Jun  8 09:37 vmlinuz -> boot/vmlinuz-3.13.0-29-generic
lrwxrwxrwx   1 root root    30 May 27 12:35 vmlinuz.old -> boot/vmlinuz-3.13.0-27-generic
root@debian:/# ls -la /home
total 32
drwxr-xr-x  3 root root  4096 Mar 29  2012 .
drwxr-xr-x 25 root root  4096 Jun  8 09:37 ..
drwxr-xr-x 94 stu  stu  20480 Jun  8 09:46 stu
root@debian:/# ls -la /home/stu
total 8596
drwxr-xr-x 94 stu  stu    20480 Jun  8 09:46 .
drwxr-xr-x  3 root root    4096 Mar 29  2012 ..
drwxrwxr-x  2 stu  stu     4096 Dec 29  2012 .acetoneiso
drwx------  3 stu  stu     4096 Mar 29  2012 .adobe
drwxrwxr-x 11 stu  stu     4096 May 28 15:12 apps
drwxrwxr-x  3 stu  stu     4096 Dec 24  2012 .appwork
drwx------  2 stu  stu     4096 Apr 23 17:42 .aptitude
drwxrwxr-x  2 stu  stu     4096 Apr 21 17:19 .armory
-rw-rw-r--  1 stu  stu      183 May  9  2013 .asunder
drwxrwxr-x  4 stu  stu     4096 May  8 13:27 .audacity-data
drwxr-xr-x  2 stu  stu     4096 May  8 14:33 Audio
drwxrwxr-x  2 stu  stu     4096 Dec 29  2012 Audiobooks
-rw-------  1 stu  stu     9493 Jun  4 13:28 .bash_history
-rw-r--r--  1 stu  stu      220 Mar 29  2012 .bash_logout
-rw-r--r--  1 stu  stu     3353 Mar 29  2012 .bashrc
drwxrwxr-x  5 stu  stu     4096 Nov 15  2012 .bitpim-files
drwx------ 50 stu  stu     4096 Jun  8 21:41 .cache
drwxr-xr-x 13 stu  stu     4096 Aug 28  2012 .cddbslave
drwxrwxr-x  6 stu  stu     4096 Mar 29  2013 .clamtk
drwx------  3 stu  stu     4096 May 17 14:09 .compiz
drwxrwxr-x  3 stu  stu     4096 Mar 29  2012 .compiz-1
drwx------ 58 stu  stu     4096 Jun  4 13:35 .config
drwx------  3 stu  stu     4096 Mar 29  2012 .dbus
drwxr-xr-x  4 stu  stu     4096 Jun  7 21:04 Desktop
-rw-rw-r--  1 stu  stu      165 Aug  8  2013 .devede
drwxr-xr-x  3 root root    4096 Apr 24 15:37 .distlib
-rw-r--r--  1 stu  stu       26 May 17 14:09 .dmrc
drwxr-xr-x  2 stu  stu     4096 May 29 14:52 Documents
drwxrwxrwx  2 stu  stu    12288 May 28 16:23 Downloads
drwx------  4 stu  stu     4096 Jun  8 17:09 .dropbox
drwx------ 10 stu  stu     4096 Jun  8 09:47 Dropbox
drwxr-xr-x  7 stu  stu     4096 May 20 01:40 .dropbox-dist
drwx------  2 stu  stu     4096 May 17 09:40 .dropbox-master
drwxr-xr-x  2 stu  stu     4096 Aug 10  2012 .eBook-speaker
-rw-rw-r--  1 stu  stu      481 Aug 10  2012 .eBook-speaker.rc
-rw-------  1 stu  stu       16 Mar 29  2012 .esd_auth
-rw-r--r--  1 stu  stu      179 Mar 29  2012 examples.desktop
-rw-r--r--  1 root root   15140 Mar 29  2012 .face
-rw-rw-r--  1 stu  stu  7970835 Apr 11  2013 Firefox_wallpaper.png
drwxr-xr-x  2 stu  stu     4096 May 17 01:40 fontconfig
drwxr-xr-x  2 stu  stu    12288 May 17 01:40 .fontconfig
drwxrwxr-x  5 stu  stu     4096 Jul 30  2013 FrostWire
drwxrwxr-x  8 stu  stu     4096 Aug  2  2013 .frostwire5
drwx------  5 stu  stu     4096 Jun  8 09:46 .gconf
drwx------  4 stu  stu     4096 Mar 29  2012 .gegl-0.0
drwxr-xr-x 22 stu  stu     4096 Jul  9  2012 .gimp-2.6
drwxr-xr-x 24 stu  stu     4096 Mar  8 14:18 .gimp-2.8
-rw-r-----  1 stu  stu        0 Jun  8 10:14 .gksu.lock
drwx------  4 stu  stu     4096 Jun  8 09:44 .gnome2
drwx------  2 stu  stu     4096 Mar 30  2012 .gnome2_private
drwx------  3 stu  stu     4096 May 18 11:02 .gnupg
drwxrwxr-x  3 stu  stu     4096 Feb 26  2013 .goldendict
drwx------  5 stu  stu     4096 Mar 10 12:31 .googleearth
-rw-------  1 stu  stu        0 Oct 23  2013 .goutputstream-007M5W
-rw-------  1 stu  stu        0 Sep 16  2013 .goutputstream-07BK3W
-rw-------  1 stu  stu        0 Sep  4  2013 .goutputstream-0NF42W
-rw-------  1 stu  stu        0 Oct 28  2012 .goutputstream-0T5XMW
-rw-------  1 stu  stu        0 May  2  2013 .goutputstream-0WMUWW
-rw-------  1 stu  stu        0 Oct 11  2013 .goutputstream-0X1Z4W
-rw-------  1 stu  stu        0 Jun 18  2013 .goutputstream-14M4YW
-rw-------  1 stu  stu        0 Mar  4 21:52 .goutputstream-1B80BX
-rw-------  1 stu  stu        0 Jun 29  2013 .goutputstream-1C05YW
-rw-------  1 stu  stu        0 Nov 16  2012 .goutputstream-1CDZNW
-rw-------  1 stu  stu        0 Jan 20  2013 .goutputstream-1CI9QW
-rw-------  1 stu  stu        0 Aug 14  2013 .goutputstream-1Q4Q1W
-rw-------  1 stu  stu        0 Mar  1 22:30 .goutputstream-1YWZBX
-rw-------  1 stu  stu        0 Mar  5  2013 .goutputstream-1Z9ITW
-rw-------  1 stu  stu        0 Aug 24  2012 .goutputstream-2CQTJW
-rw-------  1 stu  stu        0 Jul  8  2013 .goutputstream-2H8QZW
-rw-------  1 stu  stu        0 Feb 15 21:32 .goutputstream-2JOZAX
-rw-------  1 stu  stu        0 Sep  2  2012 .goutputstream-2O73JW
-rw-------  1 stu  stu        0 Aug 14  2012 .goutputstream-2XF7IW
-rw-------  1 stu  stu        0 Dec  1  2012 .goutputstream-2XVBOW
-rw-------  1 stu  stu        0 Mar  6 21:44 .goutputstream-2XWBCX
-rw-------  1 stu  stu        0 Jan 27 21:06 .goutputstream-2YEMAX
-rw-------  1 stu  stu        0 Apr 23 22:00 .goutputstream-385OEX
-rw-------  1 stu  stu        0 Jan 30 20:31 .goutputstream-3EZ39W
-rw-------  1 stu  stu        0 Aug 19  2012 .goutputstream-3IXIJW
-rw-------  1 stu  stu        0 May 19  2013 .goutputstream-3MSJXW
-rw-------  1 stu  stu        0 Sep  8  2013 .goutputstream-3QD22W
-rw-------  1 stu  stu        0 May 24  2013 .goutputstream-3QEDXW
-rw-------  1 stu  stu        0 May 20  2013 .goutputstream-3S00WW
-rw-------  1 stu  stu        0 Nov 30  2012 .goutputstream-3ZQFOW
-rw-------  1 stu  stu        0 Nov 23  2012 .goutputstream-40P6NW
-rw-------  1 stu  stu        0 May 11  2012 .goutputstream-4FJ6DW
-rw-------  1 stu  stu        0 Oct 26  2013 .goutputstream-4GAM5W
-rw-------  1 stu  stu        0 May 17  2013 .goutputstream-4WXIXW
-rw-------  1 stu  stu        0 Apr 26  2013 .goutputstream-4XKRVW
-rw-------  1 stu  stu        0 Oct 13  2013 .goutputstream-52DV4W
-rw-------  1 stu  stu        0 Oct 26  2012 .goutputstream-52ZVMW
-rw-------  1 stu  stu        0 May 14 23:59 .goutputstream-5BK2FX
-rw-------  1 stu  stu        0 Aug 23  2013 .goutputstream-5D8B2W
-rw-------  1 stu  stu        0 Sep 11  2013 .goutputstream-6B182W
-rw-------  1 stu  stu        0 May 27  2013 .goutputstream-6GPZXW
-rw-------  1 stu  stu        0 May 17  2012 .goutputstream-6H5QEW
-rw-------  1 stu  stu        0 Oct  4  2012 .goutputstream-6KVDLW
-rw-------  1 stu  stu        0 Jul 31  2013 .goutputstream-6PCC1W
-rw-------  1 stu  stu        0 Nov 12  2013 .goutputstream-6QYY6W
-rw-------  1 stu  stu        0 Jun 21  2013 .goutputstream-6UJ7YW
-rw-------  1 stu  stu        0 Jun 22  2012 .goutputstream-713AGW
-rw-------  1 stu  stu        0 May  6  2012 .goutputstream-7CUYDW
-rw-------  1 stu  stu        0 Apr  7 21:34 .goutputstream-7GZYDX
-rw-------  1 stu  stu        0 Dec 17  2012 .goutputstream-7LE3OW
-rw-------  1 stu  stu        0 Feb  3 17:35 .goutputstream-7LPHAX
-rw-------  1 stu  stu        0 Mar 17  2013 .goutputstream-7P0BUW
-rw-------  1 stu  stu        0 Mar 27 12:02 .goutputstream-7VQPDX
-rw-------  1 stu  stu        0 Oct  8  2013 .goutputstream-8AAP4W
-rw-------  1 stu  stu        0 Feb 23  2013 .goutputstream-8HUNSW
-rw-------  1 stu  stu        0 Dec 31 20:27 .goutputstream-8SKW8W
-rw-------  1 stu  stu        0 Nov 19  2012 .goutputstream-8WS3NW
-rw-------  1 stu  stu        0 May  9 20:31 .goutputstream-8WYMFX
-rw-------  1 stu  stu        0 Feb 14 22:11 .goutputstream-91VBBX
-rw-------  1 stu  stu        0 Nov 22  2013 .goutputstream-92LK6W
-rw-------  1 stu  stu        0 Mar 26  2013 .goutputstream-96ARUW
-rw-------  1 stu  stu        0 Aug 29  2012 .goutputstream-99LRJW
-rw-------  1 stu  stu        0 Jun 14  2013 .goutputstream-9GFJYW
-rw-------  1 stu  stu        0 Jun 21  2012 .goutputstream-9HG5FW
-rw-------  1 stu  stu        0 Jun 13  2012 .goutputstream-9M8XFW
-rw-------  1 stu  stu        0 Sep 26  2013 .goutputstream-9PRF4W
-rw-------  1 stu  stu        0 Oct 20  2013 .goutputstream-9XXN5W
-rw-------  1 stu  stu        0 Feb  9  2013 .goutputstream-A1O2RW
-rw-------  1 stu  stu        0 Jun 11  2012 .goutputstream-AEFYFW
-rw-------  1 stu  stu        0 Apr 13 21:07 .goutputstream-AFH1DX
-rw-------  1 stu  stu        0 Mar 22 22:53 .goutputstream-AONYCX
-rw-------  1 stu  stu        0 Jul  5  2013 .goutputstream-AQSLZW
-rw-------  1 stu  stu        0 Apr 26  2013 .goutputstream-AUWSVW
-rw-------  1 stu  stu        0 Jan 28 22:32 .goutputstream-AW239W
-rw-------  1 stu  stu        0 May 18  2013 .goutputstream-B1A4WW
-rw-------  1 stu  stu        0 May  9  2012 .goutputstream-B3UODW
-rw-------  1 stu  stu        0 Sep 17  2012 .goutputstream-B8TOKW
-rw-------  1 stu  stu        0 Feb  7 11:09 .goutputstream-BBK8AX
-rw-------  1 stu  stu        0 Jul  7  2012 .goutputstream-BEG6GW
-rw-------  1 stu  stu        0 Feb  6 22:13 .goutputstream-BQN4AX
-rw-------  1 stu  stu        0 Apr  9 21:06 .goutputstream-BRIXDX
-rw-------  1 stu  stu        0 Jun  6  2013 .goutputstream-BU4AYW
-rw-------  1 stu  stu        0 Jul 14  2012 .goutputstream-BW9EHW
-rw-------  1 stu  stu        0 Feb 11 21:29 .goutputstream-BYP2AX
-rw-------  1 stu  stu        0 Jul  6  2013 .goutputstream-C5ZXZW
-rw-------  1 stu  stu        0 Jul 19  2013 .goutputstream-C8BO0W
-rw-------  1 stu  stu        0 Apr 17  2013 .goutputstream-C8JDVW
-rw-------  1 stu  stu        0 May  9  2013 .goutputstream-CBVMWW
-rw-------  1 stu  stu        0 Oct 25  2012 .goutputstream-CL6YMW
-rw-------  1 stu  stu        0 May  4 00:11 .goutputstream-CNWCFX
-rw-------  1 stu  stu        0 Jun 11  2012 .goutputstream-CO1OFW
-rw-------  1 stu  stu        0 Oct 29  2012 .goutputstream-COMXMW
-rw-------  1 stu  stu        0 Jan  3 21:17 .goutputstream-CY2V8W
-rw-------  1 stu  stu        0 Nov  5  2012 .goutputstream-D5QINW
-rw-------  1 stu  stu        0 Nov 10  2013 .goutputstream-D79F6W
-rw-------  1 stu  stu        0 Jan 20 22:10 .goutputstream-D91Y9W
-rw-------  1 stu  stu        0 Mar  3 21:23 .goutputstream-D9QDCX
-rw-------  1 stu  stu        0 Jun  1  2013 .goutputstream-DBMXXW
-rw-------  1 stu  stu        0 Sep  7  2013 .goutputstream-DLMP2W
-rw-------  1 stu  stu        0 Dec 16  2012 .goutputstream-DM56OW
-rw-------  1 stu  stu        0 Jun  1  2013 .goutputstream-DN2MXW
-rw-------  1 stu  stu        0 Mar 15  2013 .goutputstream-DQCHUW
-rw-------  1 stu  stu        0 May 30  2012 .goutputstream-DULBFW
-rw-------  1 stu  stu        0 Mar 30 22:49 .goutputstream-DX6SDX
-rw-------  1 stu  stu        0 Jul 26  2013 .goutputstream-DYCB1W
-rw-------  1 stu  stu        0 Jun 15  2013 .goutputstream-DZOBYW
-rw-------  1 stu  stu        0 Jan  3 14:06 .goutputstream-E1MA9W
-rw-------  1 stu  stu        0 May 10 21:16 .goutputstream-EC49EX
-rw-------  1 stu  stu        0 Aug 20  2013 .goutputstream-EM311W
-rw-------  1 stu  stu        0 Aug 24  2012 .goutputstream-EV6DJW
-rw-------  1 stu  stu        0 May 21  2012 .goutputstream-EZGJEW
-rw-------  1 stu  stu        0 Nov  2  2012 .goutputstream-F33ENW
-rw-------  1 stu  stu        0 Jun 10  2013 .goutputstream-F6RJYW
-rw-------  1 stu  stu        0 Mar 28 20:47 .goutputstream-F7CQDX
-rw-------  1 stu  stu        0 Jul 29  2013 .goutputstream-FDD80W
-rw-------  1 stu  stu        0 Apr 22 22:28 .goutputstream-FFWYEX
-rw-------  1 stu  stu        0 Mar 26 21:02 .goutputstream-FH4CDX
-rw-------  1 stu  stu        0 Jun  7  2012 .goutputstream-FINIFW
-rw-------  1 stu  stu        0 Mar 10 21:35 .goutputstream-FLAGCX
-rw-------  1 stu  stu        0 Feb 22 23:44 .goutputstream-FMOJBX
-rw-------  1 stu  stu        0 Apr 20 20:47 .goutputstream-FRRHEX
-rw-------  1 stu  stu        0 Mar 19  2013 .goutputstream-FYBEUW
-rw-------  1 stu  stu        0 Jun  5  2013 .goutputstream-G270XW
-rw-------  1 stu  stu        0 Jul 11  2013 .goutputstream-G5DKZW
-rw-------  1 stu  stu        0 Oct 27  2013 .goutputstream-G7EO5W
-rw-------  1 stu  stu        0 Mar 17 22:31 .goutputstream-GECYCX
-rw-------  1 stu  stu        0 Oct 31  2012 .goutputstream-GEDMNW
-rw-------  1 stu  stu        0 Nov 15  2013 .goutputstream-GENV6W
-rw-------  1 stu  stu        0 Aug  3  2012 .goutputstream-GI53HW
-rw-------  1 stu  stu        0 Aug 11  2012 .goutputstream-GNHXIW
-rw-------  1 stu  stu        0 Jun 12  2013 .goutputstream-GO0HYW
-rw-------  1 stu  stu        0 Dec 28  2012 .goutputstream-GOB1PW
-rw-------  1 stu  stu        0 Sep 21  2012 .goutputstream-GTOQKW
-rw-------  1 stu  stu        0 Jul 12  2013 .goutputstream-GTPL0W
-rw-------  1 stu  stu        0 Jun  8  2012 .goutputstream-GWNJFW
-rw-------  1 stu  stu        0 Mar 25 22:17 .goutputstream-HF4EDX
-rw-------  1 stu  stu        0 Dec 15  2013 .goutputstream-HNKY7W
-rw-------  1 stu  stu        0 Apr 12 22:31 .goutputstream-HOHVDX
-rw-------  1 stu  stu        0 Oct 19  2013 .goutputstream-HTFN5W
-rw-------  1 stu  stu        0 Jan 28 22:02 .goutputstream-HZBOAX
-rw-------  1 stu  stu        0 Aug  6  2012 .goutputstream-HZT6IW
-rw-------  1 stu  stu        0 Jan 22  2013 .goutputstream-IQO9QW
-rw-------  1 stu  stu        0 Jan 12  2013 .goutputstream-IU2BRW
-rw-------  1 stu  stu        0 Aug  6  2012 .goutputstream-JOWDIW
-rw-------  1 stu  stu        0 Oct 22  2013 .goutputstream-JQ094W
-rw-------  1 stu  stu        0 Oct 31  2013 .goutputstream-JTAA6W
-rw-------  1 stu  stu        0 May  5  2012 .goutputstream-K4AUDW
-rw-------  1 stu  stu        0 Jan 21  2013 .goutputstream-K5ZYQW
-rw-------  1 stu  stu        0 Nov 11  2013 .goutputstream-KD0H6W
-rw-------  1 stu  stu        0 May 25  2012 .goutputstream-KE7DEW
-rw-------  1 stu  stu        0 Dec  3  2013 .goutputstream-KJN96W
-rw-------  1 stu  stu        0 Apr 11  2013 .goutputstream-KPZEVW
-rw-------  1 stu  stu        0 Nov  7  2013 .goutputstream-KWMX5W
-rw-------  1 stu  stu        0 Sep 12  2012 .goutputstream-KX52KW
-rw-------  1 stu  stu        0 Jan 21 21:42 .goutputstream-KYVQ9W
-rw-------  1 stu  stu        0 Aug  2  2013 .goutputstream-KZDA1W
-rw-------  1 stu  stu        0 Sep 13  2013 .goutputstream-L54J3W
-rw-------  1 stu  stu        0 Dec  5  2013 .goutputstream-LTSK7W
-rw-------  1 stu  stu        0 Sep 19  2012 .goutputstream-LUUXKW
-rw-------  1 stu  stu        0 Jun  1  2013 .goutputstream-LX46XW
-rw-------  1 stu  stu        0 Jul 15  2012 .goutputstream-M0MGHW
-rw-------  1 stu  stu        0 Dec 28 00:35 .goutputstream-M18D8W
-rw-------  1 stu  stu        0 May 17 09:38 .goutputstream-MB4YFX
-rw-------  1 stu  stu        0 May  4 13:22 .goutputstream-MQ0MFX
-rw-------  1 stu  stu        0 Nov 11  2012 .goutputstream-MTK6MW
-rw-------  1 stu  stu        0 Apr  5  2013 .goutputstream-MVAUUW
-rw-------  1 stu  stu        0 Jul 11  2012 .goutputstream-MXE4GW
-rw-------  1 stu  stu        0 Jun  3  2012 .goutputstream-MY1ZEW
-rw-------  1 stu  stu        0 Oct  7  2012 .goutputstream-N430LW
-rw-------  1 stu  stu        0 Jul 15  2013 .goutputstream-N8SB0W
-rw-------  1 stu  stu        0 Jun 30  2012 .goutputstream-NJPBGW
-rw-------  1 stu  stu        0 Nov 15  2013 .goutputstream-NNBE6W
-rw-------  1 stu  stu        0 Sep  8  2012 .goutputstream-NPA9JW
-rw-------  1 stu  stu        0 Jul  4  2012 .goutputstream-NPYVGW
-rw-------  1 stu  stu        0 Mar 29 12:20 .goutputstream-NRBADX
-rw-------  1 stu  stu        0 Aug 11  2013 .goutputstream-O16K1W
-rw-------  1 stu  stu        0 Aug 23  2012 .goutputstream-O2LHJW
-rw-------  1 stu  stu        0 Aug 17  2013 .goutputstream-O4JI1W
-rw-------  1 stu  stu        0 Jul 30  2013 .goutputstream-O4MZ0W
-rw-------  1 stu  stu        0 Aug  8  2012 .goutputstream-OFMRIW
-rw-------  1 stu  stu        0 Jan  1 15:41 .goutputstream-OGLB9W
-rw-------  1 stu  stu        0 May  4  2013 .goutputstream-OKBDWW
-rw-------  1 stu  stu        0 Mar 19  2013 .goutputstream-OX0DUW
-rw-------  1 stu  stu        0 Oct 28  2013 .goutputstream-P0FG5W
-rw-------  1 stu  stu        0 May 15 22:47 .goutputstream-PBNRFX
-rw-------  1 stu  stu        0 Apr 16  2013 .goutputstream-PMDOVW
-rw-------  1 stu  stu        0 Dec  9  2012 .goutputstream-PP1GPW
-rw-------  1 stu  stu        0 Aug 12  2012 .goutputstream-PP75IW
-rw-------  1 stu  stu        0 Sep  2  2012 .goutputstream-PR3BKW
-rw-------  1 stu  stu        0 Jul  8  2012 .goutputstream-QLG7GW
-rw-------  1 stu  stu        0 Jul 28  2012 .goutputstream-QPDIIW
-rw-------  1 stu  stu        0 Aug 22  2013 .goutputstream-QS211W
-rw-------  1 stu  stu        0 Sep  9  2012 .goutputstream-QW81JW
-rw-------  1 stu  stu        0 Jul 24  2012 .goutputstream-RBKIHW
-rw-------  1 stu  stu        0 Dec 14  2013 .goutputstream-RGYV7W
-rw-------  1 stu  stu        0 Jul  1  2013 .goutputstream-RJO2ZW
-rw-------  1 stu  stu        0 Sep 19  2012 .goutputstream-RMXVKW
-rw-------  1 stu  stu        0 Nov 19  2013 .goutputstream-RYYX6W
-rw-------  1 stu  stu        0 Apr 16 20:51 .goutputstream-S84DEX
-rw-------  1 stu  stu        0 Oct 22  2013 .goutputstream-SLLK5W
-rw-------  1 stu  stu        0 Apr 27 13:18 .goutputstream-SVRPEX
-rw-------  1 stu  stu        0 May 25  2013 .goutputstream-SXYXXW
-rw-------  1 stu  stu        0 Feb  8  2013 .goutputstream-T0VISW
-rw-------  1 stu  stu        0 May 12  2012 .goutputstream-TATUDW
-rw-------  1 stu  stu        0 Jun 20  2012 .goutputstream-TINEGW
-rw-------  1 stu  stu        0 Feb 20 20:20 .goutputstream-TNTWBX
-rw-------  1 stu  stu        0 Jan 15 17:05 .goutputstream-TOYN9W
-rw-------  1 stu  stu        0 Oct 18  2013 .goutputstream-TY1K5W
-rw-------  1 stu  stu        0 Aug  6  2012 .goutputstream-U00SIW
-rw-------  1 stu  stu        0 Sep 15  2013 .goutputstream-UEAO3W
-rw-------  1 stu  stu        0 Mar 12  2013 .goutputstream-UIRMTW
-rw-------  1 stu  stu        0 Feb 11  2013 .goutputstream-UN7ISW
-rw-------  1 stu  stu        0 Jun 12  2012 .goutputstream-UYAVFW
-rw-------  1 stu  stu        0 Mar 31 21:08 .goutputstream-V52CDX
-rw-------  1 stu  stu        0 Aug 13  2013 .goutputstream-V7EG1W
-rw-------  1 stu  stu        0 Nov  8  2013 .goutputstream-VDDY5W
-rw-------  1 stu  stu        0 Sep 27  2012 .goutputstream-VHAFLW
-rw-------  1 stu  stu        0 Dec  7  2013 .goutputstream-VHLX7W
-rw-------  1 stu  stu        0 May  3  2013 .goutputstream-VOHDWW
-rw-------  1 stu  stu        0 Sep 20  2013 .goutputstream-VOWH3W
-rw-------  1 stu  stu        0 Jul 29  2013 .goutputstream-W2Y10W
-rw-------  1 stu  stu        0 Jun  7  2012 .goutputstream-W4NQFW
-rw-------  1 stu  stu        0 Jul 22  2013 .goutputstream-WBL9ZW
-rw-------  1 stu  stu        0 Dec 13  2013 .goutputstream-WIY27W
-rw-------  1 stu  stu        0 Sep 25  2012 .goutputstream-WK8JLW
-rw-------  1 stu  stu        0 May 28  2012 .goutputstream-WP05EW
-rw-------  1 stu  stu        0 May 15  2012 .goutputstream-WRDNEW
-rw-------  1 stu  stu        0 Aug 27  2013 .goutputstream-WTWA2W
-rw-------  1 stu  stu        0 Apr 15 23:52 .goutputstream-WUGWDX
-rw-------  1 stu  stu        0 Jul 19  2013 .goutputstream-WWOH0W
-rw-------  1 stu  stu        0 Nov 10  2012 .goutputstream-X41HNW
-rw-------  1 stu  stu        0 Jun 26  2013 .goutputstream-X9ABZW
-rw-------  1 stu  stu        0 Aug 24  2013 .goutputstream-XH8K2W
-rw-------  1 stu  stu        0 Sep 29  2013 .goutputstream-XKAD4W
-rw-------  1 stu  stu        0 May 13  2013 .goutputstream-XN63WW
-rw-------  1 stu  stu        0 Nov 27  2012 .goutputstream-XOWJOW
-rw-------  1 stu  stu        0 Jun 19  2012 .goutputstream-YLYOGW
-rw-------  1 stu  stu        0 Aug  1  2013 .goutputstream-YMOR0W
-rw-------  1 stu  stu        0 May  7  2012 .goutputstream-YR27DW
-rw-------  1 stu  stu        0 Oct  3  2013 .goutputstream-YT883W
-rw-------  1 stu  stu        0 Jan  8  2013 .goutputstream-YTXDQW
-rw-------  1 stu  stu        0 Jun 15  2013 .goutputstream-Z07LYW
-rw-------  1 stu  stu        0 Feb  5  2013 .goutputstream-Z4D8RW
-rw-------  1 stu  stu        0 Mar 15 14:52 .goutputstream-Z87UCX
-rw-------  1 stu  stu        0 Aug  7  2012 .goutputstream-Z9N0IW
-rw-------  1 stu  stu        0 Nov 30  2013 .goutputstream-ZGG96W
-rw-------  1 stu  stu        0 Sep 20  2012 .goutputstream-ZN4UKW
-rw-------  1 stu  stu        0 Mar 23 22:47 .goutputstream-ZPR3CX
drwx------  2 stu  stu     4096 Dec  7  2013 .gphoto
drwx------ 27 stu  stu     4096 Oct 16  2013 gpodder-downloads
drwxrwxr-x  2 stu  stu     4096 Dec 12  2012 .gsharkdown
drwxrwxr-x  3 stu  stu     4096 May 17 15:53 .gstreamer-0.10
-rw-rw-r--  1 stu  stu      142 May 17 15:52 .gtk-bookmarks
drwx------  2 stu  stu     4096 Mar 29  2012 .gvfs
drwxr-xr-x  2 stu  stu     4096 Jun  8 09:46 .hplip
-rw-------  1 stu  stu   139866 Jun  8 09:46 .ICEauthority
drwxrwxr-x  7 stu  stu     4096 Aug 19  2012 .icedtea
drwx------  2 stu  stu     4096 May 17 13:29 .icons
-rw-rw-r--  1 stu  stu       44 Jul  1  2012 .install4j
drwxrwxr-x  4 stu  stu     4096 Jul 30  2013 .java
drwx------  3 stu  stu     4096 Mar 13  2013 .kde
drwx------  3 stu  stu     4096 Aug 13  2012 .launchpadlib
-rw-rw-r--  1 stu  stu     9636 May  1  2012 libnautilus-gksu.so
-rw-rw-r--  1 stu  stu     9636 Aug 28  2012 libnautilus-gksu.so.1
drwxr-xr-x  3 stu  stu     4096 Mar 29  2012 .local
drwx------  3 stu  stu     4096 Mar 29  2012 .macromedia
drwxr-xr-x  7 stu  stu     4096 Aug 14  2013 .mandelbulber
-rw-rw-r--  1 stu  stu    74842 Aug 20  2013 .mandelbulber_log.txt
drwx------  3 stu  stu     4096 Mar 29  2012 .mission-control
drwxrwxr-x  2 stu  stu     4096 Apr  3  2013 movie
drwx------  4 stu  stu     4096 Mar 29  2012 .mozilla
drwxrwxr-x  2 stu  stu     4096 Apr  3  2013 .mplayer
-rw-rw-r--  1 stu  stu        0 Dec 30  2012 .mtab.fuseiso
drwxr-xr-x  5 stu  stu     4096 Mar  9 11:05 Music
drwxrwxr-x  5 stu  stu     4096 Sep  2  2012 .mypaint
drwxrwxr-x  2 stu  stu     4096 Jul 12  2012 NewFolder
drwx------  4 stu  stu     4096 Mar 25 16:51 .nv
drwxrwxr-x  2 stu  stu     4096 Jun 21  2013 .nvidia
-rw-rw-r--  1 stu  stu     1153 Feb 27  2013 .nvidia-settings-rc
drwxr-xr-x  6 stu  stu     4096 May  2 12:26 Pictures
drwx------  3 stu  stu     4096 Mar 29  2012 .pki
drwxrwxr-x  2 stu  stu     4096 Dec 29  2012 Podcasts
drwx--x--x  5 stu  stu     4096 Mar 14  2013 .pokerth
-rw-r--r--  1 stu  stu      797 Mar 30  2012 .profile
drwxr-xr-x  2 stu  stu     4096 Mar 29  2012 Public
drwx------  2 stu  stu     4096 May 17 09:40 .pulse
-rw-------  1 stu  stu      256 Mar 29  2012 .pulse-cookie
drwx------  6 stu  stu     4096 Apr  6  2013 .purple
drwxr-xr-x  6 stu  stu     4096 Jun 19  2013 PyBitmessage
drwxrwxr-x  2 stu  stu     4096 Feb  9 16:15 .PyBitmessage
drwxr-xr-x  2 root root    4096 May 16 22:45 .rpmdb
drwxrwxr-x  5 stu  stu     4096 Nov 13  2013 .rs
drwxrwxr-x  4 stu  stu     4096 Feb 15  2013 .sabnzbd
drwx------  3 stu  stu     4096 Jun  4 13:26 .sane
drwxrwxr-x  4 stu  stu     4096 May  1  2012 .shotwell
drwx------  6 stu  stu     4096 Apr 26 17:13 .Skype
drwx------  4 stu  stu     4096 Mar 13  2013 .speech-dispatcher
drwxrwxr-x  2 stu  stu     4096 Apr  3  2013 .spumux
drwx------  2 stu  stu     4096 Aug 13  2012 .stardict
-rw-r--r--  1 stu  stu        0 Mar 30  2012 .sudo_as_admin_successful
drwxrwxrwx  2 stu  stu     4096 Jan 19  2013 Sync Folder
drwxrwxr-x  3 stu  stu     4096 Jun  6  2012 .teamviewer
drwxr-xr-x  2 stu  stu     4096 Mar 29  2012 Templates
drwx------  5 stu  stu     4096 Mar 29  2012 .thumbnails
drwxrwxr-x  2 stu  stu     4096 Aug 13  2012 Ubuntu One
drwxr-xr-x  3 stu  stu     4096 May 28 17:03 Videos
drwxrwxr-x  2 stu  stu     4096 Mar  3  2013 .VirtualBox
drwxrwxr-x  4 stu  stu     4096 Dec 13  2012 VirtualBox VMs
drwxrwxr-x  3 stu  stu     4096 Dec 29  2012 virtual-drives
-rw-------  1 stu  stu       53 Jun  8 09:46 .Xauthority
-rw-------  1 stu  stu      868 Jun  8 21:49 .xsession-errors
-rw-------  1 stu  stu     1431 Jun  8 09:44 .xsession-errors.old
root@debian:/# exit
exit
user@debian:~$ sudo umount /mnt/dev/pts
user@debian:~$ sudo umount /mnt/sys
user@debian:~$ sudo umount /mnt/proc
user@debian:~$ sudo umount /mnt/dev
user@debian:~$ sudo umount /mnt
user@debian:~$ 

```

I've not got much of a clue, but I think that went well?

CG

---

### Post by Bashing-om on 2014-06-24
captaingraviton; Hey !

That went outstandingly well ! We will do this at your pace. My primary role is to assist you in what you want to do. I must admit I do look forward to any additional enlightenment I can garner about this our operating system of choice.

Let's put my last thought back in my pocket and see what the result is when you try and boot the install system normally. Get an idea where it is failing. I had in mind to (RE-)install grub ( GRand Unified Bootloader) from that CHange Root environment. However, how about we take a poke and see if we can avoid a sledge hammer approach and try and find out why the system is not booting (??).

So, tell me what happens and what you see when you try and boot normally . 
Else in a failure to boot up:
See if we can boot into the install from the grub menu.

Cold boot the system and as soon as the bios screen clears depress and hold the right /shift/ key -> grub boot menu:
top entry highlighted and the 'c' key for a 'C'ommand line -> grub > prompt.

Let's see what grub knows about what and where.
grub prompt commands:
```

ls -la
ls -la (hd0,msdos1)/vmlinuz
ls -la (hd0,msdos1)/initrd.img
search -f /sbin/init

```
If we can get this far, and these files are present and the paths are "set"; there is a good chance we can boot this sucker.

[INDENT][INDENT]if at 1st, 2nd, 3rd we do not succeed
[INDENT][INDENT][INDENT]we'll try something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-24
Can you read this?

[ATTACH=CONFIG]254216[/ATTACH]

That first command came back with:

```

grub> ls -la
Device hd0: No known filesystem detected - Sector size 5128 - Total size 800*lotsofnumbers*

```

---

### Post by Bashing-om on 2014-06-24
captaingraviton; Yuk .

I just do not know what else we can do to get around this " Sector size 5128 ". That size is an unreal number. All I know to advise at this point is to pull off any of the files you want from that CHange Root and (RE-)install.

I hate to throw in the towel, but with a messed up partition table, and you have tried 'testdisk' and sparring of the superblock, I know of nothing else .

With a untrusty partition table I would have NO faith in the operating system at large.

Unless others can advise better ->

[INDENT][INDENT]think, thank, thunk -> (RE-)install
[/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-24
*"and you have tried 'testdisk' and sparring of the superblock"*

All I did in testdisk was a deep scan. I didn't dare hit continue after it came up with the last set of results. Maybe I'll just risk that and do it tomorrow?

Anyway, it's getting late here so I'll do that tomorrow unless you've written "For God's Sake NO!" when I check again ;)

Update tomorrow..

CG

---

### Post by captaingraviton on 2014-06-26
Well, the latest update is that I decided to pull the pin on this hard drive and wipe it completely. Even Darik's Boot and Nuke is laughing at me (it won't wipe it). I tried re-partitioning it in the gparted that works in the Debian LiveCD (gparted in the other distros won't 'see' the drive) and it pretends to work but then barfs at me when I try to install a fresh OS on it. It annoys me a bit in a way because I still don't know what originally caused this drive to go la-la cookoo on me and some of the self diagnostics that run on it say it's an ok drive? I'm pretty sure the MBR, the Grub and the Linux Pixies have all been having unprotected hex. I just wish I could wipe the damn thing and start again before I go full-on kamakazi suicide mode and attack it with a hammer and chisel. (I'd probably miss)

---

### Post by Bashing-om on 2014-06-26
captaingraviton; OK !

Calm, cool, and collected... cup of coffee ( brandy sure makes coffee great ) and let's smash that drive with 'dd'.
From the liveDVD:
```

sudo dd if=/dev/zero of=/dev/sda bs=1M

```
That will zero out the hard drive at the rate of about 1 Gig per hour. May take several cups to see this through.
To get a status us where 'dd' is at, one can do so from another opened terminal.
see:
```

man dd

```
to get the directions to get a 'dd' status.

I have zero'd out several drives in my past and have good results with dd - made a believer out of me.

[INDENT][INDENT]drastic measures for
[INDENT][INDENT][INDENT]dire straits[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by captaingraviton on 2014-06-27
Another Update:

Before I read your helpful tips, I tried again and again with Boot 'n' Nuke to no avail. I blanked and reformatted the drive in gparted (in the Debian LiveCD) again, repartitioned it again and booted into Ubuntu 14.04 LiveCD. I chose to install a fresh installation. First window stipulated that I must have at least 6GB free with which to install, and, guess what, it was greyed out. I was going insane. 

Then, because I had the side panel of the desktop open, I thought I'd go check for some loose wires again (nothing) but I did find a tiny slip of paper at the back of the casing that my past self had written to my future self, it read;

*"SATA Mode - AHCI MODE. Change the AHCI DID for Linux [enabled]"*

Back when I first changed over to a totally Linux machine I had had problems that I had tracked to the BIOS settings, and so I didn't make the same mistake again, I wrote that and hid it in the casing. So I had a look at the BIOS and yes, those settings needed changing, which tells me that somewhere along the line I'd stuck my FUBAR Stick so deeply into my machine that I'd screwed up the BIOS too.

So my current status is I have now got a fresh install of Ubuntu 14.04 and I'm waiting for a really slow backup/restore (in Deja Doup) to put my ducks back in some sort of row? I'm not too sure that I should mark this thread as SOLVED unless my tale of woe be used as a warning to others?

Either way, I thank you **Bashing-Om** and **Bucky Ball** for your friendly, professional and dedicated services to the terminally useless. 

CHEERS!

---

### Post by Bashing-om on 2014-06-27
captaingraviton; Great !

Lot of time and effort, but - you do good work.
If at this point you are up and running ubuntu, then yes --- mark this thread solved even though the solution was nuking from orbit; Repopulating with the most current release.

testimony to
[INDENT][INDENT][INDENT]whatever it takes
[/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-06-27
All good. Yup, mark it as solved if you're posting from Ubuntu. Post a new thread with a descriptive title in the appropriate area if any issues with backup or anything else. Cheers, good luck and enjoy. ;)

---

