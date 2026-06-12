---
title: "Dual boot sharing a D: drive?"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by raen on 2012-03-24
This is all hypothetical right now, as I am finding out what is and is not possible/reasonable before I even buy my new computer.

I'm thinking about dual booting Windows 7 Professional with Ubuntu [either Lucid or Precise]. I'm also thinking about having two internal hard drives for convenient extra storage (I can get a 1.5TB drive for $100 right now, but I digress).

As I understand it (and please correct my facts and/or logic), the C: drive is by definition where the OS is, and for all intents and purposes boot system X on partition A is inaccessible to boot system Y on partition B. That is to say, I cannot log in to Windows and retrieve a document I have in Ubuntu, and vice-versa.

In the case of a third partition or a separate hard drive, however (if indeed there is a practical distinction to be made here), does this restriction still apply? Or, as I'm hoping, will I be able to save documents to the D: drive that I can access just as easily in either boot, in much the same manner as accessing documents on an external storage device?

If the answer is yes, is there anything special I'll need to do in order to achieve this, or will this be taken care of as part of the process of installing Ubuntu?

Thank you.
raen

---

### Post by oldfred on 2012-03-24
Yes you can have a shared NTFS drive (really a partition). I have used a NTFS partition for several years with my XP, but now use it very little. I moved my Firefox & Thunderbird profiles into the NTFS partition just so I did not have to reboot into XP to get mail when I was first learning Ubuntu. Was even more important as spouse wanted to easily check mail & Internet. 

It includes a NTFS driver as part of the install, but it works better if you create a mount (linux lets you use any name you like not just d: ), and add it to a file fstab that loads all the mounts on reboot.

If you are getting another drive, put Ubuntu on the other drive with the data partition(s). Windows 7 install often use all 4 primary partitions allowed in MBR and make it difficult to install, but you can. Easier just to install to another drive. The important thing with multiple drives is to install the grub2 boot loader to the second drive usually sdb, so as not to overwrite the Windows boot loader in sda.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

---

### Post by darkod on 2012-03-24
First thing first, I would try to stay away from the term 'drive'. MS did a very lousy job and got people used to that term, when it has double meaning because it is also part of Hard Disk Drive for example.

On the other hand, C: D: E: etc can also be only partitions on the same physical disk. So, when you say simply drive C:, what is it?

I prefer using 'partitions' and 'disks' for this reason.

Yes, having a ntfs partition for data (or more of them for organizing data better) will make it usable from both windows and ubuntu.

Also, you are wrong in believing you can't read documents (data) from one OS to another. From ubuntu you can read everything on your ntfs partitions which includes your C: partition.

From windows you can't read linux (ubuntu) partitions by default. There are tools that make it doable but I wouldn't trust windows with linux partitions too much.

Having a ntfs partition(s) to share is a good idea. Not only because you can access it from both OSs, but also because having your D: partition makes it possible keeping all your documents, personal files and important data there. If windows some day gets messed up, you don't even care about recovering data (it's not on C: ). Simply boot with your windows dvd, format C: and reinstall.
The same would apply if you ever need to reinstall ubuntu.

You can't lose any data that is not on the system partitions. You can format them at will when ever you want (need).

---

### Post by kurt18947 on 2012-03-24
I'm doing what you're talking about but I'm using a paid-for shareware application to do it.  If you google "terabyteunlimited bootit BM" you'll find it.  I can select which partitions are visible to other partitions so I can have 2 partitions with Operating systems on them and one data partition visible to both operating systems.  The operating systems are not visible to each other unless I set them to be.  It can also relieve the 4 primary partition restriction though there's a risk to that.  You might be able to do what you want to do by setting up virtual machines or by other means as well but I'm not familiar with them.

---

### Post by Morbius1 on 2012-03-24
BootitBM is a non sequitur to the question at hand and is certainly not required to have a shared ntfs partition. I happen to use BootitBM myself and although everything you stated was true it has nothing to do with a shared partition.

