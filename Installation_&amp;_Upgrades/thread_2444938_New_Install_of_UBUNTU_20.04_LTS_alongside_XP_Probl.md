---
title: "New Install of UBUNTU 20.04 LTS alongside XP Problem- No Boot"
date: 2020-06-06
forum: Installation &amp; Upgrades
---

### Post by zeekstern on 2020-06-06
First of all, I created a Live DVD and played with Ubuntu for a day or two and did not experience any hardware or driver issues. Everything worked great, except for me. I wrote a short version of the problem and a long version that details exactly what happened. I know a lot of people don't like to read posts that are the size of a book.


Here is the short version:))


I tried to install UBUNTU 20.04 LTS version alongside my old Win XP pc. I ran into the problem where I think Grub did not get installed. I do not get the choice of Ubuntu or XP when I boot. It just goes to XP like Ubuntu isn't installed. So I'm not sure where to go from here. If there is a way to install Grub, that would be fine. If I should remove everything and start over, that is fine too, if someone tells me how.:)) My disk info is below. And the Long Version of exactly what happened during my attempt to install is also below. 


Disk 0 /dev/sda 320GB drive with Win XP installed on C: drive - Current XP system Boot drive
Disk 1 /dev/sdb 250GB drive with Win XP installed on F: drive - Old XP system- used for storage


LONG VERSION:


When I began the installation I got up to where I had to select which disk drive to use. Both drives showed up. I wanted to double check my disk config so I went back a screen and then decided to quit the Ubuntu install. I rebooted and came up in Windows, checked disks etc.


Then started the install the second time. After clicking Install I got a weird msg stating something like checking /flush or /pool filesystem or something like that. After a few minutes the Install proceeded like it did the first time. When I got to the where I was supposed to select whick disk to use, I was only presented with 1 disk this time and not able to even select the other disk.


This is exactly what I got:


The following partitions are going to be formatted:
partition #3 of SCSI4(0,1,0)(sdb) as
partition #5 SCSI4(0,1,0)(sdb) as ext4


Note that partition #3 does not have ext4. The install proceeded and I got to the screen to tell it my PC name and my name/user name. I clicked on the NO Password and then continue. I waited about an hour and the screen did not change and there was no disk activity. I thought the install had completed and the screen was just hung up so I rebooted.


The reboot did not come up where I could select XP or Ubuntu so I am assuming Grub did not get written out. I did the # file -s /dev/sda and sdb and Grub did not appear in either MBR or boot partition. 


So, I don't know where to go from here. I have no problem with removing/deleting Unbuntu and start over if necessary. Any help is greatly appreciated.


Thanks
Zeek

---

### Post by ubfan1 on 2020-06-06
Did you hashcheck the downloaded ISO and run a media check on the install media you created?  Does the install media boot on other machines, in other ports?  How much memory do you have, maybe Lubuntu would be better if memory is minimal.

---

### Post by zeekstern on 2020-06-06
Yes, hashcheck for md5 and sha1 is fine. No need for me to check everything.
I don't know what a media check is. The install media boots fine on my 2 desktops and a laptop. What do you mean "media check"?
I don't know what you mean about "in other ports". What do you mean and how do you do that?
I have 4GB memory.

Thanks for the reply/input. Much appreciated.

Zeek

I really don't think there is anything wrong with the install media.

---

### Post by TheFu on 2020-06-06
Was some storage freed up on the existing disks before attempting the install?  There needs to be 15G  or more empty, unused, storage and a free partition available.

BTW, nobody formally tests Linux installs on systems with out of support OSes. You are playing a risky game using XP.  Expect data loss and be surprised when it doesn't happen.

A few of the partition layout for both disks would be very helpful.
```
df -Th
lsblk -e 7 -o name,size,type,fstype,mountpoint
sudo fdisk -l
```

Or better, install and run the boot-info script that is part of boot-repair

---

### Post by ubfan1 on 2020-06-06
The "other ports" would be other USB ports in case the one you used had a problem of some sort. 
The "media check" used to be an option on booting the install media, along with "Try" and "Install", and "memory check".   It may have been removed. 
4GB of memory should be OK.  Second that boot-repair suggestion, run the report, make no changes, and post the link.

---

### Post by TheFu on 2020-06-06
The 20.04 installations I&#8217;ve run all checked the media automatically unless we ESC out of it quickly enough.  it is actually a hassle on the 2nd and later installs.

Linux cares about the different between a _disk_ and a _partition_ regardless of what MS-Win calls them.  Be very certain you read the installer screens correctly and use those terms accurately.  Partitions are much more important in Linux.

---

