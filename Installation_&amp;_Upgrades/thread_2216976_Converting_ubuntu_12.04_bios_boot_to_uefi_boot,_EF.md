---
title: "Converting ubuntu 12.04 bios boot to uefi boot, EFI partition not detected"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by don-handymanreality on 2014-04-15
My Asus G73S Quad-core computer with ubuntu 12.04 has become messed up after I added an external drive  with a gpt partition table and an efi partition (4TB Seagate Backup+ Desk). I have disconnected  that disk and am now attempting to convert my original 12.04 to an EFI  boot. My computer has two disks sda for my ubuntu os and another that I  am using for ntfs data created by my Virtualbox Windows 7 guest.

I have tried boot-repair a few times and I am getting nowhere. I have a  64 bit liveusb that I am booting from and my original 12.04 is 64 bit as  well.

While booted from liveUSB in uefi I get the correct efi screen though when I run boot-repair I get the following error;
"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."

Can you give me any advice as to how to get my EFI partition on my sda1 partion to work? [http://paste.ubuntu.com/7253259/](http://paste.ubuntu.com/7253259/)

 Thank you kindly for your time and consideration.

Don

---

### Post by sudodus on 2014-04-15
Only /dev/sda has a GPT (GUID partition table), not /dev/sdb, where you have Windows 7. This means as far as I understand, that windows 7 is installed in BIOS (or BIOS compatible or CSM) mode, because UEFI mode does not boot unless the drive has GPT.

Many people would use UEFI only because the installation of Windows is in UEFI mode and 'forces' any other system in a dual boot setup to be in UEFI mode too. So in your case, I suggest that you do not bother to make the system work in UEFI mode.

To boot from a GPT drive in BIOS mode, you need a small (1 GB) partition with the ***bios_grub*** flag (as you are told by Boot-Repair).

---

### Post by oldfred on 2014-04-15
I have no idea if a Windows in Virtualbox in BIOS mode will work with Ubuntu in UEFI mode?

But to boot with UEFI you need the drive to be gpt partitioned and an efi partition. The efi partition should be near beginning of drive, but some have had it further into drive and it worked. 
If drive is gpt partitioned you can boot in BIOS mode, but need the 1MB unformatted partition with the bios_grub flag.
IF drive is MBR(msdos) you have to convert to gpt partitioning to use UEFI.

How you install Ubuntu is based on how you boot installer UEFI or BIOS. 

But if you boot Boot-Repair in UEFI mode it will convert to UEFI mode or to BIOS mode if drive is gpt. If you manually installed to gpt without bios_grub then grub would not install and Boot-Repair would probably just offer BIOS update and then want the bios_grub partition.

UEFI Windows issues
  [SOLVED] UEFI Virtualbox installation boot problem - Arch
[https://bbs.archlinux.org/viewtopic.php?pid=1231228](https://bbs.archlinux.org/viewtopic.php?pid=1231228)

---

### Post by don-handymanreality on 2014-04-15
My system is not dual boot.Likely I may be facing an issue from when I originally removed Windows7, formatted, and installed Ubuntu, then installed windows as a Virtualbox VM. I only boot to Ubuntu 12.04 LTS. My sdb drive does contain my virtualbox virtual machines and shares for my virtual machines. In my case I bought an 4TB external drive for backups and when I used the included utility for that disk, Seagate 4tb Backup Plus Desk, from my Windows7 os that runs inside of Virtualbox, well, things got interesting because it has an EFI partition and will not get along with my Ubuntu installation. 

I am going to proceed with making my Ubuntu 12.04LTS uefi boot and I will take care of my Virtualbox installation afterward. Virtualbox likely won't be a problem to adjust.

Thank you for your thoughts on my issue.

---

### Post by don-handymanreality on 2014-04-15
After much time and effort I believe that I may have found an issue that may be preventing my EFI partion from being detected.

After running sudo fdisk -l I find that "Partition 1 does not start on physical sector boundary."

After trying to align the partition with gdisk and no success I gave up and deleted the partition sda1 with gparted then rebooted to liveusb in uefi mode.

After 2 reboots to Ubuntu 13.10 LiveUSB uefi mode the partition information remains in the protective mbr.

> sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): ?
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): p
Disk /dev/sda: 1465149168 sectors, 698.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): E38BF3D6-1462-4A68-9801-D3FDC4DAF176
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1465149134
Partitions will be aligned on 2048-sector boundaries
Total free space is 1024747181 sectors (488.6 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2          616448       420046847   200.0 GiB   8300  
   3       420046848       441018367   10.0 GiB    8200  

Command (? for help): q
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.





Aligning partions did not work for me.
Deleting the problem partition  not work for me.has not worked for me.



It looks like I need to find a way to zap the protective mbr or rebuild it using the gpt table. 



How would you delete the protective mbr so that it no longer retains the deleted partition entry information?

---

### Post by don-handymanreality on 2014-04-15
Also,

> sudo parted /dev/sda print | grep -i '^Partition Table'
Partition Table: gpt



---

### Post by oldfred on 2014-04-15
You do not use fdisk on gpt partitioned drives. It only has one gpt partition defined in the protective MBR. Gpt has the protective MBR so old partition tools see that drive is fully partitioned and do not damage drive.

New partition tools all start first partition at sector 2048 and make sure every partition start is divisible by 8 for good alignment. You should not have to move partitions around and doing that to Windows NTFS partitions can cause major corruption.
The reason for the alignment is new SSD  and new hard drives with 4K sectors.
       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

What partition did you delete? 
It may start to be easier just to totally reinstall? You do have good backups of /home, list of installed apps and any hardware settings you may have changed in /etc?

---

### Post by don-handymanreality on 2014-04-16
I have backup images on a USB drive. I started chasing around an error on my sda drive that I cannot seem to get rid of. Clearly, fdisk -l causes a false flag of an error because I completely wiped the drive including GPT table & MBR then started to repartition to create an EFI partition that is aligned at 4096 or so I believe it is. I've lost much faith in the GUI tools because they all seem to give different values for the same partition.

My new plan is to go with the EFI partition that I set up using gparted and then labeled and typed with gdisk. I am going to download a clean copy of Ubuntu 12.04LTS to a liveUSB and then I am going to reinstall, preferably in UEFI mode, using separate partitions for /boot, /home, & /tmp then I will figure out how to reintegrate my original home partition and packages after mounting my backup image. You could say I give up...lol.

Here's a screen shot of the crazy partition values given in the various GUI tools. (made a mistake with a pointer arrow on the "disks" window, it should be more to the right)
[IMG]http://ubuntuone.com/2sg2QWFYEG6OmTADh2iU4k[/IMG]

---

### Post by oldfred on 2014-04-16
You can attach screen shots with advanced editor and the paper clip icon at top of that editor..

Generally better without /boot. That is required with LVM and full disk encryption and may  be required with RAID or LVM. Rarely required with desktops and we regularly get users posting with full /boot partitions and then they have huge issues housecleaning. You still should houseclean /boot folder occasionally. 
I only have seen some with SSD have a separate /tmp and often those with lots of RAM mount it in RAM.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by don-handymanreality on 2014-04-16
SWEET! Thank you oldfred! That is some great advice for setting up my new Ubuntu 12.04 install. 

After playing with Ubuntu 13.10 while attempting to restore my Ubuntu 12.04 I'm almost disappointed to go back to 12.04..lol. There is some really great work going on with 13.10. Ddrescue-gui and boot-repair are some fabulous tools to work with. boot-repair even upgraded my 12.04 installation for me and installed an efi signed kernel, AMAZING! 

oldfred, thank you for your time, consideration and great tips for my reinstallaion.

---

### Post by oldfred on 2014-04-16
I have 14.04 in a test partition, but still using 12.04 as my working install. I do not have UEFI (yet). I had planned a new system a couple of years ago and started following UEFI issues, so I would know what I was doing. But I first bought a small 64GB SSD and old system was so good I put off new system. I still hope to do new system soon. :)
Boot-Repair does not yet have a trusty version, but I was able to tell it to install saucy version and at least the bootinfo report part worked.