> If the answer is yes, is there anything special I'll need to do in order  to achieve this, or will this be taken care of as part of the process  of installing Ubuntu?The answer is yes as stated by tho others above. You would have to use the "something else" option when you do the install however since it won't do it by itself. If this is the first time you are installing Linux you might want to wait until you after you install Linux and then just edit fstab to automount the partition.

I should note that by default Ubuntu will list all the Windows partitions in it's File Manager ( Nautilus ) even if you do not have it automounted. You would just need to select it to have it mount with a system selected set of permissions.

---

### Post by raen on 2012-03-24
**oldfred** and **darkod**, thank you for your very informative replies (and thank you for correcting my terminology!). I hadn't realized I could share application profiles via the non-OS partition. I also appreciate the link to "Change path of Documents" -- I anticipate that eventually coming in handy. I will definitely read all of the links very carefully later. Also, it's good to know that an added benefit of putting files on the non-OS partition is insurance against data loss in case of a system re-install or other disruptive event.

If I understand correctly, it is possible although non-trivial to create multiple partitions on the same disk as Windows. Ideally, I would like to maximize the non-OS space available. Thus, while I intend to follow advice and install Windows on one disk and Ubuntu on the other, I would like to be able to make a non-OS partition on both disks. I assume this is all taken care of during the Ubuntu installation, when I get to "Allocate drive space" --> "Specify partitions manually"? I hope this isn't a purpose-defeating course of action!

**Morbius1**, you said
> If this is the first time you are installing Linux you might want to wait until you after you install Linux and then just edit fstab to automount the partition.
Could you please clarify this? I'm not certain whether you mean my personal first time installing Linux or the first installation of Linux on the disks in question. I have installed Ubuntu before (on my netbook), although I deliberately overwrote the Windows installation. As for the disks in question, I suppose it would be the first, as I haven't even bought them yet. (I'm arming myself with information before I get started so I can plan better.) Either way, I'm not familiar with fstab.

Thank you.
raen

---

### Post by oldfred on 2012-03-24
The specify partitions manually did not include the NTFS driver as you are just installing Linux. You either leave space unallocated or partition in advance with gparted which does have the NTFS driver to format the partition. I always partition in advance so I do not know if they have changed that or not.

All the details of mounting partitions, I think I learned from Morbius1. So I will let him comment. But I will give a couple of links.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Often best to have specific example of your actual install when you get to it, and then we can give detailed directions.

---

### Post by darkod on 2012-03-24
The first step would be to sit down and plan the disk(s) layout. You are already on the right track since you are getting informed even before you buy the computer.

You definitely can have more than one partitions on the same disk. Once you have it all planned, the execution is not a problem. For example, during the windows installation you can create only the system partition, and create the other ntfs partitions that you want later after windows is up and running. The main thing would be to create C: with the size you had already planned in your disk layout.

In fact, with todays disk sizes, it's really bad practice to create C: on the whole disk. Why would you need 1.5TB C: that you can't even format tomorrow before getting the data out.

Make a plan how much you need for C: including your programs, games, etc, add some spare space and create C: with that size.

Split the rest of the disk as you want. After reading the info oldfred provided, ask more questions if you have them.

---

### Post by raen on 2012-03-24
Thank you, everybody. You've been extremely helpful. I suppose I can't take my questions any further until I've gotten to the point of actually doing this. When that time comes, I'm sure I'll be back.

Thanks again.
raen

---

### Post by Morbius1 on 2012-03-24
Now I'm getting confused - which for me is a fairly easy thing to do all by myself.
> This is all hypothetical right now, as I am finding out what is and is  not possible/reasonable before I even buy my new computer.
The OP is buying a new computer so unless he's getting it from a boutique vendor it will have Win7 installed already.
> I'm also thinking about having two internal hard drives for convenient extra storage Not sure if that's 2 additional HDD's or 2 in total but either way it means his Windows partitions are already set in size and the partitions on the 2nd ( 3rd ? ) drive will come formatted as NTFS.

You have enormous possibles with that much storage. If it were me I would separate them by OS family. One for Windows ( including a common ntfs partition that both Windows and Linux will access ) and one for Linux - many, many Linux OS's will fit on 1.5 TB. 

My only recommendation is to use Windows to manipulate ( delete, resize, whatever ) Windows partition and use Linux to manipulate Linux partitions. So, for example, on that 2nd disk which will come formatted in ntfs already it will have to have it's partitions deleted so that Linux can format them to ext4 or some other linux filsystem. Delete the partitions in Windows not Linux. Then use Linux to partition and format them for use with Linux.

---

### Post by raen on 2012-03-24
**Morbius1**:

Sorry for the confusion (and I'm a she, by the way ;)).

Regardless of the initial setup, I will have the system disks in the event I need to re-install Windows. So as far as that goes, I think I'm covered.

In the meantime, I'm gathering information, planning, and waiting for my income tax refund. \\:D/

raen

---

### Post by Mark Phelps on 2012-03-26
If then PC comes pre-formatted with Win7 already on it, even if the drive does not already have the 4 primary partition maximum, I would still (from experience) recommend the following approach (presuming you are actually going to install a second "disk"):

1) Remove the disk containing Win7 from the PC -- this is to ensure that nothing accidentally happens to it from the Ubuntu install
2) Insert the new disk -- the one for Ubuntu
3) Boot from the Ubuntu desktop CD (or USB stick if you made one) and install to the disk. You can mess around with manual partitioning if you wish, but I would just use the defaults and install it.
4) Reboot and start Ubuntu, confirming that it works OK
5) If you want to mess around with partitioning now, then reboot from the Ubuntu CD (or USB), select GParted (Gnome partition editor) and make the partition changes.
6) Shut down the PC
7) Reconnect the Win7 disk -- but contine to boot from the Ubuntu disk.
8) Once into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB default configuration file.

