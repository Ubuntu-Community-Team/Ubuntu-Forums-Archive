---
title: "Dual boot plus a VMWare setup?"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by wrycatcher on 2007-01-26
This might be a bad idea, but here's basically what I'm thinking of doing to my somewhat weaker desktop dual-boot (Ubuntu Edgy and WinXP) machine.

Setup is currently basically as follows:

[INDENT]hda (40 GB)- Ubuntu (all linux partitions) w/ a small partition (FAT) for MBR which Windows insisted I have on the C drive[/INDENT], maybe because C was the bootable drive??
[INDENT]hdb  (40 GB)- Windows XP Professional (NTFS), almost a default install, only a couple apps really added (Age of Empires is one and a USB web cam I use with Messenger Live being the other) [/INDENT]

I am thinking of shrinking the hdb (40 GB) NTFS partition down to utilize the hdb to test out VMWare with Win98 and Windows XP virtual machines from within Ubuntu.   I'm also playing with the idea of partitioning a few GB for a "shared" storage (FAT32).   I'm thinking of slicing it up something like this:

hdb1 (FAT32) 15 GB - shared storage between Linux and my dual-booted WinXP image
hdb2 (NTFS) 10 GB - Windows XP Professional
hdb3 (**???**) 15 GB - Virtual machine files for Win98 and WinXP.  

When I install the guest OSes from within the VM's, I think I can just select FAT32 or NTFS without impacting the "real" partition table, but I'm not sure.

NOTE:  If I find that my virtual windows XP via VMWare Server inside Ubuntu works well enough with what I use it for, I might decide to blow away the hdb2 partition completely and stop dual booting altogether.  However, I don't want to do that until I am content with the VMWare solution.  I am intrigued by the prospect of running Win98 using VMWare as I have wanted to run some really old school games there, stuff that won't run in XP under any "compatibility" mode.  Being able to run 98 using a VM would be _very_ a convenient solution.  

I'd really appreciate any advice or quick tips now before I embark on what seems to be a somewhat interesting experiment!

---

### Post by Buck2348 on 2007-01-26
I'm far from an expert.  I did have Win XP Home running on VMware on a 2-disk machine dual booting Win XP.  I have only 512 M RAM and I assume that's the main reason both Ubuntu and the VM XP ran a little slow.  Also, if understand your plan, you want to make a partition on hdb for the guest systems.  The virtual machines can access a partition outside VMware only through networking.  They use virtual partitions inside VMware otherwise.

I'm sure someone else can give you some better info/advice.

Buck

---

### Post by wrycatcher on 2007-01-29
Well, I hit a snag (with booting off Windows CD), but I think I have figured out a solution.  I have to hit F2 when starting the VM to select the boot order and put the CD drive higher in the boot sequence.  I also believe my Windows 98 CD isn't bootable, so I have to figure out how to install this as a VM...suggestions?

As to file system, I have guessed that I will want to store my virtual machine files on a Linux-formatted  (EXT2/EXT3) partition?   Since Windows isn't accessing the file system directly but rather through the VMWare Server layer, the file system doesn't need to be FAT32...I haven't tested that theory, but seems to make sense to me.

---

### Post by Tanker Bob on 2007-01-29
> **wrycatcher said:**
> Well, I hit a snag (with booting off Windows CD), but I think I have figured out a solution.  I have to hit F2 when starting the VM to select the boot order and put the CD drive higher in the boot sequence.  I also believe my Windows 98 CD isn't bootable, so I have to figure out how to install this as a VM...suggestions?

As to file system, I have guessed that I will want to store my virtual machine files on a Linux-formatted  (EXT2/EXT3) partition?   Since Windows isn't accessing the file system directly but rather through the VMWare Server layer, the file system doesn't need to be FAT32...I haven't tested that theory, but seems to make sense to me.

