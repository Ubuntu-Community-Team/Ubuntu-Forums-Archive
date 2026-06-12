---
title: "Problem installing Ubuntu 14.04"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by Anders_Lundqvist on 2014-08-04
Hello!

I'm a first time Ubuntu user trying to install Ubuntu on my U500VZ1.

Whenever I try to install Ubuntu I get error messages. Either it's 
"The attempt to mount a file system with type vfat in serial ata raid  isw_bjahfaabje_raidorst1 (partition#1) at /boot/efi failed"
"You may resume partitioningen from the partitioning menu"

or

"??? ???"

I'm trying to install from USB using Universal Usb Installer 1.9.5.5

Any ideas?

---

### Post by oldfred on 2014-08-04
Are you runing RAID or is this an Ultrabook with Intel SRT?

What brand is your computer model u500vz1?

I do not use RAID, but have seen efi partition both inside the RAID and outside of it. With LVM it always is outside the LVM as is /boot partition if encryption is used.

Desktop installer does not have RAID drivers.
You can add these drivers or the specific hardware drivers you need to see RAID, but I do not think the install picks that up from live mode.

 sudo apt-get install mdadm
sudo apt-get install dmraid
      
 How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)


 grub doesn't boot with efi and md raid root
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)
RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)
[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

---

### Post by Anders_Lundqvist on 2014-08-06
About the SRT I have no idea. How do I check that?

Asus

On the first link I failed on 
"Choose to partition manually and    create: 50 MB bios boot  partition with bios_grub flag (reserved bios    area) followed by a 200  MB EFI boot partition at the front of the    drive, a swap partition of  appropriate size at the end of the free    space and the remaining free  space as an EXT4 partition mounted as / ."

I have no idea to do that.

The rest of the links I dont even understand why you linked?

---

### Post by oldfred on 2014-08-06
It looks like that may be an Ultrabook not a RAID, although a few systems have two SSD and they are in RAID mode.

With RAID you cannot use standard partition tools. And if Intel SRT you have to turn that off in UEFI/BIOS.
Depending on type of RAID you may not want to turn it off.
But whatever you do you need very good full backups of Windows first.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Post this from terminal in Live installer.

sudo parted -l

---

### Post by Anders_Lundqvist on 2014-08-06
I dont have any OS on the computer at the moment. It used to run W8 but that is what I am trying to get rid of :P
So not trying to dualboot and no reason to do any backups

---

### Post by oldfred on 2014-08-06
Then do you want UEFI or BIOS as boot choice.

Either way with Ubuntu I suggest gpt partitioning and partition in advance with gparted from live installer or a separate download of gparted live.
       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

If system is Ultrabook does it have separate small mSATA SSD drive?
You then need to turn off Intel SRT in UEFI. And then install / (root) to SSD and use hard drive for /home and or data partition(s).
You may have to remove old RAID data on drive that Intel SRT writes. If so details on clearing those setting are in link in my signature.


 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Then use Something Else to install. You can use UEFI boot or BIOS boot.
You can skip the dual boot part.

 [http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

       
 Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by Anders_Lundqvist on 2014-08-06
If I use "try Ubuntu without installing" and then start qparted I get the following error "invalid argument during seek for read on/dev/sda :S

---

### Post by Anders_Lundqvist on 2014-08-06
I just read everything you just wrote there. Thank you very much for the help but there is way to much that I dont understand. Feels like the learing curve is a bit to steep for a new ubuntu user. So many terms and and facts I simply do not get. So there is no need to keep this thread alive.

---

### Post by QIII on 2014-08-06
Hello!

Think back to the very first time you used Windows.  Be honest.  Were you a bit bewildered?  Did you really know what you were doing when you first played with it?

One thing you probably didn't have to do was install it, since your machine came with Windows.  If you take a fresh machine and install Windows it can be frustrating, too.  You just know the language now so you understand the help offered.

You are in the same position as a native English speaker learning German.  It isn't the same, you shouldn't expect it to be and it takes time.

Yes.  There is a learning curve.  There is also one with Windows.

Take it as an adventure rather than a chore.  :)

---

### Post by Anders_Lundqvist on 2014-08-06
The problem is that I understand next to nothing from what Olfred says, so it kinda feels hopeless. 

It's more of a chore though considering that I dont have any compouter right now and I start second year of college in three weeks :P

---

### Post by QIII on 2014-08-06
If you don't understand, ask for a smaller breakdown in baby steps.  Nobody will bite on this forum if the Staff catches them.  We don't allow it.  If someone gets surly we step in.

We want this to be a helpful place.  The snobs do wander in and out a bit, but the vast majority of us are willing to be helpful.  

Don't be discourteous, of course.  Nobody likes that.

oldfred has amassed a great deal of knowledge.  He's here to help and will.

On your part, you'll have to be willing to put some sweat in.  :)

---

### Post by oldfred on 2014-08-06
I do tend to dump lots of info, but I do not know how knowledgeable you are.

I sounds like some issue on hard drive.

If drive was RAID or Intel SRT it could cause that type of error.

If drive is blank try this:
       Even if raid not used BIOS may have set parameters, Also check BIOS settings, should be AHCI, not RAID nor IDE.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

