---
title: "PPC installation: RAID+LVM on clean disks: no luck!"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by generica on 2006-08-31
Hi there,

I'm trying to install Ubuntu Server PPC Dapper Drake onto a PowerMac G4 Tower (800Mhz).  The machine has three drives, all of which are blank and unpartitioned.  This is a completely new installation on new disks.

Starting up from the server install disk, I cannot seem to configure any Software RAID devices, which means I can't get any further.  I want the entire system to be LVM2 on top of software RAID, including the root filesystem and swap, for reliability and ease of maintenance, as I intend to make this machine into a file server.

When you get to the stage of the installation where it asks you to set up your partitions, and you try to configure Software RAID, all that happens is it complains that there are no drives on any disks marked as "Linux RAID Autodetect".  However, there does not seem to be a way to create any partitions of this type.  I've tried many things including partitioning ahead of time using the Live CD but alas, the Live CD doesn't support RAID or LVM properly either.  (running partman from the Live CD had no RAID/LVM features, even after installing the dmraid package through Synaptic Package Manager).

I'm a reasonably competent systems administrator (self-taught) but I can't seem to decypher all the stuff in the Ubuntu LVM+RAID HOWTO file because it was written by someone who only tested it on a machine that was already partitioned (how useless is that? the described methods in the howto are completely unworkable unless the drive already has been partitioned and set up for RAID via some non-Ubuntu-Installer method and it is not documented how to set up RAID drives in the Ubuntu docs that I've found.)

Does anyone have any tips as to where I can go from here?  my other recent forum posts have been totally unresponded to by anyone, it doesn't seem like there are any experts willing to help this new-to-Ubuntu user in getting the installations to work.  I have yet to get Ubuntu installed on a single PPC machine, encountering various serious errors no matter what hardware I try it on.  I've been using Linux since 1997.  I'm at a loss...

An additional question I have, since I'm new to using LVM:  Should I create the LVM volume groups *before* the RAID stuff, or vice versa?

Thanks in advance, hopefully someone out there is reading this who has successfully set up Ubuntu Server PPC distro on a machine using LVM and software RAID. :confused: 

generica

---

### Post by squarebug on 2006-12-05
Hey generica,

I'm running into the same problems as you are, it seems you never got any reply to your post. If you've solved your problem, could you please post a quick howto? 
If not and you're still trying to get this to work, I have a bit of information for you.. it seems that there is no RAID  autodetect functionality for PPC, so the usual x86 way of automatically booting from a RAID array won't work. Instead, you need to create an initial ramdisk, but I haven't tried this on a PPC. At the time I opted for just putting my data on a software RAID 1, booting off a regular partition. Even then I had to specify my RAID array in the boot loader:
```
append="md=0,/dev/<raid part1>,/dev/<raid part2>"

```
In general, I would always put LVM on top of an existing RAID, adhering to the same logic as with hardware RAID. I would like the RAID functionality to be a level below my file system, so to speak, because I want anything I do on the file system or data level to be protected (mirrored, striped w. parity).

Currently I'm willing to settle to boot off a LVM partition on my G5, but I can't get this to work either. Any help is more than welcome.

---

### Post by generica on 2006-12-05
Hello!  Thanks for being the only person to answer... I felt like this guy> ](*,) so I ended up giving up on getting LVM on top of RAID to work and just implemented some physical redundancy and backup scripts instead.  It seems the installation routines for the PPC distribution of Ubuntu are incomplete/flawed when it comes to this particular subject.  I appreciate the tips you provided though, if I ever feel like giving it another shot I'll post back my results.

Steve

---

### Post by squarebug on 2006-12-27
Hello generica,

