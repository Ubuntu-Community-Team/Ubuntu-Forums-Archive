---
title: "Problems installing Ubuntu 10.10"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by MamaWoll on 2011-01-04
[FONT="Palatino Linotype"][SIZE="3"]Hi everybody. I new to this site and to Ubuntu. Anyway, here is my problem:
  
    I made the install disk and then went into my BIOS and changed the boot sequence and the disk loaded with no problems. I clicked "Try without installing" first to see if I would like it and that worked fine. Loaded with no problems. I got it hooked up to my wireless router with no problems....and so on. Well I decide that I wanted to install it. So I clicked on the install now icon that is on the desktop. It froze up. I restarted my computer and tried to install it from the first menu where it ask if you wasn't to try it or install it. Same thing. I thought maybe it was the disk. So I made another one. Same thing. I just can not get it to install. Can someone please help? I am currently running Vista and I would like to run them side by side until I become more familiar with Ubuntu. Then I want to uninstall Vista and install Windows 7 and  run that beside Ubuntu. [/SIZE][/FONT]

---

### Post by dino99 on 2011-01-04
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Rubi1200 on 2011-01-04
Hi and welcome to the forums :-)

Stop whatever you are doing and do not continue trying to install.

There are known issues with the 10.10 installer which might end up destroying your Windows installation.

Start the LiveCD again and choose to try NOT install.

At the desktop go to Applications > Accessories > Terminal

Run this command, copy/paste from the terminal and post the output back here:
```
sudo parted -l
```
(lowercase L not 1)

Thanks.

---

### Post by Bucky Ball on 2011-01-04
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Stop whatever you are doing and do not continue trying to install.

There are known issues with the 10.10 installer which might end up destroying your Windows installation.

Start the LiveCD again and choose to try NOT install.

At the desktop go to Applications > Accessories > Terminal

Run this command, copy/paste from the terminal and post the output back here:
```
sudo parted -l
```(lowercase L not 1)

Thanks.

+1!!! Download the 10.04 LTS ISO for now and try that. You have a good chance of screwing your system and wiping Windows if you persevere with 10.10.

Good call, Rubi (once again).

Kernel in question: 2.6.35-24. It has major probs for now and that is the latest 10.10 kernel. To be avoided.

---

### Post by johncc on 2011-01-04
> **dino99 said:**
> [http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Not a very helpful posting to someone if they are new to Linux IMO.  (The OP didn't say specifically new to Linux, but...)

MamaWoll, that is indeed strange that it would boot fine in "Try" mode ("Live CD"), but then have problem to install.

When it froze up had the screen changed at all from the one where you clicked the button to Install?  If so, can you described what it looked like prior to freezing?  Or do you mean literally that you clicked "Install" and nothing whatsoever happened.

John

---

### Post by Bucky Ball on 2011-01-04
Johncc: This is a known issue!!! There are bug reports and lots of sorry tales if you care to look. Avoid 10.10, kernel 2.6.35-24 for now. If OP perseveres there is every chance they will lose their Windows install. ;)

---

### Post by ppv on 2011-01-04
You could try use a USB thumb drive if you have one to create a bootable USB stick and then use that for installing. You could use unetbootin to create a USB stick for installation. This is incase the disc drive is having problems.

---

### Post by Bucky Ball on 2011-01-04
> **MamaWoll said:**
> [FONT=Palatino Linotype][SIZE=3]Hi everybody. I new to this site and to Ubuntu. Anyway, here is my problem:
  
    I made the install disk and then went into my BIOS and changed the boot sequence and **the disk loaded with no problems.** I clicked "Try without installing" first to see if I would like it and that worked fine. **Loaded with no problems.** [/SIZE][/FONT]

ppv: This post indicates there is nothing wrong with optical drive.

---

### Post by johncc on 2011-01-04
> **Bucky Ball said:**
> Johncc: This is a known issue!!! There are bug reports and lots of sorry tales if you care to look. Avoid 10.10, kernel 2.6.35-24 for now. If OP perseveres there is every chance they will lose their Windows install. ;)

Ok, sorry, I was just referring to the instructions to the (perhaps newbie) OP to:

> here is how to install:

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

---

