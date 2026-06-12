---
title: "Installation Failure (drops me in busybox)"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by Toxic Tom on 2013-04-09
I am trying to install ubuntu studio 12.10 64bit from a memory stick. Currently the computer is running ubuntu server 12.04 LTS 64bit. I want to completely erase the server OS and replace it with ubuntu studio. Now when I boot from the memory stick and select "install ubuntu studio" or "try ubuntu without installing" or any other option for that matter, I watch the splash screen thing for ages and then I am dropped in busybox with this message
 ```
BusyBox v1.19.3 (Ubuntu 1:1.19.3-7ubuntu1) built-in shell (ash) 
Enter 'help' for a list of built-in commands.
 
(initramfs) _
```
Help what  do I do?

---

### Post by Toxic Tom on 2013-04-09
Deleted

---

### Post by Toxic Tom on 2013-04-09
I am now trying to install 12.04 LTS and getting the same error. I have also received an error saying "panic occured" "attempted to kill init"

---

### Post by Bashing-om on 2013-04-09
Toxic Tom; Hi !

Did you verify the integrity of the .iso file ?
howto: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)[INDENT=3]
hope this helps

[/INDENT]

---

### Post by Toxic Tom on 2013-04-09
I don't think there is anything wrong with the ISO as I have tried both 12.10 and 12.04 with the same problem occurring. Also I have managed to get in today twice after continually rebooting after this error appears. Soon after it has hung and I've had to reboot. I'd just like to be able to get back into it now!

Thanks for replying BTW. It's been a slow day

---

