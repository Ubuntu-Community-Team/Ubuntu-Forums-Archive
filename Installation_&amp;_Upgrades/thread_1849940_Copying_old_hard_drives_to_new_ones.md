---
title: "Copying old hard drives to new ones"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by therebemoose on 2011-09-25
I am a new Ubuntu user, trying to fix some things I feel I goofed on, like using the beta "Oneiric Ocelot" as my version of Ubuntu to learn with. I have since mounted a smaller hard drive and installed Lucid instead, and have found myself much more pleased with the lack of crashing and functionality. I would like to move this version, changes and all, to my newer, larger hard drive, erasing the Oneiric version entirely, but keeping everything I have installed/modified with Lucid, but am hesitant now to make a move without some good insight.

I found a line of code at a site called 'life hacker' that claims it is this easy to copy my entire OS and data from one hard drive to a new larger hard drive; a single command in terminal:

[FONT="Courier New"]*dd if=/dev/sda of=/dev/sdb*[/FONT]

I am still a bit new to Linux in general, is it really this easy? Should I format the new drive somehow beforehand? As far as I can tell, if it is this easy, the only changes I would need to make are reformat the newer drive and instead change the code to:

[FONT="Courier New"]*dd if=/dev/sdb of=/dev/sda*[/FONT]

as the second drive contains what I would like to keep. I would be most appreciative of a step-by-step guide to accomplishing this. I can try and fetch any specs for those willing to help should it be necessary. Thanks in advance!


Source:
[http://lifehacker.com/5517688/how-to-upgrade-your-tiny-hard-drive-to-a-spacious-new-one-and-keep-your-data-intact](http://lifehacker.com/5517688/how-to-upgrade-your-tiny-hard-drive-to-a-spacious-new-one-and-keep-your-data-intact)

---

### Post by ld114 on 2011-09-25
I am also quite new to Ubuntu (and don't know about the commands you list), so what follows may need to be corroborated by others. I have used a live disk with "Clonezilla" to make an image of my Ubuntu hard drive in preparation for installing a new drive (the current one has 27 bad sectors and may fail soon - so I have a new disk on the way). I have successfully made an image on an external drive, then re-formatted the internal hard drive, and then copied the image on the external drive back on to the internal hard drive.

I am hoping that when the new hard drive is installed, I will be able to copy the image from the old drive on to the new one - though I have kept notes of most of my Ubuntu set up process just in case having a different physical disk causes problems.

So you might investigate Clonezilla.

---

### Post by SecretCode on 2011-09-25
Can you install both hard drives at once? If so your best plan would be keep the Lucid install as is and install the larger hard drive as well, mounting it as /home.

Otherwise, yes you can use _dd_ as suggested in that article (one of the drives will have to be attached externally) but you have to do this from a live CD, you can't boot from either of the drives you're copying. 

And you will have to resize the filesystem afterwards, using GParted also run from a live CD. 

Step by step instructions not a problem, but it depends on the above question.

---

### Post by therebemoose on 2011-09-25
Both hard drives can be installed at the same time, yes. Would it be better to leave the version I have where it is and just wipe the other drive perhaps? the smaller, older drive (the one with the version I want to keep) is a tiny 80Gb compared to the new one, which is 1Tb, and also contains the Oneiric version of Ubuntu, and is partitioned and formated for it. I just want to get rid of it and make room for Natty, which actually works.

Also, just to showcase how new I am to Linux, I thought I was running Lucid, but I actually checked and I am actually running 11.04 natty. To say the least, I am a bit embarrassed.

---

### Post by OpenJacob on 2011-09-25
You can learn more dd commands here:
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by tgalati4 on 2011-09-26
You can also use the simple cp command:

sudo cp /dev/sda /dev/sdb

This works provided sdb is equal or bigger in size.  Use

gksudo gparted 

to recapture the extra space on the bigger, second drive.

You might have to change block ID's (UUID's) of the bootable hard disk using the command: blkid

tgalati4@tpad-Gloria7 ~ $ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="48bdac78-8834-437e-be7d-333af309a27d" TYPE="ext4" 
/dev/sda3: UUID="8c308507-8a38-4070-871f-d6e92f1fbb8d" TYPE="swap" 

Take note of the UUID for the second drive and edit your grub boot entry to reflect the new, bootable, drive.

---

### Post by therebemoose on 2011-09-26
I appreciate the help everyone, so far I have just opted to format my larger drive and use it as storage, and just run my system off the 80Gb drive. However, at boot, I have even more options with GRUB than I did before the format. Did I do something crazy, or is this normal? Sorry if this is getting off topic.

---

### Post by SecretCode on 2011-09-27
What do the options look like? Extra kernel versions or different OSes on different partitions?

---

### Post by therebemoose on 2011-09-27
They are as follows:

Ubuntu with Linux 2.6.38-11-generic
Ubuntu with Linux 2.6.38-11-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Ubuntu with Linux 3.0.0.11-generic (on /dev/sda1)
Ubuntu with Linux 3.0.0.11-generic (recovery mode) (on /dev/sda1)
Ubuntu with Linux 3.0.0.9-generic (on /dev/sda1)
Ubuntu with Linux 3.0.0.9-generic (recovery mode) (on /dev/sda1)
Ubuntu with Linux 2.6.38-11-generic (on /dev/sda1)
Ubuntu with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda1)

