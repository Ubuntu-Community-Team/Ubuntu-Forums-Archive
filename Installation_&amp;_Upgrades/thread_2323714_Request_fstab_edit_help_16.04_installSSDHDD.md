---
title: "Request fstab edit help: 16.04 install/SSD/HDD:"
date: 2016-05-07
forum: Installation &amp; Upgrades
---

### Post by m9ke2 on 2016-05-07
[COLOR=#000000]I have a fresh xubuntu 16.04 install on a newly built computer I am booting from an SSD, but I don't think the new install handled  my second disk (conventional HDD) and CD device as I wanted.  The computer starts and boots fine.

[/COLOR][COLOR=#000000]I would greatly appreciate some help in figuring this out![/COLOR][COLOR=#000000].

[/COLOR][COLOR=#000000]Relevant system info:[/COLOR]
[COLOR=#000000]==============[/COLOR]
[COLOR=#000000]New Xubuntu install with all current updates installed.[/COLOR]
[COLOR=#000000]Motherboard: ASUS M5A99X EVO V2 (UEFI BIOS)
[/COLOR]16 GB RAM
[COLOR=#000000]SSD: Crucial BX-100 250 GB internal[/COLOR]
[COLOR=#000000]HDD: Western Digital 2TB internal[/COLOR]
[COLOR=#000000]CD burner: ASUS internal[/COLOR]
[COLOR=#000000]Graphics card ASUS GEForce GTX 960 (nvidia chipset)[/COLOR]

[COLOR=#000000]Config I am trying to create:
[/COLOR]1. Boot from SSD
2. Home on conventional HDD
3. Internal conventional HDD should not mount as a removable device.

Below is my fstab.  I am hoping to get some guidance in editing that fstab  to achieve 1-3 above.  I am leaving optimizing the SSD for swappiness, noatime and trim for after I can get 1-3 above in place.  

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=a8e17a42-077f-407b-92c5-84782504236a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=36C4-3FB7  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=d3554151-90ca-4cfd-828d-e86f48f749f3 none            swap    sw              0       0

```

---

### Post by Bucky Ball on 2016-05-07
Well, you'd install and put the / on a partition on the SSD, /home of the HDD. You'd choose 'Something Else' at the paritioning section of the install to do this. 

As for three, the internal drive partitions will appear in the file manager but won't mount until you click them. 

You can move your /home folder in / to its own /home partition, but as you've recently installed it is easier to simply reinstall correctly rather than incorrectly then try and patch it up post-install. (And probably a lot less frustrating and time consuming, but if you're up for a learning curve ...).

You can also just put folders like Documents, Music, Videos, etc., on the hard drive you wanted to use as /home, delete the corresponding folders in the /home folder and replace them with symlinks to the folders on the HDD, if you follow me. This is the way I would be going. Means if you install a second OS very easy to symlink that to the same data as that being used by this install. Avoids redundancy.

---

### Post by Dennis N on 2016-05-07
> **m9ke2 said:**
> [COLOR=#000000]
[COLOR=#000000]Config I am trying to create:
[/COLOR]1. Boot from SSD
2. Home on conventional HDD
3. Internal conventional HDD should not mount as a removable device.

Since you say "The computer starts and boots fine", #1 seems to be working.

As to #2, you can use the "something else" option to set up a your separate home partition on the other drive during installation. I've never done this post-install, so can't give advice on that. You are essentially moving it. OldFred suggested linking your home folders to copies on the HDD data partition. That is another way. See your previous post.

My method is to create the separate data partition on the HDD, make new folders there of my choosing, and access it all in Xubuntu with shortcuts under "Places" in the Thunar side pane. This is done post-install. Anything there can then be shared with the other OSes I have installed by just mounting it in their fstab. Example: all my music and video is on the data partition, so any OS can mount it and get to it.

As to #3, that can be done post-install - I think you said you accomplished this in your other post?

---

### Post by m9ke2 on 2016-05-07
Thanks for writing Bucky Ball.  I agree that it would be quicker to reinstall and figure out the partitioning in 'Do Something Else'.   

I actually did try that before making this fresh install but could not figure out how to make it work.

Can you suggest some specific pointers for "Do Something Else"?   If so i will reinstall following your guidance.

---

### Post by m9ke2 on 2016-05-07
Hi Dennis N!  Yes thanks to you #3 is not an issue.  And I think reinstalling using 'Do Something Else' is the way to go.  In  a previous install I did try that but did not figure it out correctly.  This is going to be an uncomplicated install meaning I am only ever going to run one OS so some of the magic that oldfred suggested is outside the scope of what i will need to do.

I think i will do a reinstall using 'Do Something Else' once i get enough education here to make it work.   I am gonna actively monitor this thread and do the reinstall when I learn enough to avoid my previous mistake.

---

### Post by Dennis N on 2016-05-07
> I think i will do a reinstall using 'Do Something Else'

Good Plan. This will also take care of requirement #3 during installation.

---

### Post by Bucky Ball on 2016-05-07
[This should give you the basic concepts]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"). I have a slightly better one somewhere but on my other machine. ;) Ask here if you need help. 

Basically, you put / somewhere on the SSD (best find out what this is before proceeding, i.e. is it sda?) and /home somewhere on the HDD (probably sdb). If you need to (if either of the disk is not blank) make a note of the names of all partitions before even booting the install media. For instance, the partition naming convention is sda is the first drive, sda1 is the first partition on the first drive. 

Also, make sure you have free space to install to before proceeding. Don't shrink the Windows partition with Linux software, us Windows software, and vice versa for resizing Linux partitions; use Linux software. 

If you're going for the method I described with the symlinks (and Dennis N reiterated) then you only need to worry about installing / to sda and, and this is very normal and rule of thumb, a /swap partition to the HDD somewhere (2Gb is fine unless you are hibernating, in which case same size or larger than the installed physical RAM).

If you go this way, you can set up the data partition on the HDD with the symlinks to it post-install. For the moment, just worry about the install, not setting up the data partition if you're using this method.

Hope that's enough to get you going. Let us know of any brickwalls you confront. Good luck. ;)

(PS: And I'm sure you've backed up any data you don't want to lose prior to launching into this. ;))

---

### Post by m9ke2 on 2016-05-07
Thank you Bucky Ball.  I will read the document you linked to and get to my install.  Leaving this thread open for now...

---

### Post by Bucky Ball on 2016-05-07
All good. ;)

---

### Post by m9ke2 on 2016-05-08
I have attached a pic of the xubuntu installer after I go to 'Something Else'
[ATTACH=CONFIG]268921[/ATTACH]
(Apologies for the pic!   I could not figure how to do a proper screen shot from within the xubuntu installer so i shot a pic of my screen with my phone).

/dev/sda = my SSD.  I want to boot from this SSD
/dev/sdb = my conventional HDD.  I want Home on this HDD.
I would like to perform this install in as simple a manner as possible.  For example, I will never want to simultaneously install any additional OS'es including other flavors of ubuntu and windows.  So I don't need to provide for that in how I do partitioning and space allocation in this install.


/dev/sda:
======
If I select /dev/sda the 'Change' button does not do anything, but the 'Change' button is active for /dev/sda1, /dev/sda2, and /dev/sda3

/dev/sdb:
======
If I select /dev/sdb the 'Change' button is inactive.   Clicking it does nothing.

I would greatly appreciate some advice for figuring out what to do in this part of the install!

---

### Post by Dennis N on 2016-05-08
You can only "change" partitions. Those are devices with the added number: sda1, sdb2, and so on. sda refers to the physical drive.

Try selecting the "free space" under sdb, then the + to add a new partition. When the partition is added, you can set it to mount as your home partition in the popup dialog.

---

### Post by Dennis N on 2016-05-08
Problems?

Besides setting a partition to mount at /home, when using the "something else" option, you also need to select one for / and one for swap. Since you are reinstalling over the existing OS, select /dev/sda2 as / and /dev/sda3 as swap. To define a partition as swap, you do that in the "use as" box and select "swap area". You can check the format boxes on the main screen. With all three (/, /home, swap) defined you are ready to continue. 

Attached is my screenshot of creating a home partition out of free space on sdb.

---

### Post by m9ke2 on 2016-05-08
Thanks Dennis N.  I selected free space under sdb and used the '+' to add a partition.  I was able to set it to mount as /home.  So that part seemed to work out fine.  Much appreciated!

Trying your suggestions regarding root and swap now...

---

### Post by Dennis N on 2016-05-08
Further clarificartions! sda2 you would define as / using the "change" button, since the partition already exists. Same for sda3. Then, since this is UEFI, you should select sda1 and after "change" select "use as" EFI system partition (but this may not be necessary, since it is already marked type EFI). I think (hope) that covers it.

---

### Post by m9ke2 on 2016-05-08
Dennis N, your suggestion regarding sda worked!  I completed the install and a look at the properties for Home showed me that it's now on my conventional HDD.

I am about to mark this thread as solved, but first i have to ask:   how did you make that screenshot from within the installer?  I tried to do that but did not figure it out.

---

### Post by Dennis N on 2016-05-08
Glad to learn you have you install successfully completed. As to the screenshot, there was really nothing preventing you from taking some during the live Xubuntu session: Menu > Accessories > Screenshot. The only difference is, in a live session you need to copy the screenshots to a flash drive before you quit or they will disappear. Enjoy your new OS!

P.S. - I actually did the complete install on that computer at the same time you did - something I had been meaning to do, so why not? Except I didn't make a separate home partition - the sdb1 partition is already a data partition for the existing OSes on there so all I have to do is have Xubuntu 16.04 mount it in its fstab and all the stuff on there is immediately available.

---

### Post by m9ke2 on 2016-05-08
Thanks to Dennis N, and everyone who participated in this thread I am up and running!  Marking Solved.

---

