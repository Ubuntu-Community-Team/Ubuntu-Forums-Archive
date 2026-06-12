---
title: "Disk Cloning Questions"
date: 2015-12-31
forum: Installation &amp; Upgrades
---

### Post by Uruz on 2015-12-31
Here's the situation:

I'm currently running entirely off of a single 1TB HDD (mono-booting 15.10), but soon will be getting a 250GB SSD.

My intention with the SSD is to dual-boot Ubuntu and Windows (done that before, it's not really the point of this thread).

Now, I want to clone my current Ubuntu installation to the new drive so I don't have to start from scratch (which I hate doing). Questions:

**1. dd or Gparted:** So, I know a system can be cloned using dd, but I also read about using Gparted to copy a partition, but that there might be other things you have to do to get it 100% functional (it wasn't very clear). Which do you think would be the better option? (obviously, Gparted is less-likely to catastrophically ruin the source data). Now, I'm moving to a smaller drive, so would dd be able to do that?
**2. Side Partitions:** My current HDD has two other partitions: a 512MB fat32 (used in booting, I suppose?), and a 3.69GB swap partition. Do these need to get copied too? I confess that there are certain glaring blind spots in my Ubuntu knowledge.
**3. Drive Preparations:** Is there anything I should do with the drive before I clone to it? i.e. Do I need to pre-partition it or will the partition table be overwritten or... again, blind spots.

Thanks for your help, everyone.

---

### Post by Elishasmantle on 2016-01-01
Hello,

Please do not take this as 100% accurate but this is my understanding.
Active Live Boot makes a trial bootable ISO file that you can copy to a USB Flash drive and use.
I believe there is an option for disk-to-image which would take your 1TB drive, copy all contents of full hdd and compress the image.
I believe, if this worked correctly, on the restore of image-to-disk to the ssd the program will recognize that you are using a smaller disk and ask if you want the program to auto-resize disk for you but to be careful, see my suggestions below.

Mondo makes a similiar : [http://www.mondorescue.org/](http://www.mondorescue.org/)

I'm pretty sure Active supports SSD drive.
mondo I am not sure about.

You mentioned DD and Gparted, but I am not sure of the full functionality of both of these utilities.
I know that you do not want to do a clone from my understanding. Cloning is sector-for-sector copy which means if copying from a 1TB drive you need a 1TB or greater to copy to.

Imaging can take the full hdd contents, skip un-used space and shrink the image down to smallest possible image. You would just want to verify that the software you use to do this supports your disk source and disk destination types.

I would do this as prep work if my purpose was what you are attempting to do ( This is to prep your drive and get your full 1TB hdd contents to below the max size of the hdd you want to migrate to) I say this because I believe this will be your safest bet for a hdd migration from a larger-to-smaller drive: 
* On your current Ubuntu install you can use Rsynch or another program and copy all your : / , /root , / var , /home etc... Rsynch you can choose / and it will copy your whole DATA contents of your whole drive to a media type you choose. ( I use mine to copy to a usb sata hdd)
1) Figure out which partitions are actually used for the Ubuntu install
2) Copy data off non-Ubuntu partitions and burn to DVD or delete, etc...
3) Delete un-needed partitions that are not part of Ubuntu install
4) Re-move any additional not often used software packages that are not needed In Ubuntu, tmp/swap files
5) Copy data off to another drive from Ubuntu install that are taking up huge amounts of hdd space ( 100GB of mp3's, movies, etc... )
6) boot from gparted dvd or usb drive and calculate your total disk space size of all the partitions. Is the total size now less than the hdd you want to migrate to?
7) If not, I believe you have to use gparted and shrink all your partitions down to minimal size and the total size must be less than your total hdd space you are migrating to.

Then, at this point I think you are ready to run the Active image disk-to-image.
You would have accomplished:
1) Shrinking the hdd down to a size that will allow you to migrate to new smaller hdd
2) All fstab/partitions will be in the size ranges needed for the smaller hdd
3) you have a Rsynch copy of all your data that in worst case scenario, you could do a full New Ubuntu install and then use Rsynch to copy over all your home dir, ETC/<files>, /VAR , etc...

Once all that was done and you were going to keep that 250GB SSD drive for a while you can use something like clonzilla for a full hdd backup and rsynch for all your files once a month or whatever schedule suits you.
I'm not familiar if there are better, easier, more dynamic ways to do Linux Back-ups at the moment.

Thank You,

Elishasmantle

---

### Post by Uruz on 2016-01-05
Okay, so I decided to go with Gparted.

I'm copied over and booting off of the SSD. My [user] folder is on an HDD and it's working just fine.

Currently, I'm working on fixing some things that got screwed up permission-wise (already fixed pulseaudio and sudo).

Two problems left:
I've got a file that's marked as executable, but Ubuntu tells me that it's not trusted or marked as executable (even though it is)
When I open a terminal, the default folder uses the long path (/media/Storage/Ubuntu Storage/[user]) instead of the short path (/home/[user])

Thanks for your help

---

