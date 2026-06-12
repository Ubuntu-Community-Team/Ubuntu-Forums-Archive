---
title: "howto move a installation on a new harddrive"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by lptr on 2007-11-26
The following is a simple howto _copying over a complet system using ONE SYSTEM_

[I]Disclaimer: Before getting into the details I have a question to anyone who did copy over all between TWO BOXES!!!  - YOUR HELP IS APPRECIATED !!!
Currently I would like to know if it is possible to do something similar (as you can read below) for two systems over a network cable. System A) is a running Linux machine having open-ssh server installed and another box B) booting from a Ubuntu Live-CD mounting that fresh harddrive that should have later a 1 by 1 copy of system A). The mentioned system on A) is pretty old and should run without changing any hardware except harddrive (if it will be possible - I don't know yet if it will start after shutdown). At the end of this howto you can find some other details regarding this. 
If I know howto copy A) to B), I will share it to the community.
[/I] 
[U]Now to the details of copying/replicating a installation to another drive:
[/U]I've been successfully copying over complete installations of Linux (all kinds of SuSE, Debian, Ubuntu) using a live-CD. Prerequisite old HDD and new HDD must be hda*X* and hdb*X* and mounted on mountpoints /OLD and /NEW.

Before you start to copy all over, partition the new drive: 
If you have a 'simple' ubuntu installation meaning just '/' (root and all other directories having on one partition) on - say - hda1 or such then you do it the easy way: Just run installer on the new harddrive and let it install a base system. Then shut down machine add both the old and new drive to system (assuming hda is old, hdb is new) and execute commands you find in **codebox #1** below.

If you want to have another advanced partitioning schema, then you can use the installer too, but you need to select manual partitioning (you could also use cfdisk, or another tool). Size the partitions to your needs. You should have '/' '/data' '/var' '/home' 'swap' exactly where you had it before. Of course size of all partitions should be larger than the amount of data having on old partitions. After this, you need also to using mkfs.xxx to format your partitions, and of course you need to place a valid boot loader into boot sector of boot drive. I don't get deeper into this, now. Maybe anyone here in the NG could be so kind to instruct doing this advanced steps? I did not explicitly searching for this, so maybe anyone described it on another thread. In this case a link would be very helpfull.

I assuming here, that you already prepared things as described before, having a partitioned and preformated new harddrive, that has a valid boot loader. 

[B] Following commands need to be run from Live-CD (Ubuntu)
[/B] First open a shell window. Then:
**[SIZE=1]codebox #1[/SIZE]**   ```
$ sudo su
$ mkdir /OLD
$ mkdir /NEW
$ mount -t ext3 /dev/hda1 /OLD
$ mount -t ext3 /dev/hdb1 /NEW
$ cd /OLD
$ tar -cSp --numeric-owner -f - . | ( cd /NEW && tar xSpvf - )
```[B][SIZE=1]codebox #1[/SIZE]
[/B]Of course this needs to be done with all other partitions (except swap). If you don't having filesystem *'ext3'* (for instance *ReiserFS*) you need to switch this (*man mount*). Probably one needs to change hda to sda (SATA drives usually will be sdx). 

Be save to have a look on your mounted drives before you start copy process (the *tar* command in last line). This could easily be verified using cat /OLD/etc/hosts or any file that is definitively known to be edited by you in the past.

To *unmount* the previously mounted partition and to remount it to a different partition, use this:
```

$ umount /OLD
$ umount /NEW
 
```If you having an old Linux box on exactly same hardware (mainboard network card etc. identical), then you should be done. Just shutdown replace OLD with NEW drive (don't forget that if you change the connector on mainboard sda may be on sdb and boot may not function). Boot and be lucky for at least three another years (average livetime of a brandnew drive).

If you having a newer installation that you simply plan to get moved, you NEED to at least change 
```
 */etc/fstab *
```and
```
*/boot/grub/menu.lst*
```Why? The issue is, that every harddrive gets an own UUID that is explicitly named in upper two files. So you need to change this UUIDs. Use Live-CD to boot with your new hardware to find out the new UUID for your boot partition  using this shell command:
 ```

 $ ls -l /dev/disk/by-uuid/

```and replace the old values in both files with new values using your favourite text editor (vi, nano, whatever...).

A similar thing with newer Linux distributions is with NICs (network interface cards). As you maybe know every NIC has an unique factory ID. Newer distros fixate this, too. This ID is mapped in Ubuntu based installation in the file
 ```
 /etc/udev/rules.d/70-persistent-net.rules  
```There you will find a line like this:
```
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:11:22:33:44:55", ATTRS{type}=="1", NAME="eth0"

```you have to replace the factory id address of NIC (here 00:11:2..) with your new id. If you want to find the new ID you can your shell and following command.
```
$ dmesg

```searching for your specific NIC address and editing mentioned net.rules file. Otherwise you will have trouble using network config tools provided by Ubuntu.


Ok. By now that's it. This is the actual short howto duplicating HDDs 1:1.

* Again: I would love to get an input of howto transfering a complete installation from a running system. We having a box personally I am afraid to shut down. Otherwise we would have used upper description. So we need to have the complete system transfered over LAN-wire. I have some base ideas of doing this but never done this before. * 
If anyone did something like this and has a proofed way, please let me know how to do it. Thanks in advance!

If anyone find some addons to get added here - let me know I will take it into this description. If there is another howto describing things better, let me know, too. I will refer to this. 

Hope that this will help some of you out there and saving some time.

rob*

---

