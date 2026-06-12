---
title: "Windows 10 - corrupted Linux partitions?"
date: 2015-11-21
forum: Installation &amp; Upgrades
---

### Post by Luke M on 2015-11-21
This is really a Windows 10 problem, so I beg your indulgence.

I "upgraded" to Windows 10 and now my Linux partitions seem to be corrupted - they aren't recognized as ext4. I've read about Windows 10 deleting partitions, but that's not what happened in my case. The Linux partitions are still there, but they can't be mounted (unknown filesystem). What the heck did Windows do?

---

### Post by brian-mccumber on 2015-11-21
Windows overwrote the Linux boot manager.

---

### Post by yancek on 2015-11-21
How are you trying to 'recognize' them and mount them?  Obviously, you won't see anything on them from windows.  Are you trying to mount using the install DVD/flash drive?  If you still have the install medium boot it up and run the command:  sudo gparted  Post the output here or a link to an upload of it.

---

### Post by rocco6 on 2015-11-21
Use [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Luke M on 2015-11-21
> **brian-mccumber said:**
> Windows overwrote the Linux boot manager.

You mean grub? No, it's still there. It goes into grub rescue.

> **yancek said:**
> How are you trying to 'recognize' them and mount them?  Obviously, you won't see anything on them from windows.  Are you trying to mount using the install DVD/flash drive?  If you still have the install medium boot it up and run the command:  sudo gparted  Post the output here or a link to an upload of it.

There are 4 partitions, two Windows (originally there was one; Windows 10 created a new recovery partition) and two Linux (main and home). Gparted doesn't recognize the filesystem on the Linux partitions (should be ext4).

This is just a wild guess, but is it possible that Windows 10 performs a full disk encryption, including Linux partitions?

---

### Post by brian-mccumber on 2015-11-21
I posted what I posted above because while I have been browsing the forums here, I have seen alot of threads about Windows 10 corrupting grub on Linux installations by overwriting part of it that points grub to the boot files.

I have also read that UEFI causes problems with Linux installs also.

 I am just trying to help, I've never have these problems because I don't dual boot.

---

### Post by oldfred on 2015-11-21
From live installer post this:

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Luke M on 2015-11-21
boot-repair info:

[http://paste.ubuntu.com/13402345](http://paste.ubuntu.com/13402345)

---

### Post by oldfred on 2015-11-21
Partition table say they are Linux type 83, but partitions are missing format info.

I might try fsck on both sda3 & sda4.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Luke M on 2015-11-21
I tried deleting the Linux partitions and then scanning the empty space with testdisk, thinking that maybe Windows "moved" the partitions. Result: nothing found. It really seems like Windows wiped the disk because there's no trace of the ext4 partitions. Why would it do that???

---

### Post by Bucky Ball on 2015-11-21
You just deleted the Linux partitions so that had nothing to do with Windows wiping the drive. The Win install just made the Linux partitions unrecognisable. It didn't wipe them, but of course they aren't there now. Why didn't you follow the advice from oldfred which might have given you some hope? Unusual testdisk doesn't find anything, though ... :-k

---

### Post by Luke M on 2015-11-21
I have a horrifying theory. The disk was an SSD. Maybe Windows did a "TRIM" which considered the Linux partitions as empty space. If so, it's really hopeless.

---

### Post by Luke M on 2015-11-21
> **Bucky Ball said:**
> You just deleted the Linux partitions so that had nothing to do with Windows wiping the drive. The Win install just made the Linux partitions unrecognisable. It didn't wipe them, but of course they aren't there now. Why didn't you follow the advice from oldfred which might have given you some hope? Unusual testdisk doesn't find anything, though ... :-k

I did try running e2fsck, but as expected, that didn't work. I don't know what you mean by "made the Linux partitions unrecognisable".

---

### Post by sudodus on 2015-11-22
I'm sorry that this happened to you. But you are not alone. Installing operating systems and upgrading to new versions are risky operations, and if we are brave enough to do it, we will get a damaged system sooner or later. If we are lucky we begin to ***backup*** our system before it happens ;-)

-o-

If you had important files, that were not backed up, you can try to recover them with ***PhotoRec***. It works without a working file system, but if the file data are wiped (for example by trim) it does not work. I wish you good luck :-)

---

### Post by Bucky Ball on 2015-11-22
[Here's]("Photorec description: http://www.cgsecurity.org/wiki/PhotoRec") a link for Photorec. If all you've done is delete the partitions it is odd Testdisk is not picking them up. 

Avoid using the disk unless you are attempting to retrieve data from it. The more you use it, the more possibility of writing over the data (which is hopefully there even though you can't see it ... yet.)

---

### Post by Luke M on 2015-11-23
> **Bucky Ball said:**
> [Here's]("http://Photorec description: http://www.cgsecurity.org/wiki/PhotoRec") a link for Photorec. If all you've done is delete the partitions it is odd Testdisk is not picking them up.

It's not odd, it just confirms that the actual partitions (as opposed to the partition table) have been destroyed. Again, all I did was to "upgrade" from Windows 8.1 to Windows 10. In the future I'll keep Windows and Linux on separate drives.

> **Bucky Ball said:**
> Avoid using the disk unless you are attempting to retrieve data from it. The more you use it, the more possibility of writing over the data (which is hopefully there even though you can't see it ... yet.)

Yep. I ran photorec on the full drive, but it will take some time to sift through the 200,000 files to see if anything from the Linux partitions was found.

---

### Post by oldfred on 2015-11-23
Some possible help on sorting files:

 Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by Luke M on 2015-11-25
Well, photorec didn't recover anything from the Linux partitions. So it really was 100% erased. This was with the just-released version of Windows 10 (November/10586), so it's probably a Windows install bug, a very bad one!

---

### Post by Bucky Ball on 2015-11-25
Not sure if it's a Windows bug. It's possibly intentional that when installing it, it wipes any other OS in its path. MS generally don't play nice with Linux OSs. :)

---

### Post by Luke M on 2015-11-26
> **Bucky Ball said:**
> Not sure if it's a Windows bug. It's possibly intentional that when installing it, it wipes any other OS in its path. MS generally don't play nice with Linux OSs. :)

It's definitely not intentional since it doesn't benefit Windows in any way (it's not using the space). In fact, Win10 didn't even mess with the MBR, so to that extent it plays better than some previous versions. Just don't install it on an SSD...

---

### Post by oldspammer on 2016-05-04
My ubuntu 15.10 i386 that used 3 Tbyte LVM formatting (LVM = logical volume manager) was working fine until I booted and upgraded a separate 750 Gbyte WDC black 2.5" HDD with Windows 7 up to Windows 10 Pro.

The ubuntu 15.10 i386 on a two partition 3 Tbyte HDD (swap & ext4) that had worked hours before was able to boot up to a point where scripts or services or drivers were loading up and some important ones returned failure or whatever.  That ubuntu had originally had 12.04 server installed and had been upgraded to desktop 12.10, then 13.x, then 14.x, then 15.04, then finally to 15.10 with recent updates.

I used my other working Windows 7 machine to download and burn an ISO of a install / boot DVD of ubuntu 15.10 i386 to attempt repairs.

Repairs worked to get the system booting again, but wiped out all of my samba / smb4k installation/configuration, fstab cifs mounting of Windows shares, applications that had been installed in the olden days of 12.10 and so on--video editing software, image editing software, streamtuner2--more than 20 applications--gone from the ubuntu 'upgrade' to itself that was supposed to preserve all but some system configuration files.

I had done a gnu ddrescue disk image backup of my mom's Windows 7 laptop PC prior to upgrading it to Windows 10 and had wanted to get a few files off of that 500 Gbyte image file (valuable data recovery from the ubuntu 15.10 i386 HDD files).

I was able to recover some files of my mom's Windows 7 laptop image file and place them into a .tar.bz2 archive, but forgot to exclude 2 different web browser caches and download folder(s) that ended up making the archive about 27.7 Gbytes in size--hardly good as a handy to use thing unless using a USB thumb drive was almost completely consumed to contain it.

I have tinkered around with the ubuntu 15.10 i386 fstab mounting entries for cifs access to my Windows PCs, but none of the stuff that I have tried seems to work. Mount errors for cifs give error 19 even though the entries look fine when compared to another working ubuntu 15.10 64-bit computer's fstab cifs mounting entries?

A bad sign foretold of trouble when Windows 10 pro could see my ubuntu 15.10 i386 3 Tbyte second HDD and in the file manager properties reported that that ubuntu disk was "not formatted" and popped up a window offering to "format" that HDD where upon I clicked No or cancel or whatever to abort that foolishness.

---

### Post by oldfred on 2016-05-04
@oldspammer
If you are looking for help on one of your systems, please start your own thread.
If just comments, then not required.

---

### Post by oldspammer on 2016-05-04
> **oldfred said:**
> @oldspammer
If you are looking for help on one of your systems, please start your own thread.
If just comments, then not required.

My comment was a "me too" with a lengthy story.

It is impossible for me to completely recover from the sequence of things that happened to me, so my comment is a warning about the ubuntu recovery process as it currently stands.

---

### Post by coffeecat on 2016-05-04
This is an old support thread, where the OP has not logged in since shortly after their last post here.

Thread closed.

---