When you reboot, you should see a GRUB menu allowing you to choose which OS to launch.

---

### Post by raen on 2012-03-26
Thanks, Mark. I'll keep that in mind.

> **Mark Phelps said:**
> If then PC comes pre-formatted with Win7 already on it, even if the drive does not already have the 4 primary partition maximum, I would still (from experience) recommend the following approach (presuming you are actually going to install a second "disk"):

1) Remove the disk containing Win7 from the PC -- this is to ensure that nothing accidentally happens to it from the Ubuntu install

(SNIP)


---

### Post by raen on 2012-05-05
> **Mark Phelps said:**
> If then PC comes pre-formatted with Win7 already on it, even if the drive does not already have the 4 primary partition maximum, I would still (from experience) recommend the following approach (presuming you are actually going to install a second "disk"):

1) Remove the disk containing Win7 from the PC -- this is to ensure that nothing accidentally happens to it from the Ubuntu install
...
6) Shut down the PC
7) Reconnect the Win7 disk -- but contine to boot from the Ubuntu disk.
8) Once into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB default configuration file.

When you reboot, you should see a GRUB menu allowing you to choose which OS to launch.

I'm almost ready for this step and now I'm a little confused. What should I expect immediately after I connect the Win7 disk simultaneously with the Ubuntu disk? You seem to imply I'll be going right into Ubuntu as though Windows were still unplugged.

Thanks,
raen

---

### Post by darkod on 2012-05-06
Since the windows disk was disconnected during install, ubuntu is not aware of it. The first time you boot ubuntu, run in terminal
sudo update-grub

That will detect windows and make the entry in the boot menu.

---

### Post by raen on 2012-05-06
> **raen said:**
> I'm almost ready for this step and now I'm a little confused. What should I expect immediately after I connect the Win7 disk simultaneously with the Ubuntu disk? You seem to imply **I'll be going right into Ubuntu as though Windows were still unplugged**.

Yep, that's exactly what happened. :D And then I updated GRUB and Ubuntu can see Windows now. Woot!

Now I work on sharing documents between them.

Thanks!
raen

---

### Post by raen on 2012-05-06
All right. So the dual boot is working and Precise can see everything on the Windows disk.

