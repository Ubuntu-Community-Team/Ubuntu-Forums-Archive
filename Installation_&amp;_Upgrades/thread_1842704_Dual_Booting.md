---
title: "Dual Booting"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by sovelliss06 on 2011-09-12
So I think I might be in a kind of pickle. I had windows installed on my hard drive before, and installed ubuntu 11.04 over it, completely wiping windows. I decided (after trying to play some games on ubuntu) that I wanted to have a partition of windows, so I tried to boot with windows, but my windows installation CD won't recognize the hard drive. I, instead, reinstalled ubuntu on a smaller partition with a FAT32 buffer for data transfer between the two OSs, and an unwritten NTFS format for windows to be installed on, but the windows installation still won't recognize the hard drive. I looked around and found this.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

    About halfway down it mentions that windows needs some "boot record"? I'm not sure how this affects the system to prevent it from recognizing the hard drive but whatever I suppose. So I have a couple questions...

1. What are GRUB and the MBR and what  exactly do they do?

2. How can I get windows to recognize my hard drive?

3. Would it be easier for me to just wipe the hard drive and start over installing windows first, and how would I do that?

---

### Post by Hakunka-Matata on 2011-09-12
Hi, welcome to the forums.

Please post the output of ```
sudo sfdisk -luS
```

---

### Post by sovelliss06 on 2011-09-12
....and voila

raatz@Un-Versed:~$ sudo sfdisk -lus
[sudo] password for raatz: 
unrecognized format - using sectors

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048 195311615  195309568  83  Linux
/dev/sda2     195313662 293083135   97769474   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     195313664 293083135   97769472   b  W95 FAT32

Disk /dev/sdb: 1018 cylinders, 124 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/128/22 (instead of 1018/124/62).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *      1128   7831551    7830424   c  W95 FAT32 (LBA)
        start: (c,h,s) expected (0,51,7) found (0,1,1)
        end: (c,h,s) expected (1023,127,22) found (970,127,22)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

---

### Post by YesWeCan on 2011-09-12
Zut alors! Que faites vous ici?
Je ne sais pas le mot pour "extended partition". Desole.
:p

---

### Post by YesWeCan on 2011-09-12
Vous ne pouvez pas mettre les Fenetres dans le partage etendu.

---

### Post by sovelliss06 on 2011-09-12
I'm here to find out how to get my computer to actually work for me rather than against me. How would an extended partition help? I'll look about I suppose.

---

### Post by YesWeCan on 2011-09-12
Sorry about that. You cannot install Windows in an extended partition. Delete sda5 and sda2 and it will work. :)

---

### Post by sovelliss06 on 2011-09-12
I've got a third unallocated space of about 100 gigs and it still won't recognize it. I tried formatting it into ntfs so it would be more windows friendly and still nothing. I'll try your suggestion though.

What if I just cleared the hard drive? How would I do that?

---

### Post by sovelliss06 on 2011-09-12
I deleted the FAT32 and it's extension, and tried to install and got the same message.This is my new setup, i have about 140 gigs unallocated, and in the windows setup all it says is

[I]Unknown Disk:
There is no disk in this drive.

[/I]raatz@Un-Versed:~$ sudo fdisk -lus
[sudo] password for raatz: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a353

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   195311615    97654784   83  Linux


If i could just clean the  whole hard drive and put it back to it's default state I'm sure I'd be fine. How do I wipe the HHD? I have no options for it in BIOS and I can't seem to find a way to do it in GParted because I need to be logged in to use it, and then I don't have the ability to unmount.

---

### Post by YesWeCan on 2011-09-12
"There is no disk in this drive" is a reference to a removable media device like a CD or floppy. This is not to do with your HD.
I dont think reformatting the drive will help, but you can run Disk Utility and click on Format Drive and choose MBR. You have to do this from a live CD.

---

### Post by mastablasta on 2011-09-12
> **sovelliss06 said:**
>  
If i could just clean the whole hard drive and put it back to it's default state I'm sure I'd be fine. How do I wipe the HHD? I have no options for it in BIOS and I can't seem to find a way to do it in GParted because I need to be logged in to use it, and then I don't have the ability to unmount.
 
you need to boot from a liveCD disk or liveUSB then and only then you can use gparted to fully modify the disk. so boto up the OS, delete the partitions, format the whole thing in NTFS.
 
then reboot with windows disk, use their utility to create one partition. one for the os the other one to use later. and install the OS (it should be a primary partition for the win OS). Then once done install Ubutnu on the free space left on disk. 
 
linux can see NTFS Partition. windows can also see linux partitions with propper tools (for example : [http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)). if you don't want to use the tools then create an NTFS partition. but you can do this later when installing ubuntu or even after ubuntu is already installed.
 
more info on side by side dual boot: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by sovelliss06 on 2011-09-12
Okay, thanks all. I'll give it a shot at some point tomorrow. I really appreciate the help for this. I'll be back with more results.

---

### Post by sovelliss06 on 2011-09-13
Okay, so I got the livecd to erase and reformat the hard drive, which didn't fully take care of the problem so I ended up using an application to return the hard drive back to default. I have windows installed right now (not at my comp) and I'm going to install ubuntu when I get back to it. 
    I had another question though. I stated in my initial post that I had a FAT32 partition for file transfer between the two systems, but not having had the chance to use them yet I'm not sure how they work. If anyone could give me some beginners tips or pointers on installation or use or even a link to an online guide I would really appreciate it. 

Thanks for all the help everyone. I'm glad this community exists and that you guys DO actually care.

---

### Post by Hakunka-Matata on 2011-09-13
> **sovelliss06 said:**
> Okay, so I got the livecd to erase and reformat the hard drive, which didn't fully take care of the problem so I ended up using an application to return the hard drive back to default. I have windows installed right now (not at my comp) and I'm going to install ubuntu when I get back to it. 
    I had another question though. I stated in my initial post that I had a FAT32 partition [COLOR=Red]for file transfer between the two systems[/COLOR], but not having had the chance to use them yet I'm not sure how they work. If anyone could give me some beginners tips or pointers on installation or use or even a link to an online guide I would really appreciate it. 

Thanks for all the help everyone. I'm glad this community exists and that you guys DO actually care.

Make a ntfs partition, give it a label that you recognize as your "go between" partition.  Both Ubuntu and WIndows can read & write to the partition.  most people choose to use a ntfs formatted partition instead of a FAT 32 partition.

---

### Post by sovelliss06 on 2011-09-14
Any particular reason to use ntfs or is it just preference? Also, one more question, Is it possible for me to switch over to Windows and Vice-versa without having to restart my computer every time?

---

### Post by SecretCode on 2011-09-14
fat32 doesn't support files larger than 4GB, that's one reason to use ntfs. And there's no real reason not to use ntfs.

To your second question, the basic answer is no, you have to restart. The truth is you can use a virtualisation tool like VirtualBox and some complicated work to make it treat the physical windows partition as a virtual disk. But unless you are very careful, windows thinks you are booting it on different hardware and will trigger activation or even bluescreen.

---

