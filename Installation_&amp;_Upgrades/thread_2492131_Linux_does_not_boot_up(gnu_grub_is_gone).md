---
title: "Linux does not boot up(gnu grub is gone)"
date: 2023-10-31
forum: Installation &amp; Upgrades
---

### Post by d3vestator on 2023-10-31
afte[I]r getting everything working with my wifi, i decided to install an old version of Python(accidentally) which causes my computer not to boot into grub anymore and therefore cant get to ubuntu.
.ubuntu is still available in bios, but doesn't recognize a partition[/I]

---

### Post by oldfred on 2023-10-31
Its not just booting, but major parts of the system rely on the default install of python3.

Quickest is reinstall & restore from you backup.

You may be able to chroot into your system can reinstall entire desktop, whichever desktop you have.
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)

---

### Post by MAFoElffen on 2023-10-31
We'll continue this now here...

During this, boot from an installer LiveCD, connect your wifi, get back to this thread from FireFox, and open a terminal session.

Do not shutdown, nor reboot until we are through. If at any time, you get an error or have a question, stop and ask here. Understood? 

The first thing I need information on is how that Live Environment see this: You never did post this yet, and I need this information. Why? becaseu when we triedthis last time, is had an error, and we needed to figure out the correct partition to use in your mounts.
```

lsblk -e7 -o name,label,size,fstype,mountpoint

```
Because at the time you did your 'system-info' report, it said that this was your system's layout:
```

nvme0n1     476.9G                                                    INTEL SSDPEKNU512GZ
|_nvme0n1p1   260M vfat     SYSTEM /boot/efi                          
|_nvme0n1p2    16M                                                    
|_nvme0n1p3 247.4G ntfs     OS                                        
|_nvme0n1p4   1.1G ntfs                                               
|_nvme0n1p5   200M vfat     MYASUS                                    
[COLOR=#ff0000]|_nvme0n1p6   228G ext4            /                                  [/COLOR]

```
But when you mounted /dev/nvme0n1p6 and looked at it in mount details, for some reason it had fuse as the filesystem type and threw errors...
```

ubuntu@ubuntu:~/Downloads$ sudo ~/Downloads/GetMeIn
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which

root@ubuntu:/home/ubuntu/Downloads# mount | grep -v -e 'snaps\|/var\|/sys\|/proc\|/run\|/sys\|tempfs\|mqueue\|hugetlbfs\|devpts'
udev on /dev type devtmpfs (rw,nosuid,relatime,size=7822232k,nr_inodes=1955558,mode=755,inode64)

/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime,errors=continue)
/cow on / type overlay (rw,relatime,lowerdir=/filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work,xino=off)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,inode64)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime,inode64)
[COLOR=#ff0000]/dev/nvme0n1p6 on /mnt type fuseblk (ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096)[/COLOR]

```

---

### Post by MAFoElffen on 2023-10-31
(Still from being booted from the LiveUSB...)

Try these commands, line by line. See if they go without errors.
```

sudo su
umount -a
mount /dev/nvme0n1p5 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env bash --login
mount -a
ls -lah /usr/bin/python*

```
I'll stop there for now, do not shutdown or back out. I want to get you "in" to that point for now.

Post the output of the last command.

---

### Post by d3vestator on 2023-10-31
ill start tmrw then, sometime around noon,

---

### Post by MAFoElffen on 2023-10-31
Okay. What time zone? I'm UTC/GMT -8

---

### Post by d3vestator on 2023-10-31
Cst

---

### Post by d3vestator on 2023-11-01
```


ubuntu@ubuntu:~$ lsblk -e7 -o name,label,size,fstype,mountpoint
NAME        LABEL         SIZE FSTYPE MOUNTPOINT
sda                       7.5G        
&#9492;&#9472;sda1      UBUNTU 22_0   7.5G vfat   /cdrom
nvme0n1                 476.9G        
&#9500;&#9472;nvme0n1p1 SYSTEM        260M vfat   
&#9500;&#9472;nvme0n1p2                16M        
&#9500;&#9472;nvme0n1p3 OS          243.5G ntfs   
&#9500;&#9472;nvme0n1p4 New Volume    3.9G ntfs   
&#9500;&#9472;nvme0n1p5               228G ext4   
&#9500;&#9472;nvme0n1p6               1.1G ntfs   
&#9492;&#9472;nvme0n1p7 MYASUS        200M vfat   


```

