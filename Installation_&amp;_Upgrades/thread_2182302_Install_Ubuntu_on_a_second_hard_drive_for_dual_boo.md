---
title: "Install Ubuntu on a second hard drive for dual boot on Widows 8 PC"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by John_Lane on 2013-10-20
I would like to install Ubuntu on my Windows 8 PC as a dual boot option. Also I would like to install Ubuntu on my second hard drive D: so that I don't mess up anything on my Windows hard drive C:.I have downloaded the .iso file and created a bootable DVD.
Are there instructions somewhere on the web site to do this?
Thanks,
John

---

### Post by oldfred on 2013-10-21
When you say d: in Windows is that really another physical hard drive or a partition? Windows mixes that up and it can be either.
In Linux drives are sda, sdb, sdc and partitions are the numbers after the drive or sda1, sda2, sdb1 etc. So it is clear which is a drive and which is a partition. 
Many Windows users try installing Ubunbu and it clearly offers an option to erase Windows drive. Windows uses think their d: drive will be preserved when it is really is a d: partition then it is also erased as it still is sda and the entire sda drive is overwritten.

So post this using terminal from live installer flash drive or DVD. You can copy & [paste or last letter is an el not 1 - one or  i- eye.

sudo parted -l

---

### Post by John_Lane on 2013-10-21
> **oldfred said:**
> When you say d: in Windows is that really another physical hard drive or a partition? Windows mixes that up and it can be either.
In Linux drives are sda, sdb, sdc and partitions are the numbers after the drive or sda1, sda2, sdb1 etc. So it is clear which is a drive and which is a partition. 
Many Windows users try installing Ubunbu and it clearly offers an option to erase Windows drive. Windows uses think their d: drive will be preserved when it is really is a d: partition then it is also erased as it still is sda and the entire sda drive is overwritten.

So post this using terminal from live installer flash drive or DVD. You can copy & [paste or last letter is an el not 1 - one or  i- eye.

sudo parted -l

Hi ,
Thanks for the reply..
I am new to Linux but my D: drive is a second hard disk.
Here is my attemp at posting the terminal results:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  420MB   419MB   ntfs         Basic data partition          hidden, diag
 2      420MB   735MB   315MB   fat32        EFI system partition          boot
 3      735MB   869MB   134MB                Microsoft reserved partition  msftres
 4      869MB   970GB   969GB   ntfs         Basic data partition
 5      970GB   970GB   367MB   ntfs                                       hidden, diag
 6      970GB   1000GB  30.1GB  ntfs         Basic data partition          hidden, diag


Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? ^C                                                                
Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? ^C                                                             
Model: ATA Maxtor 6Y080M0 (scsi)
Disk /dev/sdb: 82.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 


Hope this makes sense to you as it way beyond my knowledge of Ubuntu.

Thanks,
John

---

### Post by oldfred on 2013-10-22
Since Windows is UEFI on gpt drive, your sdb drive also needs to be gpt and Ubuntu installed in UEFI mode.
Usually all boot loaders are installed in one efi partition, but I suggest an efi partition on every drive.

You may need to make sure backup gpt partition is ok or corrected with gdisk or totally repartition with gparted with gpt partition table.
       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

      
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
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

Make sure you boot Ubuntu install flash drive in UEFI mode. This shows both screens, but from UEFI menu you should see two choices to boot.
      
 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Examples of users who installed on two drives in link in my signature.

---

### Post by John_Lane on 2013-10-24
Hi Oldfred,

I am still having no success installing Ubuntu 13.10 on the 2nd hard drive in my Windows 8.1 PC.
When I attempt to do the install to 2nd drive db the message pops up saying:" No root file system is defined. Please correct this from the partitioning menu."
I have no idea what to do or what it means by the partitioning menu.
Can you give me some advice that is not too complicated for a beginner?
Thanks,
John

---

### Post by ubfan1 on 2013-10-24
When you have created the partitions you want on the 2nd hard disk, for each partition you select "use as" dropdown (select either ext4 or swap), and then you have a mount point dropdown, select the "/" for the root file system. (or swap).

---

### Post by oldfred on 2013-10-24
Whether you partition in advance or use partitioner during install with Something Else, you have to select the partition, choose its format usually ext4 and select its mount point (/ , /home, etc). If partitioned in advance it will auto find swap, or you specify swap and it has no format. 

Example with a /home. I think install screen has changed slightly so now you have to click on the change button.
 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

This was after I click change even though I was not changing size.

---

### Post by John_Lane on 2013-10-25
> **oldfred said:**
> Whether you partition in advance or use partitioner during install with Something Else, you have to select the partition, choose its format usually ext4 and select its mount point (/ , /home, etc). If partitioned in advance it will auto find swap, or you specify swap and it has no format. 

Example with a /home. I think install screen has changed slightly so now you have to click on the change button.
 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

This was after I click change even though I was not changing size.


Hi again to oldfred,

Well I got so frustrated with booting from the Ubuntu install DVD and trying different things with the partitions on the sdb drive that I gave up and cloned my Windows 8.1 hard drive to the second hard drive. I then removed the original Windows hard drive from the computer. I confirmed that I could run Windows from the cloned hard drive and then booted from the Ubuntu DVD and chose the install with the first option to erase and overwrite the whole hard drive. The Ubuntu installation seemed to succeed with no errors reported and seems to run OK.
I then re-installed the original Windows hard drive and attempted to choose the Ubuntu drive to boot from the Boot Manager using F12 key.
Ubuntu failed to start. I then did the Boot-Repair commands from Terminal and after it was finished it's procedure it gave me the following URL --http://paste.ubuntu.com/6298398/
It seems to work now and I can choose to start either Windows 8.1 or Ubuntu 13.10 by pressing the F12 key when I power on the computer and choosing the appropriate hard drive.

Thanks for all your assistance and patience with an old guy who is trying to learn something about the Linux world. I guess I am a bit slow learning. I actually was quite familiar with computers running Windows and Apple operating systems as I am a retired Electronics Tech and had considerable experience in the IT business, but I am getting old and my brain has slowed down.

John

---

### Post by unixpcguy on 2013-10-25
I selected use as swap and it worked for me. Glad you have it setup.

---

