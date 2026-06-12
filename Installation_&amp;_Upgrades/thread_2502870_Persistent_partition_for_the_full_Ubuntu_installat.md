---
title: "Persistent partition for the full Ubuntu installation"
date: 2024-12-03
forum: Installation &amp; Upgrades
---

### Post by syn0ptic on 2024-12-03
Hey!
I wonder if there's a way to add persistent partition to the full Ubuntu installation?
So all the changes I made should be saved on persistent partition even if I reinstall the whole system. 
Sorry if there's such topic but I couldn't google it.

---

### Post by grahammechanical on 2024-12-03
I do not understand what you want. Please explain more fully.

I consider all partitions to be persistent. The size of the partition does not change unless I run a program to re-size the partition. Data on partitions is persistent until some action is taken to change the data.

I have a partition that I Label Data. I store all my work on the Data partition. If I re-install Ubuntu I make sure that the installer program does not touch the Data partition. I have on my drive Ubuntu 20.04 and 2 x Ubuntu 24.04 install. I can access my information in the Data partition from the file manager and applications in the three installs of Ubuntu.

I open the Spreadsheet application (Calc) and it remembers the spreadsheets I was working with and that are stored on the Data partition. It will open those spreadsheets from the Data partition and save my work back to the Data partition. It will do this provided I have mounted the Data partition.

The Data partition can be mounted by using the file manager to open the Data partition to reveal the folders on the partition. Or, I can edit the /etc/fstab file and it will mount automatically.

Is this the kind of thing you are looking for?

Regards

---

### Post by TheFu on 2024-12-04
> **syn0ptic said:**
> Hey!
I wonder if there's a way to add persistent partition to the full Ubuntu installation?
So all the changes I made should be saved on persistent partition even if I reinstall the whole system. 
Sorry if there's such topic but I couldn't google it.

We call these things "backups".

You can, and should, split your install areas up.  OS, settings, temporary data, personal configs, data, etc.  For most desktop users, all the data and personal configs are stored in their HOME directory.  That's part of the Unix design going back to the 1960s.  On most Linux systems, this is in /home/{username}.

If you learn about where the different parts of linux files and directories are kept, then what seems like a mystery isn't anymore.  There are standards for where stuff goes and they aren't hard.  There's a 1 pg table here: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)   Takes about 2 minutes to skim, the table.

At a minimum, split your /home into a different partition. Let everything else go to / - another partition.
Of you want to more control or protection, you can split the OS into finer control areas. I do this:
```
NAME                              TYPE FSTYPE        SIZE FSAVAIL FSUSE% LABEL       
nvme0n1                           disk             931.5G                            
&#9500;&#9472;nvme0n1p1                       part ext2            1M                            
&#9500;&#9472;nvme0n1p2                       part vfat           50M   43.8M    12%             /boot/efi
&#9500;&#9472;nvme0n1p3                       part ext4          700M  313.8M    46%             /boot
&#9492;&#9472;nvme0n1p4                       part LVM2_member 930.8G                            
  &#9500;&#9472;vg01-swap01                   lvm  swap          4.1G                            [SWAP]
  &#9500;&#9472;vg01-root01                   lvm  ext4           35G   24.7G    23%             /
  &#9500;&#9472;vg01-var01                    lvm  ext4           20G   13.1G    28%             /var
  &#9500;&#9472;vg01-tmp01                    lvm  ext4            4G    3.6G     0% tmp01       /tmp
  &#9500;&#9472;vg01-home01                   lvm  ext4           20G    4.6G    72% home01      /home
  &#9492;&#9472;vg01-libvirt--01              lvm  ext4          137G    2.8G    98% libvirt--01 /var/lib/libvirt

```
I use LVM rather than partitions. Much more flexible for many needs. You can see I'm using less than 50% of the SSD's 1TB storage. That's because LVM's power and flexibility is mostly useful when it isn't fully allocated. Adding more storage when and where it is needed is 5 seconds of effort with LVM. Zero downtime.  

