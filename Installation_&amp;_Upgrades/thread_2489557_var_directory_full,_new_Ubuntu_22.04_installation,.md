---
title: "var directory full, new Ubuntu 22.04 installation, no further apps permitted"
date: 2023-08-02
forum: Installation &amp; Upgrades
---

### Post by julius-nepos on 2023-08-02
[FONT=apple-system, BlinkMacSystemFont, Segoe UI Adjusted, Segoe UI, Liberation Sans, sans-serif]InstalledUbuntu 22.04 onto a system with a 512 GB flash hard drive + a 6 TB HDD.Then upgraded to xUbuntu.

[/FONT]
[FONT=apple-system, BlinkMacSystemFont, Segoe UI Adjusted, Segoe UI, Liberation Sans, sans-serif]Unableto install Google Chrome but was able to install the xUbuntu-desktop(XFCE).  single boot, everything should be clean partitions.

[/FONT]
[FONT=apple-system, BlinkMacSystemFont, Segoe UI Adjusted, Segoe UI, Liberation Sans, sans-serif]Iget the following Disk Usage picture {see at end}. It appears that the vardirectory has filled up and I am unable to install any apps. 

Icreated the following partitions when I installed Ubuntu:
partitions on 500GB (.5TB) hard drive
efi - UEFIboot loader, 1 GB primary partition 
/ - Linux system ext4 100 GB
/home - data 273.1 GB 
swap 128 GB[/FONT]
[FONT=apple-system, BlinkMacSystemFont, Segoe UI Adjusted, Segoe UI, Liberation Sans, sans-serif]
Ididn't write down the mount point I created for the 6,000 GB harddrive but it should be findable somewhere.[/FONT]

As mentioned it appears that I have NO room to install any apps despite this being a new clean system with 6.5 TB available.

---

### Post by TheFu on 2023-08-02
Less images.
More data.

Please run and post, as text, these commands:
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
```

No images, please.  We can't copy/paste slices of images like we can with text.

---

### Post by ActionParsnip on 2023-08-03
Also, what is the output of:
```

