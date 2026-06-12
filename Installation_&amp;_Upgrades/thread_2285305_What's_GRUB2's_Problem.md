---
title: "What's GRUB2's Problem?"
date: 2015-07-04
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2015-07-04
I customarily put a Ubuntu install on my USB HDD as a fallback if I can't boot from my internal primary drive.  This has never been a problem before.

But now all of a sudden, Grub2 has these complaints:
```

sudo grub-install /dev/sdb1
Installing for i386-pc platform.
grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: error: embedding is not possible, but this is required for cross-disk install.

```
The USB HDD is formatted ext4, so it's in the same family, but what is this about a cross-disk install?  True, I am doing this from /dsv/sda1, but I just want a basic boot capability on the USB HDD, not a case where it sees the root (/) as being on /sdev/sda1 when I boot from /dev/sdb1/  Can I still get this done with Grub2?

And on the topic of Grub2, reports on the internet (not just Ubuntu) have it that some Linux installs are failing to boot up on certain laptops, and someone has compiled two lists:
  (1) a Blacklist of laptops it won't work on, and
  (2) a Whitelist of laptops where it does work.

The installs all went great.  But the machines either would not boot up, froze while booting up, or showed a blank screen after booting up.

My own new laptop worked fine initially when the internal drive was still dormatted with a FAT, ext2, and LVM partitons, but when I wiped all that off and when straight ext4, the reinstall failed to boot.  That really got me into a question of "What's going on here?"

Anyway, I dealt with some boot issues on my old laptop while searching out leads on the internet, and it seems like Grub2 takes issue with a lot of things now that weren't issues before, but it's not always going a good job of it.  I put together a text file of some of the central complaints and efforts to get around it.  Two prominent ones stood out:
  (1) Uncomment-out the "#GRUB_DISABLE_LINUX_UUID=true" line in /etc/default/grub (make it "GRUB_DISABLE_LINUX_UUID=true"), or
  (2)  Revert back to Legacy Grub.  Several postings tell you how.  And apparently apt-get can set a flag to lock this in place so future updates will not change it back.

Some posting responses were from team members that were working on Grub2, and they welcomed suggestions.  At the same time, I sense an undercurrent of an effort to make Grub2 and the Ubuntu installer more supportive of HDD restructuring coming out of Seattle, or more compatible with a Windows-dominated world.

I'm not interested in Windows myself, but obviously this is a telling point for some.  I just want compatibility within a strictly Linux universe, and I think we are losing it.  There were even complaints posted that Ubuntu was separating itself from the other Linux distros in the area of graphics support.  Not sure what that is all about, but some were leaving Ubuntu in favor of Mint as a consequence.

Ubuntu is fine for what I do, and has a great support community here, something that other distros may not be able to claim.  So I am not making any such move myself.
an                         
But about Grub2, that is a different matter.  I used Boot-Repair-Disk, got the iso file downloaded and used Brassero to burn it to a CD, then booted from the CD.  As part of the repair process, it told me that Grub2 had to go, or otherwise my new laptop would be unbootable.  That pretty much confirmed what I had learned from other sources, so I followed it's instructions, and now my new laptop boots into Ubuntu just fine.  

I guess a part of the problem with Ubuntu is its total reliance on Grub2 as the only default option during the install.  That and the fact that if it has total domination of the HDD (choice number 1), It sticks to the FAT, ext2, LVM partitions format that Windows left behind.  It does give you a choice there, but urges you to keep the existing format because it will make it easier to resize or shift partitions around in the future.  Partition resizing and shifting are not big things in my book, but I went with the idea anyway, which is probably why my first install on the new laptop worked.

It's when I changed my mind and went straight ext4 that things went bad.  Grub2 has to be able to support the past (legacy) approach as well as move with the times, and it is currently showing that it can't do that.

