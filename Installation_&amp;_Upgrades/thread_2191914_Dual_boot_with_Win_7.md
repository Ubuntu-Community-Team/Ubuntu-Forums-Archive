---
title: "Dual boot with Win 7"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by Remember2Wipe on 2013-12-04
Hello there and thanks for viewing my thread. So I got everything ready to install Ubuntu (first time) alongside with Windows 7. This is my first time dual booting o I just want to be sure I'm doing this right.

Everything was all fine and dandy until I got to the installation bit of Ubuntu. 

Here's my Hard Drive layout as viewed through Windows 7 (see pic 1)

In one of my earlier threads, someone said to just install on unused space. When I'm choosing where to install Ubuntu, I just get this screen (see pic 2)

What should I do? Will installing it to that partition erase files?


Thanks in advance

---

### Post by ubfan1 on 2013-12-05
Are you sure they are the same disk?  The windows disk has 22G free, and is 596G total, while sda is 640G with no partitions at all.

---

### Post by fantab on 2013-12-05
Boot with Ubuntu and 'Try Ubuntu without installing', open Terminal [Ctrl+Alt+T], run the following command and post its output here:

```
sudo parted -l
sudo fdisk -l
```

Another thing, was this HDD ever part of a RAID Setup? Get into your BIOS and check what mode is SATA set to....

---

### Post by ubfan1 on 2013-12-05
Also check for an option "Dynamic Disks" under Windows and turn it off if present.

---

### Post by Remember2Wipe on 2013-12-05
Trying this first.

Following this guide. Where it says to click "Convert Dynamic Disk to Basic Disk" is greyed out when using the partition wizard. Does this mean it isn't a dynamic disk?
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by Remember2Wipe on 2013-12-05
Did first thing. A bit confused since it says some apple and mac stuff on there. Never had OS X installed

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?
Model: ATA Hitachi HTS54756 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: hp DVD-RAM UJ8B1 (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      3669MB  3678MB  9306kB               EFI

---

### Post by Remember2Wipe on 2013-12-05
I will say, I've been running this off of a LiveCd for 30 min or so and it's much faster than Win7 right now. Love the interface and everything

---

### Post by oldfred on 2013-12-05
Your Windows does not show an efi partition and Windows only boots from gpt partitioned drives with UEFI which has to have the efi partition for boot files.

I would see what this says:
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

It looks like you DVD has the Mac partition??

---

### Post by fantab on 2013-12-05
> Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table. 

Yes, **Fixparts**, should take care of this for you...

With GPT partition table you don't have to worry about 'Dynamic Disks' so much. And you don't have one.

Like oldfred points out, you don't seem to have an EFI partition of about 200Mb with FAT32, which is a must for UEFI However, I have seen one particular OEM at least, using NTFS for this... Linux will have a problem using NTFS EFI during partition.
Check in your BIOS/UEFI to see what mode it is using to boot: UEFI or BIOS/Legacy/CSM? Although it is a given that Windows will only boot from GPT in EFI mode.

After using Fixparts you should be able to install Ubuntu... but before you do that "Try Ubuntu without installing" and post the output of commands as requested in my post #3.

---

### Post by Remember2Wipe on 2013-12-05
> **fantab said:**
> Yes, **Fixparts**, should take care of this for you...

With GPT partition table you don't have to worry about 'Dynamic Disks' so much. And you don't have one.

Like oldfred points out, you don't seem to have an EFI partition of about 200Mb with FAT32, which is a must for UEFI However, I have seen one particular OEM at least, using NTFS for this... Linux will have a problem using NTFS EFI during partition.
Check in your BIOS/UEFI to see what mode it is using to boot: UEFI or BIOS/Legacy/CSM? Although it is a given that Windows will only boot from GPT in EFI mode.

After using Fixparts you should be able to install Ubuntu... but before you do that "Try Ubuntu without installing" and post the output of commands as requested in my post #3.

First off, thanks to both of you for taking the time to help a noob out here. 

As a noob, I have more questions.

You got a bit technical in that part, would it be possible to...dumb it down a bit? Like as in, step by step instructions? 

Also, as this is my first time using a non-Windows OS, how do I go about installing fixparts? I've downloaded the package and I don't know what to do with the files (no .exe!!!).

Probably seems like I'm not ready for Ubuntu if I can't even install it, but my goal here is to learn :)

---

### Post by Remember2Wipe on 2013-12-05
> **oldfred said:**
> 
It looks like you DVD has the Mac partition??


