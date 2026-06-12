---
title: "[SOLVED] Hardy Install Problem"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by k33bz on 2008-06-13
Ok so I finally go my desktop fixed, after replacing ram, cpu, video card, and finally getting my motherboard repaired. Which guessing they couldnt do, because they sent me a brand new one, exact same model. I put everything together, got my windoze (dual boot) which worked just fine after re-activating it. Then went onto my linux (Fiesty Fawn, kernel 2.6.20-16-generic)

Well it froze during boot up with the boot loader, so I restarted and tried in safe mode. And it froze again, for about 5 mins, right after loading up my device drivers for my usb ports. then gave me this read out:
```
check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev ALERT! /dev/disk/by-uuid/11656662-477a-4445-b24e-279812baa932 Does not exist. Dropping into shell! 
Busybox v1.1.3 (Debian 1:1.1.3-3ubuntu)
Built in shell (ash) Enter 'help' for a list of commands.
/bin/sh: cant access tty; job control turned off
(initramfs)
```

Now I am figuring that maybe my new motherboard, even though it is the same model and everything, isnt working together with my hdd, so I tried to do it with a liveCD, I could access my Windoze HDD with a LiveCD, but it wouldnt see my Ubuntu HDD. (And yes I mean HDD, not just partitions, I have 2 seperate HDDs for my OS, one for MS, and hte other for Ubuntu.)

So can someone please help.
Thanks.

I was told that it would probable be better to just re-install Ubuntu, so i have with Hardy, but I get the same errors.

---

### Post by Pumalite on 2008-06-13
You might need all_generic_ide at the boot line.

---

### Post by Herman on 2008-06-13
I think you should go into your BIOS and check to make sure your hard disks are recognized (detected), and set up properly in there.

Do you have Sata hard drives or Pata (IDE)?

 Check to make sure your cables are plugged in correctly and if they are IDE type hard disks, are your jumpers set correctly (master/slave/cable select), on both hard disk drives and your CD/DVD drive as well?

What output do you get from this command, 
```
sudo lshw -C disk
```?

---

### Post by k33bz on 2008-06-13
> **Pumalite said:**
> You might need all_generic_ide at the boot line.

how do i do that

---

### Post by k33bz on 2008-06-13
> **Herman said:**
> I think you should go into your BIOS and check to make sure your hard disks are recognized (detected), and set up properly in there.

Do you have Sata hard drives or Pata (IDE)?

 Check to make sure your cables are plugged in correctly and if they are IDE type hard disks, are your jumpers set correctly (master/slave/cable select), on both hard disk drives and your CD/DVD drive as well?

What output do you get from this command, 
```
sudo lshw -C disk
```?

The Windows HDD is a SATA, and my Linux one is IDE. And yes BIOS detects both of them, I have it set in BIOS where my IDE boots first, Its the one with the MBR. As far as jumper settings all is in its proper place, If I do mess with the jumper settings on the Drives I get grub errors, anywhere from 13, 17, 18, 21, and 22. Depeneding on the settings I have placed it on. or how I installed it.

Wish I could post the output of that command, I cant boot Linux at all to even enter the command, I will try with a liveCD and post that.

---

### Post by k33bz on 2008-06-13
????

---

### Post by k33bz on 2008-06-14
results from sudo lshw -C disk

sorry if everything is not exact, have to type it from my other screen.

```
*-disk
         description : ATA Disk
         product: SAMSUNG HA250JC
         physcial id: 0
         bus info: scsi@4:0.0.0
         logical name: /dev/sdb
         version: WE20
         serial: S094J1FLC04723
         SIZE: 232gIb (250GB)
         capabilities: partinioned partinioned:dos
         configuration: ansiversion=5 signature=000d83d6
cdrom
         description: DVD writer
         product: 16x16
         vendro: DVDRW
         physical id: 1
         bus info: scsi@5:0.0.0
         logical name: /dev/cdrom
         logical name: /dev/dvd
         logical name: /dev/scd0
         logival name: /cdrom
         version: PTS2
         capabilities: removable audio cd-r cd-rw dvd dvd-r
         configuration: ansiversion=5 mount mount.fstype=iso9660 mount.options=to,noatime,relatime state=mounted status=ready

medium
         physical id: 0
         logical name: /dev/cdrom
         logical name: /cdrom
         configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted

disk
          description: ATA Disk
          product: WDC WD1600JD-22H
          vendor: Western Digital
          physical id: 0.0.0
          bus info: scsi@0:0.0.0
          logical name: /dev/sda
          version: 08.0
          serial: WD-WCAL96050389
          size: 149GiB (160GB)
          capabilities: partinioned partinioned:dos
          configuration: ansiversion=5 signature=e8a9e8a9  
```