### Post by Bashing-om on 2013-04-09
Toxic Tom;
That error is also indicative that grub (ubuntu's boot loader) is not able to hand off to the operating system. Many times due to a corrupted file.
Try this from the liveCD'
```
sudo fdisk -l ## to determine the boot partition ("*" flagged)
sudo fsck /dev/sda1 ## sda1 assumes same output from "fdisk" as first hard disk, first partition is flagged as bootable
```
adjust accordingly !
"fsck" is ubuntu's file system check and repair utility. [INDENT=3]just try'n to help

[/INDENT]

---

### Post by Toxic Tom on 2013-04-09
Thanks for the help. I just checked the 12.10 iso and it was fine. I'll check the 12.04 one tomorrow. I'll also try the fsck thingy too. Where do I have to input that code?

Also random other question: when partitioning a hard drive, does it matter what order the partitions go in, if so what order should they go in? (Making 3 partitions for root, home and swap)

---

### Post by Bashing-om on 2013-04-09
Toxic Tom;

Input terminal codes:
From the liveCD; try ubuntu mode; booted to the desk top -> key combo ctl+alt+t will give a terminal.
One must run the "fsck" utility on devices that are not mounted, hence the use of the liveCD.

Partitioning:
 In my experience, it does not matter the order that partitions are created, the installer will find the appropriate partitions.(/boot on older drives, make it the first partition).[INDENT=2]regards

[/INDENT]

---

### Post by Toxic Tom on 2013-04-10
Okay but I don't have a live CD, I've been doing this all from USB. I haven't got any disks that are big enough for the iso.

---

### Post by Toxic Tom on 2013-04-10
Right so I just got into Ubuntu in persistent mode (IDK why it worked this time?) and I did fdisk. 2 different partitions were flagged with a * (/dev/sdb1 and /dev/sdc1) what do I do here?

---

### Post by Toxic Tom on 2013-04-10
Sorry for all the posts :P but I have found that sdb1 is my liveUSB and sdc1 is another USB stick that was left in the computer. The hard drive is sda1. Now when I try to install, I get this error "Input/output error during read on /dev/sda1" I also get this error when opening GParted from terminal and when it opens, GParted does not show sda1 in it's list.

---

### Post by Bashing-om on 2013-04-10
Toxic Tom 	;

What can I say ? Until you are able to boot up into ubuntu's "try ubuntu" mode from some means /CD, DVD,pendrive or USB thumb drive//  so we can run a file system check, there is nothing we can do at this point.

Can you boot up an install medium to ubuntu's desktop ?
If not, how may I assist so that it is possible for you to boot to the "try ubuntu" desk top ??
[INDENT=2]
reducing to simplest terms

[/INDENT]

---

### Post by Toxic Tom on 2013-04-10
Thanks, I'm in the "try ubuntu" bit now. What do I do?  ```
sudo fsck /dev/sda
``` returns ```
Attempt to read block from filesystem resulted in short read while trying to open /dev/sda Could this be a zero-length partition?
```

---

### Post by Bashing-om on 2013-04-10
Toxic Tom;

Not the return we would have liked to have seen. File system not happy at all. 
Run this from the "try ubuntu" mode; Terminal code:
```
 sudo fdisk -lu
``` to see if we can read the disk.[INDENT=2]
making progress

[/INDENT]

---

### Post by Toxic Tom on 2013-04-10
```
sudo fdisk -lu
```returns```

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009b1f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7826383     3913161    c  W95 FAT32 (LBA)
```

---

### Post by Bashing-om on 2013-04-10
Toxic Tom;
Something is real screwy here// What in the world !
All I am seeing from that "fdisk" output is a 4Gig usb device (sdb) and nothing at all for what I expected to be the hard disk as "sda". (??)
1. Is the hard drive connected (cables to the controller) ?
2. Are you booting in "try ubuntu" mode - still I would think we should have seen the  sda drive// When I boot off tonight I will verify this.

Lets see if "parted" detects that drive.
Again from the live media in try ubuntu mode - so the partitions are not mounted !
```
  sudo parted /dev/sda unit s print
```[INDENT=2]
which way did he go George ?
[/INDENT]

---

### Post by Bashing-om on 2013-04-10
Toxic Tom;

Yikes !!! ... I confirm that it is possible to have an absolutely apparently good disk drive and installed operating system that the liveCD in "try ubuntu" mode does not see !! Neither "fdisk" nor "parted" recognize this drive.

Peeps -> My info:
liveCD:version 12.04.1
sda: installed os's -> 10.04.4 fully updated and lubuntu 12.04.2 fully updated
sdb: data disk
sdc: installed os -> ubuntu 12.04.2 fully updated and no known problems or difficulties - My primary Operating System !
-----------
From the liveCD "fdisk" nor "parted" recognize disk drive sdc. sdc appears not to exist. When I plug in a usb thumb drive, that usb drive becomes sdc.

@Toxic Tom; I am going to think a lot on this, and see what results from booting an older liveCD and see if the result is the same.
-----------
Can't work on something you can not even see. This may be a real challenge fixing your system.[INDENT=3]
what to do, what to do

[/INDENT]

---

### Post by Toxic Tom on 2013-04-11
Thanks for your consideration, yes the hard drive is connected with a cable (i think esata?) and sdb is the USB stick that I am booting from. The hard drive is blank, formatted with killdisk. Could this be a problem?

The funny thing is that the ubuntu installer (in try ubuntu mode) detects it, but when I try to install onto it I just get "input/output error during read on /dev/sda". Should the hard drive be in IDE or AHCI mode? I think it's currently in AHCI.

Thanks again,

---

### Post by Bashing-om on 2013-04-11
To clear the air; ->peeps -> my sdc drive:
All good now, Livecd now recognizes the drive.

I had suffered a power outage while having a lot going on in my system. When power was restored I booted back up and did the "unpardonable", in that I failed to run a file system check !
This morning, knowing there was an abnormality, I did run the file system check/repair, from both a reboot and from the liveCD.
At this time from the liveCD "fdisk", "parted", and "blkid" recognize the sdc drive ! Whew ! All good in my world.

@ Toxic Tom; Back on your situation. As your drives' a Esata set your bios to AHCI. As you have wiped that drive the partitioning table no longer exist and a file system can not be established. We are going to fix that with GParted from the liveUSB "try ubuntu" mode.

The question presently is what partitioning scheme are we going to use ? Small hard drive == MBR (msdos) while large drives == GPT(EFI).

How big is the drive we are going to install ubuntu onto ?[INDENT=2]
meanwhile back at the ranch

[/INDENT]

---

### Post by Toxic Tom on 2013-04-11
The drive is about 320gb. How are we going to format it in GParted if it's not detected though?

---

### Post by Bashing-om on 2013-04-11
Toxic Tom;
Sorry if I seem confused, because I am. Your post 11 indicated that GParted recognized the disk, just not the partition (??).
Did you run "killDisk" after this ?[INDENT=3]
regards

[/INDENT]

---

### Post by Toxic Tom on 2013-04-12
You know when you click on 'install ubuntu' and you get like an installation walkthrough thing and one of the steps is where you can partition the drive, this bit recognizes the drive. GParted OTOH doesn't. Sorry if I am not explaining this clearly!

---

### Post by Bashing-om on 2013-04-12
Toxic Tom; We need to find some way to recognize that disk, as none of the tools I have suggested thus far work; I think it is time to look at that disk with "testdisk". testdisk is available from ubuntu's software repository.
'Bout the only thing I can think of presently.
[INDENT=3]
Good Luck

[/INDENT]

---

### Post by Toxic Tom on 2013-04-12
Okay, I'll try it out. I wont be able to until Monday though as I am currently away from home. Please update me if you have any more ideas though!

Thanks for your help,

Toxic Tom

---