And one final question:  I'm daling with multiple bootable partitions and a bootable USB HDD, and I designate which one I want grub installed on with a "sudo grub-install /dev/sdX# (where X is a letter for the drive and # is the partition number, like /dev/sda1, /dev/sda2, /dev/sda3. /dev/sdb1, and so on).  But I follow that with a "sudo update-grub" command.  How do I know which of those bootable partitions is being updated?  I can't specify one, as I can with grub-install.  Shouldn't there be a "update-grub /dev/sdX#" way of doing things?  And to go with that, how about just making any partition bootable, but only make one or two of them primary, one an alternative to the primary.  Something like this:
sudo grub-install /dev/sda1 /dev/sda2 /dev/sda3 /dev/sdb1 PRI=/dev/sda1 SEC=/dev/sdb1

---

### Post by ubfan1 on 2015-07-04
I think its the UEFI changes on your new laptop that't the problem, not grub2.  That FAT partition on your original internal hard disk held the Windows bootloaders, and should have been left for the Ubuntu bootloader too.  Some reading:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and even though there's no Windows left:
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
  
  Now it is possible to take you new laptop, and in the UEFI settings, put it into legacy or compatibility mode, and then have grub in the master boot block (whether partitioned MSDOS or gpt), but I've not done that.  Additionally, the UEFI installs should normally be 64 bit (32 bit is possible with a LOT more work...) and it looks like you are using 32 bit grub.  But maybe you switched to compatibilty mode, so 32 bit Ubuntu becomes a choice.  When you installed grub to the USB hdd, if you had switched to compatibilty mode, you should have specified /dev/sdb instead of the sdb1 partition, but in UEFI mode -- I'm not sure.  Within the live media installer, just using sdb never worked for me on a UEFI machine, but even using /dev/sdb1 fails sometime, with the bootloader being put onto the sda's (missing now) EFI partition.  Anyway, looks like you got to a successful Ubuntu boot.
  Laptops change so fast, it's hard to know which are compatible.  Many of the compatibility lists are out of date.  I use linlap.com to check on laptops.
  update-grub just looks at the mounted disks, and rewrites the grub.cfg file in /boot/grub to  allow you to chose which kernel to boot.
So did you stick with UEFI mode or switch to compatibility mode?

---

### Post by grahammechanical on 2015-07-04
Do you have an operating system on sdb? It is not clear that you do have one there.

Grub looks for its configuration file grub.cfg at /boot/grub/grub.cfg. To create grub.cfg we run sudo update-grub and that script creates grub.cfg from several scripts in /etc/grub.d/. We are not allowed to edit grub.cfg but we can edit those scripts in /etc/grub.d/. And so make changes to the Grub boot menu that way. I am just explaining how Grub works.

So, I am wondering if those files exist in sdb and if they do not then that coluld be why Grub is talking about embedding and cross-install.

Regards.

---

### Post by Dennis N on 2015-07-04
> **oldefoxx said:**
> I customarily put a Ubuntu install on my USB HDD as a fallback if I can't boot from my internal primary drive.  This has never been a problem before.
But now all of a sudden, Grub2 has these complaints:
```

sudo grub-install /dev/sdb1
Installing for i386-pc platform.
grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: error: embedding is not possible, but this is required for cross-disk install.

```
The USB HDD is formatted ext4, so it's in the same family, but what is this about a cross-disk install?  True, I am doing this from /dsv/sda1, but I just want a basic boot capability on the USB HDD, not a case where it sees the root (/) as being on /sdev/sda1 when I boot from /dev/sdb1/  Can I still get this done with Grub2?

You have a basic error with **sudo grub-install /dev/sdb1**:
With this command, you are installing grub to a partition (sdb1). It should be to the MBR (sdb) to be bootable.
And if you are doing this from an OS on some partition of sda as you say, that might account for the message about a "cross-disk" install attempt, as grub always boots to the os you install from.

---

### Post by oldfred on 2015-07-05
I do not know who suggested turning off UUIDs in grub, but that almost always is a terrible idea.
The reason grub & Linux switched years ago from device like /dev/sda to UUID is that device changes.

Most of my systems insert flash drive somewhere else. My older system with many drives would see flash drive as sde when plugged in, but sdb when rebooted. And then my boot from sdc is really a boot from sdd. But with UUID that is not an issue. If I had UUID off, then I would not have been able to boot without manually editing grub on boot.