Does this mean I can skip the part where I mess with fstab and go straight to creating symlinks so that (to pick one folder) /home/me/Documents actually points to /media/docfiles/Users/me/Documents ?

I thought I had instructions on how to do that bookmarked, but I can't track it down anymore.

Also, if there are two users on both systems, would it be easier to just log into one account and establish those symlinks, then log into the other account and repeat the process? There are only 5 folders for a total of 10: Documents, Downloads, Music, Pictures, Videos.

Also, if there's already something in both /home/me/Downloads and /media/docfiles/Users/me/Downloads, will the contents merge? Or should I do some backing up first?

Thanks!
raen

---

### Post by oldfred on 2012-05-06
I have not done multi-user configuration, but that can get more complicated depending on what you want to do. I think you need to explain how you want users to read, write, control certain folders as permissions can be set multiple ways.

Are you wanting to link directly to Windows 7's folders? I would not do that as Windows often does not like too much writing into its system. Better to have a shared NTFS data folder set to read/write and only have the Windows system folder set to read only. Also do not hibernate in Windows or any write into the Windows system will corrupt the hibernation.

While you can use Nautilus to see all the NTFS partitions they are only mounted as you have clicked on them. On a reboot they will not be remounted until you click. So if you try to link, reboot, and then the link does not have the mount after the reboot. Better to edit fstab to permanently mount and set permissions that you want.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)
Info on permissions for groups
[http://www.zzee.com/solutions/unix-permissions.shtml#setuid](http://www.zzee.com/solutions/unix-permissions.shtml#setuid)

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)

I think this is older, morbius1 may have more updated info.
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)

---

### Post by raen on 2012-05-06
> **oldfred said:**
> I have not done multi-user configuration, but that can get more complicated depending on what you want to do. I think you need to explain how you want users to read, write, control certain folders as permissions can be set multiple ways.

Are you wanting to link directly to Windows 7's folders? I would not do that as Windows often does not like too much writing into its system. Better to have a shared NTFS data folder set to read/write and only have the Windows system folder set to read only. Also do not hibernate in Windows or any write into the Windows system will corrupt the hibernation.

While you can use Nautilus to see all the NTFS partitions they are only mounted as you have clicked on them. On a reboot they will not be remounted until you click. So if you try to link, reboot, and then the link does not have the mount after the reboot. Better to edit fstab to permanently mount and set permissions that you want.

I have the Windows 7 disk partitioned such that the system, installed programs, etc, are on a smaller C and data storage is on a larger D. I re-directed part of the user profiles so that Documents, Downloads, Music, Pictures, and Videos are on D.

I have a comparable setup with Precise: /(root) is on /dev/sda1 and /home is on /dev/sda2

On both OSes there are the same two users. I would like to be able to easily access files like music or LibreOffice documents no matter which OS we're logged in to.

Thanks,
raen

---

### Post by raen on 2012-05-07
> **oldfred said:**
> The specify partitions manually did not include the NTFS driver as you are just installing Linux. You either leave space unallocated or partition in advance with gparted which does have the NTFS driver to format the partition. I always partition in advance so I do not know if they have changed that or not.

Often best to have specific example of your actual install when you get to it, and then we can give detailed directions.

Oh, yes, please. I don't trust myself to generalize from others' particulars.

I have the dual boot set up and I'm logged into Precise right now. If I go to Places, I can see and mount my NTFS partitions. The one I want to permanently mount is currently at /media/AllTheThings

Here are screenshots from GPartEd:
[ATTACH]217465[/ATTACH]
[ATTACH]217466[/ATTACH]