```

root@ubuntu:/home/ubuntu# mount /dev/nvme0n1p6 /mnt
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
root@ubuntu:/home/ubuntu# mount --make-private --rbind /dev  /mnt/dev
mount: /mnt/dev: mount point does not exist.
root@ubuntu:/home/ubuntu# mount --make-private --rbind /proc /mnt/proc
mount: /mnt/proc: mount point does not exist.
root@ubuntu:/home/ubuntu# mount --make-private --rbind /sys  /mnt/sys
mount: /mnt/sys: mount point does not exist.
root@ubuntu:/home/ubuntu# mount --make-private --rbind /run  /mnt/run
mount: /mnt/run: mount point does not exist.
root@ubuntu:/home/ubuntu# chroot /mnt /usr/bin/env bash --login
chroot: failed to run command &#8216;/usr/bin/env&#8217;: No such file or directory
root@ubuntu:/home/ubuntu# ls -lah /usr/bin/python*
lrwxrwxrwx 1 root root   10 Mar 25  2022 /usr/bin/python3 -> python3.10
-rwxr-xr-x 1 root root 5.7M Jun 29  2022 /usr/bin/python3.10
-rwxr-xr-x 1 root root  960 Dec 23  2020 /usr/bin/python3-futurize
-rwxr-xr-x 1 root root  964 Dec 23  2020 /usr/bin/python3-pasteurize
root@ubuntu:/home/ubuntu# 


```

```

oot@ubuntu:/home/ubuntu# mount /dev/nvme0n1p6 /mnt
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

```

it looks like nvme0n1p6 partition got changed, and it is not a root partition anymore
can you explain the point of a mount?

---

### Post by oldfred on 2023-11-01
Did you renumber partitions?
Before you showed p6 as ext4 which then is / (root) partition as only ext4 partition.
But newest post shows p5 as ext4?

Your NTFS partition must be hibernated which Windows fast startup does.

You have to mount a partition to use it. Typically gui apps automount a partition with default settings.

---

### Post by d3vestator on 2023-11-01
ok, i did not renumber the partitions, not even sure how
what do you mean by NFTS parition hibernated. for which partitions because p5 was never a NFTS but a VFAT. p3 and p4 were the only NFTS

---

### Post by oldfred on 2023-11-01
Partitions do not renumber themselves. Drive order can change, but not partitions.
There are commands to renumber partitions, but those often cause major issues.

Your post #3 shows

```
|_nvme0n1p4   1.1G ntfs                                               
|_nvme0n1p5   200M vfat     MYASUS                                    
|_nvme0n1[COLOR=#ff0000]p6[/COLOR]   228G [COLOR=#ff0000]ext4[/COLOR]            /             
```

Post #8 shows this:

```
&#9500;&#9472;nvme0n1p4 New Volume    3.9G ntfs   
&#9500;&#9472;nvme0n1[COLOR=#ff0000]p5 [/COLOR]              228G [COLOR=#ff0000]ext4[/COLOR]   
&#9500;&#9472;nvme0n1p6               1.1G ntfs   
&#9492;&#9472;nvme0n1p7 MYASUS        200M vfat
```

Wehn you tried to mount the NTFS, it showed error.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)

---

### Post by yancek on 2023-11-01
Your partitions are changing and as pointed out above, they don't change themselves so something else is going on.  Your first 2 partitions didn't change and the windows OS partition only shows a change in size from  247.4G to 243.5G.  Partition 4 also changed but only the size, from 1.1 to 3.9GB.  What was partition 5 is now partition 7 and as pointed out above, what was the / ext4 filesystem partition previously (partition 6) is now partition 5 and partition 6 is now 1.1GB rather than the original 228GB?  Your original vfat partition 5, a 200MB vfat partition is now partition 7.  Partition devices have changed and a partition has been added.  These things don't change themselves so if you haven't done this intentionally or accidentally, that indicates serious problems.  I have no idea how that would happen.

---

### Post by d3vestator on 2023-11-01
after just getting my wifi working in the previous thread, i didnt touch anhything else, execept for when i decided to install Python which turned to be a old version. besides that i no clue. unless something got changed when i was doing the other fixes with my drivers, but that was before i had this issue thing that cause some serious issue was installing which turned out by e


i assume the probability of reinstalling ubuntu is very high?

---

### Post by oldfred on 2023-11-01
Pretty much the rule is to re-install & restore from backups if it takes more than an hour to repair.

You should have good backups? Many, many threads on backup & what you need to have.

---

### Post by MAFoElffen on 2023-11-01
No matters. 

You still should be booted in that terminal session right? Because I asked you to (this time) not to exit, backpout, reboot or shutdown this system right?

So this point, type "exit<Enter>" intl the terminal session closes... Then go back to Post #2 and reread the instructions there. I changed on command and added another.

Remember what I told you? Do each line, one by one, and pay attention to your output from each of those commands. If there is any error or you have a question, immediately stop. Do not pass go, do not do anything else, before posting back here to let us know.

Why? Because each command builds upon the next. If one does not work, then later commands will not work. Then you are just wasting your time, because nothig esle will work until that all can be done, successfully, in order. Understood?

