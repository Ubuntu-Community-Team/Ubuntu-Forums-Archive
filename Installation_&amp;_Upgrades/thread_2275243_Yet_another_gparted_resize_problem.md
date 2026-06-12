---
title: "Yet another gparted resize problem"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by Eric_Shields on 2015-04-25
I give up.  I've spent hours now, created a live USB stick (of the same version I'm running, just in case), ran gparted from it, turned off swap (sudo swapoff -a), unmounted everything even though it looks like the normal drive isn't mounted anyway (sudo umount -a), and STILL I can't resize my partition.  It's a really simple setup:  I have a boot partition (~200MB) and an extended with a single partition inside that containing the other ~114GB.  All I want to do is increase the boot partition size cause it's full (and causing issues), which of course first requires shrinking the extended.  Problem is, every single time I run gparted, both the extended and the partition inside it have the same min and max size and won't let me change them, either by altering the size value, or using the slider.  There are no "key" icons, as other posts have mentioned.

What the heck am I missing?  Every forum post/question on the subject just says "Run it off Live CD and you're good to go", followed by thanks (or no response at all).

Thanks,
Eric

---

### Post by dino99 on 2015-04-25
When you need to resize/shrink an embedded partition, some free space is needed as its all data is moved. How much free space (%) is available ?
You also did not tell us which gparted version is used nor the ubuntu one

---

### Post by Eric_Shields on 2015-04-25
A couple more hours of fun and I discovered part of the problem:  The partition was set up with LVM, which apparently doesn't work with gparted.  I was able (finally) to resize the logical volume (and file system) and the physical volume using the LVM tool, but while gparted shows the new state of the volume inside the extended partition, it still refuses to allow me to resize that (thus freeing space to increase the boot partition).

I'm running Ubuntu 14.04 (At least that's what the Live USB is) and gparted 0.18.0 (the version bundled in the Ubuntu install).
I have 0 bytes free on /boot (hence the problem), but ~60GB free on the drive.

Right now I'm trying to figure out if I really have to rewrite my partition table in fdisk (or according to the fdisk man page, the preferred cfdisk) to do this next step.  Some days I really %$@&ing hate Linux.

Or that's what I'm doing tomorrow, at least.  Cause right now I just want to punch something, and I should have been in bed 4 hours ago.

---

### Post by Bucky Ball on 2015-04-25
I understand your frustration. Perhaps avoid LVM in future unless you have a specific reason to use it. It can be a horror story for the uninitiated, particularly in situations just like yours. 

I'd be tempted to backup whatever is inside that extended partition, delete everything except your install and recreate the extended and logical drives inside it NOT using LVM. Also, you don't mention a /swap partition? You're not using one by choice, you just don't have one or you just didn't mention it?

---

### Post by oldfred on 2015-04-25
I have always considered LVM for advanced users only. 
But if you have to have full drive encryption then you have LVM also.
I do not know LVM, but something about shrinking the LVM, another change of default size and then you can change physical partition.

         Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