### Post by zeekstern on 2020-06-06
Sorry for the confusion TheFu. 
The 20.04 desktop ISO I created lets you "Try Ubuntu" or "Install Ubuntu". The stuff I read suggested you Try it first as a way to see if your PC could handle it. Since my PC is a 2008 (or maybe 2006) model that sounded perfect for me.  The ubuntu site (and the Install CD) says you can replace your existing OS or [COLOR=#111111][FONT=Ubuntu]run Ubuntu alongside your current operating system. That is what I am attempting to do.

Since I was running Ubuntu alongside Xp, I did not think it would matter if the OS is out of support. Ubuntu should not care about XP except maybe where it resides.[/FONT][/COLOR]:confused:
I did not re-partition any of the drives. I have a 320gb and 250gb. The first time I started the Install it came out with this:

```
/dev/sda	Size			Used	
/dev/sda5 ntfs	42948mb	[42.948gb]	4542mb [4.542]GB
/dev/sda2 ntfs	277120mb [277.12] GB	86711mb	[86.71]GB Win XP Professional
/dev/sdb
/dev/sdb1 ntfs	239067mb	146892mb Win XP Professional
/dev/sdb2 fat32	10988mb		57mb	ms-dos 5.x/6.x/win3.1


Device for boot loader installation:
/dev/sda	ATA Hitachi Hdt72103 (320.1 GB)
/dev/sdb	ATA WDC WD2500JS-00N (250.1 GB)

```

[COLOR=#111111][FONT=Ubuntu]I then cancelled the Install. Then the second time  around I got this:

[/FONT][/COLOR]```
The partition tables of the following devices are changed:
SCSI4(0,1,0)(sdb)


The following partitions are going to be formatted:
partition #3 of SCSI4(0,1,0)(sdb) as
partition #5 SCSI4(0,1,0)(sdb) as ext4



```

Note that it did not say what #3 was going to be formatted as. Not sure if it matters, just pointing it out.
Since the install didn't work, I can't install anything and run it. I booted up from the install CD and ran the fdisk -l. Below is not everything because I don't have a way to get the results from that PC to mine. I can't save it to a 95 partition, cause I don't know how. I have to type the results:

Here is /dev/sdb which is where Ubuntu is probably installed:
```

Disk /dev/sdb: 232.91 GiB
Disklabel type: dos

Device         Boot    Size        Id      Type
/dev/sdb1      *      148.1G     7      HPFS/NTFS/exFAT
/dev/sdb2               10.2G      49   unknown
/dev/sdb3               513M     b       W95 FAT32
/dev/sdb4                 74G       5     Extended
/dev/sdb5                 74G      83    Linux

Partition table entries are not in order

```

So it looks like sdb4 and 5 have Ubuntu on it?

Oh, the other disk that has my active Win XP on it is broken down to **sda1** 40G, W95 Ext'd LBA, 
**sda2 **258.1G HPFS/NTFS.exFat and **sda5 **40G HPFS/NTFS.exFat 

If you need anything else, please let me know. As you can tell, I am a newbie to Linux and I really appreciate the help.

Zeek

---

### Post by zeekstern on 2020-06-06
Thank you ubfan1. 
How can I install the boot-repair tool if I am not able to boot up? Then if I did, how could I get the report off of it to post? 
I hope to get a USB disk tomorrow. Then I guess I could pipe the results to the usb. 
Don't forget, you're dealing with a newbie:)) I will Google and see how to use the usb with ubuntu.

Zeek

---

### Post by zeekstern on 2020-06-06
I attached the lsblk and fdisk output. It might be easier to read.

---

### Post by TheFu on 2020-06-07
Just some thoughts ... no real answers follow.

Looks like you found the power of redirection. Nice.  For lurkers, that is were we take the output from a command an redirect them into a file.
```
sudo fdisk -lu >> /tmp/fdisk-output
```
or
```
sudo fdisk -lu | tee /tmp/fdisk-output
```
The tee command redirects to the file AND prints on the screen.
The first command appends to the output-file.  Tee can do that, with a **-a** option.  **tee -a /tmp/fdisk-output**

In a "try ubuntu" environment, you can install packages and run them.  They just won't be saved after a reboot.
So, install boot-repair and run the information gathering part only. That should create a URL that can be posted here.  There's nothing secret in the URL. It just runs a bunch of commands an posts them to a pastebin-like website. Nothing traceable back to you or me. Without the URL there's no connection and in a few weeks, that data gets removed (I assume).
So, 

```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *           63 310602776 310602714 148.1G  7 HPFS/NTFS/exFAT
/dev/sdb2       466929225 488392064  21462840  10.2G 49 unknown
/dev/sdb3       310603776 311654399   1050624   513M  b W95 FAT32
/dev/sdb4       311656446 466927615 155271170    74G  5 Extended
/dev/sdb5       311656448 466927615 155271168    74G 83 Linux
```

The order shown above doesn't reflect the partition order on disk. Just look at the "start" numbers. 

