---
title: "Upgrade to 12.04 - Ubuntu stops to boot after grub menu"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by tschill on 2012-05-05
I do have a dual boot Ubuntu/WinXP computer, which worked fine with Ubuntu Desktop 11.10. I waited, until I had seen enough user saying, that they didn't experience any problems with the upgrade to 12.04, but here we are...

After the uneventful upgrade the reboot got stuck after choosing from the Grub menu the 3.0.0.-19 kernel. Like before the upgrade, I see the startup screen with the Ubuntu logo for a minute and then the screen switches to messages scattered over the screen and the computer is stuck. I can enter a terminal with CTRL/ALT/F1 and restart the computer with CTRL/ALT/DEL at this point. 
This happens also when I use older kernel versions. I tried to apt-get update from the terminal, but that was not clever, because in the terminal I don't have an internet connection established. Then I tried in the terminal the command dpkg --configure -a and got an  error message "error parsing file /var/lib/dpkg/status near line 35128  package lxbdaacs: blank line in value of field Description". 

I also created a live USB for 12.04, which runs fine (and from which I am writing at the moment). Now with a working internet connection, I tried apt-get update, but this only showed how little I know, since obviously this command only updated the USB stick version, not the fawlty 12.04 version on the hard drive.

Is there a way to have access from the live USB Ubuntu, to run an apt-get update for the hard drive? Didn"t find anything in the forum.

People in other threads also asked for the output of fdisk -l  and etc/fstab. Especially the output of the latter one looks not right to me (i.e. I see the word error)

fdisk -l

> Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xebe4cb8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    22870015    11433984   27  Hidden NTFS WinRE
/dev/sda2   *    22870016   377688063   177409024    7  HPFS/NTFS/exFAT
/dev/sda3       377690110   586072063   104190977    5  Extended
/dev/sda5       377690112   582070971   102190430   83  Linux
/dev/sda6       582072320   586072063     1999872   82  Linux swap / Solaris
etc/fstab

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c51b490a-9943-4c5e-9be4-19daab9626f3 /               ext3    errors=remount-ro 0       1
# /media/sda2 was on /dev/sda2 during installation
UUID=5AF44E88F44E65FB /media/sda2     ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
#UUID=ad606e1d-a2cb-48fc-b9e2-8b404496efec none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0Would be glad for any suggestions, since I am only a Ubuntu beginner and don't have a strategy what to try first to restore my Ubuntu OS.

---

### Post by tschill on 2012-05-05
In another thread I found how to access the linux partition from live USB

```

sudo mount /dev/sda5 /mnt
sudo chroot /mnt
```Afterwards I was able to run apt-get upgrade, but this only led to an error message about unmet dependencies. It was suggested to run 

```
apt-get upgrade -f
```or 

```
apt-get -f install
```Both strategies led to the same, well known error message:

> Can not write log, openpty() failed (/dev/pts not mounted?)
dpkg: error: parsing file '/var/lib/dpkg/status' near line 35128 package 'lxbdaacs':
 blank line in value of field 'Description'
E: Sub-process /usr/bin/dpkg returned an error code (2)

I tried 

```
dpkg --clear-avail 			 		
```

but get the same error message afterwards.

What now?

---

### Post by tschill on 2012-05-05
Hm. I had a look at /var/lib/dpkg/status file with gedit. The line mentioned in the error message is indeed empty. It seems there is a . missing, whysoever. So I tried to change the file, but I don't have the permission to change it. 
How can I change the status file from the terminal, from which I accessed my Ubuntu file system on the harddrive with chroot?

---

### Post by darkod on 2012-05-05
With chroot you should have maximum permissions. The file might be locked for editing even for root.

Unfortunately I don't know to fix this error.

---

### Post by oldfred on 2012-05-05
It looks like you just mounted your root partition and chrooted to that. You need to mount & bind several more partitions.

# are comments do not copy , example below is to reinstall grub2 which you may or may not need.

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /usr/ /mnt/usr
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
#sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
#sudo chroot /mnt/ /bin/bash

sudo chroot /mnt
apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
# possibly this also
dpkg-reconfigure grub-pc
# run any other commands needed while in chroot
#Exit by pressing CTRL-d.
umount /mnt/dev /mnt/proc /mnt/sys /mnt/usr
umount /mnt

Other examples of chroot:
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by tschill on 2012-05-05
Thank you two for the anwers. It was my mistake - I tried to change the status file from the live USB Ubuntu, where I obviously didn't have root permissions. So after some chmod juggling I managed to insert the missing . in the file and afterwards Ubuntu was able to proceed to the login screen. After the login some of the programs are visible, but there are obviously problems that need to be addressed. Most importantly, the wireless connection (including the dropbox icon) and the shutdown buttons are missing from the task bar. So an update/upgrade from the harddisc Ubuntu version/synaptic manager/update manager is not possible. Hm. 