Now try them again, and tell us how goes.

---

### Post by d3vestator on 2023-11-02
Just to let you know I am going to have to shut off my ubuntu os. I need access to my windows os for school. So either I keep redoing the commands or we wait till Friday where I can leave it running

---

### Post by MAFoElffen on 2023-11-02
Did you do the commands, if you had, and got in, 

...from getting that far successfully, that output from the last command would be 2-3 more commands from getting you fixed and going again.

See how that might be important to you and in your own best interest?

from there we would then do these...
```

ls -lah /usr/bin/python*

```
That was the output we are wanting to see if it needs redone to point to what it should be, Which is this command:
```

ln -sf python3.10 /usr/bin/python3

```
Doing this to check to see if it is now fixed, checking the output of
```

python3 --version

```
Which should now say: "3.10.12"

Then to back off your changes, check to make things work again and cover out tracks
```

apt update
ppa-purge ppa:deadsnakes/ppa
apt install --reinstall python3

```
Then to cover what anything else might have been changed with that
```

grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy
update-grub
update-initramfs -c -k all

```
That should cover everything at the point. So we back out of the chroot and clean up
```

exit
umount /mnt
reboot

```

---

### Post by yancek on 2023-11-02
The error you reported in Post 8 and referenced above by oldfred means you were using windows and rebooted into Ubuntu and tried to access a windows partition from Ubuntu.  In order to do that, you need hibernation off which requires booting into windows and going into the power settings.  Thousands of sites explaining how to do this.  Mounting a filesystem which is hibernated from another OS has a high probability of data loss which is why it is not done.

Out of curiosity, have you tried making any changes in windows in regard to partitions?

---

### Post by MAFoElffen on 2023-11-02
@yancek -- it meant when it restarted the Live Environment, somehow it saw this hibernated ntfs partition as a different partition number than it was showing up at previously... Which now besides being in a different order, now mysteriously has 7 partitions, instead of 6... LOL

Yes, he needs to go into Windows and turn off "fastboot," and quit hibernating Windows when he is trying to do this. The Windows filesystem needs to be shutdown completely for OS_PROBER in update-grub to see his Windows to add it to the Boot menu properly... But it's not the partition we need to mount.

It really doesn't matter. He needs mount that 280GB partition with the ext4 filesystem. That is his root partition for Ubuntu. We are trying to hit a moving target there... LOL

I tell you what, do this as a replacement... That is all the commands, and adjusts for whatever is the current ext4 filesystem, directly by using the filesystem UUID for mounting the root partition he has.
```

sudo su
umount -a
TARGET=$(lsblk -e7 -o name,size,fstype,uuid | awk '/vfat/ {print "UUID="$4}')
mount -t ext4 $TARGET /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env bash --login
mount -a
ls -lah /usr/bin/python*
ln -sf python3.10 /usr/bin/python3
python3 --version
apt update
ppa-purge ppa:deadsnakes/ppa
apt install --reinstall python3
grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy
update-grub
update-initramfs -c -k all
exit
umount /mnt
reboot

```
I have tried to map this all out for you and make it as simple as can be, for the circumstances. I previously tried make this into something simpler for you, by turning that into a script for you... Then you had questions on what that script did, so I went back and explained what "each line" did for you... But installing and running that script was a challenge for you to do from a LiveUSB, so here we are...

I'm running out of ways to make this simpler or to explain it in different ways.

---

### Post by yancek on 2023-11-02
Drives being seen in a different order or with different names such as sda changing to sdb is not uncommon.  Having an internal drive showing as sda then booting a usb most often will show the usb as sda and the internal drive as sdb.  That's easily explained but changing of filesystems of a specific partition and the sizes of multiple partitions as is the case here is difficult to understand.

---

### Post by MAFoElffen on 2023-11-02
@et_all

Honestly, I don't know what is going on. I have seen drives change "device names" on reboot, that is why I usually use UUID's, /dev/disk/<something>-by/ or Label's, etc for permanent mounts.... 

But this is the very first time I have seen a partition table change names/numbers "within it", and the change the order they appear on their own. That seems to defy physics, as that relates to a block device and what is written to it. I mean, I'm talking about in over 35 years. Media is just a block deice with binary data written to it in a certain way. I've dealt with that with disk editors with Assembler. Dang. This has my mind blown with that. Data just doesn't change and move on it's own.

And what he did would have broke most everything with Python on his system, but not the underlying devices... IDK

What wouldn't change with that, is the filesystem & fstype within that partition and the filsytem's UUID. That does stay dependably static. 

Whatever is going, I'm actually glad that happened. It showed me this may be a "new" condition possibility, that I never knew was even possible in this Quantum reality. I do not know if I need to add that new possible condition to the scripts of the Ama-Gi project, and let Yannubuntu know we might need to add to the boot-repair, and boot-info code? In our reports, we assume that partition data on a disk is going to stay static between <re->boots.