du -sh /var/*

```

---

### Post by julius-nepos on 2023-08-03
Hi & thanks for helping.  I was able to find that Chrome is apparently installed [it has my bookmarks].
Output is as follows:

sudo lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint

```
NAME        TYPE FSTYPE   SIZE FSAVAIL FSUSE% LABEL MOUNTPOINT
sda         disk          5.5T                      
&#9492;&#9472;sda1      part ext4     5.5T    5.1T     0%       /home
sr0         rom          1024M                      
nvme0n1     disk        476.9G                      
&#9500;&#9472;nvme0n1p1 part vfat     960M  903.9M     6%       /boot/efi
&#9500;&#9472;nvme0n1p2 part ext4   100.6G   89.6G     4%       /
&#9500;&#9472;nvme0n1p3 part swap   121.1G                      [SWAP]
&#9492;&#9472;nvme0n1p4 part ext4   254.3G  228.5G     3%       /usr

```


john@Caligula:~$ df -hT -x squashfs -x tmpfs -x devtmpfs

```
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p2 ext4   99G  3.8G   90G   5% /
/dev/nvme0n1p4 ext4  250G  8.1G  229G   4% /usr
/dev/nvme0n1p1 vfat  959M   55M  904M   6% /boot/efi
/dev/sda1      ext4  5.5T  9.5G  5.2T   1% /home

```

john@Caligula:~$ sudo du -sh /var/*

```
3.0M    /var/backups
597M    /var/cache
5.5M    /var/crash
2.5G    /var/lib
4.0K    /var/local
0    /var/lock
129M    /var/log
4.0K    /var/mail
4.0K    /var/metrics
4.0K    /var/opt
0    /var/run
3.8M    /var/snap
52K    /var/spool
84K    /var/tmp
```
john@Caligula:~$

---

### Post by julius-nepos on 2023-08-03
Hi,
Thanks so much for replying.  All the outputs are listed together.

---

### Post by TheFu on 2023-08-03
Please edit the post above to wrap the terminal output in forum code-tags.  The output depends on the columns being retained. Too hard to read otherwise. Don't edit anything, just wrap it with the correct tags ... like you would for BOLD or Italics.  The advanced editor has a button (#) for this.

My signature below has a link for BBcode stuff, including how to use 'code-tags', if you need more detailed instructions.

Since /var isn't in a separate file system, we need to look at how full / is.  Can't tell without the columns lining up, but it looks like / has about 90G free.

"Directories" don't fill up, unless you've enabled disk quotas.  That's not something accidentally enabled.  File systems can fill up, but I don't see that. Actually, I think your / is much too large. 40G is all anyone should need for /, especially if they put /home/ onto a different file system, which you've done.

---

### Post by ActionParsnip on 2023-08-03
Looks fine.... What makes you think you have low space?

---

### Post by TheFu on 2023-08-03
Since you've made a separate /usr, you've basically dropped the requirement for / to 20G.  Back in the days when storage was expensive and we used NFS whenever possible across machines, having /usr separate from / made sense.  Not so much these days.

BTW, if you want to extend the life of your SSD, best to leave at least 20% unused.  I've posted my OS layout here a number of times. Bares repeating, 
```
NAME                             TYPE FSTYPE        SIZE FSAVAIL FSUSE% LABEL       MOUNTPOINT
nvme0n1                          disk             931.5G                            
&#9500;&#9472;nvme0n1p1                      part ext2            1M                            
&#9500;&#9472;nvme0n1p2                      part vfat           50M   43.9M    12%             /boot/efi
&#9500;&#9472;nvme0n1p3                      part ext4          700M    343M    42%             /boot
&#9492;&#9472;nvme0n1p4                      part LVM2_member 930.8G                            
  &#9500;&#9472;vg01-swap01                  lvm  swap          4.1G                            [SWAP]
  &#9500;&#9472;vg01-root01                  lvm  ext4           35G   25.8G    19%             /
  &#9500;&#9472;vg01-var01                   lvm  ext4           20G   16.1G    12%             /var
  &#9500;&#9472;vg01-tmp01                   lvm  ext4            4G    3.6G     1% tmp01       /tmp
  &#9500;&#9472;vg01-home01                  lvm  ext4           10G    3.9G    55% home01      /home
  &#9500;&#9472;vg01-libvirt--01             lvm  ext4          137G    2.8G    98% libvirt--01 /var/lib/libvirt
  &#9492;&#9472;vg01-lxd--containers--01     lvm                 30G
```
See how much easier it is to read with 'code-tags'?
I happen to have a 1TB SSD, but as you can see, I'm actually using less than 200G, so this setup would work for your 500GB SSD too.  My /var/ really should be smaller, I made it larger in expectation for bloated snap packages.  The last two items are for virtual machines and lxd containers. If you don't use those, then you don't need them.

---

### Post by julius-nepos on 2023-08-03
Thanks,
I suspected that I had run out of room as I saw my graphical disk-useage report showing the /var at all red.  Also I thought I was having problems installing Chrome and I was unable to see any control panel for gnome.
I tried re-installing the gnome control panel but couldn't seem to find it.  I've used xUbuntu on another computer with 18.04 , abt 2 years ago so went back to it now.

There were a bunch of YouTube guides on Linux partitioning but NONE that I could find addressed the issue of a smaller flash boot drive with a large HDD for data.  

Thanks for your partitioning layout.  I bought a used HP-2145 {Windows-11, floortop server, 64G Ram} which only had a 500 G flash drive and bought a 6 T HDD for it.
I did Not specifically create the /usr directory, it seems to have created on it's own.   I will need a LOT of space under   /home

---

### Post by TheFu on 2023-08-03
I've never seen /usr split to a separate file system under any Linux installer. Doing that is definitely a manual thing.

It would be smart to have HOME just used for settings and active document, but not for large files/media.  Keep that elsewhere.  It is about doing backups.
BTW, if the larger HDD is internal, it would be smart to place the SWAP onto it, not on the SSD.  This way, you'll "feel" the system getting slow when swap is being used. That's a good thing. If you feel it, then you can take action, usually by closing a bloated browser.

If you have any specific layout questions, ask.  Some background for the purpose of each file system would be helpful, for the non-OS stuff.

You didn't mention backup storage. Hope you have that covered.

---

### Post by julius-nepos on 2023-08-03
depulicate post, will update it.

---

### Post by TheFu on 2023-08-04
If this is solved, please use the "thread tools" button to do that.  It will help the community save time.

---

### Post by julius-nepos on 2023-08-04
I'm not sure why /usr was created.  Can I merge it with either /home or with / ?   Of course /home is on the slower HDD so merging it with that would span two physical drives.
Yes both drives are internal.

I'll definitely feel when SWAP is being used, even on the flash drive.  The computer is to be used for engineering calculations (CFD).

I may have to get an external drive for backup storage, I used to use DVD's but they're getting very small these days.

---

### Post by TheFu on 2023-08-04
> **julius-nepos said:**
> I'm not sure why /usr was created.  Can I merge it with either /home or with / ?   
You had to have done something.  No need to merge. Just boot off alternate media, mount both file systems, then move the entire /usr/  into / , and remove the /usr mount from the /etc/fstab.  Comment it out, until you are positive you did what you wanted.  Your / is huge - 3x large even with /usr directory moved into it.  BTW, use sudo/root to perform the move. This will retain the owner/group/permissions.  It is just 1 command.  Probably something like:
```
sudo mv /mnt/old-usr/*  /mnt/new-slash/
```
That command assumes you mounted the /usr in the Try Ubuntu environment to  /mnt/old-usr and the new / to   /mnt/new-slash/.
If you want to be really careful, use 
```
sudo rsync -av --progress  /mnt/old-usr/  /mnt/new-slash/
```
Same caveats about the mount locations hold.

> **julius-nepos said:**
> Of course /home is on the slower HDD so merging it with that would span two physical drives.
Yes both drives are internal.
You don't need to move **everything** in /home to the SSD.  Just everything that isn't huge.  Keep huge files on the HDD.  Create symbolic links from the SSD $HOME/something to /media/HDD/something to make accessing it seamless.  This is a very common practice.  For example, let's say you have /home/john/Music  with 5TB of files. Again, from the Try Ubuntu flash drive boot environment, mount the old home somewhere ... say /mnt/old-home.   Then move the directories with all the huge files up above the /home/{username}/ directory.  Now the /home/{username}/ just contains settings, caches, and smaller files.  Be careful to set the permissions on the new, huge, file directories to be as restrictive as you need. You'll have something like this.
```
/mnt/old-home/home/john
/mnt/old-home/home/Music
/mnt/old-home/home/Videos
```
Now mount the SSD / directory, create /home ... so probably something like  /mnt/new-slash/home/. Then you can move /mnt/old-home/home/john --->  /mnt/new-slash/home/.
Fix the /etc/fstab so that /home mounts to /media/HDD and reboot.

After the reboot, you should have these on the SSD:
/
/home/
/usr/

And on the HDD, you'll have 
/media/HDD for the 6TB file system with  /media/HDD/Music and /media/HDD/Videos.  The location changed because we moved the mount point.
Lastly, create symbolic links from inside your $HOME to /media/HDD/Music and /media/HDD/Videos.  

Be certain you setup your backups to work for the different file systems.  File systems are a natural place to split backups.

> **julius-nepos said:**
> I'll definitely feel when SWAP is being used, even on the flash drive.  The computer is to be used for engineering calculations (CFD).


I studied CFD in grade school. Never used it in the real world, though I know my current desktop is about the same performance as the Cray Y-MP my University had at the time.  It was one of the fastest computers in the world back then. At one point it was in the top 10.  RAM is cheap, but fine CFD grids can bring any computer to its knees.  I did with both a Cyber/CDC and with the Cray.  Got into trouble for eating all the "fake" money for the rest of the semester in the CFD class.  My grids were a little too fine. Something that ran all weekend and never finished on the CDC, ran for 20 minutes on the Cray and provided expected outputs.  Back then, we were doing tiny models compared to what they do today.

My advice about swap is - don't use a swap file. Use a swap partition/LV.  You'll probably need to test to figure the needed size.  Watch memory use with **free -hm** and be ready to kill the CFD model when it gets close to filling all swap plus RAM minus 1GB.  Then I'd probably double the swap.  You'll want to leave room on the HDD for 127GB of swap. Plan accordingly with your partitioning. This is were LVM really shines. Going larger is trivial, provided you didn't already allocate all the VG storage. But going smaller is a pain.  My disk layout above shows how I allocate just what is needed AT-THE-TIME and no more.  Adding more space to an ext4 LV is 5 seconds, zero downtime. Start small. Add only when needed.

> **julius-nepos said:**
> 
I may have to get an external drive for backup storage, I used to use DVD's but they're getting very small these days.
I switched from DVD storage to cheap HDDs for backups around 2008 when the hassle of using optical storage was becoming too great.  Considering that a cheap DC 4TB HDD can be picked up for $45, there's not much need.  These come with a 5 yr warranty, since they are made for data center use. Usually, they will come with 4-5 yrs of DC use already - they are just broken in by that point.  I stopped buying HDDs with less than 5 yr warranties a few years ago.  I did the math vs hassle.  I'd had a number of 3yr warranty drives fail between 3-5 yrs, but I've never, ever, had a 5yr warranty disk fail.  I have some with 13 yrs of 24/7 spinning now. The SMART data is just starting to show stats for concern.  I'm moving all the data off them onto a new 8TB 5 yr warranty HDD.  I don't need to change my backup storage, since everything was already being backed up.  Daily, automatic, versioned, backups.  "Pulled" are better than pushed.  It will change your life and you'll sleep better.

Had a major problem with an old system a few weeks ago after a lightning strike. Pushed a UPS to failure and 3 of 4 drives in the external array seem to have issues. Could be with the array circuits or the drive or the disk controller - I don't know.  The lightning strike killed the GPU - which was very old and already dying. I swapped in a spare 1030 GT, which seemed to fix that issue.  Anyway, there were some other drives connected to the system and all the data from them has been moved to the new HDD already. I just need to get 2TB from the external array moved.

Just remember this about Linux storage.  If the directories and files "appear" to be where they are expected with the owner, group, permissions, ACLs, and xattrs that are expected, that is sufficient.  We can't move /var anywhere, but we can move all the files elsewhere and mount a new file system with those files to /var.  The OS doesn't care.  

When it comes to data files, we can put them anywhere we like, subject to permissions needs.  In general, I try to keep my HOME less than 15GB and put large files on a different file system, mounted somewhere else.  For example:
```
Filesystem                                       Type  Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_d0wbmk                         zfs    24G  7.0G   17G  30% /
bpool/BOOT/ubuntu_d0wbmk                         zfs   1.8G  401M  1.4G  23% /boot
/dev/vda2                                        vfat  512M   17M  496M   4% /boot/efi
rpool/USERDATA/tf_5njgy6                         zfs    27G  9.6G   17G  37% /home/tf
rpool/USERDATA/root_5njgy6                       zfs    17G  384K   17G   1% /root
rpool/ROOT/ubuntu_d0wbmk/srv                     zfs    17G  128K   17G   1% /srv
rpool/ROOT/ubuntu_d0wbmk/var/lib                 zfs    17G   27M   17G   1% /var/lib
istar:/d/D1                                      nfs4  3.5T  3.5T   41G  99% /d/D1
istar:/d/D2                                      nfs4  3.6T  3.5T  141G  97% /d/D2
istar:/d/D3                                      nfs4  3.6T  3.6T   15G 100% /d/D3
istar:/d/D6                                      nfs4  3.6T  2.0T  1.5T  57% /d/D6
istar:/d/D7                                      nfs4  3.6T  451G  3.0T  13% /d/D7
```
Most storage for that system is on the network, not local.  Sorry for showing ZFS. That's a different type of file system and I'm just playing with it on the OS.  Most of my systems use ext4 managed via LVM2.  LVM is an enterprise volume manager to allow tremendous flexibility. LVM has been used on Linux inside enterprises for over 23 yrs. It is rock solid.  ZFS is solid for data, but seems to have some remaining issues for use as the OS file system/volume manager.  ZFS is pretty cool, but needs more time to be the single file system we need for everything. Of course, you'll find some people who are willing to risk their data and systems suggesting using ZFS for everything.  I'll not use it except for data storage on systems I need to always work.  On a test system - ZFS - go for it. There's no risk, since nothing important is on it.

---

### Post by julius-nepos on 2023-08-22
Sorry for the long delay.  Okay I'm going to try the move for /usr into /.

---

### Post by julius-nepos on 2023-08-23
> **TheFu said:**
> Just boot off alternate media, mount both file systems, .
I've been able to boot off of an Ubuntu 20.04 install DVD.  How do I even see the directories on the HardDrives?   How do I mount them?

---

### Post by TheFu on 2023-08-24
> **julius-nepos said:**
> I've been able to boot off of an Ubuntu 20.04 install DVD.  How do I even see the directories on the HardDrives?   How do I mount them?

Find any tutorial you like and follow it. You'll need to mount the storage to temporary locations to do the migration of files/directories. Basically, you will use CLI commands with 'mount' to do the temporary mounts.  But the /etc/fstab inside the install will be used for mounts that happen at boot time, once the migration is done.

---

### Post by julius-nepos on 2023-08-24
Okay, found some useful articles. 
 Have been able to mount the partitions on the flash drive to /mnt/flash1,  flash2,  and flash4.  Didn't see a need to mount swap.

---

### Post by julius-nepos on 2023-08-24
I've mounted the SSD, the HDD and also stuck in a 16Gb thumb drive.  I've mounted them using the mount command:

        sudo mount /dev/nvme0n1p1 /mnt/flash1   and so on for 0n1p2 and 0n1p4.  I've mounted the HDD to /mnt/hdd1  and the thumb drive to /mnt/sdb1

Unfortunately, everything seems to be mounted READ-ONLY, thus I can get a directory listing but I can't copy it to any file.  Is there any way to mount something so that I can at least write to the thumb drive?

Also, there is no /usr partition found.  There is under /dev/nvme0n1p2 ext4 100Gb 7.6Gb used, a bunch of directories including boot, dev, etc, home, sys, usr, var, and others.    
On the 5.46 Tb HDD, there is my user directory john with directories Desktop, Documents, Music, etc. inside.

Sorry, I can get a listing but I can't write to any mounted files. I booted using the live Ubuntu 20.04 CD {DVD}.

---

### Post by TheFu on 2023-08-25
Linux will mount file systems read-only to protect them if they weren't correctly closed previously.  When that happens, **fsck** needs to be run.  Also, those mount commands are the bare minimum and leave the mount command to make guesses about the file system.   For non-Linux file systems, without additional options, the user and group will be root:root, which is almost never what is desired.  

When running inside a Live-Boot environment (Try Ubuntu is the same), the username, ubuntu, it used with a userid of 999, not 1000, which is what the first userid gets in a standard install.  Because these are different, you cannot use a normal account to move files.  Anytime you are dealing with system files, it is necessary to be cognizant about users, groups, who own each file, each directory and ensure those are retained. In most #14 above, I showed commands with specific assumptions.  You'd need to follow those assumptions OR change the commands to match the changes you decided to make.

Linux is always a multi-user OS, regardless of what we may believe. We need to treat it like there are 5000 different users on the system.

---

### Post by julius-nepos on 2023-08-25
It may be more efficient at this point to re-partition and install 22.04 It seems that a separate partition for /usr is very antiquated & has to do with a read-only partition.

It appears that fsck must be run at boot and even after clearing any errors I'll still have the merge problem to deal with.  Since a live install is apparently only 999 userid and I guess I need 1000 or more I see no way to get the permissions necessary to merge the partitions.  Of course I'll lose my OpenFOAM installation but I can always re-install.

The only concern is how the /usr partition got in there.  I wrote down the partitions I was making on a page and it did not include /usr.

---

### Post by #&amp;thj^% on 2023-08-25
> **TheFu said:**
> 
Linux is always a multi-user OS, regardless of what we may believe. We need to treat it like there are 5000 different users on the system.

+1

---

### Post by TheFu on 2023-08-25
> **julius-nepos said:**
> It may be more efficient at this point to re-partition and install 22.04 It seems that a separate partition for /usr is very antiquated & has to do with a read-only partition.

Well, the reason for having a /usr separate is from the 1990s when HDD storage was much, much more expensive.  Similar operating systems running on similar CPUs would NFS mount the same /usr across many different systems.
Storage is cheap and /usr **is** part of the OS, so it makes sense to have it on the same partition as other static OS files.  Linux is changing and it is still unusual for /usr to be in a separate file systems or to be mounted read-only today, though some distros which want to be highly secure do run that way.  ChromeOS on chromebooks is one example.  ChromeOS is 2 full OS installs - usually an "A" install and a "B" install with ROOT-A and ROOT-B being partitioned separately.  Actually, ChromeOS has 11 partitions, last time I checked.  About 50% of those are for "A" and the other 50% are for "B".  The 1 left over is for user data and gets mounted regardless of which OS is being run (A or B).

> **julius-nepos said:**
> 
It appears that fsck must be run at boot and even after clearing any errors I'll still have the merge problem to deal with.  
This is true and not really hard. It is a basic skill necessary for all Linux admins.

> **julius-nepos said:**
> Since a live install is apparently only 999 userid and I guess I need 1000 or more .... I see no way to get the permissions necessary to merge the partitions.  Of course I'll lose my OpenFOAM installation but I can always re-install.

This is NOT true. It is a misinterpretation.  Userid values are just sequential to be unique. There's nothing more implied. Higher isn't better. It is just different.  Standard Unix permissions apply.  Learn about those and these things become obvious.

> **julius-nepos said:**
> 
 I see no way to get the permissions necessary to merge the partitions.  Of course I'll lose my OpenFOAM installation but I can always re-install.
I posted the commands AND pointed you at them already, but those commands will not fill in lacking knowledge.  Learn the basics of Unix file and directory permissions and all will become clear. 

Learning file permissions well takes about 45 minutes.  I suspect a fresh install, reinstall of your data and reinstall of any non-standard applications will require hours. Not understanding Unix file permissions will lead to frustration for hours, weeks, months and years until you spend the time/effort to just learn them.  Why delay?  You have a need, now.

Of course, it is your choice which way to head.

---

### Post by julius-nepos on 2023-08-25
I've spent all day yesterday on this until 11:30 pm at night.  Just learned that I can move or merge things as I don't have permission, drives are Read-Only,  and I don't have the full syntax for the mount commands.  I'll try a bit more but basically this issue has held up all computer operations for days.

I''' do a fsck which apparently needs to be done from a live CD.  Or else by putting some fsck file in some boot directlry and then booting normally.

---

### Post by TheFu on 2023-08-25
> **julius-nepos said:**
> I've spent all day yesterday on this until 11:30 pm at night.  Just learned that I can move or merge things as I don't have permission, drives are Read-Only,  and I don't have the full syntax for the mount commands.  I'll try a bit more but basically this issue has held up all computer operations for days.

I''' do a fsck which apparently needs to be done from a live CD.  Or else by putting some fsck file in some boot directlry and then booting normally.

a) check the mount to see if it is actually read-only.  the command is 'mount' and the options for each file system (including fake ones) will be displayed.  
"rw" means read-write.
"ro" means read-only.
For example, here's one of mine ... I picked the shortest one
```
/dev/md2 on /raid2 type ext4 (**rw**,noatime,errors=remount-ro)
```
It is mounted rw currently.

b) To provide the best mount commands, we need to know the _file system_ and _where you want it mounted_ .... temporarily and permanently. The command that I'd use for this is:
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
I have an alias for it, so I don't have to type it all the time.  There are a number of *Linux how-to mount stuff* tutorials.  For temporary mounts, I'd use the **sudo mount .... ** version. For permanent mounts, I'd setup the /etc/fstab .  Lots of tutorials on setting up the /etc/fstab.  If I google for "ubuntu mount /etc/fstab", this link is the first result: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)  In general, stuff you find at websites with "ubuntu" in the DNS part of the name are reputable.  The DNS part of that link is: "help.ubuntu.com", just to be clear.

c) fsck can only be run on un-mounted file systems.  So, for some file systems that aren't mounted, it can be run without anything too special.  Point it at the device, not the directory.  Using the output from my **mount** command above, the device is /dev/md2. It is the first part of the fstab lines that do mounts, assuming a device is used and not a UUID or LABEL instead.  You can see which file systems are currently mounted using the 'df -Th' command.  Using the same md2 example, that line from df is :
```
Filesystem                               Type  Size  Used Avail Use% Mounted on
/dev/md2                                 ext4  1.3T  384G  810G  33% /raid2

```
Each of these commands shows some of the same data, but some different data, which can be matched to get a complete picture.

Just because the current userid cannot write to an area on disk, that doesn't mean it is read-only.

The command to be used once /dev/md2 is umounted is:
```
sudo fsck -y /dev/md2
```

So ... what to do if the file system you need to run fsck is already mounted?  Well, un-mount it.  Of course, not all file systems on a running OS can be un-mounted.  /usr is an example. This can only be fsck'd by booting into 'Rescue' mode (that's in the advanced Grub menu item at boot), providing a grub boot option either at boot time or by modifying the grub config file (I find these a hassle) or by booting into a *Try Ubuntu* environment from an Install ISO. That ISO can be a flash drive or optical media.  I much prefer flash devices, since they are much faster than any optical drive and with a good flash drive, we can have 20 different ISO files and boot each by selecting in a menu.

In the recovery menu, I think there is an option to run fsck on all file systems.  That should work for all Linux file system, but not for vfat/fat32/exfat or NTFS file systems.

Sadly, the old **sudo touch /forcefsck** method stopped working when systemd took over Linux around 2016.  Not all changes are good. This is a perfect example, IMHO.  Placing that file at the top level of a mount would automatically force an fsck on the file system at boot and delete the file when completed.  It was simple, effective, could be run from halfway around the world and doesn't require a special console device to accomplish like the "new" systemd crap method does for systems not in the same room.  It is very frustrating, since we had this standard capability for 20 yrs before it was removed.  It was too easy and worked, so they couldn't leave it alone.

---

### Post by julius-nepos on 2023-08-27
Okay, at least I was able to do some reporting.  When I mount the SSD as it's whole partition e.g. nvme0n1, I get errors.
When I mount each of it's sub partitions, e.g. nvme0n1p1 it seems to work fine.

sudo fdisk -l```

Disk /dev/nvme0n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: THNSN5512GPUK NVMe TOSHIBA 512GB 

Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6A0A95FD-90DA-4D2A-B396-15B583BFA4AE


Device             Start        End   Sectors   Size Type

/dev/nvme0n1p1      2048    1968127   1966080   960M EFI System
/dev/nvme0n1p2   1968128  212905983 210937856 100.6G Linux filesystem
/dev/nvme0n1p3 212905984  466812927 253906944 121.1G Linux swap
/dev/nvme0n1p4 466812928 1000214527 533401600 254.4G Linux filesystem


Disk /dev/sda: 5.47 TiB, 6001175126016 bytes, 11721045168 sectors
Disk model: WDC WD6004FZWX-0

Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 1106BD65-71F7-43EE-956C-0706C2192522

Device     Start         End     Sectors  Size Type
/dev/sda1   2048 11721043967 11721041920  5.5T Linux filesystem

```[FONT=Verdana]

Results from this
[/FONT]ubuntu@ubuntu:~$ sudo fsck -y /dev/nvme0n1
```

fsck from util-linux 2.34

e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/nvme0n1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
Found a gpt partition table in /dev/nvme0n1

```


ubuntu@ubuntu:~$ sudo fsck -y /dev/nvme0n1p1

```

fsck from util-linux 2.34
fsck.fat 4.1 (2017-01-24)
/dev/nvme0n1p1: 22 files, 13875/245276 clusters


ubuntu@ubuntu:~$ sudo fsck -y /dev/nvme0n1p2

fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/nvme0n1p2: clean, 56244/6594560 files, 1923900/26367232 blocks

ubuntu@ubuntu:~$ # note p3 is a swap partition
ubuntu@ubuntu:~$ sudo fsck -y /dev/nvme0n1p3

fsck from util-linux 2.34

ubuntu@ubuntu:~$ sudo fsck -y /dev/nvme0n1p4

fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/nvme0n1p4: clean, 292379/16670720 files, 3617722/66675200 blocks

ubuntu@ubuntu:~$ sudo fsck -y /dev/sda

fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:

    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
Found a gpt partition table in /dev/sda

```

 ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1

```

fsck from util-linux2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sda1: clean,210380/183144448 files, 14390401/1465130240 blocks

ubuntu@ubuntu:~$ sudo mount -rw /dev/nvme0n1 /mnt/SSD
mount:/mnt/SSD: wrong fs type, bad option, bad superblock on /dev/nvme0n1,missing codepage or helper program, or other error.

ubuntu@ubuntu:~$sudo mount -rw /dev/sda /mnt/HDD
mount: /mnt/HDD: wrong fs type,bad option, bad superblock on /dev/sda, missing codepage or helperprogram, or other error.

```

All of these mounts seem to work tho:
```

ubuntu@ubuntu:~$ sudo mount -rw/dev/sda1 /mnt/HDD
ubuntu@ubuntu:~$ sudo mount -rw/dev/nvme0n1p1 /mnt/SSD/p1
ubuntu@ubuntu:~$ sudo mount -rw/dev/nvme0n1p2 /mnt/SSD/p2
ubuntu@ubuntu:~$ sudo mount -rw/dev/nvme0n1p4 /mnt/SSD/p4

```

ubuntu@ubuntu:~$sudo lsblk -e 7 -oname,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
note that sdb is my thumb drive 16Gb flash

```

NAME        TYPE FSTYPE    SIZE FSAVAIL FSUSE% LABEL                    MOUNTPOINT
sda         disk           5.5T                                         
|_sda1      part ext4      5.5T    5.1T     0%                          /mnt/HDD

sdb         disk          14.6G                                         
|_sdb1      part vfat     14.6G   13.9G     5% JOHN K WO                /mnt/flash
sr0         rom  iso9660   2.6G       0   100% Ubuntu 20.04.1 LTS amd64 /cdrom

nvme0n1     disk           477G                                         
|_nvme0n1p1 part vfat      960M  903.9M     6%                          /mnt/SSD/p1
|_nvme0n1p2 part ext4    100.6G   88.2G     5%                          /mnt/SSD/p2
|_nvme0n1p3 part swap    121.1G                                         
|_nvme0n1p4 part ext4    254.4G  227.8G     4%                          /mnt/SSD/p4

```

So do I have bad superblocks, whatever those are?

---

### Post by TheFu on 2023-08-28
Running fsck on whole disk device files can be dangerous.  Only run it on file systems.  That might be a partition or it might be on a logical volume, depending on how you setup things.

/dev/sda is the whole disk. NEVER run fsck on that.
/dev/sdb is the whole disk. NEVER run fsck on that.
/dev/nvme0n1 is the whole disk. NEVER run fsck on that.

Things can end badly.

Also, fsck is a front-end program to the file-system-specific versions of fsck.  Not all file systems have an fsck, so that won't work.  The name of fsck.{file system type} is the usually convention.  
```
$ fsck.{tab}{tab}
fsck.btrfs   fsck.ext2    fsck.ext4    fsck.fat     fsck.msdos   fsck.xfs     
fsck.cramfs  fsck.ext3    fsck.f2fs    fsck.minix   fsck.vfat    fsck.zfs  
```
I think the btrfs, zfs, vfat/fat, and msdos versions above are likely placeholders to tell you NOT to to it.  You may see people using the direct **e2fsck** program for ext2/3/4 file systems.  I've only used that when things are REALLY bad. I can't remember any time when it actually helped.

BTW, whole disk devices cannot be mounted either.  Only devices with a file system can be mounted.  Now, it is possible to lay down a file system without any partition table on the device.  This is a terrible idea.  Usually people do it because they are setting up RAID5 or RAID1 arrays.  It is a mistake for a number of reasons.  Always, always, setup a partition table on any read-write storage device ... er ... except maybe a 1.44MB floppy.

---

### Post by julius-nepos on 2023-08-28
Hi & thanks for the clarification on fsck,  

When I ran fsck on the whole disk, I got errors.  When I ran it on the filesystem, it seemed to respond with no errors.  Except for my SSD boot partition: nvme0n1p1.
This seems to be reported either as ext4 or as FAT32.

```

nvme0n1     disk           477G                                         
|_nvme0n1p1 part vfat      960M  903.9M     6%                          /mnt/SSD/p1

```

Running from the regular install, the system seems to work nicely.  As you'll recall my only issue was getting rid of the /usr partition and merging or copying it back into /.

BTW, you've put a lot of time into helping me w/ this issue.  Is there anything I can do in recompense?  Tho not good with Linux, I can help a bit with html, CFD, or numismatics as you can tell from my avatar.

---

### Post by TheFu on 2023-08-28
You having a working solution is all I hope to see.

---