I have a very similar setup.  I am running two WinXPPro SP2 VMs under Kubuntu edgy on a 320GB drive, plus have a separate 60GB WinXP Pro drive set up for dual boot.  The best approach for the VM "disk" is to create it as a file on your Linux partition.  I have mine under /home/username/.  The host (linux) doesn't care how you format the VM disk.  Both my guest "disks" are NTFS.

Buck2348 is correct that the only way to share data across VMs and the host is through VM shares which are part of the VM networking layer.  Inside VMWorkstation (or Server), tell the VM app each host disk/directory that you want to share on each VM.  Once you install VMTools in your guest system, VM shares show up as another network.  Simply map drive letters in the guest to the appropriate network shares like you would in any network setup.

For overall partitioning on the 320GB drive, I just have a small ext3 boot partition for Kubuntu (because my old BIOS won't boot partitions containing more than 1024 cylinders), one huge ext3 partition for all my applications and data (mapped in Kubuntu as "home"), and a 1GB linux swap partition.

That said, having a common FAT32 partition for swapping data w/o network shares is a good idea.  I would suggest using your XP drive as the data swapping medium.  The network layer should resolve the issue of Win98 not reading NTFS partitions, but I've never tried that.  Another issue is that many version of Linux will read but not write to an NTFS partition.  I have an external 120GB USB2 backup hard drive which I use for swapping data quickly.  Note that it will belong to the linux host and is only accessible to the guest Windows OS as a VM shared drive.  I don't know of any way around this.  If all you will use if for is to swap stuff, you don't have to make that partition very large.  Since the USB2 drive is my backup, I use much less than 1GB for this swapping task.  I have not made any part of my Kubuntu host ext3 partitions accessible to my VMs.

I'm not an expert by any means, but this setup works great for me.  There may be better ways to execute your plan which others may offer.  So far, I'm very impressed with VMWare's software and the whole idea of VMs.  If you suspend them in between sessions, they come back up in a minute or two ready for use again.  I use one VM to ActiveSync my Windows Mobile PDA every day since linux doesn't yet support this action.  It takes just a few minutes in the morning to do this.  Dual-booting would take most of 30 minutes with my setup.  I haven't booted to the WinXP dual-boot disk in several weeks, but I access the data stored on it all the time both in Kubuntu and the VMs.

Your goal of running Win98 in a VM is exactly why VMs exist (VMWare - "Because one OS isn't enough"), and it sounds like you're headed in the right direction.

Oh - the Win98 boot disk.  Most Win98 CDs were not bootable.  Win98 usually came with a floppy disk to boot the computer, then would run the setup on the CD.  You can create a bootable floppy with your WinXP dual-boot setup, then use that floppy to boot the naked VM to setup Win98.  You can even rip the Win98 CD to an iso file, then point the VM's CD "drive" to that iso file.  That's what I did with my XPPro CD.  This is especially helpful if you blow away several VMs looking for the perfect solution.

Sheesh, this has turned into a book.  Hope some of it helps.

---

### Post by wrycatcher on 2007-01-29
Thanks Tanker.   Sounds like a good setup you have.   We've all been there when it comes to wiring some of this stuff together (VMWare, boot diskette images, setup CD, heck I've even mucked with FreeDOS and some "boot manager" images).  I've learned a lot.   Fortunately I was around in the early DOS days and so I can find my way around the basic boot disk and DOS utils.  Ah, the memories...the hours of tweaking, trial and error, and re-installations.

The funny part of this is I love my Ubuntu OS (Edgy).   The issue is getting all my "former PC life" migrated and merged into that in a nice, tidy way without having to dual-boot or second machine. Tthat's the goal for me, just one machine with one bootable host OS, and as many VM's as I need (right now, just Win98SE and WinXP, but maybe I'll try BSD or other Linux versions at some point.  Very nice inside a VM (or alternately a "LiveCD").  I like choices and freedom, but I also value simplicity and an intuitively-structured and managed environment.

---

