---
title: "usb install BOOTMGR missing"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by kinunshele on 2012-01-05
Hi all

Trying to install Ubuntu Studio 11.04 32 bit as a dual boot alongside dowsXP on an Advent 4213 netbook from a usb stick (it has no optical drive). I resized the main partition on the netbook with partition wizard, leaving an unallocated partition on the C drive of 60Gb, intended for the ubuntu OS - this seemed to go well enough with everything intact. 

Downloaded LiLi USB Creator and set up the ISO image on it as per instructions: []("https://help.ubuntu.com/community/Installation/FromUSBStick")

The usb stick is a 16Gb Sandisk model, FAT32 formatted and doesn't have the U3 Launchpad.

I've set the 1st boot drive in the netbook BIOS as the sandisk usb drive, but every time I power up I get the 'BOOTMGR missing, press any key to continue' message. I feel I have tried to RDFM(!) in detail, and am spending far too long doing this when I should be working - any ideas please would be much appreciated.

Suspect something to do with 'grub', but am now right at the limit of my experience and understanding! Have I missed something vital?

Thank you

---

### Post by Mark Phelps on 2012-01-07
I don't know about that USB creator, but I used the Universal USB Installer from PendriveLinux.com and it worked great.

---

### Post by kinunshele on 2012-01-07
Thanks Mark, i didn't see your reply before reformatting my partitions (2, one of 20Gb and one of 40Gb, formatted NTFS) and trying this again with v11.10 of Ubuntu. Still using the Lili USB bootloader, this time I get a lovely GUI to start with promising an easy peasy install alongside existing XP, then suddenly goes to the 
error: no such partition 
Grub rescue page. Searched around for info on this but I'm afraid other than figuring out that somehow grub has not been found, this is beyond my limited skills. Tried a soft boot to get into XP, but it just returned to the error page, then black screen of death, not even soft boot would work.

I did back up all the data on this machine, but as it is a netbook with no optical drive all the advice telling me to reinstall windows/ ubuntu with a cd is leaving me feeling pretty hopeless. 

I will have a go at preparing with the USB boot loader you mentioned and reading the destructions on here more carefully...

thanks again

---

### Post by Basher101 on 2012-01-07
you should keep a windows installation/recovery CD ready in case of a failed install to repair your windows bootloader via startup repair..

+1 for the universal USB installer, used it alot too and it never failed me once to date

---

### Post by kinunshele on 2012-01-07
thanks to you too basher, as i said it's a netbook so has no optical drive. Being a rebranded ECS G10IL bought from a retail outlet it has/ had 'Techguys' recovery facility built in instead. This has now died along with xp. I can still access BIOS though

BTW the failed installation read my OS as vista for some reason... unless i'm going completely insane it really was xp

---

### Post by Basher101 on 2012-01-07
> **kinunshele said:**
> thanks to you too basher, as i said it's a netbook so has no optical drive. Being a rebranded ECS G10IL bought from a retail outlet it has 'Techguys' recovery facility built in instead. This has now died along with xp. I can still access BIOS though

you can put bootable windows images on USB sticks too - [http://wiki.eeeuser.com/windowsxpusb]("http://wiki.eeeuser.com/windowsxpusb")

---

### Post by kinunshele on 2012-01-07
oh, good one basher i should have thought of that before breaking my wife's computer! given my success so far tho making an xp usb installer probably would have been an epic journey as well

steep learning curves r us at the mo

well not sure if i have the license details for xp on this little netbook anymore, but maybe i can get ubuntu joy happening eventually just as a single install, and satisfy her iphone needs with wine (i mean the emulator, although the red liquid stuff might work alongside it) and itunes....


i'm pretty sure v11.04 ubuntu studio isn't right for a small machine like the advent 4213 anyway, but apparently all newer releases of the main ubuntu OS are compatible with netbooks as well as desktops/ laptops

---

### Post by kinunshele on 2012-01-07
Thank you all for your help so far... something really weird has happened. After trying the reinstall with pendrive usb creator, i got through the install process as far as choosing 'something else' rather than dual boot or replace xp. It kept telling me that the 2 drives i had partitioned (which were listed along with intact xp drive) did not have proper root system, and to sort this out in the partition menu.

I went back several times and tried different options in the format menus but to no avail. I then gave up and quit the install process, and lo and behold, a beautiful ubuntu desktop appeared. It even allows me to access the xp drive with all the data still intact (is it obvious i'm new to this?)

There is an icon that says 'Install ubuntu' and next to that at the top of the 'finder' strip there is a hard disk icon that also says 'install ubuntu'. 

Do I need to install grub2 on what is now 70Gb of free space, after formatting it, and if so what type of file system should it have? also do i need to do this in windows (assuming i can now boot back into xp) as i'm not sure how to with the ubuntu partition window i mentioned above.

Thanks again

---

### Post by kinunshele on 2012-01-07
ok so i'm being really dim here, but basically it seems to be running ubuntu fine from the usb, but i've no idea how to get the original windows xp boot happening, or what i have to do to the 70Gb partition i made on the hard drive in order to get ubuntu installed permanently, either as a dual boot or single boot.

i can access the xp files and folders, including windows etc, from the launcher

wld rally appreciate some more advice as i feel that it's getting close now!

---

### Post by darkod on 2012-01-07
You are just running it in live mode now.

If I understood right, you created the partitions for ubuntu from windows as NTFS. Never create partitions for linux from windows, linux doesn't install on ntfs.

Start the install again, and select the something else option again. This option is for manual partitioning. The error last time was because you never specified which partitions to use for install. It can't assume.

When the list of partitions on the disks shows, select the 20GB and 40GB you created as ntfs (they are two partitions, right?), and delete them. That will become unpartitioned space.

Then in that space create a 56GB logical partition, ext4 filesystem, with mount point /. That will be the system partition.
In the remaining 4GB create a swap area partition, also logical. That doesn't have a mount point.

That should be it. At the bottom of the windows you have a drop down box where to install the bootloader grub2. Select the same disk where you are installing ubuntu.

---

### Post by kinunshele on 2012-01-07
> **darkod said:**
> You are just running it in live mode now.

If I understood right, you created the partitions for ubuntu from windows as NTFS. Never create partitions for linux from windows, linux doesn't install on ntfs.

Start the install again, and select the something else option again. This option is for manual partitioning. The error last time was because you never specified which partitions to use for install. It can't assume.

When the list of partitions on the disks shows, select the 20GB and 40GB you created as ntfs (they are two partitions, right?), and delete them. That will become unpartitioned space.

Then in that space create a 56GB logical partition, ext4 filesystem, with mount point /. That will be the system partition.
In the remaining 4GB create a swap area partition, also logical. That doesn't have a mount point.

That should be it. At the bottom of the windows you have a drop down box where to install the bootloader grub2. Select the same disk where you are installing ubuntu.

Darkod, thank you so much... all OK now at least from Ubuntu side, i'm very grateful!

---