[http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

But if you regularly houseclean out old kernels you should not be having issues with /boot partition size. Default is not large, we have many posts where users have filled /boot partition.

      
 Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove
sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by Eric_Shields on 2015-04-25
> **Oldfred][COLOR=#000000]But if you regularly houseclean out old kernels you should not be having issues with /boot partition size. Default is not large, we have many posts where users have filled /boot partition.[/COLOR][/quote]
[COLOR=#000000]I avoid messing around in any of Linux's core stuff if I can help it.  It's far too easy to mess with something that seems innocuous but turns out was actually key to something else that was a dependency of a 3rd thing that is used by a 4th thing in this one specific instance that causes a warning to appear only when using a 5th thing that's not related to the broken 4th thing.  Or for the entire system to just crash.  Honestly, I don't know why I picked 250MB anyway.  It's a 120GB drive that doesn't really store anything locally.  I know Linux isn't large, but experience should have told me to make it big enough to ensure future needs...  That said, I'll bookmark that thread, since it's likely useful to know regardless.

And no, it is not an encrypted drive.[/COLOR]

[QUOTE=Bucky Ball said:**
> I understand your frustration. Perhaps avoid LVM in future unless you have a specific reason to use it. It can be a horror story for the uninitiated, particularly in situations just like yours. 

I'd be tempted to backup whatever is inside that extended partition, delete everything except your install and recreate the extended and logical drives inside it NOT using LVM. Also, you don't mention a /swap partition? You're not using one by choice, you just don't have one or you just didn't mention it?

So far as I know, LVM was installed by the Ubuntu installer, likely as a default based on a choice I made (perhaps something along the lines of answering the question "Will you ever want to add additional hard drives?").  However, this was several years ago and I do not recall.  I've considered simply reformatting a number of times during this process, especially since there is not much on the computer I really care about anyway, but once I get into a problem like this, where it SHOULD be simple and have taken less than an hour to complete, then I want to understand WTF is going wrong.

As to the swap partition, one existed inside the volume group, but at the end.  After I resized the logical volume, there was no way to move the allocations around (the only answer I was able to find was "simply installing another physical drive so there's enough space".  That is not an option, since the computer in question is a NUC and I'd have to buy another $100+ drive to do so.  I'm not even sure I have an empty slot.).  So, I deleted the swap partition with the intent to leave enough space to remake it.  Right now, the partitions are as follows, according to cfdisk:

unallocated space 1.05MB
/dev/sda1  boot  ext2  254.01MB
unallocated space 1.05MB
/dev/sda2  lvm2_member 119770.75MB
unallocated space .40MB

And according to gparted:
/dev/sda1  243MiB ext2 flag: boot
/dev/sda2  111.55GiB  extended
/dev/sda5  111.55GiB  lvm2pv  flag: lvm, warning icon mentioning 4.00GiB of unallocated space inside the partition (which corresponds to the "[lv|pv]resize -L-4G -r" command I ran via lvm)

And according to system-config-lvm (which I discovered after doing everything in command line lvm):
Partition 5:  
  root: 25621 extents
  unused space: 1911 extents

I don't know WTF an extent is, but going into the properties gives MiB values that match up to unused space equaling the size that the swap was.  I also love that every one of these programs uses a different unit of measure.  MB, MiB, extents, fdisk wouldn't tell me anything but sectors (which required looking up yet another command to figure out how much space that meant, since sectors are configurable...)

So, as far as I can tell, everything is where it should be.  Except that *@&%ing sda2 container that nothing will let me resize down.

---

### Post by Bucky Ball on 2015-04-25
What is going wrong? LVM probably. ;)

---

### Post by Eric_Shields on 2015-04-25
While I appreciate the sentiment, that doesn't really help :P

Any idea at all how to resize the lvm container?  Is manually rebuilding the partition table in fdisk the only way?  If so, doing so doesn't change anything on disk, so it's up to me to make sure everything is calculated exactly right, right?

---

### Post by gedakc on 2015-04-25
Several steps are required to migrate space from within a LVM Logical Volume to add to a different physical partition.

Step 1)  Free up space within the LVM Physical Volume.  Inside the LVM PV is where the LVM Logical Volumes are stored.  These can be resized with the **lvresize** command (try **man lvresize** to learn the options for the command).  If the LVM ***LV*** is shrunk, then there should be unallocated space within the LVM ***PV***. 

Stepl 2)  Using [GParted Live]("http://gparted.org/livecd.php") (latest version 0.22.0-1), you can resize a partition containing an LVM PV.  Of course the LVM PV must have unallocated space inside in order to be shrunk.

Step 3)  Using GParted Live, grow the partition you wish to have larger.

'Hope that helps.

---

### Post by Eric_Shields on 2015-04-25
gparted live is not working.  Every time I try to make the live USB ([http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)), it gives the error:  "An uncaught exception was raised:  unorderable types: NoneType() <= str()"  I've tried both the i586 and i868 versions, just in case that was the problem.

---

### Post by Eric_Shields on 2015-04-25
Update:  I realized I was, apparently, trying to create a boot disk for gparted the wrong way, so went to download Tuxboot.  Except that I didn't have enough space on /boot (see original problem).  So, I followed Oldfred's advice and ran the autoremove.  That freed up enough space to install Synaptic.  But I had no idea what I was looking at in that giant list of linux-image results, so I clicked through to his mentioned forum thread.  On that thread I found a magic bashrc addition (I KNEW there had to be a magic command somewhere.  It wouldn't be Linux otherwise.) that deleted nearly 1.5GB of stuff, including a large portion of what was filling up /boot.

Granted, this technically solved the original problem, but everything else was now in a crazy state, and I still wanted to increase /boot for future needs just in case.  So I continued with the Tuxboot install, which finally let me boot up via gparted Live, which FINALLY let me actually resize that god damned sda2.  So I poked until I had the 4G boot partition I wanted, read all the data loss warnings, and hit go.

Fingers crossed.

---

### Post by Eric_Shields on 2015-04-25
Close enough.  Still need to remake my swap partition, but 2 days, a dozen programs, and some serious stress headaches finally accomplished what should have taken less than an hour.  Marking solved, and I'll try to write up a "here's all the stuff I did, in order" list soon, just so people can try to avoid those pitfalls.

---