Why would that be I wonder? I just downloaded the 64 bit ISO and burned to a blank DVD using imgburn.

What effect does this have on installation?

---

### Post by Remember2Wipe on 2013-12-05
Well I'm turning in for the night. Hopefull I can get this solved soon:-({|=

---

### Post by oldfred on 2013-12-05
I started with CP/M which was before DOS, so I am not afraid of the command line, but even changing systems a new command line and entering commands can be an issue (or scary). 

While most applications you normally will use in Linux have gui equivalents, we do not know what gui enviroment you are using. Default is Unity, I use fallback, but their is KDE, LXE and the other favors also. But the underlying commands are all the same so we often give commands to copy or type into terminal as that is easiest to explain. 
You can just copy and paste terminal commands, just be sure that you only do it from sources you trust. 

fixparts is a lower level fix of partition tables on disk, so it is terminal commands. The site you download from has the commands you should run.

I am just copying & pasting from Rods books site. His example uses sdc or the third drive in his system, your should be sda, so you have to edit to sda, which I am doing here. If not sda then change to your drive.
First command backs up just the partition table  info, so worst case we have an easy way to restore. copy parts.txt from your /home to another drive, or flash drive. You can use your nautilus file browser for that copy.
Then you need to use the commands inside fix parts. If it offers to delete stray gpt data say yes. You can use p to display partitions, if they look ok use w to write them which really should just be the same as you have but without the gpt data. Then use q to quit. If for any reason it does not look correct just use q.

**sfdisk -d /dev/sda > parts.txt**
**fixparts /dev/sda**

---

### Post by Remember2Wipe on 2013-12-06
Alrighy then, I'm back and will try the advice

---

### Post by Remember2Wipe on 2013-12-06
Tried my luck with Gparted. I get the following message (don't know if this tells you guys something you don't already know)

/dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?"

---

### Post by Remember2Wipe on 2013-12-06
General/noob question. I downloaded the package "gptfdisk-0.8..8-1.src.rpm"