Again... I still do not understand how that is or was possible for this OP. Partition tables are "not temporary". They are static data written to disk. This has caught my attention and interest to explore more.... After we get him fixed and going again. But...

The first priority is to get him going again. The next priority immediately after that is to _teach him how to do a backup on his system_!!! We need to be able to them him: "Restore your system to your last good backup where your system was still healthy."  

I told him late in his last thread, by the time he fixes his problems on this laptop, his education level on Linux along this path so far, is going to turn him into a Linux Expert. These are not issues that normal everyday users have to deal with, or touch. I am proud of him so far. He has the tenacity and perseverance so stick to and through things to the end.

---

### Post by d3vestator on 2023-11-02
```

root@ubuntu:/home/ubuntu# mount /dev/nvme0n1p5 /mnt
root@ubuntu:/home/ubuntu# mount --make-private --rbind /dev /mnt/dev
root@ubuntu:/home/ubuntu# mount --make-private --rbind /proc /mnt/proc
root@ubuntu:/home/ubuntu# mount --make-private --rbind /sys /mnt/sys
root@ubuntu:/home/ubuntu# chroot /mnt /usr/bin/env bash --login
root@ubuntu:/# mount -a
root@ubuntu:/# ls -lah /usr/bin/python*
lrwxrwxrwx 1 root root   10 Aug 18  2022 /usr/bin/python3 -> python3.10
-rwxr-xr-x 1 root root 5.7M Jun 11 00:26 /usr/bin/python3.10
-rwxr-xr-x 1 root root 5.0M Aug 25 08:20 /usr/bin/python3.8
-rwxr-xr-x 1 root root  960 Jan 25  2023 /usr/bin/python3-futurize
-rwxr-xr-x 1 root root  964 Jan 25  2023 /usr/bin/python3-pasteurize

root@ubuntu:/# lsblk -e7 -o name,label,size,fstype,mountpoint
NAME        LABEL   SIZE FSTYPE MOUNTPOINT
sda                 7.5G        
&#9492;&#9472;sda1              7.5G        
nvme0n1           476.9G        
&#9500;&#9472;nvme0n1p1         260M        
&#9500;&#9472;nvme0n1p2          16M        
&#9500;&#9472;nvme0n1p3       243.5G        
&#9500;&#9472;nvme0n1p4         3.9G        
&#9500;&#9472;nvme0n1p5         228G        /   **Is this the mnt, doesn't it usually say /mnt**
&#9500;&#9472;nvme0n1p6         1.1G        
&#9492;&#9472;nvme0n1p7         200M        
root@ubuntu:/# umount -a


```

i accidentally forgot one the commands when i typing them out. i forgot the mount --make-private --rbind /run /mnt/run. is this fine

---

### Post by MAFoElffen on 2023-11-02
At this point, type "exit", then do that mout of /mnt/run, then do the chroot and mount -a commands again to get back into the chroot.

The reason that is important to be there is that without that, resolvd will not work, and you will not have any working DNS to do anything with APT within the chroot.

Tell me when you have that redone and back into the chroot.

---

### Post by d3vestator on 2023-11-02
ok,

is it still possible that i couldve changed something within the partitions?.

---

### Post by MAFoElffen on 2023-11-02
IDK. To check that, from inside that chroot, do 
```

ls /

```
Then show this
```

python3 --version
apt update

```
If the Python version shows 3.10.12, go on.

If the update went without errors, just say so.

---

### Post by d3vestator on 2023-11-02
python 3.10.12
apt update dosent work

---

### Post by MAFoElffen on 2023-11-02
Your wif was connected before you chrooted in right?

Does either of these work?
```

ping -c 4 8.8.8.8
ping -c www.google.com

```
from the commandline inside the chroot?

---

### Post by d3vestator on 2023-11-02
both
i have a question does chroot allow you to change the root directory while its running

---

### Post by MAFoElffen on 2023-11-02
no... you would have to exit the chroot, unmount everthing, remount everything somewhere else, then chroot into that mountpoint...

Both of those work, but apt update does not? Please show me the errors of that.

---