---

### Post by Herman on 2008-06-14
Wow! You *typed* all that?  Sorry about that, I thought you would just copy and paste it.

So, your 160 GB Western Digital IDE hard drive is your first hard disk, (/dev/sda), with Ubuntu in it and you have Windows XP in hard disk 2, (/dev/sdb), which is a Samsung 250GB Sata hard disk right?
Alright, thanks for that, I think that clears your motherboard and hardware. 

Okay then, why can't Linux find your correct filesystem for booting in?
> ls /dev ALERT! /dev/disk/by-uuid/11656662-477a-4445-b24e-279812baa932 Does not exist. Dropping into shell! Can you please post the output from 'sudo blkid' here please? You can run that command in a terminal in a LiveCD, and you should be able to just copy the information from that and paste it into your reply post, that would be a lot easier than typing it out by hand. :)
...unless the computer in question can't be connected to the internet for some reason I suppose. 
If it's inconvenient for you, just tell me if the output from 'sudo blkid' includes the specified file system UUID number.

If it appears to contain the file system , but the UUID number has been changed somehow, (by running alien hard disk partitioning software possibly), you might be able to copy the new partition number and edit your GRUB menu with that and your computer should then boot. I'll explain more details about how to do that later if it's needed.

If it still seems that your partitions have disappeared, we will need to run further tests to try to find out what happened and decide what to do next.
> I could access my Windoze HDD with a LiveCD, but it wouldnt see my Ubuntu HDD.

---

### Post by k33bz on 2008-06-14
> **Herman said:**
> Wow! You *typed* all that?  Sorry about that, I thought you would just copy and paste it.

So, your 160 GB Western Digital IDE hard drive is your first hard disk, (/dev/sda), with Ubuntu in it and you have Windows XP in hard disk 2, (/dev/sdb), which is a Samsung 250GB Sata hard disk right?
Alright, thanks for that, I think that clears your motherboard and hardware. 

Okay then, why can't Linux find your correct filesystem for booting in?


Can you please post the output from 'sudo blkid' here please? You can run that command in a terminal in a LiveCD, and you should be able to just copy the information from that and paste it into your reply post, that would be a lot easier than typing it out by hand. :)

no the WD one is the one with XP on it, and the samsung is the one with Ubuntu on it. I will still have to type it all out, hope it aint alot. My dekstop has no internet at this time, only my laptop.

will post results in next post.

---

### Post by k33bz on 2008-06-14
results from sudo blkid

```
/dev/sda1: "UUID5EFC4553FC45271D" LABEL"Local Disk" TYPE-"ntfs"
/dev/loop0: TYPE="squashfs"
```

---

### Post by k33bz on 2008-06-14
no, the partitions are there, they are verified with supergrubdisk, I have tried several different ways to have my linux boot.

---

### Post by Herman on 2008-06-14
:confused: Hmmm, the plot thickens! 

Your Ubuntu hard disk is detected but no file systems seem to be detected there at all.
> no, the partitions are there, they are verified with supergrubdisk, I have tried several different ways to have my linux boot.Or, maybe they are detected by some programs, but not by others. Something strange and interesting seems to be afoot here. 

Let's take a look at your MBRs now, please post the output from 'sudo fdisk -lu',
```
sudo fdisk -lu
```

---

### Post by k33bz on 2008-06-14
```
disk /dev/sda: 160.0 GB. 160041885696 bytes
255 heads, 63 sectros 0f 1*512 = 512 bytes
Disk Identifier: 0xe8a9e8a9

device boot             start           end           blocks  id 
/dev/sda1 *               63    312560639          156280288+  7

system
HPFS/NTFS


Disk /dev/sdb" 250.0GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units= sectors of 1 * 512 = 512 bytes
Disk Identifier: 0x000d83d6

device   boot     start     end             blocks     id       
/dev/sdb1 *     63        476246924      238123431     83
/dev/sdb2      476246925   488392064      6072570       5
/dev/sdb5      476246988   488392064      6072538+      82

system
Linux
Extended
Linux swap / solaris
```

as said before i have to type it all out, i tried to line it all up as best as i could. Notice on the system  description line 1, 2, and 3, correspond with the lines from above.

---

### Post by Herman on 2008-06-14
:) Alright. The partition table looks okay. 

What happens when you run this command from a LiveCD,
```
sudo e2fsck -C0 -p -f -v /dev/sdb1
```Maybe there's something wrong with the file systems. That command should fix your main file system or give some output telling us what to try next.