Left it in downloads (I opened the file viewer and didn't recognize any file types :/)

Ran the commands[B]
sfdisk -d /dev/sda > parts.txt[/B]
**fixparts /dev/sda**

I'll just post terminal info as that'll probably help more
> [COLOR=#ff0000][Tried Gparted here][/COLOR]
[B]ubuntu@ubuntu:~$  sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gparted is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo fixparts /dev/sda
sudo: fixparts: command not found
ubuntu@ubuntu:~$ sudo fixparts /dev/sda
sudo: fixparts: command not found
ubuntu@ubuntu:~$ sfdisk -d /dev/sda > parts.txt
/dev/sda: Permission denied
[/B][COLOR=#ff0000][/Tried Gparted Here][/COLOR][B]

sfdisk: cannot open /dev/sda for reading
ubuntu@ubuntu:~$ fixparts /dev/sda
The program 'fixparts' is currently not installed. You can install it by typing:
sudo apt-get install gdisk
ubuntu@ubuntu:~$ sudo apt-get install gdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gdisk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 336 kB of archives.
After this operation, 760 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/main gdisk amd64 0.8.7-1 [336 kB]
Fetched 336 kB in 0s (754 kB/s)
Selecting previously unselected package gdisk.
(Reading database ... 168741 files and directories currently installed.)
Unpacking gdisk (from .../gdisk_0.8.7-1_amd64.deb) ...
Processing triggers for doc-base ...
Processing 33 changed doc-base files, 1 added doc-base file...
Processing triggers for man-db ...
Setting up gdisk (0.8.7-1) ...
ubuntu@ubuntu:~$ sfdisk -d /dev/sda > parts.txt
/dev/sda: Permission denied

sfdisk: cannot open /dev/sda for reading
ubuntu@ubuntu:~$ fixparts /dev/sda
FixParts 0.8.7

Loading MBR data from /dev/sda
Problem opening /dev/sda for reading! Error is 13.
You must run this program as root or use sudo!

Unable to read MBR data from '/dev/sda'! Exiting!

ubuntu@ubuntu:~$ 
[/B]

---

### Post by Dennis N on 2013-12-06
> **Remember2Wipe said:**
> General/noob question. I downloaded the package "gptfdisk-0.8..8-1.src.rpm"

Left it in downloads (I opened the file viewer and didn't recognize any file types :/)


This is the wrong type of package for Ubuntu. You should download [B]fixparts_0.8.8-1_amd64.deb
[/B] for a 64-bit system, or** fixparts_0.8.8-1_i386.deb** for a 32-bit system.

---

### Post by oldfred on 2013-12-06
The .rpm are for Redhat and its family of Linux distributions.
The .deb are for Debian and its family of Linux.
Mostly minor differences on locations of some key files, but one can be converted to another, but best not to have to.
You will have to double click on the .deb file to install it. Then it should work.

You need sudo on the sfdisk command. I never remember is sudo required, but if it comes back with permission denied and I did not use sudo then I just try again with sudo.

---

### Post by Remember2Wipe on 2013-12-06
Thanks

---

### Post by Remember2Wipe on 2013-12-06
Thanks. Guessed the mistake was something stupid](*,)

EDIT: Downloaded [fixparts_0.8.8-1_amd64.deb]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.8/fixparts-binaries/fixparts_0.8.8-1_amd64.deb/download") and when I open began to install it in software center it says: [B]
[SIZE=4]This Package if Bad Quality[/SIZE]
The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.[/B][I]
Lintian check results for /home/ubuntu/Downloads/fixparts_0.8.8-1_amd64(1).deb:
E: fixparts: maintainer-address-malformed rodsmith <rodsmith@nessus>"


[/I]Should I be concerned?

Ya, sorry for asking so many questions. Must be getting pretty annoying on your end.

Edit Dos: Ignored and installed. Package Operation failed
Info:
>  Selecting previously unselected package fixparts. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 168761 files and directories currently installed.) 
Unpacking fixparts (from .../fixparts_0.8.8-1_amd64(1).deb) ... 
dpkg: error processing /home/ubuntu/Downloads/fixparts_0.8.8-1_amd64(1).deb (--install): 
 trying to overwrite '/usr/share/man/man8/fixparts.8.gz', which is also in package gdisk 0.8.7-1 
Processing triggers for man-db ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--install): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 

---

### Post by oldfred on 2013-12-06
That was the version I downloaded a while back. I tried to reinstall and it gives me an error but that is because it already is installed.

I have not seen that error, but if you downloaded it from sourceforge it should be ok.

---

### Post by Remember2Wipe on 2013-12-07
Getting ready to just end this thread. Will try downloading Fixparts again. If that doesn't work then I'll backup data that I want to keep and start fresh. I have the Windows Installation disc so it's not a problem. If I was to start over, what could I do to make sure I don't make these mistakes again so I could (hopefully) have a cleaner run through this?

---

### Post by oldfred on 2013-12-07
The issue is the when Windows converts a gpt drive to MBR(msdos) it does not do it correctly and leaves gpt backup partition data on drive. 
You have to fully reformat and fixparts is the easiest way to fix that issue.
Just about everything else is a full zero out entire drive and start over.
Normally fixparts just works. not sure why you are having so many issues. 
Are you running it from the live installer?

---

### Post by fantab on 2013-12-08
If you want to start afresh then BACKUP all your important DATA.
Boot with Ubuntu DVD/USB, "Try Ubuntu without installing", open terminal [ctrl+alt+T] and run the following command:
```
sudo dd if=**/**dev**/**zero of=**/**dev**/**sda bs=512 count=1
```

This will zero out your HDD... all data and the partition table and its backup will be removed.

Open Gparted.

Look under 'Device' on the menu bar, you will have an option to '*create a new partition table*', create it. Default will be '**msdos**'. If you go into 'Advanced' you have more options from dropdown, including **GPT**.

A quick note about 'msdos' and GPT.
**msdos/MBR**: is almost 30 years old and is being phased out. It does not support HDD more than 2TB/2000Gb. It has only 4 Primary Partitions limit. To overcome this Limitation we use an EXTENDED partition which can furter contain 100 or more LOGICAL partitions. MBR/msdos is compatible with BIOS. 

**BIOS has been replaced with newer UEFI**. UEFI deals/communicates better with newer hardware.
[More on UEFI]("http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement").

**GPT**: is a requirement for UEFI. This is the present and the future. It supports HDD more than 2TB. It have more than 100 PRIMARY Partitions, hence no need to create an Extended Partition.
More [Advantages of GPT]("https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT")

If your BIOS/UEFI supports EFI booting then I recommend that you install your OS in EFI mode [you can enable EFI boot in UEFI/BIOS]. For EFI to work you need GUID Partition Table [GPT] on you HDD.
To be able to boot in UEFI you need a dedicated partition on your GPT HDD of about 500Mb or less, formatted with FAT32 with a 'boot' flag.
Windows can install and Boot from GPT ONLY in UEFI/EFI mode.
[How to install Windows 7 in UEFI/EFI mode]("http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html").

Ubuntu on the other hand can boot from GPT both in 'Legacy/MBR/CSM' and UEFI mode.
However, if you are dual-booting then you have to use ONE mode ONLY for both (all) your OS. In other words, if you install Windows in UEFI then Ubuntu must also be installed in UEFI.
To install Ubunt in UEFI mode you MUST boot your DVD/USB in UEFI/EFI mode only.
More info: [https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode)

If you want to opt for 'msdos' boot then you can, as well. Its your call.

Suggested Partition Scheme for:
```
**GPT: (all partitions are Primary)**
500Mb FAT32 'boot' flag (for EFI)
50Gb NTFS Windows C: 
200Gb NTFS Windows D: (This partition can be used to share data between Windows and Ubuntu)
20Gb Ext4 '/' Ubuntu system files
20Gb Ext4 Free (In case you want to try another Distro or another ubuntu flavor or version)
4Gb SWAP
All the remaing GB Ext4 (you can either use this as '/home' or just plain Data partition)
```

[Adjust the Size of your data parittion accordingly and based on your needs]

```
**MBR/'msdos': (Only 4 Primary Partitons)**
50GB Primary NTFS Windows C:
200Gb Primary NTFS Windows D:
20Gb Primary Ext4 '/' Ubuntu
All the remaining Gb EXTENDED
20Gb Logical Ext4 Free
4Gb SWAP
All the remaining GB Logical Ext4 (Linux data partition).
```

Choose you option wisely.
Good Luck...

---

### Post by Remember2Wipe on 2013-12-08
I took a break for this for a day. I've been messing around with partitions in the past couple of days. Through messing around I learned a lot and can better understand other pieces of advice here. And everything is so organized :)

 Anyway, regarding OldFred, I'm running fixparts off of the Ubuntu livecd.

Thanks for the info fantab. If this doesn't work then I'll come back to your information.


> To be able to boot in UEFI you need a dedicated partition on your GPT  HDD of about 500Mb or less, formatted with FAT32 with a 'boot' flag.

Alright,
How to set flags? 
What is a dedicated partition? 

I've been using MiniToolPartition Wizard for partitioning if that makes any difference. Are those options only for GParted? I don't see them anywhere.


Seriously, huge thanks for sticking to this thread for so long. Very helpful

---

### Post by oldfred on 2013-12-08
I only know gparted. 
A dedicated partition is just one set as the efi partition for UEFI boot. Not for BIOS boot.
If you have gpt and Windows you have UEFI boot as Windows only boots from gpt partitioned drives with UEFI.
If your drive is MBR(msdos) partitioned you must be booting with BIOS even if motherboard has UEFI.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    
Ubuntu will boot from gpt with either BIOS or UEFI boot modes and new versions of Ubuntu installer will boot in either mode and then install in that mode. But drive need to be correctly partitioned to match unless a totally new drive.

Most of all the links explaining this is in the link in my signature.

---

### Post by Remember2Wipe on 2013-12-09
Do these partitions look acceptable? Just want a final opinion before I try installing again.

---

### Post by oldfred on 2013-12-09
It looks reasonable.
It shows operations pending, so it is like gparted in that you have to run the changes.
I usually try not to queue changes as sometimes they seem to conflict or if an error somewhere it causes issues. Hopefully your minitool works ok.

Did you run fixparts? Or does mintool have a way to remove the backup gpt partition table?

---

### Post by Remember2Wipe on 2013-12-09
I'm going to try fixparts again later tonight. I was just laying out partitions, I haven't applied the changed yet. I don't think minitool has a way to do that.

Got to go, homework to do!

Will hopefully update later tonight

---

### Post by Remember2Wipe on 2013-12-12
Hello and thank you to anyone who is still following this thread. Sorry I am a bit later than I said I would be, school:(. 

I gave it a shot for the first time in about a week. I'v successfully installed fixparts now. Did the same thing as last time but this time it worked. Not complaining

Anyway, what do I do now? I've been following the instructions as laid out on [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/).

I open up the terminal and paste the following into the terminal:
# [B]fixparts /dev/sdc

[/B]It just jumps down to the next line without showing any sign of it having done anything. Shouldn't it look more like the stuff posted below? I tried changing the last letter to "a" and "b" (I have no idea why, thought it might do something). Anyway, I'm pretty open to working on this for the rest of the week. No more long absences

> # **fixparts /dev/sdc**
FixParts 0.8.8

Loading MBR data from /dev/sdc

MBR command (? for help): **p**

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 3981312 sectors (1.9 GiB)
MBR disk identifier: 0x00000000
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *             62      1171799   primary              Y      0x07
   2               1171800      1562399   primary              Y      0x83
   3               1562462      3124799   primary     Y        Y      0x0C
   5               3124862      3980213   logical     Y        Y      0xAF

MBR command (? for help):


---

### Post by fantab on 2013-12-13
You are checking your HDD right? Then the HDD will be /dev/sda.

So you will 
```
sudo fixparts /dev/sda
```

If there are any errors then you will get the following warning:
> NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N):


Select 'Y' to fix the issue. 
To exit fixparts type 'w' to save an exit.

---

### Post by Dennis N on 2013-12-13
> **Remember2Wipe said:**
> 

I open up the terminal and paste the following into the terminal:
# [B]fixparts /dev/sdc

[/B]It just jumps down to the next line without showing any sign of it having done anything. Shouldn't it look more like the stuff posted below? I tried changing the last letter to "a" and "b" (I have no idea why, thought it might do something).

You don't want the # with your command. # means what follows is not a command but a comment. That's why nothing happened. Second, shouldn't the drive be sda as shown in post #1? Third, you need to precede the command with sudo, which gives you temporary powers to run such tools which can modify things.

In summary, try:

**sudo fixparts /dev/sda**

Hope it works.

---

### Post by fantab on 2013-12-13
In the context, '**#**' is not a comment but indicates 'root' privilege.

---

### Post by Remember2Wipe on 2013-12-14
Followed your advice.

> 
ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.8

Loading MBR data from /dev/sda

NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N): y
Erasing GPT data!

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