### Post by d3vestator on 2023-11-02
```


oot@ubuntu:/# sudo apt update
Running in chroot, ignoring command 'start'
Hit:1 http://ca.archive.ubuntu.com/ubuntu jammy InRelease
Ign:2 http://security.ubuntu.com/ubuntu jammy-security InRelease
Err:1 http://ca.archive.ubuntu.com/ubuntu jammy InRelease       
  Couldn't create temporary file /tmp/apt.conf.sVVRUQ for passing config to apt-key
Ign:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease                                   
Err:4 http://security.ubuntu.com/ubuntu jammy-security Release                                      
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_jammy-security_Release - open (30: Read-only file system) [IP: 2620:2d:4002:1::101 80]
Ign:5 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease                                 
Err:6 http://ca.archive.ubuntu.com/ubuntu jammy-updates Release                                     
  Could not open file /var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_jammy-updates_Release - open (30: Read-only file system) [IP: 2620:2d:4002:1::103 80]
Err:7 http://ca.archive.ubuntu.com/ubuntu jammy-backports Release
  Could not open file /var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_jammy-backports_Release - open (30: Read-only file system) [IP: 91.189.91.83 80]
Hit:8 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu jammy InRelease
Err:8 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu jammy InRelease
  Couldn't create temporary file /tmp/apt.conf.u5nDpE for passing config to apt-key
Hit:9 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy InRelease
Err:9 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy InRelease
  Couldn't create temporary file /tmp/apt.conf.LlA4SU for passing config to apt-key
Hit:10 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu jammy InRelease
Err:10 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu jammy InRelease
  Couldn't create temporary file /tmp/apt.conf.LkxR2S for passing config to apt-key
Reading package lists... Done
W: chown to _apt:root of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (30: Read-only file system)
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (30: Read-only file system)
W: chown to _apt:root of directory /var/lib/apt/lists/auxfiles failed - SetupAPTPartialDirectory (30: Read-only file system)
W: chmod 0755 of directory /var/lib/apt/lists/auxfiles failed - SetupAPTPartialDirectory (30: Read-only file system)
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.4unT4R - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.7pBrGa - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.f1vxqV - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.K4Gb6t - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.ofSU74 - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.d9h3a8 - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.VDTBzy - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_jammy_InRelease - PrepareFiles (30: Read-only file system)
W: chown to _apt:root of file /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_jammy_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chmod 0600 of file /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_jammy_InRelease failed - Item::QueueURI (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_jammy-security_InRelease - PrepareFiles (30: Read-only file system)
W: chown to root:root of file /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_jammy_InRelease failed - 400::URIFailure (30: Read-only file system)
W: chmod 0644 of file /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_jammy_InRelease failed - 400::URIFailure (30: Read-only file system)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ca.archive.ubuntu.com/ubuntu jammy InRelease: Couldn't create temporary file /tmp/apt.conf.sVVRUQ for passing config to apt-key
W: Problem unlinking the file /var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_jammy-updates_InRelease - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_jammy-security_Release - PrepareFiles (30: Read-only file system)
E: The repository 'http://security.ubuntu.com/ubuntu jammy-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Problem unlinking the file /var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_jammy-backports_InRelease - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_jammy-updates_Release - PrepareFiles (30: Read-only file system)
E: The repository 'http://ca.archive.ubuntu.com/ubuntu jammy-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Problem unlinking the file /var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_jammy-backports_Release - PrepareFiles (30: Read-only file system)
E: The repository 'http://ca.archive.ubuntu.com/ubuntu jammy-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Problem unlinking the file /var/lib/apt/lists/partial/ppa.launchpadcontent.net_deadsnakes_ppa_ubuntu_dists_jammy_InRelease - PrepareFiles (30: Read-only file system)
W: chown to _apt:root of file /var/lib/apt/lists/ppa.launchpadcontent.net_deadsnakes_ppa_ubuntu_dists_jammy_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chmod 0600 of file /var/lib/apt/lists/ppa.launchpadcontent.net_deadsnakes_ppa_ubuntu_dists_jammy_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chown to root:root of file /var/lib/apt/lists/ppa.launchpadcontent.net_deadsnakes_ppa_ubuntu_dists_jammy_InRelease failed - 400::URIFailure (30: Read-only file system)
W: chmod 0644 of file /var/lib/apt/lists/ppa.launchpadcontent.net_deadsnakes_ppa_ubuntu_dists_jammy_InRelease failed - 400::URIFailure (30: Read-only file system)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu jammy InRelease: Couldn't create temporary file /tmp/apt.conf.u5nDpE for passing config to apt-key
W: Problem unlinking the file /var/lib/apt/lists/partial/ppa.launchpadcontent.net_mafoelffen_system-info_ubuntu_dists_jammy_InRelease - PrepareFiles (30: Read-only file system)
W: chown to _apt:root of file /var/lib/apt/lists/ppa.launchpadcontent.net_mafoelffen_system-info_ubuntu_dists_jammy_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chmod 0600 of file /var/lib/apt/lists/ppa.launchpadcontent.net_mafoelffen_system-info_ubuntu_dists_jammy_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chown to root:root of file /var/lib/apt/lists/ppa.launchpadcontent.net_mafoelffen_system-info_ubuntu_dists_jammy_InRelease failed - 400::URIFailure (30: Read-only file system)
W: chmod 0644 of file /var/lib/apt/lists/ppa.launchpadcontent.net_mafoelffen_system-info_ubuntu_dists_jammy_InRelease failed - 400::URIFailure (30: Read-only file system)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy InRelease: Couldn't create temporary file /tmp/apt.conf.LlA4SU for passing config to apt-key
W: Problem unlinking the file /var/lib/apt/lists/partial/ppa.launchpadcontent.net_yannubuntu_boot-repair_ubuntu_dists_jammy_InRelease - PrepareFiles (30: Read-only file system)
W: chown to _apt:root of file /var/lib/apt/lists/ppa.launchpadcontent.net_yannubuntu_boot-repair_ubuntu_dists_jammy_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chmod 0600 of file /var/lib/apt/lists/ppa.launchpadcontent.net_yannubuntu_boot-repair_ubuntu_dists_jammy_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chown to root:root of file /var/lib/apt/lists/ppa.launchpadcontent.net_yannubuntu_boot-repair_ubuntu_dists_jammy_InRelease failed - 400::URIFailure (30: Read-only file system)
W: chmod 0644 of file /var/lib/apt/lists/ppa.launchpadcontent.net_yannubuntu_boot-repair_ubuntu_dists_jammy_InRelease failed - 400::URIFailure (30: Read-only file system)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu jammy InRelease: Couldn't create temporary file /tmp/apt.conf.LkxR2S for passing config to apt-key
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (30: Read-only file system)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (30: Read-only file system)

```

