---
title: "after partitioning system will not boot"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by dwlamb on 2012-12-26
I replaced a hard drive recently. Though I used Clonezilla, after the job of cloning the disk, Gparted in Ubuntu reported the partition as out of alignment and recommended repartitioning. I also decided to make some changes. The functions of the partitions did not change, only the sizes.  I changed the file system on one but feel it is inconsequential for it is not key to the system.

A 1Tb drive, it's partitioned accordingly;

    sdc1 ext4 sound and video library 625Gb
    it was NTFS; I just converted it for this PC no longer runs Windows
    sdc2 Extended partition 306.51
    sdc5 ext4 /home 68.36Gb
    sdc6 ext4 /var 58.59
    sdc7 ext4 used for back-ups which are copied to another machine 179.56Gb

To back-up the individual partitions, I booted the system with PartedMagic.  Since I was resizing partitions, I opted to save the partitions as individual tarballs with gzip rather than use Clonezilla. It was only necessary to back-up sdc5 and sdc6. sdc1 and sdc7 were mirrored elsewhere.  I deleted the partitions as they were and created a new partition table as above.  I restored the tarballs to the partitions.

I updated the fstab and it appears here:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0 
# / was on /dev/sda1 during installation
UUID=14bcdc12-5a52-492c-b286-192fcb29c0cb  /               ext4  errors=remount-ro         0  1 
# WAS NTFS before manual repartition
UUID=9c219770-f503-45c2-828d-1e2799a8befb /media/sdc1     ext4  defaults                  0  0
# /home was on /dev/sdc5 during installation
UUID=0d5b622b-9d7a-46e0-846d-fd8ab12e57c6  /home           ext4  defaults                  0  2 
# /var was on /dev/sdc6 during installation
UUID=75a477a6-c155-4add-8c2a-7a439eda9277  /var            ext4  defaults                  0  2 
# swap was on /dev/sda5 during installation
UUID=2572f5fa-280d-4d53-980f-623061df7f35  none            swap  sw                        0  0
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0 
/dev/sdb1                                  /media/sdb1     ext4  users,user,owner          0  0
/dev/sdc7                                  /media/sdc7     ext4  defaults           0  0

```There are no errors on the fstab when I boot.  I get as far as a log-in screen.  After entering My user name and password, the screen goes black and then cycles back to the log-in screen.  The machine does not reboot, it simply cycles back like restarting X-term.

I broke it but now I want to learn how to fix it.  Kindly don't suggest a total re-install unless it is absolutely necessary due to and error in my back-ups.

Can someone more knowledgeable than I help?

---

### Post by oldfred on 2012-12-26
Best to see all the details. Run BootInfo report. You can run from Ubuntu liveDVD or flash drive or download a full ISO to install as a repair flash drive.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by efflandt on 2012-12-27
Are you using current UUID's in fstab from **sudo blkid** run "after" the repartitioning?

---

### Post by dwlamb on 2012-12-28
> **efflandt said:**
> Are you using current UUID's in fstab from **sudo blkid** run "after" the repartitioning?
 
Yes.  As I originally wrote:

> **dwlamb said:**
> There are no errors on the fstab when I boot. 

Had I not modified the fstab with new UUID's I would be receiving errors.  That was a challenge early on but I did the troubleshootinng as far as UUID's by the time I posted here.

---

### Post by dwlamb on 2012-12-28
Taking oldfred's advice, I ran Boot-Info.  That report indicated a recommended course of action to rebuild the GRUB so the repartitioned drive could be included in the MBR.

Using this how-to [https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal) I thought solved the issue.  But the machine will not boot.  It is still behaving as outlined originally: I will get a log-in screen, enter My credentials and then the machine cycles back to the log-in screen.

I have tried re-installing the GRUB2 again and ran the repair tool in Boot-Info.  No joy.

I ran a new Boot-Info report and am at a loss to interpret it for it still states to rebuild the GRUB so the MBR is updated.  A most recent Boot-Info can be viewed here: [http://paste2.org/p/2658430](http://paste2.org/p/2658430)

---

### Post by oldfred on 2012-12-28
Boot-script looks normal and if you can boot as far as log-in then it is some sort of  gui issue or possibly video issue.

Can you boot with recovery mode? And run updates? Or to command line?

What video card do you have.

---

### Post by dwlamb on 2012-12-29
I can boot into recovery mode and run updates.  What I can not do is get into mysql.  The var directory is on this drive.  As a php/MySQL programmer, I wanted to keep my databases and server files separately.

The error I get is:
```

ERROR 2002 (HY000): Can't connect to local MySQL server through socket 'var/run/mysqld/mysqld.sock' (2)
 
```The graphics card is an older Nvidia and was working fine before this.  Is there anything in var related to running gui?  I have Unity, Gnome and KDE Plasma desktops installed.  Ninety percent of the time I run the KDE Desktop.

Sometimes over the past few days trying to debug this, during start-up I get a text-based start up screen (large type reddish on maroon) and can make out some of the start up steps.  The mysql server starts and then stops immediately.  Anything else I can not distinguish and certainly can not screen capture.

I do not understand how the system can be broken.  These were the basic steps:

[LIST]
[*]I backed-up my home directory to a zip file
[*]rebooted into Parted Magic
[*]mounted sdc5 which held var and tarballed it
[*]mounted sdc7 and copied the tar back-ups I keep to an external drive
[*]still in PartedMagic, launched GParted
[*]deleted all partitions and made new ones
[*]once I was happy with the partitions and sizes I wanted, restored the back-ups to their respective locations
[*]updated the fstab with the new UUID's
[*]rebooted and can't get in
[/LIST]
Are there hidden files in var that would not have been visible in a file manager while in PartedMagic and that gui-environment which is very similar to a Live-CD?

Have I done something and have no choice but to format/re-install?

As part of my back-ups, I have var backed-up every day using root credentials.  If I do a format/re-install, can I restore var in its entirety on top of a fresh install (after I set-up a LAMP)?

---

### Post by oldfred on 2012-12-29
It seems like an ownership or permission issue. But I do not know MySQL.

What are the owners & permissions on your sql folder & files & what should they be.

---

### Post by dwlamb on 2012-12-29
Ownership should be and is root.  With being signed in as root in a live CD-like environment and full control, how would the permissions or ownership be altered unless I did something to modify them at time of back-up or restore?

Dragging and dropping them in a file-roller interface should not change ownership or permissions.

> **oldfred said:**
> It seems like an ownership or permission issue. But I do not know MySQL.

What are the owners & permissions on your sql folder & files & what should they be.

---

### Post by dwlamb on 2012-12-30
I deleted everything and did a format/reinstall.

---