### Post by MamaWoll on 2011-01-04
> **johncc said:**
> Not a very helpful posting to someone if they are new to Linux IMO.  (The OP didn't say specifically new to Linux, but...)

MamaWoll, that is indeed strange that it would boot fine in "Try" mode ("Live CD"), but then have problem to install.

When it froze up had the screen changed at all from the one where you clicked the button to Install?  If so, can you described what it looked like prior to freezing?  Or do you mean literally that you clicked "Install" and nothing whatsoever happened.

John




The screen that pops up says Preparing to install Ubuntu. then says:
I need 2.6GB drive space.Green check.
Plugged into a power source? Green check
Connected to the Internet? Green check.

Then I click install and it just stays on that screen forever.

---

### Post by Bucky Ball on 2011-01-04
Cool, sorry john, exceptional circumstances with this particular kernel.

Your advice would otherwise be pretty good.

---

### Post by Bucky Ball on 2011-01-04
:confused: Posted in error.

---

### Post by ppv on 2011-01-04
> **Bucky Ball said:**
> ppv: This post indicates there is nothing wrong with optical drive.

Yeah.....thats true...but you never know if those specific sectors are bad on the disc ;-)

But that too cannot be the case here as the OP had tried another disc also.

It was just a suggestion to get the possibility of a bad disc or a bad drive out...so that the main problem would be known...as usually USB drives could be preferred to the discs for various reasons.

---

### Post by Rubi1200 on 2011-01-04
@MamaWoll
please post the output of the command I mentioned

@Bucky Ball
I don't know what issues you are referring to with the 10.10 kernel.

The problems I am talking about have to do with the new Ubiquity installer.
See here for more:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)
Both kansasnoob and Mike D have encountered posts from users whose Windows installs were wiped out.

---

### Post by Bucky Ball on 2011-01-04
> **Rubi1200 said:**
> 
@Bucky Ball
I don't know what issues you are referring to with the 10.10 kernel.

The problems I am talking about have to do with the new Ubiquity installer.
See here for more:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)
Both kansasnoob and Mike D have encountered posts from users whose Windows installs were wiped out.

Well, if you have a Broadcom card 2.6.35-24 will kill it. I have also encountered about three victims of the Windows wipe. Miscellaneous other issues which may or may not be attributed to that kernel. For the moment, the first two are problem enough (users running fine on 10.10 until they update the kernel to the one mentioned then things start breaking).

Minor glitch. Sure it will be sorted soon. ;)

My Toshiba Satellite Pro is running that kernel pretty well faultlessly so this is not everyone. The installer seems to be causing probs though, as you mention.

---

### Post by Bucky Ball on 2011-01-04
> **Rubi1200 said:**
> 
@Bucky Ball
I don't know what issues you are referring to with the 10.10 kernel.

The problems I am talking about have to do with the new Ubiquity installer.
See here for more:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)
Both kansasnoob and Mike D have encountered posts from users whose Windows installs were wiped out.

Well, if you have a Broadcom card 2.6.35-24 will kill it. I have also encountered about three victims of the Windows wipe. Miscellaneous other issues which may or may not be attributed to that kernel. For the moment, the first two are problem enough (users running fine on 10.10 until they update the kernel to the one mentioned then things start breaking).

Minor glitch. Sure it will be sorted soon. ;)

My Toshiba Satellite Pro is running that kernel pretty well faultlessly so this is not everyone. The installer seems to be causing probs though, as you mention. That didn't seem to be happening a week ago.

---

### Post by Bucky Ball on 2011-01-04
> **Rubi1200 said:**
> 
@Bucky Ball
I don't know what issues you are referring to with the 10.10 kernel.

The problems I am talking about have to do with the new Ubiquity installer.
See here for more:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)
Both kansasnoob and Mike D have encountered posts from users whose Windows installs were wiped out.

Well, if you have a Broadcom card 2.6.35-24 will kill it. I have also encountered about three victims of the Windows wipe. Miscellaneous other issues which may or may not be attributed to that kernel. For the moment, the first two are problem enough (users running fine on 10.10 until they update the kernel to the one mentioned then things start breaking).

Minor glitch. Sure it will be sorted soon. ;)

My Toshiba Satellite Pro is running that kernel pretty well faultlessly so this is not everyone. My wireless has always been crappy with 10.10 though. The installer seems to be causing probs just recently, as you mention. That didn't seem to be happening a week ago.

---

### Post by Bucky Ball on 2011-01-04
> **Rubi1200 said:**
> 
@Bucky Ball
I don't know what issues you are referring to with the 10.10 kernel.