---

### Post by MAFoElffen on 2023-11-02
no... you would have to exit the chroot, unmount everthing, remount everything somewhere else, then chroot into that mountpoint...

Both of those work, but apt update does not? Please show me the errors of that.

There is either something wrong with the filesystem (suspected) or the storage container is full. With what you have been doing, I am suspecting maybe the first.
```

exit
fsck /dev/nvme0n1p5
lsblk -e7 -o name, size,fstype,fsuse%,mountpoint

```

---

### Post by MAFoElffen on 2023-11-03
Did fsck find any errors in the filesystem? Wondering if you are working on this today after you got back home...

---

### Post by d3vestator on 2023-11-03
am i suppose exit completely from the chroot? to perform the fsck and lsblk?

```

root@ubuntu:/home/ubuntu# fsck /dev/nvme0n1p5
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
/dev/nvme0n1p5 is mounted.
e2fsck: Cannot continue, aborting.


root@ubuntu:/home/ubuntu# lsblk -e7 -o name, size,fstype,fsuse%,mountpoint
lsblk:unkown column: name

```

if i exit the chroot and fsck /dev/nvme0n1p5
```

fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
/dev/nvme0n1p5 is mounted.



WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

```
am i saying yes

---

### Post by MAFoElffen on 2023-11-03
No!
```

sudo umount /mnt 

```
Then do it...

---

### Post by d3vestator on 2023-11-03
```

root@ubuntu:/home/ubuntu# umount /mnt
umount: /mnt: target is busy.

ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: target is busy.


```

---

### Post by MAFoElffen on 2023-11-03
Then reboot the LiveUSB... use "try"... The from the terminal, do
```

sudo fsck /dev/nvme0n1p5

```
Before you do anything else.

---

### Post by d3vestator on 2023-11-03
```

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p5
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
/dev/nvme0n1p5: clean, 280389/14942208 files, 6198168/59756800 blocks


```

---

### Post by oldfred on 2023-11-03
We all make typos, but computers do not like them.
When you have an issue, double check what you typed.