sdb4 is an "extended primary partition".  You can look up what that means on wikipedia, but it is a trick for an old-style partition table to allow more than just 4 partitions. It contains all the "logical partitions" for the drive.  sdb5 is the only logical partition shown. That is to be expected.  Notes the "Start , End and Sector counts" between sdb4 and sdb5 are almost the same?  They overlap ... because sdb5 must be entirely inside sdb4.

What is sdb2? It has 10G. Looks like sdb2 is at the end of the disk, after the Extended partition. Might it be a Windows Recovery partition? 

Also, sdb3 is pretty small, so probably not very useful. Did that get resized to make room for Linux? 

/dev/sda is the entire disk.
/dev/sda1 is the first created partition.
/dev/sda2 is the seconds created partition. The 1 and 2 have nothing to do with location ON THE DISK at all, they are just the order a partition was made.

Logical partitions on DOS partition tables (compared to GPT partition tables) all have a number of 5 or greater.  Any /dev/sda5 is a logical partition, if the partition table is DOS. If you look at the fdisk output, you can see : **Disklabel type: dos**  If it was GPT, then it would say GPT/gpt.  GPT supports 128 primary partitions, not just 4, and has more redundancy with 2 copies of the partition table at opposite ends of the disk. GPT supports very large disks too, so any 2TB or larger HDD should have a GPT partition table. That's a problem for WinXP since it doesn't support GPT.  OTOH, Linux does and has for a very long time.  GPT includes a DOS partition table to be backwards compatible, but only the primary partition within the first 2TB are supported. All changes to a GPT table should only happen from OSes with full GPT support.

Partitions these days are GPT and don't use "extended" or "logical" partitioning unless specifically required.

That's a bunch of writing for nothing but background.  I haven't booted WinXP since before it was EOL, so I'm not comfortable providing any detailed instructions.  I do have a WinXP virtual machine somewhere with an Old MS-Office 2007 install on it.  Found it. ;)  I'm curious now.  /Backups/VirtualBox/VDI/WinXPPro.vdi Hummmm. I stopped using virtualbox around 2011 and never used it on Linux. Maybe it will run under KVM's hypervisor?

---

### Post by zeekstern on 2020-06-07
Geez, I thought I replied hours ago, I must have forgot to submit it. This has been a long day. I had to replace the battery, the PC wouldn't boot, then I got it to boot but it would not boot up from Cdrom. Then I couldn't get into XP and on and on.

Here is the URL from boot repair:  [https://paste.ubuntu.com/p/NB9xYKpWYR/](https://paste.ubuntu.com/p/NB9xYKpWYR/)

The quick response is it worked. I now get a menu with these options:

 Ubuntu
 Advanced options for Ubuntu
 Memory test (memtest86+ serial console 115200)
* Microsoft Windows XP Professional (on /dev/sda2)
  Microsoft Windows XP Professional (on /dev/sdb1)
  MS-DOS 5.X/6.X/Win3.1 (on /dev/sdb2)

I have to put my glasses on to see it and I have to be real quick to select one, otherwise it boots Ubuntu as the default.
Would you believe they all work?
Well, not really. The XP on /dev/sda2 and Win3.1 do not work.:)) It looks like I can edit that menu but I don't want to touch it until I find out for sure.
Have you ever edited the menu?

The only Ubuntu issue I found so far is that after logging in, the Package ibus 1.5.22-2ubuntu2 crashes. The executablePath is /usr/libexec/ibus-x11.
I'm thinking maybe uninstall/re-install and check for updates? I noticed the Process  "/usr/libexec/ibus-x11 --kill-daemon" is running. Maybe that is killing it. I haven't had time to look into it.

TheFu, I want to thank you for your help, and for the great info on the disk/partition stuff. That is great info. That's going into my Ubuntu book:))

Oh, you asked about sdb2 and 3. 
sdb2 10.2gb is Windows Hidden Partition 5. The Type 49 is Venix 80286 filesystem. Love it:))
sdb3 513mb is Windows Volume 4. The Type is 04 DOS 3.0+ 16-bit FAT.  sdb3 appeared after my first attempt to install Ubuntu.

Thanks again!!

Zeek

---

### Post by TheFu on 2020-06-07
Thank ubfan1,  the boot-repair idea was his.

i haven't dual booted in over a decade, so no, i haven't edited the grub boot menu.  it is possible.  Seems you have stuff working.  

Before changing anything big, backup the files (copy them elsewhere) so you can put them back if needed.  You'll probably want to learn update-grub and grub-install BEFORE touching anything. 

Those can only be run either from the running ubuntu install OR via a chroot env from the try ubuntu. Basically, boot into the try ubuntu and make the OS think it is running the installed version, then do the update-grub.  There are 50 guides for that.

---