```
$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002d3d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   390627047   195312500   83  Linux
/dev/sda2       390627328  2920509439  1264941056   83  Linux
/dev/sda3      2920511486  2930276351     4882433    5  Extended
/dev/sda5      2920511488  2930276351     4882432   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8325555

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   629147647   314470400    7  HPFS/NTFS/exFAT
/dev/sdb3       629147648  2930274303  1150563328    7  HPFS/NTFS/exFAT
``````
$ sudo fdisk -lu

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002d3d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   390627047   195312500   83  Linux
/dev/sda2       390627328  2920509439  1264941056   83  Linux
/dev/sda3      2920511486  2930276351     4882433    5  Extended
/dev/sda5      2920511488  2930276351     4882432   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8325555

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   629147647   314470400    7  HPFS/NTFS/exFAT
/dev/sdb3       629147648  2930274303  1150563328    7  HPFS/NTFS/exFAT

``````
$ sudo blkid

/dev/sda1: UUID="87718c8d-0144-4611-9949-fb5d2f533846" TYPE="ext4" 
/dev/sda2: UUID="c6bdbff2-91ec-4527-bf02-b9364ce83d88" TYPE="ext4" 
/dev/sda5: UUID="ee6d5fd7-0434-4e91-b283-eeb8becfed07" TYPE="swap" 
/dev/sdb1: UUID="BCB6DB3FB6DAF8BA" TYPE="ntfs" 
/dev/sdb2: LABEL="Seven" UUID="A052D58452D55F98" TYPE="ntfs" 
/dev/sdb3: LABEL="AllTheThings" UUID="CCC2E33EC2E32C00" TYPE="ntfs" 
``````
$ mount

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raen)

```And the current state of fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=87718c8d-0144-4611-9949-fb5d2f533846 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=c6bdbff2-91ec-4527-bf02-b9364ce83d88 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ee6d5fd7-0434-4e91-b283-eeb8becfed07 none            swap    sw              0       0
```I hope this is enough information. :)

Thanks,
raen

---

### Post by oldfred on 2012-05-07
I really do not know multi-user. My wife & I just use one (but separate Thunderbird accounts) and I do not use my XP hardly at all. I last did multi-user in Novell Netware  20 years ago.

But lets first mount the data partition. You have two mount choices and several permission choices. If linking data folders you many not want to see the mount in Nautilus as it can get confusing to see it two different ways or it will not let you mount it again if you click on it. But if just mounting you may want to see it like you do now with Naulitus. ?? If you mount in /media you will see it in Nautilus. If you change all /media to /mnt then it will not be in Nautilus and you have to drill down from computer to /mnt to /mnt/data or whatever mount it is. But if linking that may be an advantage. examples below all use /media.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Unmount first if you have it mounted via Nautilus,
sudo umount /media/AllTheThings

You may have this mount already. Note that the mount point does not have to have the same name as the label, but it can be. (I get confused on my system as I have used label of Data and mount of data and those are different.)
# note that # are comments do not type.
sudo mkdir /media/AllTheThings
#backup current fstab
sudo cp /etc/fstab /etc/fstab.backup
#Add new entry to fstab as below
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

You can use device (/dev/sdb3 or UUID as UUID=CCC2E33EC2E32C00 )instead of label.
> LABEL="AllTheThings"  /media/AllTheThings ntfs defaults,uid=1000,windows_names,umask=000 0 0

I suggest you try the above first, confirm you can see the mount in Nautilus automatically and can read & write ok.
Then you may want to make some changes as below:

More info on NTFS mounting:
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Note that the above entry is for user 1000 which is the first or admin user (you). If you have other users they probably will not see the mount and you may need to edit to allow other users. I am not familiar how to do that, but have some other examples below. NTFS does not support permissions or ownership so you may just need to include the group everyone is in like gid=46.
I think I copied this from another post by Morbius1 who understands this, I just link to it or try to copy for my use.
Another example but not your UUID:
> UUID=DA9056C19056A3B3 /windows/D      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0This will mount an ntfs partition to /windows/D ( in this case ) with read write access to owner and group and no one else ( the umask=007 part ). The gid=46 is group=plugdev. All members of plugdev will have read/write access and all local login users are members of plugdev by default.
Set windows boot partition - Morbius1:
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.

And still another example, I copied:
> /dev/sda1 /media/WinXP ntfs defaults,uid=1000,gid=46,umask=007 0 0
I've just mounted an ntfs partition with me (uid=1000) as owner and with permissions for me and all local login users ( gid=46 ) to read / write and with no permissions for anyone else (umask=007).

---