I tried to run an upgrade as chroot, but now for a change the following error message appears:

> E: Could not perform immediate configuration on 'util-linux'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)In other threads it was suggested, to upgrade util-linux first with synaptic manager before upgrading, but the synaptic manager on live USB Ubuntu refers to the util-linux of the USB Ubuntu and the harddisc Ubuntu version doesn"t have access to the internet.

Any ideas?

---

### Post by darkod on 2012-05-05
And now that the blank line error is solved, how about running:
sudo dpkg --configure -a

so it can finish with any pending packages still not configured after the upgrade. You should run it from the hdd ubuntu, not live mode.

---

### Post by tschill on 2012-05-05
Sorry, forgot to mention that. I tried dpkg --configure -a from the harddisc version, luckily I can open a terminal there. To make a long story short, I get an error message: "Processing was halted because there were too many errors." I could post the whole list of error messages, if this is of any help. But long cat is  long.

---

### Post by oldfred on 2012-05-05
Are you running these before the dpkg update?

apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
apt-get dist-upgrade
apt-get -f install

---

### Post by tschill on 2012-05-05
Yes. That ended with the error message 

> E: Could not perform immediate configuration on 'util-linux'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

---

### Post by oldfred on 2012-05-05
It seems like it is trying to work from your USB liveCd not the chroot root.

---

### Post by tschill on 2012-05-06
I am sure I am working on the sda5 version - the hard disc blinks and the USB stick doesn't. Or did I misunderstand you?



[Here]("http://superuser.com/questions/199582/apt-error-could-not-perform-immediate-configuration-on") it is suggested to go to package in /var/cache/apt/archives and run dpkg -i on package. So in my case it was 

```
dpkg -i util-linux_2.20.1-1ubuntu3_i386.deb
```

The output was

> (Reading database ... 436089 files and directories currently installed.)
Preparing to replace util-linux 2.19.1-2ubuntu3 (using util-linux_2.20.1-1ubuntu3_i386.deb) ...
Unpacking replacement util-linux ...
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on upstart-job; however:
  Package upstart-job is not installed.
  Package upstart which provides upstart-job is not configured yet.
dpkg: error processing util-linux (--install):
 dependency problems - leaving unconfigured
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 util-linux


One problem leading to the next. Is this the point, where one should give up and start for the sake of community"s nerves a clean install?

---

### Post by oldfred on 2012-05-06
If you have good backups or can copy whatever you want from /home, then a clean install is quicker.
Otherwise we have to try to find what is the underlying issue.

---

### Post by tschill on 2012-05-06
I do have access to all files on sda5 (the file structure in itself is not affected). I do have backups of everything important and most databases for my programs are on the windows partition anyhow. It is just the trouble to re-install all programs, assign them to their windows counterparts, so that both use the same database (like firefox/thunderbird for instance). But when I look at the output of dpkg then I see so many unmet dependencies, that I don't know where to start. 
Too bad, that the fresh install from the USB drive doesn't keep most file associations. 

Something that really bothers me - I thought the old kernel versions are kept in Grub, that at least you can run previous versions, that worked so far. But two times I upgraded Ubuntu and both times the errors affected not only the upgrade, but also every previous version. Any strategy to prevent this in the future?

---

### Post by oldfred on 2012-05-06
I had to do a clean install when I went from 32bit to 64 bit from 9.04 to 9.10. I had done upgrades from 6.06 and found clean install so much better that I only do clean installs. But you have to have good backups, export list of apps and maybe some other things. 

I also went to a new larger drive and had lots of room, so I just install a new / (root) to a 25GB partition and can still boot old version. I have all data in other partitions including my Firefox & Tunderbird profiles and use profile.ini to redirect to the shared data partition.

---

### Post by tschill on 2012-05-06
Thanks, this sounds like a good strategy. At the moment I am afraid to destroy my computer, if I try to rearrange my partitions. But the next installation will be something like what you described.

I think, you can close this thread now.

---

### Post by virtualXTC on 2012-06-13
> **tschill said:**
> Then I tried in the terminal the command dpkg --configure -a and got an  error message "error parsing file /var/lib/dpkg/status near line 35128  package lxbdaacs: blank line in value of field Description". 


I experienced this same issue after upgrade.  I just edited /var/lib/dpkg/status removing the line in question / adding a period to the one before it.  You can do this with out chroot by just pressing Ctrl-alt-F2 and logging in, then editing with your favorite command line editor using superuser permissions.
ie:
```
$ sudo nano /var/lib/dpkg/status 
```
(the key commands for nano to jump to a line are CTRL-W then CTRL-T)

After fixing this I also had the same issue with a different package listed in a similar file.  The fix was the same and now my system is able to continue the upgrade.

Good luck!

---