MBR command (? for help):    


Is it done?

I think I'm reaching the END!! It detects muh partitions now, but when I select my ext4 partition it says "No Root File system is defined. Please correct this from the partitioning menu."

Assuming it's an easy fix?

---

### Post by oldfred on 2013-12-14
With manual partitioning you have to create partitions (+), unless you did that in advance (change), but  then still have to select partition, tell system what format to use, ext4, and what mount point like / (root). You can also have partitions for /home also. Swap has no format. If created in advance it seems to automatically find swap.

---

### Post by Remember2Wipe on 2013-12-14
Created an ext4 partition beforehand. Just did what you did in second screenshot now I think it's good

Posting one lost screencap before install. Everything look good?

---

### Post by Dennis N on 2013-12-14
> **Remember2Wipe said:**
> Created an ext4 partition beforehand. Just did what you did in second screenshot now I think it's good

Posting one lost screencap before install. Everything look good?

The boot loader should **not** be installed to sda6, but to sda. Fix that choice. Otherwise looks ok.

---

### Post by Remember2Wipe on 2013-12-14
Whew. Forgot I changed that LOL. Good thing you caught that

Whew *wipes sweat from forehead.


See anything else?

 Also, not really vital to installation but what do the mount point options do? I just copied the other guys example but I'm curious