I feel like I didn't clean something up properly, or somehow my computer is being haunted by my mistakes...

---

### Post by oldfred on 2011-09-27
The kernel versions shown as 3.0.0.xx are from beta "Oneiric Ocelot". Do you still have that on your 1TB drive?

As the system gets updated you get new kernels. You have to manually houseclean.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Since you have a large drive, I suggest you keep the Oneiric partition or the install on that drive.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by therebemoose on 2011-09-27
Ubuntu with Linux 2.6.38-11-generic
Ubuntu with Linux 2.6.38-11-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
[I]Ubuntu with Linux 3.0.0.11-generic (on /dev/sda1)
Ubuntu with Linux 3.0.0.11-generic (recovery mode) (on /dev/sda1)
Ubuntu with Linux 3.0.0.9-generic (on /dev/sda1)
Ubuntu with Linux 3.0.0.9-generic (recovery mode) (on /dev/sda1)
Ubuntu with Linux 2.6.38-11-generic (on /dev/sda1)
Ubuntu with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda1)[/I]

When I would try to boot the italicized items, I would get something along the lines of "error: drive does not exist". When searching for outdated/unwanted kernels with Synaptic, I only found the current kernel I am using (Natty). The Grub Customizer did help to clean up my Grub boot menu, but I think all I did was hide the stuff I want to get rid of (all of the italics). Is there something I am missing?

I understand the benefits of rotating through new and old versions of any OS, but I think I goofed somewhere in the upgrade process, as Oneiric would constantly have crashing utilities, nautilus and daemon among them. I would prefer to wait for something stable and reliable and go from there, I am still fairly unequipped to handle problems with Ubuntu.

As for Knoppix, I am not sure I understand the benefit. I can see it in some way streamlines installing/removing hard drives, but I am not sure how it applies to what I am doing. I am still interested in moving all data from my 80G drive to the 1T drive, and perhaps installing another clean version of Ubuntu on the 80G drive as a fallback plan should things get really hairy.

All said, thank you very much for the help!

---

### Post by oldfred on 2011-09-27
I was not suggestion Knoppix as the advantages work with Ubuntu on the 1TB also, just a bit larger partition.

If you do not have the install. Then the os-prober will update and not find it.
sudo update-grub

You can do a clean install to the 1TB drive and use rsync to copy /home over. You can list all installed apps in your current install and reinstall to the new install. If a system setting or two are missing then you can go back in your old install and see what it was.

My backup procedure is just so I can have my stuff and settings, but no system as I will do a clean install.
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

Oldfred's list of stuff to backup May 2011, I used above rsync scripts and added a few things:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

