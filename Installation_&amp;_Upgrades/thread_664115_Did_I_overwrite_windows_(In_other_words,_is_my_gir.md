---
title: "Did I overwrite windows? (In other words, is my girlfriend going to kill me?)"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by MikePGS on 2008-01-10
After looking into it for a bit, i decided to do a dual boot installation with Vista (which i already had) and Dapper Drake (i had the disk for it, so decided to install it instead of the latest version, with the intent to upgrade to the latest version later). I put in the cd and off of the live cd (and following the instructions of the Ubuntu Bible) i made a partition for Ubuntu (10 gigs) and logged off so the computer would restart. After telling me it needed to check the disk it went to a black screen and continued to do so for quite some time. Thinking that maybe i needed to put ubuntu on the partition i went to install it and chose the use largest free space option, again as intructed to do by the Ubuntu Bible. The installtion went fine, then i went and installed all the upgrades. I then had it restart and it went straight into Ubuntu. Since i was under the impression a screen would come up that would allow me to choose which operating system i wanted to use, i panicked a bit. I then restarted again and the same thing, though this time i hit escape to go into the menu. When in the menu, it gave me five or so different options... all Ubuntu options, Windows isn't even mentioned. I then went into System-Administration-Disks and looked at the partitions, and the largest partition listed is still the Windows NTFS file system partition. I read a little bit about the subject and it implied that GRUB needed to be configured or something, but before i go into that, is there something I can do to make sure i didn't delete windows, and my girlfriends files, which would result in her murdering me?  I tried to browse, but it said i didn't have permission. Do i need to set up a root account first? Any help would be greatly appreciated. Thanks in advance.

---

### Post by Mze on 2008-01-10
Post output of this command in the terminal:

fdisk -l

To access NTFS drive to check if all data is still there run this command:

sudo apt-get install ntfs-3g

Reboot might be required.

---

### Post by cb951303 on 2008-01-10
no need for root account or privilages to look up your ntfs drive. normally you should be able to see the NTFS but just to make sure install the "ntfs-3g" package.  also configuring grub is prettttty easy. just google for "windows grub configuration".

---

### Post by MikePGS on 2008-01-10
just type in fdisk -l in the terminal? (Sorry, i'm a complete newb :()

---

### Post by MikePGS on 2008-01-10
i typed fdisk -l in the terminal and got this

Disk /dev/sda: 1974 MB, 1974730752 bytes
243 heads, 62 sectors/track, 64 cylinders
Units = cylinders of 15066 * 2048 = 30855168 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          64     1928324    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 62) logical=(0, 1, 1)

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

---

### Post by MikePGS on 2008-01-10
> **Mze said:**
> Post output of this command in the terminal:

fdisk -l

To access NTFS drive to check if all data is still there run this command:

sudo apt-get install ntfs-3g

Reboot might be required.

I tried that and it said cannot find ntfs-3g

---

### Post by LaRoza on 2008-01-10
You used an old version of Ubuntu, which doesn't have NTFS write support built in, and it cannot resize or alter the Vista partitions because of the change in NTFS. Trying to do so, as you seem to have done, make Windows unusable. The newest version of Ubuntu, 7.10, would have worked fine.

Since you were going by the book, I would say it is time to restore with your backup disks...

---

### Post by MikePGS on 2008-01-10
> **LaRoza said:**
> You used an old version of Ubuntu, which doesn't have NTFS write support built in, and it cannot resize or alter the Vista partitions because of the change in NTFS. Trying to do so, as you seem to have done, make Windows unusable.

Since you were going by the book, I would say it is time to restore with your backup disks...

Yikes. I hope you mean the Vista disk, but I doubt it somehow. Would installing a newer version fix this, or is my information pretty much gone?

---

### Post by LaRoza on 2008-01-10
> **MikePGS said:**
> Yikes. I hope you mean the Vista disk, but I doubt it somehow. Would installing a newer version fix this, or is my information pretty much gone?

The information is probably there, just use a live disk (of Gutsy) to copy it to a safe location, a flash drive or another disk/partition.

Vista, as far as I know, is unfixable. You will have to reinstall it. If you make backups of your data, as one should always do when altering partitions, you will have lost little but time.

---

### Post by MikePGS on 2008-01-10
> **LaRoza said:**
> The information is probably there, just use a live disk (of Gutsy) to copy it to a safe location, a flash drive or another disk/partition.

whew, i sure hope it is. Is there built in software that lets me burn Iso's?

---

### Post by Mze on 2008-01-10
Try:

sudo apt-get install ntfs-config

You might have to turn on extra repositories in Synaptic, not sure though since you installed Dapper Drake.

I also think you've toasted part of your Windows partition, from the results of fdisk. doesn't look like the partitioning went well.

---

### Post by LaRoza on 2008-01-10
> **MikePGS said:**
> whew, i sure hope it is. Is there built in software that lets me burn Iso's?

Yes, in Ubuntu, no in Windows.

---

### Post by MikePGS on 2008-01-10
> **LaRoza said:**
> The information is probably there, just use a live disk (of Gutsy) to copy it to a safe location, a flash drive or another disk/partition.

Vista, as far as I know, is unfixable. You will have to reinstall it. If you make backups of your data, as one should always do when altering partitions, you will have lost little but time.

I stupidly didn't back it up, however if vista isn't fixable thats fine so long as i can get the information locked in it.

---

### Post by Mze on 2008-01-10
[NTFS support for Dapper Drake]("http://lunapark6.com/ntfs-3g-read-write-ntfs-drives-on-your-linux-box.html") : a few steps or (if cumbersome) just burn and run a Live CD as suggested by LaRoza and copy data off Vista partition.

---

### Post by MikePGS on 2008-01-10
> **Mze said:**
> [NTFS support for Dapper Drake]("http://lunapark6.com/ntfs-3g-read-write-ntfs-drives-on-your-linux-box.html") : a few steps or (if cumbersome) just burn and run a Live CD as suggested by LaRoza and copy data off Vista partition.

I just made a live cd of Gutsy and am on it atm. How do i copy off the partition from here please?

---

### Post by Mze on 2008-01-10
Click on Places >> Computer

You should see a disk icon denoting your Vista partition. 

Copy files to a USB pendrive as needed.

For dual booting Vista and UBuntu: this [tutorial]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") helped a lot of people.

---

### Post by MikePGS on 2008-01-10
> **Mze said:**
> Click on Places >> Computer

You should see a disk icon denoting your Vista partition. 

Copy files to a USB pendrive as needed.

For dual booting Vista and UBuntu: this [tutorial]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") helped a lot of people.

Jeez, now it says unable to mount partition. It says something about going into windows (which i can't do) and turning off external devices, or forcing it to open. Any idea as to how i can do that?

---

### Post by Mze on 2008-01-10
Under System >>> Administration see if you have Gnome Partition Editor and fire it up. should mount the Vista Partition.

---

### Post by MikePGS on 2008-01-10
[IMG]http://i149.photobucket.com/albums/s54/MikePGS/Screenshot.png[/IMG]

---

### Post by MikePGS on 2008-01-10
I went into partition editor and tried the check and repair option, but it didn't work. I'm going to bed now, but please give me as much advice as possible while i'm gone.

---

### Post by Mze on 2008-01-10
Looks like there was a process going on on the Vista drive that didn't complete. I guess you would have to risk the "force" option as suggest by the dialog box. Don't know what others might suggest in this instance. Will try Googling for more info. :(

---

### Post by MikePGS on 2008-01-10
> **Mze said:**
> Looks like there was a process going on on the Vista drive that didn't complete. I guess you would have to risk the "force" option as suggest by the dialog box. Don't know what others might suggest in this instance. Will try Googling for more info. :(

Yikes, this is awful. I just want to get her pictures and files off Vista. If they're gone, i might just have to leave under the cover of night.

---

### Post by Mze on 2008-01-10
Looks like you have some work to do after running a seach for the [error msg]("http://www.google.ca/search?hl=en&q=if+you+don%27t+have+Windows+then+you+can+use+the+%27force%27+option+%2Bubuntu&btnG=Google+Search&meta=") you got. 

Try a few of the links generated to see how this issue was solved.

Good luck

---

### Post by Dark_X on 2008-01-10
If you reinstall vista from a retail disc and you don't format the drive it should leave the files on the hard drive so you can access them later.  Read this: [http://news.softpedia.com/news/Vista-Windows-old-47133.shtml](http://news.softpedia.com/news/Vista-Windows-old-47133.shtml) From what I remember you don't need to be logged in to another operating system for this to work.

---

### Post by BLTicklemonster on 2008-01-10
Been nice knowin' ya, Mike.

:)

---

