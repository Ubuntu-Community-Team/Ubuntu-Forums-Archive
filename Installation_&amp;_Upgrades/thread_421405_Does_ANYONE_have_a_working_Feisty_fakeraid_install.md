---
title: "Does ANYONE have a working Feisty fakeraid installation?"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by ifinishwhatistar on 2007-04-24
I've been searching the forums extensively and have found many posts about the following problem in one form or another: 

- You've got a raid (fakeraid) array (i.e. through dmraid with some fake 'hardware' controller e.g. nvraid, intel, whatever).  
- After installing Feisty (in my case upgrading from Edgy), grub complains that it can't find the root directory.  In fact, it can't find ANY of the partitions on the raid drive.

In my case and in others that I've read, a quick fix for this problem can be fixed by simply using an older kernel/initrd (I've only tried 2.6.17-11 which works for me), and Feisty will run on the old kernel.

So I'd like to know, does anyone have a functioning Feisty on fakeraid array with the new 2.6.20-15 kernel?

BTW, I'd request not getting responses like 'don't use fakeraid.'  I'd prefer not to have to erase my drives again.

---

### Post by ld50 on 2007-04-24
I dont have a working array but I would REALLY like to see this answered, I've been trying for two days to get it set up and the best I can get is a Grub error.  So as of now its back to installing 6.10 untill I see a solution.

---

### Post by zero-Q on 2007-04-26
I have same problem and I ll use 610 till the bug fixxed...

---

### Post by g8m on 2007-04-26
I have been doing some reading because I just got a asus p5b motherboard. What I found on several forums including fedora's, debian's and gentoo's is that linux does not support fakeraid. If you want to use a raid configuration you can use software-raid. And even if u use software-raid u need a partition outside the raid array to boot the kernel from.

---

### Post by ifinishwhatistar on 2007-04-28
Right, I meant software RAID.  

I think I've confirmed that my problem is definitely RAID-related, not the same "tty" error that the other threads are about.

I tried starting from the Feisty LiveCD.  I installed dmraid from the CD.
If I activate the raid arrays I get:

```
root@ubuntu:~# dmraid -ay -v -d
DEBUG: _find_set: searching nvidia_bfcfchfc
DEBUG: _find_set: searching nvidia_bfcfchfc
DEBUG: _find_set: searching nvidia_bfcfchfc
DEBUG: _find_set: not found nvidia_bfcfchfc
DEBUG: _find_set: not found nvidia_bfcfchfc
DEBUG: _find_set: not found nvidia_bfcfchfc
DEBUG: _find_set: searching nvidia_bfcfchfc
DEBUG: _find_set: not found nvidia_bfcfchfc
DEBUG: checking nvidia device "/dev/sdb"
DEBUG: set status of set "nvidia_bfcfchfc" to 16"
RAID set "nvidia_bfcfchfc" already active
INFO: Activating stripe RAID set "nvidia_bfcfchfc"
DEBUG: freeing devices of RAID set "nvidia_bfcfchfc"
DEBUG: freeing device "nvidia_bfcfchfc", path "/dev/sdb"
```

If I list the contents of the raid mapper directory, I get:

```
root@ubuntu:~# ls /dev/mapper/
control  nvidia_bfcfchfc
```

BUT!  If I fdisk the controller I get:

```
root@ubuntu:~# fdisk -l /dev/mapper/nvidia_bfcfchfc 

Disk /dev/mapper/nvidia_bfcfchfc: 122.9 GB, 122942259200 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_bfcfchfc1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/mapper/nvidia_bfcfchfc2            3917        3926       80325   83  Linux
/dev/mapper/nvidia_bfcfchfc3            3927        4176     2008125   82  Linux swap / Solaris
/dev/mapper/nvidia_bfcfchfc4            4177       29893   206571802+  83  Linux

```

So fdisk returns exactly what it should--it shows my four partitions on my raid array...but dmraid fails to actually put the partitions in /dev/mapper, and so I can't access them.

This is exactly what happens when I load feisty with the 2.6.20-15 kernel...even though it works with the 2.6.17-11 kernel.