---

### Post by Dennis N on 2013-12-14
I usually use a setup like you have done. There is no separate home partition. I have done it with separate home also, but this seems more space efficient to me, and you don't have to be concerned about one partition (home or root) filling up while the other has unused space.

---

### Post by oldfred on 2013-12-14
If you are talking about all the other standard Linux mount points that is old style or for servers. Some users may want specific partitions for certain parts of the system like a server install. Most desktops just need / or maybe / & /home. And unless you have lots of RAM some swap is suggested.

Just about every system folder can be another partition.
 Explanation of file structure
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)

---

### Post by Remember2Wipe on 2013-12-14
Installation finished. I think I can officially say #rekt.

Huge thanks to everyone who helped me through this. I learned A LOT

---

### Post by oldfred on 2013-12-14
The fixparts site has several versions. You need to download the .deb version which is for Debian based which Ubuntu is based on. Then it is somewhat like an exe in that you just have to double click on it and it will install.
But it is a command line tool and you have to then in terminal run the commands. I think the site shows it without sudo as he uses a different version of Linux where you change to administrator and then just run commands. You will need sudo in front of the example commands on the fixparts site.

I still forget which commands need sudo, so when you get a error that you do not have permission or rights try again with sudo in front as that is the way Ubuntu gives temporary superuser rights to the administrative user.

---