after much trial and more error I found a way to at least get a bootable RAID system on my PPC (bootable LVM on RAID doesn't seem possible, see below). The following is rather lenghty, and for reference purposes I tried this on a G5 dual 2GHz with 2 WD SATA drives.

Using the Ubuntu Alternate 6.10 disk and kernel 2.6.17-10 you will find raid support compiled in, so there is no need to create a custom kernel. However, I was not able to create a raid set for my root partition and boot from it during the normal install (i tried all install modes on Alternate). So if you have your mind set on booting your PPC from a software raid stack, you will have to play some tricks. First and most important, you have to boot the rescue-powerpc64 image, this seems to be the only one with the necessary /dev/md inodes already prepared. You could create the inodes you need yourself (e.g. mknode /dev/md0 b 9 1), but I decided not to make life harder for me than necessary

My goal was to create  a small (5GB) RAID1 partition md0 to hold my Root file system (/) and a second, larger RAID1 partition md1 with LVM on top. I wanted to use the second RAID partition  to hold my data and some of the OS directories (/var, /tmp and /usr). Once you are able to install Ubuntu on the first partition and to boot from that creating the second RAID partition is trivial, therefore I will concentrate on the first step. 

If you ask why not one big RAID stack with LVM on top, the answer seems to be that yaboot cannot boot from LVM (_[http://oss.gonicus.de/openpower/index.php/Red_Hat_-_Software_Raid](http://oss.gonicus.de/openpower/index.php/Red_Hat_-_Software_Raid)_). 

And before I continue, some clarification about PPC disk partitioning. I used mac-fdisk for all disk operations. The first partition that is listed in mac-fdisk is the partition map itself (unlike in x86 fdisk), you obviously need it. If you delete the partition map you lose all existing data on the disk. The second partition is the Apple bootstrap partition (in the case of MACs) or PReP (in the case of other systems like IBM, Sun). This partition holds the boot loader, yaboot. Be aware that at least on IBM systems this partition may not exceed a certain size. For Apple systems I am not aware of a size limitation, Apples default size is 800MB. PPC based systems do NOT need a separate /boot partition, they use the bootstrap/prep partition instead. 

The way to a bootable RAID1 installation that worked for me was the following:
[LIST] boot Ubuntu Alternate PPC and select the rescue-powerpc64 image
[*] partition your disks
[*] manually create a RAID set
[*] manually create the /target directory and mount the raid set on it
[*] start the Ubuntu partitioner and adjust the mount points
[*] resume the normal install
[*] adjust the yaboot.conf file (unfortunately Ubuntu gets the partition value wrong)
[*] exit and reboot hopefully into your new Ubuntu-on-RAID installation
[/LIST]

Boot from the Alternate CD and select rescue-powerpc64. Follow the wizard until you're presented with a dialog to mount a partition. At this point, select Back to get to the main menu. Select the last item, Execute a shell. Now use mac-fdisk to create the partitions for your RAID set. In my case, I wanted a RAID1 system, comprised of two partitions /dev/sda4 and /dev/sdb3. Use the option 'C' to create a partition of a specific type. Specify the size of the partition, its name and enter 'Linux_raid_autodetect' as the partition type. After you created both partitions, initialize the RAID set.
```
mdadm --create -l1 -n2 /dev/md0 /dev/sda4 /dev/sdb3
```
Check the status:
```
mdadm -D /dev/md0
```Create a file system on the RAID device:
```
mkreiserfs /dev/md0
```Create the /target directory
```
mkdir /target
```Mount the device:
```
mount -t reiserfs /dev/md0 /target
```The installer expects to handle the md0 device through /dev/md/0. However, in the rescue image this device doesn't exist. I created a softlink to account for that:
```
mkdir /dev/md
ln -sf /dev/md0 /dev/md/0
```

Now you can exit out of the shell by typing 'exit'. You are now back at the installer main menu. 

Select Partition disk, your RAID device should now be listed on the following screen. Select Manually partition disk. On the next screen, you'll find your RAID set mounted as /dev/mapper/md0 and also both of the partitions that make up your RAID device. You need to remount /dev/md0 as / and you need to unmount both partitions (in my case /dev/sda4 and /dev/sdb3). These two partitions must not be mounted. You will receive warnings about this later which you can ignore. In addition, you may want to create swap and extra partitions. Exist the partitioner by selecting Finish and write partition table.

Back at the Main menu, continue the installation as usual. Everything should run smooth now until you're prompted to remove the CD and reboot. 

Unfortunately, yaboot seems to get the disk scheme wrong. This results in a non-bootable system. To remedy this you have to boot again from CD, into rescue-powerpc64. As before, open a shell. You will need to manually start the RAID array, mount and chroot it and then edit your /etc/yaboot.conf.
```
mdadm --assemble /dev/md0 /dev/sda4 /dev/sdb3
mkdir /target
mount -t reiserfs /dev/md0 /target
mount -t proc proc /target/proc
chroot /target
nano /etc/yaboot.conf
```

In my case, the partition was set to 0, but my system partition is actually 4 (/dev/sda4). Note that had my RAID array been assembled the other way round (sda copying off sdb), the system partition would have been three. Your root should already be set to /dev/md0. Edit the following line to reflect your system partition:
```
Partition=4
root=/dev/md0
```
Also, I needed the following append line for my kernel, this should go under the 'image' statement:
```
append="md=0,/dev/sda4,/dev/sdb3"
```
Save the changes to yaboot.conf and write the changes to the Apple bootpartition:
```
ybin -v
```
Exit from the chroot environment and unmount the disk:
```
umount /target/proc
umount /target
```
Exit the shell by issuing 'exit'. Now back at the installer Main menu, you can just abort the installation and reboot your system. Hopefully, this time it will boot into your new RAID installation.

---