Does anyone have any experience with a functioning raid array of this type or any ideas as to what could possibly be wrong?

My hardware:
HDD: 2x120gb maxtor SATA in RAID0 via nforce4 nvidia raid controller through dmraid
MB: Gigabyte GA-8N-SLI (nForce4 chipset)
CPU: Pentium D 940
GeForce 7900GT

---

### Post by swp6499 on 2007-05-01
after a long and painfull all night process i am successfully dual booting xp and fesity in raid 0 with dmraid on nvraid...im not so good at how to's but ill try......i had a lot of help from a good friend with this...

first we booted the feisty live cd and enabled the extra repos and installed the dmraid package...
after dmraid was installed in terminal type dmraid -ay then ls /dev/mapper should output your partitions if u already had any( iad a previous install of fedora on raid0)
as long as your nv-????????? partitions show up you are good
if they show up fdisk your nv-?????? main partition.... partition as desired( iwent ahead an wrote all my partitions including my swap partition but i didnt set any flags for any of these partitions in fdisk) write to disk
reboot back into the live cd as ubiquity will not recognize the partitions yet...once rebooted enable the extra repos again and reinstall the dmraid package then ls /dev/mapper to make sure your partitions are there...if they are there start ubiquity and go through the install until you get to the guided partition part and click on manually configure partition...what we had to do was set the nv-?????? partion we wanted to use for boot here in this screen and use the "do not use" on the partitions you dont want ubiquity to touch and the point ubiquity to the partition you want as boot and install...once ubiquity fails installing grub we followed the rest of the fakeraid howto on ubuntu wiki...the once all setup in terminal mkswap the nv-???? partition you set as swap and then in terminal swapon the nv-??????? partition you set as swap...

i know this may sound too easy or maybe we just got lucky.....but thats what we did .....i really hope this helps if anyone has any questions please do not hesitate to ask...i will try if i can to help as much as possible....

---

### Post by bnuytten on 2007-05-14
> **swp6499 said:**
> after a long and painfull all night process i am successfully dual booting xp and fesity in raid 0 with dmraid on nvraid...im not so good at how to's but ill try......i had a lot of help from a good friend with this...

first we booted the feisty live cd and enabled the extra repos and installed the dmraid package...
after dmraid was installed in terminal type dmraid -ay then ls /dev/mapper should output your partitions if u already had any( iad a previous install of fedora on raid0)
as long as your nv-????????? partitions show up you are good
if they show up fdisk your nv-?????? main partition.... partition as desired( iwent ahead an wrote all my partitions including my swap partition but i didnt set any flags for any of these partitions in fdisk) write to disk
reboot back into the live cd as ubiquity will not recognize the partitions yet...once rebooted enable the extra repos again and reinstall the dmraid package then ls /dev/mapper to make sure your partitions are there...if they are there start ubiquity and go through the install until you get to the guided partition part and click on manually configure partition...what we had to do was set the nv-?????? partion we wanted to use for boot here in this screen and use the "do not use" on the partitions you dont want ubiquity to touch and the point ubiquity to the partition you want as boot and install...once ubiquity fails installing grub we followed the rest of the fakeraid howto on ubuntu wiki...the once all setup in terminal mkswap the nv-???? partition you set as swap and then in terminal swapon the nv-??????? partition you set as swap...

i know this may sound too easy or maybe we just got lucky.....but thats what we did .....i really hope this helps if anyone has any questions please do not hesitate to ask...i will try if i can to help as much as possible....

I tried this approach too but it gets messy when you have to select the partitions and mount points. For some reason both "normal" and "fakeraid" devices are displayed. I guess you just have to ignore the "normal" devices and only use the fakeraids. But I am not sure which are which :-) Anyway, here's a good [tutorial]("https://help.ubuntu.com/community/FakeRaidHowto"). I managed to setup Feisty on an Nforce5 RAID0. I have now a dual boot windows/linux install.

I have a few comments for the tutorial.

