---
title: "Transfering files from NTFS to ext3/ext4."
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by iTheBadGuy on 2009-12-21
I have both Ubuntu Karmic & Jaunty CD's. I had Jaunty installed a while back, now i want Ubuntu back. So i decided to install Ubuntu on my 120GB SATA drive. I have 3 HDDs one of 40GB (Windows Drive) one of 200GB (Where i keep all my stuff) and the empty 120GB SATA drive. 

I'm going to partition the 120GB for the home folder & the OS, but I would like to have access to my 200GB drive, which is formatted in NTFS. Is it possible to access the 200GB HDD without having to format it into ext3/4?. If not, then is there a way i can somehow transfer all the data on the 200GB drive to the 120GB drive after Ubuntu is installed?.

I've only used up about 15GB in the 200GB drive. I don't have external drives, and i don't have a USB stick to pass all the data from. I also don't have DvD's to burn all the files to.

Also, when i had Jaunty installed everything was awesome. After i installed Karmic it told me the 120GB SATA drive had some bad sectors and i had to back-up and replace the drive ASAP. Do i really have to? i mean, Jaunty never gave me any problems like this..

The reason why i want to move the data from one drive to the other is: I want to use Ubuntu as my default OS. I had it in the past and loved it. I only went back to windows because of Photoshop. But i found a way to install it with WINE. The other ways i tried didn't work. This one seems to do the trick.

Any methods that might help me with this?. By the way, do you recommend installing Jaunty or Karmic?, because i was kinda skeptic after the whole "Replace the drive because of bad sectors" - I don't have this problems with Jaunty or Windows.

Thanks and sorry for the long post.

EDIT:

I just found this: [http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows) It's about mounting the NTFS partition(drive too(?)). Is this what i need? to just "mount" the drive using the tut in the link?. It also said something about writing is experimental and I should continue at my own risk. Reading is fine tho. So if i move files from one disk to the other (NTFS to ext3/4) I might have problems?.

---

### Post by lidex on 2009-12-21
You can access ntfs filesystems from ubuntu. Just make sure you have these packages installed: (Run this command in a terminal)

```
sudo apt-get install ntfsprogs ntfs-config libntfs10 ntfs-3g libntfs-3g49
```

This is on Jaunty

---

### Post by iTheBadGuy on 2009-12-21
And on Karmic? I'm thinking of just switching to EXT4 when i install Karmic(If I'm installing Karmic). I hear it's faster. What's your opinion on EXT4?

---

### Post by lidex on 2009-12-21
Should work on Karmic as well - just not sure of the package names. Ext4 sounds good on paper. I'm just not ready to jump Jaunty yet. I may wait for Lucid and at that point I'll backup my data, reformat and do a clean install.

---

### Post by vanadium on 2009-12-21
There is no need to install anything: ntfs is fully supported by default since more than a year now.

Concerning ext4, it is the default file system of Ubuntu 9.10, so I trust it is reliably enough for me to use it.

---

### Post by lidex on 2009-12-21
> There is no need to install anything: ntfs is fully supported by default since more than a year now.

Thanks for that info. Wasn't sure of the default.

---

### Post by SecretCode on 2009-12-21
For a new install I'd choose Karmic, but my main system is still on Jaunty.

The disk warnings are probably something to consider - I've noticed the Karmic Disk Utility (Palimpsest) spots (or monitors) SMART errors that Jaunty/Windows never reported. The disk is really reporting those errors. But how serious they are depends on the details, I suppose.

---

### Post by iTheBadGuy on 2009-12-21
Well, i decided to install Karmic. And yes the NTFS drive appeared in my Places. I mounted it without any problems and transfered all my data form the NTFC to the EXT4 (I also decided to go with the default of Karmic EXT4). Everything worked out great. No problems what-so-ever. Hope everything continues this smooth.

As for the drive with bad sectors.. It says:

Current Pending Sector Count:
"Number of sectors waiting to be remapped. If the sector waiting to be remapped is subsequently written or read successfully, this value is decreased and the sector is not remapped. Read errors on the sector will not remap the sector, it will only be remapped on a failed write attempt."

Warning:
Normalized: 1
Worst: 1
Threshold: 0
Value: -2 sectors.

Type: Failure is a sign of old age (Old Age).

Ok, so should i be concerned? This made no sense to me =/. I told it to not notify me again, but this is the "/" & the "/home" drive...

---

### Post by SecretCode on 2009-12-21
I don't know enough about hard drives to say ... maybe someone else can advise

---

