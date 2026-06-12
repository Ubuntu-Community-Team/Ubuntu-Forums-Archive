---
title: "problem installing Kubuntu. 2 HDs, 2OSs"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by bill blakely on 2013-02-14
My first post to the forums. My apologies for the bad formatting. (How do you get commands in those neat boxes?)  

I have tried to install Kubuntu to my second HD. Windows on the first drive, Xandros on the second.  

SHORT VERSION
 I have an older system, but I believe it to be adequate.. 

Motherboard is an Intel D865perl (2004). Processor is 3.2 GHz. 4 GB RAM. 
I have two hard drives,

 IDE 1     28.62 GB           Primary (C; drive)  fat32     28.62 GB   2.74 GB used (9.6%))         /disks/C            
IDE 2     114.5 BG           Primary (hdb 1)`    linux swap         502 MB           Primary (hdb 2)      Reiserfs           114 GB 18.,19 GB (16% used)    /  

I used GParted to resize hdb2 and create hdb3 on the unallocated space. I downloaded Kubuntu 12.10, burned it to a DVD, and installed, accepting all defaults. 

Upon rebooting, I got the Xandros lilo screen, with no Kubuntu showing. 

GParted showed a sdb3 of 47.8 GB, and a sdb4, extended of 48.6 GB. 

Assuming that I made an error, I re-partitioned the drive and reinstalled Kubuntu
. I rebooted and got the Xandros lilo screen. 
I edited lilo.conf until I got it right (?), and ran /sbin/lilo as root,  but when I click the Kubuntu line, I get a blank screen, not black, but blank.  

VERBOSE VERSION 

After the second installation, GParted shows - 
/dev/sdb1           linux swap                    502 mb 
/dev/sdb2           reiserfs                   17.58 gb 14.26gb 3.32  
/dev/sdb3           ext4 1.70 Gb         180.16 Mb 1.52 Gb 
/dev/sdb4           extended  
/dev/sdb5           ext4             94.73 GB   4.60   90.14 GB

 moved boot flag to /dev/sdb5  
(sorry about the lousy formatting.) 

After putzing with lilo.conf, /sbin/lilo -v (as root) returns -
 Boot other: /dev/hdb4, on /dev/hdb, loader CHAIN           Added Kubuntu_12.10           
Writing boot sector           /boot/boot.0340 exists - no boot sector backup copy made            

I shut down, restart Kubuntu in lilo screen. When I click the Kubuntu line the screen flashes-
 Preparing Kubuntu_12.10           
Loading kernel           
Initializing kernel
Black Screen 

I ran "Boot Info Script" and the RESULTS.txt file is-
 Boot Info Script 0.61      [1 April 2012]   ============================= Boot Info Summary: ===============================   ============================ Drive/Partition Info: =============================  no valid partition table found "blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/hda1        1819-13E7                              vfat    /dev/hdb1        428ce911-fb9b-4cba-b453-268b7132a960   swap    /dev/hdb2        36849585-2ef5-4e2d-98de-b5da14a8bda1   reiserfs /dev/hdb3        1ee5e512-5cec-42b9-85c8-258577cb5422   ext3    /dev/hdb5        f39e47dc-7d76-4ca5-84be-0117414d4cb2   ext3     ================================ Mount points: =================================  Device           Mount_Point              Type       Options  
/dev/hda1        /disks/C                 vfat       (rw,noexec,nosuid,nodev,fmask=111,dmask=0,uid=1001,gid=1001)
/dev/hdb2        /                        reiserfs ()rw,usrquota,grpquota)   
========= Devices which don't seem to have a corresponding hard drive: =========  hdc hdd sda sdb sdc sdd No RAID disks   =============================== StdErr Messages: ===============================  ./downloads/bootinfo/bootinfoscript: line 2660: printf: -v: invalid option printf: usage: printf format [arguments] blkid: invalid option -- g blkid 1.0.0 (12-Feb-2003) usage:    blkid [-c <file>] [-h] [-o format] [-s <tag>] [-t <token>]     [-v] [-w <file>] [dev ...]           -c        cache file (default: /etc/blkid.tab, /dev/null = none)           -h        print this usage message and exit           -s        show specified tag(s) (default show all tags)           -t        find device with a specific token (NAME=value pair)           -v        print version and exit           -w        write cache to different file (/dev/null = no write)           dev       specify device(s) to probe (default: all devices) File descriptor 4 left open File descriptor 5 left open File descriptor 7 left open File descriptor 11 left open   No volume groups found mdadm: No arrays found in config file 
------------------------ 

Well, not what I expected at all. "No valid partition table found." No ext4. No mount points for Kunbuntu. 
The hdb3 is a "lost&found"file. It contains 180.kb of what?  
My Options seem to be: 
>delete hdb3,4,5 and create a new partition hdb3
 >reinstall 12.10 
>download and install 12.04 
>download and run "boot-repair" and hope for the best..  
All help greatly appreciated. 
Thank you, bill

---

### Post by carl4926 on 2013-02-14
Try installing again
Be sure to choose
Something else: [https://docs.google.com/file/d/0B3e0lLG3OdqETlE1dndoVTZWbWM/edit?usp=sharing](https://docs.google.com/file/d/0B3e0lLG3OdqETlE1dndoVTZWbWM/edit?usp=sharing)

Then at the advanced partitioner set
/dev/sdb5 ext4 
As /
Just double click the partition in the windows that looks like this
[https://docs.google.com/file/d/0B3e0lLG3OdqEXzhmUkZlWDFUak0/edit?usp=sharing](https://docs.google.com/file/d/0B3e0lLG3OdqEXzhmUkZlWDFUak0/edit?usp=sharing)

Be sure to set Grub to **sda**

---

### Post by deadflowr on 2013-02-14
I'd go with option one and delete and start over.

If your verbose versions numbers are to be believed, then sdb3 only has 1.7GB and sdb5 (as well as sdb4, which is the extended partition holding the sdb5 logical partition) has over 90GB.

I'd reorganize it.

Start fresh.

---

### Post by oldfred on 2013-02-14
+1 on re-installing.

The edit panel above your message has # which will auto enclose anything you have highlighted with code tags. Also quote and other editing features.

Does your system use cable select and your BIOS let you choose which drive to boot from? If so use manual install and add grub2 to same drive as Ubuntu install. Otherwise you have to install grub to sda as those old BIOS IDE systems only boot from primary master.

You can also use Boot-Repair which runs bootinfoscript and includes even more data. It also copies to pastebin so you can just post the link.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by oldos2er on 2013-02-14
> **bill blakely said:**
> My first post to the forums. My apologies for the bad formatting. (How do you get commands in those neat boxes?)

Use code tags: [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by bill blakely on 2013-02-14
Thank you all.
That's three votes for -
>running GParted and deleting hdb3,4,5
>creating new partition hdb3
>reinstalling Kubuntu 12.10

More questions -
When running GParted do I check the box "Create New Partition Table"?  (seems like I should, but didn't before)

Is the hdb3 partition a "lost & found" partition? I don't know what that is, exactly, nor do I know how big it should be.

My system now boots from IDE 2. The windows drive is IDE1.

How do I install GRUB during the installation? (you may have told me and I didn't get it.)

Anything else I should know to prevent future deodorant malfunctions?

Carl4926, your links didn't display properly in my Firefox 2.

Oldfred, I don't know what cable select is.

Thanks again, bill

---

### Post by deadflowr on 2013-02-14
If you want to keep sdb1, and sdb2** Do Not** create a new partition table, as that will reset the whole disk.

---

### Post by oldfred on 2013-02-14
If you can boot from both drives you do not have to worry about cable select unless you change a hard drive. Just for reference. Just look at pictures for an overview.
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)

Only with Something Else or manual install do you get the option on which drive's MBR to install the grub2 boot loader into. 

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

    Note on page 2 the "device for boot loader installation" graphic.

---

### Post by carl4926 on 2013-02-14
> Carl4926, your links didn't display properly in my Firefox 2.

[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)

---

### Post by bill blakely on 2013-02-19
The Third Time was indeed a charm. Almost.
I've got Kubuntu up and running.
Windows and Xandros appear in the GRUB screen, but won't load when I click them. (Hit "enter" actually)

Here's what I think I did wrong - 
The screen shots you gave me, and thank you very much, they were a great help, were from 12.04, I think. The 12.10 screens are a little different.

At the Installation Type screen I took a deep breath and selected "Manual"
 I was given a partition screen where I could select each partition.
I selected sdb3, made it "ext4 Journaling file system,  checked "format", and made the mount point "/"

If I had relaxed a bit more, I could have selected sdb1 and made it "swap", and sdb2 and said "don't use this partition" and entered a mount point. 

I just looked at the KDE Partition Manager, and I couldn't figure out how to set a mount point for sdb2 (Xandros)

I suppose I could do this by running GParted again. Would I have to install GRUB? And if so how?

Tell me I don't have to reinstall. 
Thank you, bill

---

### Post by carl4926 on 2013-02-20
They are showing in Grub > But don't load?
Tell us what happens...

FYI: If a swap partition exists, on any of your HD's the installer will automatically use it, so you don't need to set a mount point.

If you are using a separate /home partition you would want to set the mount and format options for that.

Other OS's do not need to be set with a mount point (although there are circumstances where you might do this), and this has not bearing on Grub and the OS booting.

Perhaps you should update kubuntu and then check again.

---

### Post by oldfred on 2013-02-20
You do not set mount points with gparted, but if you want permanent mounts you can edit fstab. You can just use Nautilus in Ubuntu, I assume Kubuntu's file manager would be the same if you just click on a partition it will mount. If a Linux formatted partition you may have to manually mount to get permissions and ownership correct.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