---

### Post by don-handymanreality on 2014-04-17
And the saga continues after another 12 hours of trying to make eufi boot on my Asus G73sw i7 quad core laptop.

It seems that there has been a line blowing by on my screen before grub 2.0 loads. I could not find anyway to log it or find it in any logs so I had to shoot a video just to grab one image of what it says.

> "could not open "\EFI\BOOT\fallback.efi": 14

Besides the fact that the efi file is all in lower case I am completely stumped as to how to recover.

My last attempts with boot-repair end up with a blinking cursor on the screen and it will not boot past it. I am going to try disabling my nic in the bios and see if that has any effect because I found this post for OpenSuse where someone has done extensive testing and they have issues with eufi after disabling & enabling the nic card. Bottom of post #40 [here]("http://forums.opensuse.org/showthread.php/490605-TOSHIBA-Satellite-P50-A-UEFI-W8-dualboot-Cannot-install-12-3-%28nor-13-1-beta%29/page4")

Anyone got any ideas?

---

### Post by oldfred on 2014-04-17
Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)

Some in bug report have this:
It looks like the current work around is copy & renaming some efi files.

---

### Post by don-handymanreality on 2014-04-17
Thanks for the tip, though, renaming to fallback.efi woiuld not work for me to convert my 12.04 Desktop to dual boot Ubuntu 13.10 Desktop on my Asus G73Sw laptop.

