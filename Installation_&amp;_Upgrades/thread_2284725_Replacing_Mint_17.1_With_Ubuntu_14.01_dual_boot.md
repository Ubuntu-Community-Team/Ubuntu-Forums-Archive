---
title: "Replacing Mint 17.1 With Ubuntu 14.01 dual boot"
date: 2015-07-01
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2015-07-01
Hello everyone, quick question regarding replacing Mint with Ubuntu

I have gotten use to Ubuntu and I would like it to be  my primary desktop  distribution but I currently have one machine Dual booting Mint and Windows 8.1, what would be the best way to install Ubuntu on this machine and replace Linx Mint?

You see I don't want to lose any allocated space when I try to Install Ubuntu on this same machine.

When I first started Using Ubuntu I had a few different versions of Linux which one I installed on this same machine after trying a few distribution I was not happy with it so I removed it and lost about 50 gigabyte of space when it was removed

 So now I have Mint on a partition for about 150-gigabyte and if I remove Linux mint I don't want to loose that space.

thanks for any help on this

---

### Post by oldfred on 2015-07-01
Only use Something Else install option which has no issues.
And best to have full backup of Windows. You should have that anyway, but whenever making major system changes, best to have it current.

Any auto install option may have this reinstall bug which erases entire drive.
       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I do prefer smaller system partition (/ or root) of 25GB and use rest as data partition or /home or both. Usually best not to write into Windows system partition, but set it as read only to avoid issues. And then use a shared NTFS data partition. But Windows fast start-up uses hibernation and also keeps other NTFS data partitions mounted and can cause issues. So you must have fast start-up off if dual booting.

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by RobGoss on 2015-07-01
Hello  Fred, Question? So what your saying is there's no way for me to gain that allocated space back to my Windows hard drive with out messing something   up with Windows.

What about just removing Mint and applying that 150GB back to my system drive

---

### Post by oldfred on 2015-07-01
You can do anything you want.
Just use Windows tools for Windows changes and Linux tools for Linux changes to avoid issues. 

Do not delete any partition that has boot files unless you have changed boot to work directly for other system first. 
And/or have current version repair/live installer CD or flash drive for every system you have installed. You cannot fix most Windows issues from Linux, so best to have Windows repair flash drive.

---

### Post by RobGoss on 2015-07-01
Sounds good Fred thanks a bunch

---