[COLOR=#ff0000]nmve[/COLOR]0n1p5 is a NVMe drive

---

### Post by MAFoElffen on 2023-11-03
You never did post the results of this so we could see how full it was(?)
```

lsblk -e7 -o name,size,fstype,fsuse%,mountpoint

```
After posting that, then... Okay, try to make all the mounts and chroot into it again...

---

### Post by d3vestator on 2023-11-03
im getting unkown column:name

---

### Post by MAFoElffen on 2023-11-03
Sorry. Had an extra space there. Now look at it.

---

### Post by d3vestator on 2023-11-04
```

root@ubuntu:/home/ubuntu# lsblk -e7 -o name,size,fstype,fsuse%,mountpoint
NAME          SIZE FSTYPE FSUSE% MOUNTPOINT
sda           7.5G               
&#9492;&#9472;sda1        7.5G vfat      48% /cdrom
nvme0n1     476.9G               
&#9500;&#9472;nvme0n1p1   260M vfat          
&#9500;&#9472;nvme0n1p2    16M               
&#9500;&#9472;nvme0n1p3 243.5G ntfs          
&#9500;&#9472;nvme0n1p4   3.9G ntfs          
&#9500;&#9472;nvme0n1p5   228G ext4          
&#9500;&#9472;nvme0n1p6   1.1G ntfs          
&#9492;&#9472;nvme0n1p7   200M vfat          
root@ubuntu:/home/ubuntu# 

```

ill start again tmrw

---

### Post by MAFoElffen on 2023-11-04
Okay. Good night.

---

### Post by d3vestator on 2023-11-04
i chrooted back into my system

---

### Post by MAFoElffen on 2023-11-04
Post the output of this within CODE Tgas:
```

df -h
ls -lah /

```

---

### Post by d3vestator on 2023-11-04
```

root@ubuntu:/# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p5  224G   20G  193G   9% /
tmpfs           7.6G     0  7.6G   0% /dev/shm
tmpfs           1.6G  2.1M  1.6G   1% /run
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           1.6G  164K  1.6G   1% /run/user/999
/dev/nvme0n1p1  256M   52M  205M  21% /boot/efi

root@ubuntu:/# ls -lah /
total 2.1G
drwxr-xr-x  20 root root 4.0K Feb 26  2023 .
drwxr-xr-x  20 root root 4.0K Feb 26  2023 ..
lrwxrwxrwx   1 root root    7 Feb 26  2023 bin -> usr/bin
drwxr-xr-x   4 root root 4.0K Oct 30 22:55 boot
drwxr-xr-x   2 root root 4.0K Feb 26  2023 cdrom
drwxr-xr-x  20 root root 4.7K Nov  4 11:12 dev
drwxr-xr-x 139 root root  12K Oct 30 23:19 etc
drwxr-xr-x   5 root root 4.0K Jul 22 15:35 home
lrwxrwxrwx   1 root root    7 Feb 26  2023 lib -> usr/lib
lrwxrwxrwx   1 root root    9 Feb 26  2023 lib32 -> usr/lib32
lrwxrwxrwx   1 root root    9 Feb 26  2023 lib64 -> usr/lib64
lrwxrwxrwx   1 root root   10 Feb 26  2023 libx32 -> usr/libx32
drwx------   2 root root  16K Feb 26  2023 lost+found
drwxr-xr-x   3 root root 4.0K Feb 26  2023 media
drwxr-xr-x   4 root root 4.0K Sep  3 18:27 mnt
drwxr-xr-x   2 root root 4.0K Aug  9  2022 opt
dr-xr-xr-x 484 root root    0 Nov  4 11:11 proc
drwx------   7 root root 4.0K Nov  4 14:44 root
drwxr-xr-x  36 root root 1.1K Nov  4 14:41 run
lrwxrwxrwx   1 root root    8 Feb 26  2023 sbin -> usr/sbin
drwxr-xr-x  16 root root 4.0K Mar 28  2023 snap
drwxr-xr-x   2 root root 4.0K Aug  9  2022 srv
-rw-------   1 root root 2.0G Mar 20  2023 swapfile
dr-xr-xr-x  13 root root    0 Nov  4 11:11 sys
drwxrwxrwt  11 root root 4.0K Oct 30 23:21 tmp
drwxr-xr-x  14 root root 4.0K Aug  9  2022 usr
drwxr-xr-x  14 root root 4.0K Aug  9  2022 var


```

---

### Post by #&amp;thj^% on 2023-11-04
Just driving by, but there is no "core" shown there.
```
ls -lah / | grep core
-rw-------   1 root root 239M Nov  4 11:13 core
```

---

### Post by d3vestator on 2023-11-04
there isnt one

---

### Post by MAFoElffen on 2023-11-04
> **1fallen said:**
> Just driving by, but there is no "core" shown there.
```
ls -lah / | grep core
-rw-------   1 root root 239M Nov  4 11:13 core
```
I don't see that as a problem...
```

mafoelffen@noble-s03:~$ ls -lah / | grep core
mafoelffen@noble-s03:~$ exit
logout
Connection to 192.168.122.250 closed.
mafoelffen@Mikes-B460M:~$ ls -lah | grep core
mafoelffen@Mikes-B460M:~$ exit
logout
Connection to 10.0.0.3 closed.
mafoelffen@Mikes-ThinkPad-T520:~/Downloads$ ls -lah | grep core
mafoelffen@Mikes-ThinkPad-T520:~/Downloads$

```
Not on these 3 working machines either...

@D3vastator, can you successfully do this from within the chroot?
```

apt update

```

---

### Post by d3vestator on 2023-11-04
```

root@ubuntu:/# apt update
Running in chroot, ignoring command 'start'
Hit:1 http://ca.archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]                                               
Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                                                
Get:4 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease [109 kB]                                                     
Get:5 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [524 kB]                                              
Get:6 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [1,149 kB]                                         
Hit:7 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu jammy InRelease                                     
Get:8 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [245 kB]             
Get:9 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [101 kB]                                                                   
Get:10 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [16.1 kB]                                                                   
Get:11 http://ca.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [1,105 kB]                                                                   
Get:12 http://ca.archive.ubuntu.com/ubuntu jammy-updates/restricted i386 Packages [32.8 kB]                                                               
Get:13 http://ca.archive.ubuntu.com/ubuntu jammy-updates/restricted Translation-en [179 kB]                                                               
Get:14 http://ca.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 c-n-f Metadata [520 B]                                                               
Get:15 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [661 kB]                                                                     
Get:16 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [999 kB]                                                               
Get:17 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [219 kB]                                                                     
Get:18 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [305 kB]                                                                    
Get:19 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata [22.1 kB]                                                                     
Get:20 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [41.6 kB]                                                                         
Get:21 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]                                                                    
Get:22 http://ca.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 c-n-f Metadata [472 B]                               
Get:23 http://ca.archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata [4,932 B]                                                                     
Get:24 http://ca.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [18.8 kB]                                                                        
Get:25 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages [360 kB]                                                                                        
Hit:26 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy InRelease                                           
Get:27 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [940 kB]                          
Get:28 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [186 kB]           
Get:29 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [43.0 kB]                                 
Get:30 http://security.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [11.4 kB]
Get:31 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages [1,085 kB]
Get:32 http://security.ubuntu.com/ubuntu jammy-security/restricted i386 Packages [32.4 kB]
Get:33 http://security.ubuntu.com/ubuntu jammy-security/restricted Translation-en [176 kB]
Hit:34 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu jammy InRelease 
Get:35 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 c-n-f Metadata [520 B]
Get:36 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages [797 kB]
Get:37 http://security.ubuntu.com/ubuntu jammy-security/universe i386 Packages [563 kB]
Get:38 http://security.ubuntu.com/ubuntu jammy-security/universe Translation-en [146 kB]
Get:39 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [55.1 kB]
Get:40 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 c-n-f Metadata [16.8 kB]
Get:41 http://security.ubuntu.com/ubuntu jammy-security/multiverse amd64 Packages [36.5 kB]
Get:42 http://security.ubuntu.com/ubuntu jammy-security/multiverse amd64 c-n-f Metadata [260 B]
Fetched 10.4 MB in 4s (2,663 kB/s)                                       
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done

```
look like it worked

---

### Post by MAFoElffen on 2023-11-04
Wahoo!!! While that is still working, please do:
```

mount -a
apt install -y ppa-purge 
ppa-purge ppa:deadsnakes/ppa
apt install --reinstall -y python3
grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy
update-grub
update-initramfs -c -k all
exit
umount /mnt
reboot

```

---

### Post by d3vestator on 2023-11-05
```

root@ubuntu:/# apt ppa-purge ppa:deadsnakes/ppa
E: Invalid operation ppa-purge

```
I assume thats fine?

---

### Post by MAFoElffen on 2023-11-05
Dang... Typo. Should have been
```

ppa-purge ppa:deadsnakes/ppa

```

---

### Post by oldfred on 2023-11-05
Pretty much the rule is for all of us, is if it takes more than an hour to fix, better to just reinstall & restore from backups.
Ubuntu is not like Windows that takes hours to install & update.

My first backup was a simple rsync to another drive's partition. Now I understand that really is not a backup procedure as it does not recover deleted or very old files, but a lot better than nothing. 
I backup /home, my data which is not in /home, and a list of installed applications to make it easy to reinstall them. I do change system wide settings in a few files like grub, so copy those into /home so also backed up. 

Some like full image backups. But they take a lot of space and users often do not regularly make them. An image is obsolete as soon as you have changed/used system.

discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2465713](https://ubuntuforums.org/showthread.php?t=2465713)
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)[[://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224|&p=13677224#post13677224]]
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) & 
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)

If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)

An old post by oldfred:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
List apps:
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)

Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by d3vestator on 2023-11-05
i got back into my system. i had some ipgu pram errors, however i remebered that it wasnt a big deal becasue i use the nvidia gpu
regarding backups, is it fine if i do use the default backup GUI that's already on ubuntu?

before i close the #4 thread, thank you @MAfoElffen especially and others for taking time and patience to help me get my system up and functioning again. It was jaunt, but we did it.

---

### Post by MAFoElffen on 2023-11-05
Now that you are back up... To close out your other thread ([https://ubuntuforums.org/showthread.php?t=2490858&page=2&highlight=nvidia+driver](https://ubuntuforums.org/showthread.php?t=2490858&page=2&highlight=nvidia+driver)), do
```

sudo apt remove nvidia*
sudo apt install nvidid-driver-470

```
Then mark this as "Solved"...

Now for you to leanrn about doing a backup o your system, so you can always restore back to this point... Where it is working.

---