So, I went with a complete wipe of my sda drive and I left my sdb drive with the two ntfs partitions stay as they were, then, I installed Ubuntu 13.10 Desktop in uefi mode from a LiveUSB. I used the "lvm" "encrypted drive" & "other" options on install and created a new partiton table on the drive with 200mb for EFI, 30 GB for /, 150 GB for /home, & 18 GB for SWAP.

On reboot I did not see a grub 2.0 boot screen, so, I used the command below to determine if I did truly reboot into UEFI from my hard drive.
> [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

The result was:
EFI boot on HDD



[ATTACH=CONFIG]252147[/ATTACH]

[lshw output]("http://ubuntuone.com/5MaacFlR0eSBse6Heo9PS8")

Now I will attempt to install 12.04 in EFI mode to the balance of my sda drive and then I may know if it was even possible to dual boot this computer with UEFI installed os's.

---

### Post by don-handymanreality on 2014-04-17
NOTE: Before I install 12.04 I took a look at my bios and I notice that there is no "UEFI:" before my boot selection though I am booting into EFI mode? The boot selection is not my sda drive descrtiption and is simply "ubuntu." Previously I was often following the advice of the last alert box from boot-repair that instructed me to make sure that the "hard drive" was first in the boot order. Now if I change to the actual hard drive as being first in the order I get the same black screen with blinking cursor that was frustrating me in trying to make the conversion of 12.04 Desktop to EFI mode. 

Maybe I was selecting the wrong entry and should have been selecting the "ubuntu" entry all along?
 
[ATTACH=CONFIG]252150[/ATTACH]

Dagnabit! It figures that 14.04 LTS would come out today...sigh! all that work with 13.10 was for naught.

---

### Post by oldfred on 2014-04-17
I have only seen one or two UEFI with LVM installs. Those had both the efi and /boot outside the LVM as the LVM was encrypted. 
Not sure if UEFI will read a efi partition inside an LVM as it may not have driver. Grub now has drivers for RAID & LVM so you do not have to have a /boot outside of RAID or LVM, but I do not think most UEFI have the extra drivers.

---

### Post by don-handymanreality on 2014-04-17
Ok, well, installing the latest Ubuntu 12.04LTS through LiveUSB results in a blank black screen right from the very start. So it is a complete non starter at the moment.I suspect the Nvidia Geforce GTX 460M Cuda 1.5 GB drivers because they have always given me grief in 12.04.

I'll have give up here and look into moving my old 12.04 /home directory into my new install of 13.10 AFTER I use the upgrade tools to upgrade it to 14.04LTS. I'm sure that will be fun..lol.

---

### Post by don-handymanreality on 2014-04-17
How can I tell if my current installation is LVM? Do you know a command I could use?

---

### Post by don-handymanreality on 2014-04-17
oldfred, you are correct my install is no lvm. as indicated by the lvs & lvdisplay commands that indicate that lvm is not installed.

---

### Post by oldfred on 2014-04-17
Since about 10.10, I have had to use nomodeset with every boot of ISO to install and one first boot or until I install nVidia drivers. 

I always install nVidia driver from repository as years ago, I installed from nVidia and had nothing but problems, took forever to totally house clean that install, so I could go back to one that worked.

---

### Post by don-handymanreality on 2014-04-18
Thank you for the 'nomodeset' tip I will definitely look into it. I've just gotten back from a service call and I am REALLY enjoying the new Ubuntu 14.04 LTS. After I finish perusing the settings I will go back to researching moving my /home directory and maybe attempting another dual boot with 12.04 for anything that does not effectively work in 14.04.

---

### Post by don-handymanreality on 2014-04-19
So, about that VirtualBox running in an EFI installation of Ubuntu 14.04 Desktop? Yep, it runs just fine.

Attached is a screenshot of VirtualBox on EFI mode Ubuntu, running Apple Snow Leopard, the latest Lulbuntu Tizen IDE, the latest OpenSuse and a vm of Windows 7 that is also running "BlueStacks" beta 1 and my Android apps from my Google Apps Premiere account with "two-factor" authentication.

Sort of a fake computer in multiple fake computers on a real Asus G73Sw computer....lol.

I think I'm done with attempting to convert a bios boot 12.04 to an EFI boot. Unless you, oldfred, would like me to continue because I appreciate your assistance, and, because I believe that I can make it work as a dual boot thanks to what I have learned and the tips you have supplied.

---

### Post by don-handymanreality on 2014-04-19
Now, I'm going to make my Asus Nexus 7 LTE 2013 dual boot Ubuntu Touch....lol.

---

### Post by oldfred on 2014-04-19
You seem to like challenges. :)

