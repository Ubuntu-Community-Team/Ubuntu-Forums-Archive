---
title: "repartitioning, request advice"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by mringer on 2010-10-03
My PC is dual-boot UB8.04 and Win XP. Disk is 120GB, currently partitioned
as follows:

P1, size 10GB, ntfs, boot flag, windows  C:  drive, mounts as /windows
P2, 10GB, ext3, mounts as /
P3, 10GB, swap
P4, 90GB, ext3, mounts as /home

and I want to increase  P1  to 20G. I was proposing to do the following, 
and would be grateful if anybody could warn me that I should be taking
some additional precaution.

Make backups & verify ( tar -d )

Using the Live CD, delete  P3   and  P4
Move P2 to new position, starting at 20G.
recreate  P3  and  P4 , refill  P4  from its backup.
then try to reconfigure grub

In previous posts, people have said that I should first defragment  P1  
before trying to enlarge it using the XP disk manager. But when I tried
to defragment, it failed, saying there was not enough free space. There
is about  1GB  free and it wanted 1.5GB, which does seem excessive. Can
anybody recommend a better defragmenter?

Is the XP disk manager clever enough to enlarge the file system to use 
the enlarged partition?

I would very much like to have some reliable way to repair XP if I make
some mistake and trash its partition. Merely backing-up  P1  and 
un-tarring is not reliable. On some previous occasion, I un-tarred the
backup and I got what seemed to be a valid NTFS file system but it 
would not boot (I have no idea why). Also the defragmenter said that
some files in the present (working) Windows partition are immovable.
(I dont know what files or why). I dont expect that tar would be
able to reinstall these files in their correct places.

Please any recommendations? thank you

---

### Post by Herman on 2010-10-04
> Also the defragmenter said that
some files in the present (working) Windows partition are immovable.
(I dont know what files or why). I dont expect that tar would be
able to reinstall these files in their correct places.The 'immovable files' in Windows are the 'page file', which Windows uses something like Linux uses a swap area, as a temporary storage place for memory items, especialy when the RAM starts getting filled up. The 'page file' shows up as a big green unmovable block in the defragmenter.
You can turn off the Windows page file by looking in 'Control Panel' -->'System' --> 'System Properties'-->'Advanced' tab -->'Performance, Settings button' --> 'Advanced' tab, 'Virtual Memory',-->'Change', [COLOR=#ff0000]take note of your settings[/COLOR] (on a piece of paper), and click the radio button for 'no paging file' -->'Set', 'Apply', 'Okay'.
Then restart your computer and now you can run defrag as many times as you need to, without the big green block in the way.
> In previous posts, people have said that I should first defragment  P1  
before trying to enlarge it using the XP disk manager. But when I tried
to defragment, it failed, saying there was not enough free space. There
is about  1GB  free and it wanted 1.5GB, which does seem excessive. Can
anybody recommend a better defragmenter?A better way to defrag is to remove all the files you can, (all the user files), and copy them into some other disk, such as a different hard drive, and then copy them back again later. It's probably faster than defragging and probably also a lot better than any defrag utility money can buy.

If you're going to do that then you might as well leave them in the other media as a backup while you are working on your partitions, since you need a backup before using any partition editor anyway and now is a good time.
I guess that kind of makes defragging redundant. Don't bother, it's just a waste of time.
You should have at least two copies of your files though, in case they're important to you and something bad happens to your one and only backup.  :)

---

### Post by Herman on 2010-10-04
> Is the XP disk manager clever enough to enlarge the file system to use 
the enlarged partition?I don't know, you or somebody advising you might be confusing the Vista/Windows7 Disk Manager with the XP Disk Manager. 
It's possible the XP Disk Manager has been updated and improved since I last tried it.
I have always had good luck using GParted myself.

Try it and let us know.  :)

---

### Post by Herman on 2010-10-04
> I would very much like to have some reliable way to repair XP if I make
some mistake and trash its partition. Merely backing-up  P1  and 
un-tarring is not reliable. On some previous occasion, I un-tarred the
backup and I got what seemed to be a valid NTFS file system but it 
would not boot (I have no idea why). Things like that need to be looked at on a case by case basis, there could be a number of different problems. It would probably be possible to get it to boot, but you would probably need a Windows XP 'Installation CD', so you can run 'fixboot C:', and update the boot sector. The boot sector needs the block address for the boot loader files. Apart from that if your partition number has been changed, you would need to edit boot.ini. It would also be a good time to run CHKDSK too.
If you do have a Windows XP installation disk, it would possibly be worth considering simply re-installing Windows instead, because then you'd know it's 'clean' and in pristine condition. The only problem is, Windows is such a complicated system to back up and restore, it used to take me days to get it back how I wanted them again when I used to be a Windows user.
If you don't have a Windows Installation CD you should consider getting one somehow, because you need it for taking care of your system if you're going to keep using Windows.