The problems I am talking about have to do with the new Ubiquity installer.
See here for more:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)
Both kansasnoob and Mike D have encountered posts from users whose Windows installs were wiped out.

Well, if you have a Broadcom card 2.6.35-24 will kill it. I have also  encountered about three victims of the Windows wipe. Miscellaneous other  issues which may or may not be attributed to that kernel. For the  moment, the first two are problem enough (users running fine on 10.10  until they update the kernel to the one mentioned then things start  breaking).

I would be using 10.04 LTS myself except that kernel won't run on my machine. After hours of trying and researching I discovered this was the one to use. :)

Minor glitch. Sure it will be sorted soon. ;)

My Toshiba Satellite Pro is running that kernel pretty well faultlessly  so this is not everyone. My wireless has always been crappy with 10.10  though. The installer seems to be causing probs just recently, as you  mention. That didn't seem to be happening a week ago.

---

### Post by MamaWoll on 2011-01-04
> **Rubi1200 said:**
> @MamaWoll
please post the output of the command I mentioned

@Bucky Ball
I don't know what issues you are referring to with the 10.10 kernel.

The problems I am talking about have to do with the new Ubiquity installer.
See here for more:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)
Both kansasnoob and Mike D have encountered posts from users whose Windows installs were wiped out.





ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD1600BEVT-7 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary  fat16        diag
 2      41.9MB  15.8GB  15.7GB  primary  ntfs
 3      15.8GB  160GB   144GB   primary  ntfs         boot


Model: Ut165 USB2FlashStorage (scsi)
Disk /dev/sdc: 4043MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type      File system  Flags
 1      512B   4043MB  4043MB  extended               boot
 5      1024B  4043MB  4043MB  logical   fat32        lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$

---

### Post by Rubi1200 on 2011-01-04
What I see here is a 160GB drive with 3 primary partitions. I assume this is an internal drive.

There is also a flash drive which I assume you are using for backup/storage.

Is this all correct so far?

Where did you want to try and install Ubuntu?

You need to prepare the partitions first from within Windows using the built-in Disk Management tools to shrink the partitions.

First, though, you need to make backups of all important data.

You also need to defragment the drives at least twice before starting.

If you don't have a Windows installation/recovery disk, I suggest you get hold of one just in case.

Only once you have defragmented and booted Windows a couple of times to make sure everything is okay after resizing would it be reasonably safe to continue with installing Ubuntu.

And, to be honest, I recommend you download and install version 10.04 not 10.10

Firstly, because of the issues we mentioned before, and, secondly, because it has support with updates until 2013.

If you have any questions, feel free to ask.

---

### Post by MamaWoll on 2011-01-04
> **Rubi1200 said:**
> What I see here is a 160GB drive with 3 primary partitions. I assume this is an internal drive.

There is also a flash drive which I assume you are using for backup/storage.

Is this all correct so far?

Where did you want to try and install Ubuntu?

You need to prepare the partitions first from within Windows using the built-in Disk Management tools to shrink the partitions.

First, though, you need to make backups of all important data.

You also need to defragment the drives at least twice before starting.

If you don't have a Windows installation/recovery disk, I suggest you get hold of one just in case.

Only once you have defragmented and booted Windows a couple of times to make sure everything is okay after resizing would it be reasonably safe to continue with installing Ubuntu.

And, to be honest, I recommend you download and install version 10.04 not 10.10

Firstly, because of the issues we mentioned before, and, secondly, because it has support with updates until 2013.

If you have any questions, feel free to ask.



Yeah, I'm in the process of making a disk with 10.04 on it now. That is just way too much for me to do trying to install 10.10. I really don't want to screw anything up on my laptop. I need it for work. Thanks for the help though and for suggesting 10.04. How much different is the 10.04 compared to the 10.10?

---

### Post by Rubi1200 on 2011-01-04
Don't forget you can only have 4 primary partitions. I suggest you shrink the largest partition (C ?) and make space there for Ubuntu. About 20GB should be more than sufficient.

10.04 v. 10.10?

To be honest, not much difference other than some packages were updated, some replaced.

Read the release notes for both:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

---

### Post by MamaWoll on 2011-01-04
I'm having the same problem with the 10.04. It gets to 3 of 7 in the installation and stops. WTF? :confused:

---