---

### Post by don-handymanreality on 2014-04-20
oldfred, ha ha not really, though, I would like to get my box set up to work as well as proprietary systems and a full back up solution. I was quite happy with my 12.04 install for a couple of years.

It was a proprietary Seagate Backup Plus Desktop Drive that pooched my earlier os. Foolishly I thought I could buy a USB drive and just plug it in..sigh! The drive had an EFI partition that got me interested in upgrading.

I went into my Windows 7 virtual machine and thought I'd use the utility that came with the disk to set up the back up for JUST windows, and, boom my host system was screwed. None of this was planned it just sort of happened.

I'm on an adventure to replace the Android on my tablet because it all of a sudden decided that it could steal all my pictures and images and upload them to the web without my express permission. None of my previous Android devices did this only the damned Nexus 7 2013 with Android 4.4 kit kat. It took with my pictures images of peoples SIGNATURES from my invoicing app. If I turn off the picture sync it turns off my email & calendar sync. Now Google has got to go.

Sadly the Ubuntu Touch installation page is woefully out of date. The adb backup is not working correctly for me. I'll give it a shot tomorrow.

---

### Post by Keishiko on 2014-12-15
> **don-handymanreality said:**
> Now, I'm going to make my Asus Nexus 7 LTE 2013 dual boot Ubuntu Touch....lol.

Hi, were you able to successfully convert your your Nexus 7 LTE (I've read some article that said that only Nexus 7 Wifi can be dual booted) to dual boot? Can you make a tutorial on how this could be done? Thank you so much and more power.

---