[LIST]
[*]If you have problems with the cdrom as an apt source, just comment it out or adjust your /etc/fstab (on the chroot partition, not on the live cd) so you can mount it automagically ;-)
[*]Concerning the dmraid error message... I used dpkg-reconfigure --force dmraid and just went on.
[*]Last but not least, use adduser in stead of useradd. I got it all up and running but when logging in, I got a message that my home directory did not exist... No worry since you can rerun livecd, install dmraid, mount your linux root partition, chroot and do the adduser thing.
[*]You may want to manually unmount the six mounted partitions before you reboot. Keep in mind that you can  unmount /target only when /target/boot, /target/dev, etcetera are unmounted.
[/LIST]

If you have any questions, feel free to ask :-)

---

### Post by jewishj on 2007-05-18
I tried all the suggested approaches, but was really only able to get this working by using a hybrid of the following two wikis: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) and [https://wiki.ubuntu.com/FakeRaidEdgy](https://wiki.ubuntu.com/FakeRaidEdgy)

I have an EVGA NVIDIA nForce 590 SLI board and 2x WD Raptor SATA drives in a RAID 0 so I was able to get it working with that configuration.

When I would try to use just the FakeRaidHowTo wiki (HT) I would end up with a system that booted but would be very unstable - with a messed up X and a weird problem with some options in the administration menus not showing up.  Trying the FakeRaidEdgy wiki (EG) would result in the partitioning not working and GRUB complaining about bad partition tables and such. 

To get everything working well, I did the following (you will need a Live CD and an Alternate Install CD to do it this way):

1) Boot from Live CD and follow HT to the point where the partitions are created and formatted using fdisk and mkfs/mkswap/etc.  I stopped right before the target directory is made (the "mkdir /target" line at the top of the "Mounting the Temporary File Structure" section).

2) Restart, and put in the Alternate Install CD.  Then follow the text-only installer until you get to the partitioning, follow the instructions in EG to get dmraid running in the installer.  You should already have all of your partitions ready to go and showing up in the partitioner after you get dmraid running.  When I went in here, I saw listings for my the RAID listed and for each partition on the RAID seperately.  Something like this:

nvidia_bgfabdcg
     -Partition 1:  swap  8GB
     -Partition 2:  ext3   147.4GB

nvidia_bgfabdcg1
     -Partition 1:  swap 8GB

nvidia_bgfabdcg2
     -Partition 1: ext3 147.4GB


Not exactly like that... but it's close enough that you'll recognize it.  Anyways, I just set the mount directories for the fdisked partitions instead of the partitions on the RAID recognized by the partitioner (I just went in and told it to use the partition nvidia_bgfabdcg1 as swap and use the partition under bgfabdcg2 as / - and left the listings under nvidia_bgfabdcg alone - and finished.  I did not have it remake the filesystems where I could avoid it.

3) After going through that, I went through the rest of the install process, and when LILO failed to install - I chose "OK" and then "Continue without bootloader" to finish the install.

4) When the system rebooted, I put the Live CD back in and did the following steps (all of which can be found in detail in HT):

-update repositories and install DMRAID
-create /target dir and mount the raid to it
-copied /etc/apt/sources.list to /target/etc/apt/sources.list
-copied dev, sys, and proc to /target and chrooted into it
-ran apt-get update and then installed dmraid and grub with apt-get install
-followed the instructions in HT to configure and load grub

Reboot and everything worked great!  Finally!

Anyways, I hope that can help someone else.  Feel free to ask any questions or anything.

---

### Post by igloocentral on 2007-05-24
I just made a bunch of changes to the [FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) to try and simplify things for people a bit. I also wrote a [FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug) for people who are really in trouble.

I had the messed up X session and I think it was caused by the acpid conflict which I fixed in the Howto by issuing the 'killall acpid' before installing ubuntu-desktop. I'd love to know if the updated HT works for you!

**bnuytten** - I'd love to know what error you got when using the cdrom as an apt source. I did add the -m flag to the "apt-cdrom -m add" command to get rid of one error. Also I added "mkdir /home/alice" so that you have a home directory when you log in.

---

