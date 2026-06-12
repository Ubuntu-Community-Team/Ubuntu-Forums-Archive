---
title: "Update Plan for Dual-Drive System (SSD &amp; HDD)"
date: 2015-05-11
forum: Installation &amp; Upgrades
---

### Post by Geoffrey_Arndt on 2015-05-11
Just wanting to confirm (or correct) some basic "assumptions" about updating Ubuntu 14.10 to 15.04.

>   Currently have an all Intel laptop running Ubuntu 14.10 perfectly as sole OS (no Windows),
>   Have two drives, sda (500GiB 7200rpm HDD) and sdb (120GiB SSD),
>   Ubuntu OS is installed to sdb and bootloader is installed to sdb,
>   Extra Drive (sda) used only for data files,
>   Laptop uses a traditional BIOS (no UEFI).

Above scenario works great, and I want to keep everything exactly the same when 15.04 is finished installing.

Plan A is to use the Software Updater to do an online update (after ensuring 14.10 fully updated, and after disabling all PPA's so system just using original sources).

But if Plan A install fails (for whatever reason), a Full Reinstall from a new 15.04 iso on flash-stick is Plan B.

So, the assumption is; if doing a full re-install, will the Ubuntu installer see the existing Ubuntu install on sdb, install 15.04 there (or offer to install at sdb) AND update or replace GRUB to sdb also?    

As I've only done installs to single disk systems -  - if GRUB is placed at sda (which I believe is the normal default) - - will Ubuntu boot up normally so the OS at sdb is loaded as it is now?   In other words, is it necessary to install GRUB to sdb during the install?   What is the process or Terminal command(s) to install or move GRUB to sdb post-install?   (ps - I also have a flash-stick with the latest "Boot-Repair" iso in case needed).

Thanks for your advice.

---

### Post by oldfred on 2015-05-11
Also backup list of installed applications, perhaps settings in /etc if you made any, and all of /home.

I have lots of space, so I create a second (or third or fourth) / (root) partition and do a new install. I keep entire system on SSD and all data on HDD. That also gives me the flexibility to copy something I missed in backup. In beginning I needed one or two things, but now rarely have to go back for something.

If you use Something Else you have the option to choose which drive to install grub into. Do not use the auto fix in Boot-Repair as it installs grub to every MBR. 
I do like to have another test or backup install on data drive, just as another way to boot system. Now 20 or 25GB out of a large data drive is not that much.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home, procedures have not changed if still BIOS between versions, so still good references:
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

 Lots of detail, screen shots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

If grub gets moved to sda, you have to change default drive in BIOS.
But it is easy to boot into system, with one time boot key like f10 or f12, and reinstall grub to any MBR you specify once booted.
      
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

### Post by Geoffrey_Arndt on 2015-05-11
Thanks oldfred . . really appreciate the info and tips.   So, if I add a 30GiB partition to HDD sda and install a "backup" or secondary Ubuntu (maybe 14.04.2?), then GRUB at sdb will provide a startup menu offering choice of which Ubuntu to load?   Nice idea, I hadn't thought of that.

1).   Also, re changing default drive (if GRUB on sda), then sda would need to be the top (1st choice) re boot sequence?

2).   If Auto-Fix installs GRUB to each drives MBR, that would then cause GRUB to fail with some error status - - can a remove command string fix that scenario?

3).   Thanks also for clarifying how to update GRUB from a terminal on sdb (the OS drive) rather than the LIVE Media (which is not something apparent to average user like me).

Am planning on doing install sometime this week or week-end at latest.   Will advise how things go, etc.

---

### Post by oldfred on 2015-05-12
BIOS or one time boot key should give you the option on which drive to boot from.

I found with my system order drives are plugged into SATA ports are drive order. But I must have skipped a port. I normally booted from sdc or later sdd, but if I add a flash drive it becomes sdb and ever later drive changes. One then must be very careful.

Boot-Repair's advanced mode lets you choose which install and which drive to use for boot loader.

I liked these reasons:
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

If grub does install to incorrect drive, you may need to change an internal setting. A major update to grub will probably reinstall to incorrect location and create boot issues.

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 


 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