---

### Post by k33bz on 2008-06-14
> **Herman said:**
> :) Alright. The partition table looks okay. 

What happens when you run this command from a LiveCD,
```
sudo e2fsck -C0 -p -f -v /dev/sdb1
```Maybe there's something wrong with the file systems. That command should fix your main file system or give some output telling us what to try next.

umm that is so wierd

```
e2fsck: No such device or address while trying to open /dev/sdb1
Possibly non-existent or swap device?
```

---

### Post by Herman on 2008-06-14
Your partitions exist in your partition table, but the hard disk doesn't seem to be showing the file system information for some reason.

Try running 'sudo badblocks -sv /dev/sdb1' and see what happens, (you don't have to type the output this time unless it's very breif), sorry about all the typing you've had to do, and thanks for sticking with me.
```
sudo badblocks -sv /dev/sdb1
```
If you get much output from that it will be a bad sign.
If your hard disk is healthy, you should see something like:
Checking for bad blocks 0 to (some number)
Checking for bad blocks (read-only test: done (you will see numbers progressing here while the program is running)
Pass completed, 0 bad blocks found.

Otherwise, you might get a huge list of bad blocks, but I hope not.

---

### Post by k33bz on 2008-06-14
> **Herman said:**
> Your partitions exist in your partition table, but the hard disk doesn't seem to be showing the file system information for some reason.

Try running 'sudo badblocks -sv /dev/sdb1' and see what happens, (you don't have to type the output this time, sorry about all the typing you've had to do, and thanks for sticking with me.
```
sudo badblocks -sv /dev/sdb1
```

Its ok, I rather type as much as i need to to get this fixed. 
anyway, ti reports back as no such device or adress while trying to determine device size......


This is really odd.

---

### Post by Herman on 2008-06-14
Right then. Let's go to TestDisk and we'll see if there's anything there or not.

Well, you could try 'sudo badblocks /dev/sdb', to run the badblocks command on the whole hard disk first, but that might take a while.
If we limit the area we want checked we could just test a sample of your hard disk to see if it's okay. 
Maybe try,
```
sudo badblocks -sv /dev/sdb 10000000
```The next step will probably be TestDisk I think, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html").

---

### Post by k33bz on 2008-06-14
that states

last_block - 0 (last-block)
badblocks: invalid blocks count - last-block


wuestion, can a hdd be password protected by a previous owner, even if it has been formatted, I ask, because all this seem weird, and i received this hdd from a dvdr in a dumpster?

will try Test disk

edited: TestDisk command not found

just noticed the download, which one should i get?

---

### Post by k33bz on 2008-06-14
also please do note, I had recently got ym mother board back from ASUS, was under warranty for repair. everything had worked before i sent, they couldnt fix MOBO so they sent me a new one, XP worked fine after reactivation, but original HDD with Fiesty on it, was reporting same problems as my new HDD (one found in dumpster), was told that it would be better to re-install Ubuntu, so I fished this HDD out so I could install, then transfer data over from original HDD.

---

### Post by Herman on 2008-06-14
> that states

last_block - 0 (last-block)
badblocks: invalid blocks count - last-block
:oops: Oops, sorry, I edited the command after I posted it and realsized I had made a mistake in it, it should work okay now, my appologies.
> wuestion, can a hdd be password protected by a previous owner, even if it has been formatted, I ask, because all this seem weird, and i received this hdd from a dvdr in a dumpster?
I don't know, I haven't seen that problem ... wait a minute, unless it's an encrypted file sys... no, you installed Ubuntu in it yourself didn't you? Or was Ubuntu already installed when you got it?

> will try Test disk

edited: TestDisk command not found

just noticed the download, which one should i get? 	TestDisk only takes a minute to install (temporarily) in the Live CD and it will probably be the next thing we'll try. Yes, when you're ready you can install it and we'll give it a try. 
If you happen to have a GParted Live CD or System Rescue or Knoppix, you might not need to download TestDisk, just swap CDs and run TestDisk from one of those CDs.

---

### Post by k33bz on 2008-06-14
> **Herman said:**
> :oops: Oops, sorry, I edited the command after I posted it and realsized I had made a mistake in it, it should work okay now, my appologies.
I don't know, I haven't seen that problem ... wait a minute, unless it's an encrypted file sys... no, you installed Ubuntu in it yourself didn't you? Or was Ubuntu already installed when you got it?

TestDisk only takes a minute to install (temporarily) in the Live CD and it will probably be the next thing we'll try. Yes, when you're ready you can install it and we'll give it a try. 
If you happen to have a GParted Live CD or System Rescue or Knoppix, you might not need to download TestDisk, just swap CDs and run TestDisk from one of those CDs.


ok, will go back and check the new command and post the results of that. 

I got testdisk downloaded, and transfered to desktop pc, umm, how do i install it, sorry, i tried just executing it bl cliking on it. nothing happend.

Oh and yes, It is unarchived. I see in side /Desktop/testdisk-6.9/linux with a binary file called testdisk_static


yes i have installed ubunut on it myself lastnite

---

### Post by Herman on 2008-06-14
> I got testdisk downloaded, and transfered to desktop pc, umm, how do i install it, sorry, i tried just executing it bl cliking on it. nothing happend. Oh, we install software in Ubuntu a lot differently than the way it's done in Windows. 

With your Hardy Heron, (or Feisty) Live CD running, just type 'sudo apt-get install testdisk', and as long as the computer you're running the LiveCD in is connected to the internet, it should be downloaded and automatically installed in a minute or so.
```
sudo apt-get install testdisk
```

---

### Post by k33bz on 2008-06-14
ok, that test is done with the badblocks

checking blocks 0-10000000
checking for bad blocks (read-only test): done
pass completed, 0 bad blocks found.

---

### Post by k33bz on 2008-06-14
> **Herman said:**
> Oh, we install software in Ubuntu a lot differently than the way it's done in Windows. 

With your Hardy Heron, (or Feisty) Live CD running, just type 'sudo apt-get install testdisk', and as long as the computer you're running the LiveCD in is connected to the internet, it should be downloaded and automatically installed in a minute or so.
```
sudo apt-get install testdisk
```

I can tdo it that way, like i said, my desktop has no internet connection :(

so I already have it downloaded sitting on the desktop of my dekstop, so umm, ya, lol, how do i install it :)

---

### Post by meierfra. on 2008-06-14
> Originally Posted by Pumalite
You might need all_generic_ide at the boot line.

how do i do that

Select Ubuntu at the Grub Menu. But do not press enter, press "e" instead.
At the new screen, select the second line and press "e".

Add "all_generic_ide" to the end of the line. Press "enter" and then "b" to boot.

If this worked, you need to edit menu.lst:

> gksudo gedit /boot/grub/menu.lst

Add "all_generic_ide" to the end of the "kernel" lines.

---

### Post by Herman on 2008-06-14
> my desktop has no internet connection :sad:

so I already have it downloaded sitting on the desktop of my dekstop, so umm, ya, lol, how do i install it :smile: I don't like installing things that way, it's possible, but not the easiest or the best way to do things.

A better idea would be for you to download the latest [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/") or [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")  or [System RescueCD]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.sysresccd.org%2F&ei=qmpTSPndLZKqtQPq65SCAw&usg=AFQjCNHLezgCI1IM3RH_amPHKhYtEeiaEQ&sig2=AH3XQuVcG_iHgQAJ7EDw8A") and run TestDisk from any of those.

---

### Post by k33bz on 2008-06-14
> **meierfra. said:**
> Select Ubuntu at the Grub Menu. But do not press enter, press "e" instead.
At the new screen, select the second line and press "e".

Add "all_generic_ide" to the end of the line. Press "enter" and then "b" to boot.

If this worked, you need to edit menu.lst:



Add "all_generic_ide" to the end of the "kernel" lines.


Whew, that worked, thankyou thank you, thank you, I am bout to edit all the lines with the generic_ide

and thank you Herman, cause you have been so helpful and patient with me.
Hopefully soon I can get internet for my dekstop, so I can use synaptic, or apt-get, or even aptitude.

---

### Post by Herman on 2008-06-14
:) Well I'll be ...

Well done meierfra and Puma! :lolflag:
Sorry k33bz, looks like I got you to do a lot of work for nothing.  Thanks for sticking with me though.

Regards, Herman

---

### Post by meierfra. on 2008-06-14
You didn't give Pumalite a "Thank You" yet. He is really the one who deserves it.

---

### Post by k33bz on 2008-06-14
> **Herman said:**
> :) Well I'll be ...

Well done meierfra and Puma! :lolflag:
Sorry k33bz, looks like I got you to do a lot of work for nothing.  Thanks for sticking with me though.

Regards, Herman


No problem, I learned alot from you.

> **meierfra. said:**
> You didn't give Pumalite a "Thank You" yet. He is really the one who deserves it.

O, sorry, thought it was you that mentioned it way back then, bout to give him a thanks too.,

---