---

### Post by oldefoxx on 2015-07-06
My old laptop stopped booting up today, I am using Firefox off the Boot-Repair disk to catch up on this thread while it works on fixing the boot process on the laptop I am using.

Not sure what the right answer is, but kow that Grib2 id not keeping up with what I want done:  If I don't have the USB HDD drive attached, I want the option to choose between sda1, sda2, and sda3.,
With the usb hdd attached, I want the boot process to rever ti it, show me the same three partition shoices, but append sdb1 below them.  This is just in case I can't boot from sda at all.

Nice to know that I need to be doing grub-install /dev/sda and grub-install /dev/sdb.  I will do that from now on.

When Grub2 give you a warning like that, does it mean it failed to install, or that it jjust didn't complete that step?  I get the impression that it failed to install, but I am not  sure.

As to doing update-grub, where does that end up at?   I checked, and the --help  showed no options for directing its actions to any particular drive or partition.  It could be that it only acts with the internal drive, which would really limit its usefulness in dealing with a backup on a USN HDD or another internal partition.

Yes, I installed Ubuntu 14.04 to the USB HDD right after reformatting it as two ext4 partitiona and a swap partition.  I keep it up to date, if I can boot to it.

> 
Grub looks for its configuration file grub.cfg at /boot/grub/grub.cfg. To create grub.cfg we run sudo update-grub and that script creates grub.cfg from several scripts in /etc/grub.d/. We are not allowed to edit grub.cfg but we can edit those scripts in /etc/grub.d/. And so make changes to the Grub boot menu that way. I am just explaining how Grub works.

So, I am wondering if those files exist in sdb and if they do not then that coluld be why Grub is talking about embedding and cross-install.


I haven't messed with the /cfg file. and the only change I made to /etc/default/grub was to uncomment the line about UUIDs.  I personally donGrub looks for its configuration file grub.cfg at /boot/grub/grub.cfg. To create grub.cfg we run sudo update-grub and that script creates grub.cfg from several scripts in /etc/grub.d/. We are not allowed to edit grub.cfg but we can edit those scripts in /etc/grub.d/. And so make changes to the Grub boot menu that way. I am just explaining how Grub works.

So, I am wondering if those files exist in sdb and if they do not then that coluld be why Grub is talking about embedding and cross-install.
[/QUOTE]

I've made no changes to the procuded Grub files, and I haver only looked at the .cfg file (It's a monster), and the one change I did make was to .etc/default/grub where I removed the "#" from before the line about disabling Gru'b's use of UUIDs.  I don't see UUIDs as anything but a hinderance if you are trying to set up wo or more PCs to act as much like each other as possible, with one USB HDD to act as a go-between.  I could just mimic the HDD UUID's on each, or get off using UUIDs altogether.

---

### Post by oldfred on 2015-07-06
UUID are unique, so no issue between sda & sdb.

If you have two installs of Ubuntu on different drives, you always install grub to the second drive. You can do that only with the Something Else install option. Then if second drive is external you can set BIOS to boot external first and it will normally boot that drive. But if external not plugged in then it boots second choice in BIOS which should be internal drive.

Post this:
       sudo blkid -c /dev/null -o list

If you did not orginally install grub to sdb, it may be remembering to reinstall to original location. You can check & update if needed:
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by oldefoxx on 2015-07-06
Thanks for the reply and info.  I will follow up later.  Boot-Repair ran for hours with no gain that I could see, so I shut down and just went ahead and reinstalled Ubuntu 14.04 to sda1 and sda2.  The old install to sda1 was seeing mounted drives under /media/[username] of sda1  sda21  sda3  storage  and usb-ext4.  The last two correspond to sdb2 and sdb1, respectively.

 I don't know how in the world sda2 suddenly became sda21, and it was showing up as sda2 in the GUI, so I figured (or hoped) a reinstall would fix that.  The reinstall of Ubuntu 14.04 on sda2 was because update-grub no longer found a boot image on sda2.