The extra partitioning (logical volumes) are so I can mount each storage chunk with different mount options to gain more security than the defaults.  I've posted detailed descriptions about each and why they are sized the way they are a few times. Search these forums for that.
That's just the OS storage.  This specific system has plenty of storage:
```
$ inxi -D
Drives:    Local Storage: **total: 15.46 TiB** used: 3.28 TiB (21.2%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 980 1TB size: 931.51 GiB 
           ID-2: /dev/sda vendor: Western Digital model: WD8002FZWX-00BKUA0 size: 7.28 TiB 
           ID-3: /dev/sdb vendor: Western Digital model: WD8002FZWX-00BKUA0 size: 7.28 TiB 
```
I just pulled 4x2TB HDDs from it to be retired after moving the data to sda.  I added 100G to an LV under sda yesterday to allow for some video processing space.  Did that expansion while the same file system was active and busy.  HQ video files eat lots of storage during processing.  Usually over 30GB/hr of video.  3 hours is about 100GB and that's at 1080p, not even 4K resolution.

---

### Post by syn0ptic on 2024-12-04
> **grahammechanical said:**
> I do not understand what you want. Please explain more fully.

Is this the kind of thing you are looking for?

Regards

If all of your third party Apps are still there after fresh Ubuntu   install that's what I'm looking for. I need additional abstraction level   of the filesystem that should keep all my Apps and system tweaks even   if I reinstall Ubuntu. Can you imagine you're using full Ubuntu   installation which stores all the changes to the system in the   persistent file instead of default system partition?

I googled something:
[https://askubuntu.com/questions/109413/how-do-i-use-overlayfs](https://askubuntu.com/questions/109413/how-do-i-use-overlayfs)
And I got some questions from 
[h=3]Example 1, overlaying the root filesystem[/h]
1) Do I need to pack my "/" into ubuntu.squashfs image ?
Note that filesystem.squashfs above is a *directory* created by casper, not a file.
2) How do I get the same directory created by casper?

---

### Post by yancek on 2024-12-04
Sound like you are looking for a way to remaster your system in case you need to reinstall so try an online search to remaster Ubuntu.  Haven't done this in years and the last piece of software I remember was called Systemback.  Probably other similar software.  You can get a list of installed apps using the commands listed at the site below.

Will the installer know on which partition 18.04 is installed, and whether I want it partitioned? 

>  If all of your third party Apps are still there after fresh Ubuntu   install that's what I'm looking for. 

When you reinstall, just select not to format the partitions.  Just did this with another Linux OS this week and all the software was retained as was all my personal data.  I'd always suggest you have a backup copy of personal data.

---

### Post by TheFu on 2024-12-04
> **syn0ptic said:**
> If all of your third party Apps are still there after fresh Ubuntu   install that's what I'm looking for. I need additional abstraction level   of the filesystem that should keep all my Apps and system tweaks even   if I reinstall Ubuntu. Can you imagine you're using full Ubuntu   installation which stores all the changes to the system in the   persistent file instead of default system partition?

I googled something:
[https://askubuntu.com/questions/109413/how-do-i-use-overlayfs](https://askubuntu.com/questions/109413/how-do-i-use-overlayfs)
And I got some questions from 
[h=3]Example 1, overlaying the root filesystem[/h]
1) Do I need to pack my "/" into ubuntu.squashfs image ?
Note that filesystem.squashfs above is a *directory* created by casper, not a file.
2) How do I get the same directory created by casper?

This is all much harder than
a) backing up your data and personal settings
b) creating a list of installed packages. That's 1 command. You'll need to be careful about how you install packages, since there are multiple, incompatible, packaging systems that Canonical (and others) are forcing onto desktop users now.

Then your restore process begins with a fresh OS install. You can change the hardware underneath completely. Then restore your personal data and the list of installed packages.  Next, tell APT to install all the previously installed packages.  That's 2 commands.

If you modify config files outside your HOME, then you'll want to backup and restore those. Most end-users don't.  For servers, you probably will have a few times under /etc/ modified.  Grab all of /etc/ in your backups as reference, but selectively restore them.  /etc/ is tiny.

If you install snap packages, keep a list of those that are installed.  1 command will put them all back and find your snap-package data/settings in your HOME.  There's a built-in snap-export command, which will make a tgz "backup", if you prefer to waste storage. It is dumb and doesn't do versioning, but whatever.

If you want to create a new installable "master" that's harder.  Ubuntu had a tool like that until around 2012-ish.  I think some instructions for doing it manually existed for 2015 and earlier releases.   A few other distros still do. I think MX Linux does.

You already need backups, so why not have your backups fill this desired outcome too?  Just something to consider.

---