---

### Post by Herman on 2010-10-04
An easier way would be to make a backup of your files.
Boot your Ubuntu Live CD and start GParted.
Resize P4, (your ext4 /home partition for Ubuntu), to less then 80GB, to leave more than 10GB of free space at the and.
Copy P2, (your 10 GB Ubuntu /), and paste it in the >10 GB free space you just made after /home.
Delete your original P2 to make room to resize Windows XP.
Resize your swap to the right until it's only about 1GB, (you don't need 10 GB of swap area).
Resize Windows XP to the left another 19GB in the free space where your / and swap used to be.
You don't need to defrag Windows to use GParted, it's simply not necessary, saving you lots of time. You should run CHKDSK/R though, and GParted will flag the file system with the 'dirty' flag deliberately to stimulate a file system check next time you boot XP anyway.
Finally, re-install GRUB.

Another idea might be to just delete your 10GB swap area and resize /home by only 1 GB and make a new swap area in the free space.
Then resize your / just a bit smaller and copy-paste it to the right where your 10 GB swap are was, then resize it to meet /home. Delete your original  /.
Then resize Windows by 10 GB or so to fill the free space. :)

---

### Post by mringer on 2010-10-07
Update: I managed to move & resize the 3 Linux partitions without much
trouble. Only problem was that the system on the Live CD ( X-UB, 8.04 )
was repeatedly mounting these partitions and then I could not move or
size them while mounted. I think I must have umounted each of these
about a dozen times. 

But when I resized the windows partition, I could not find any way to
resize the file system (NTFS). So the partition is now 20G, with 9G
used and 1G free. Several posters have recommended using Windows's
disk management tool, but I cannot find any option to resize the 
filesystem. (I am using XP, I suspect that you can only resize in 7).

SO then I tried the XP install disk, this of course over-wrote the 
master boot block, so I tried to boot from the Live CD and this 
failed. I got a flood of errors saying something like

read error from /dev/sr0 block=<number>

Please what is this device? I did check the integrity of the 8.04 
live CD, it said no errors. Also I was able to boot from the 7.10
CD (in safe graphics mode) But it is really scary that I couldnt 
boot the 8.04 CD.

---

### Post by mringer on 2010-10-08
Further update: I have now re-checked the 8.04 CD. It still refuses
to boot. I regret that I didnt report the errors correctly, what they
actually say is

[number] buffer I/O error on device sr0 logical block [number]
squashfs error sb_bread failed reading [number]

and the CD offers a choice to check itself for errors, none found.

---

### Post by Herman on 2010-10-08
I'm pretty sure /dev/sr0 is your CDROM drive.
Check to make sure your CD doesn't have scratches or dirt on it.
I have cleaned CDs by wiping then with a soft cloth damped with what we call in Australia 'methylated spirits', which I think is the same thing as 'denatured alchohol' in the USA in Canada, I'm not sure.
Maybe you have a speck of dust or dirt on the optical lense in your CDROM drive.
You might need to clean it or have somebody clean it for you.

If you have a spare USB flash memory stick, you could maybe use a different computer to copy the Ubuntu Live CD to a USB instead. ('System', 'Administration', 'Startup Disk Creator' in later versions of Ubuntu). If your computer is capable of booting a USB device, you can boot i and it runs just like a Ubuntu Live CD, only better.

Another option to consider, if you have a larger sized USB flash memory stick free, would be to install Ubuntu in the USB flash memory stick as a normal installation. If you use a modern version of Ubuntu, like Lucid Lynx, it will boot with GRUB2. That means if you boot it in the computer with the booting problems, you can run update-grub in the USB Ubuntu and it will add the internal Ubuntu to the USB Ubuntu's GRUB Menu. 
After that's done you can reboot and use the USB Ubuntu's GRUB Menu to boot your internal Ubuntu. Then once it's booted, all you need to do is re-install GRUB.

Yet another idea would be to get yourself either a [Super Grub Disk]("http://www.supergrubdisk.org/") or a [Parted Magic Live CD]("http://partedmagic.com/"). Either of those will often boot in a problem computer when nothing else can.
Super Grub Disk can be used to boot your internal operating system so you can fix it.
Parted Magic contains GParted, for partitioning and file system work, plus many other useful tools for a variety of different kinds of maintenance and recovery work, (including Super Grub Disk).

---

### Post by mringer on 2010-10-15
further update: to resize the NTFS partition, what actually worked
was ntfsresize which is part of the ntfsprogs package (in UB). I 
do not know of any windows program that will resize a ntfs partition.

---