The reinstall of the OS on sda1 ended with a reported error when the installer tried to put back some of the packages, updates or additions.  I mean it finished okay, but warned that some of the packages would have to be manually installed.  That's expected anyway, as I never find a reinstall that comes back with everything put back in place.  Nothing ever is.

Reinstall on sda2 was to deal with whatever screwup that was hiding the previous OS install.  After I finished, I found nothing in any of the /home/[username] folders.  I can deal with that, as I keep extra copies of everything on storage.  In fact I am using storage as a merge point for everything I have going on on all three OS partitions and the one OS partition I've set up on the new laptop.

I used the new laptop for my nightly task last night as my old laptop was really tied up with Boot-Repair.  The new laptop really put the spurs to the task, cutting the time required way down.  A big savings was just having 3x the RAM, so that it did not have to depend on the swap partition, which always means lots more time for seeks, reads and writes when you push the PC too hard as to what you want it to be doing.

I just stopped by here to see what progress has taken place.  Very pleased to see and read the info being offered.  But I'm actually looking elsewhere for posted instructions on how to set a new cursor theme and make it work everywhere.  I used apt-get to install dconf-tools, then used dconf-editor to set a new cursor theme (DMZ-Black) and size (48).  But after logging out and back in, I still have a small white mouse cursor.  So contrary to some other's postings, I guess I still have to do it the manual command line way.  Unfortunately, the steps that worked before are buried in several different threads and posts, and nobody took me up on my idea to judt get it all together in one thread and in one post, because honestly, in the wild scramble before, it did not stick in my mind as to whwn any given step made a difference.

I know it took a variable assifnment, which was CURSOR= and the desired cursor theme folder name right after.  It too a update-alternatives line command using $CURSOR, and a gsettings command.  You also had to set the x-cursor size and x-cursor theme, and you had to create a cursor.theme file in the designated cursor theme folder (if one is not there already).  You have to deal with !/.Xresources (or eliminate it), and set a scaling factor (from 1 to 3, with 24 eq 1, 32 eq 1.35, 48 eq 2, 64 eq 2.65, and 96 eq 3, (I think that is about right).  In other words:
normal (default) = 1.0 eg 24
medium = 1.35 eg 32
large = 2 eg 48
huge = 2.65 eg 64
gigantic = 3.0 eg 96
Or to show this a a sliding scale:
```

-----------------------24------32--------------48--------------64------------------------------96
-----------------------1.0-----1.35------------2.0-------------2.65----------------------------3.0

```
Looking at the scale, you can see a natural progression here, and that 36 would be the midpoint between 24 and 48, not 32.  But 32 is 1/3rds the way to 96, and 64 is twice that, so 64 is 2/3rds the way to 96.  And if you are going to count by 24's, then you are missing a step, because it should go 24, 48, 72, then 96.   The scale factors for 32 and 62 are a bit off, but we can assume that by experimenting, someone decided that the scale factors of 1.33333 and 2.66666 for 32 and 64 should be adjusted a bit.

My old laptop is booting again, and I am just trying to get things back as I had them. Once I get cursors set right for sda2, I will then have it, and much more, to do for sda1.  So I might not be back on this thread for a few days.

If you study the above scale a bit, you will see it is not quite linear.   Were it linear, 48 would be twice 24 (and it is, as 2,0 is twice 1.0), but 96 is not twice 48 (it would have to be 4.0, not 3.0 as shown, but 3.0 is the limit allowed).  How they juggle this in doing the scale factor is not apparent.

Oh yeah, you have to set the /usr/share/icons/default as well.  I wish it were all in one place, but like trying to deal with Grub2 issues, it's scattered all over.

An aggrevation of trying to merge folders and files accross partitions or eith external storage is rhat you can't do it via the GUI (can't group select folders and files, don't have the right permissions, or will overwrite the same file if it already exists and is a newer version).  Having to use the terminal mode ahd "cp", you can force an overwite, repeat theoughout a folder, and/or
keep folder and file permissions, but you can't automatically skip if the exact same file is already there or if the target file is newer than the source file.  For those few things, I miss some of the features of Windows.

---

