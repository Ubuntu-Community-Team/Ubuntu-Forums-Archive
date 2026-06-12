---
title: "Grub2 &amp; The MBR"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by Robbobden on 2011-02-01
If I elect to install Grub2 to the MBR (Ubuntu 10.10 LiveCD), will Grub  data be written to any sector beyond the first 512 byte sector ?  I'm  not talking about the boot sector of the partition where Ubuntu is installed, but say the very next sector adjacent to the MBR.  The reason I ask this question is that after installation, I backed up the MBR using the Linux dd command, then burned a DVD image of the Ubuntu partition.   Then I zero'd the MBR and wiped the HD.   When I restored the MBR, again using the dd command, and pasted the image back,  all I got after reboot was the word:  'grub'  and couldn't get anything to start.  This was an exercise to see if I could recover everything after a HD crash or failure.

So, I may have wiped something I wasn't aware of that needed to be backed up.  Any comments ?

Thanks !

RDL

---

### Post by srs5694 on 2011-02-01
I think so, but I'm not 100% positive of that. On an MBR disk, many boot loaders, and I *think* this includes GRUB 2, write to the first few sectors (about 60 of them) immediately following the MBR. This area is officially unallocated on most MBR disks, and boot loaders and some other utilities interpret "unallocated" to mean "available for squatting." This usually works fine, but if two or more utilities try to use this space, they'll trample each other; and it may require extra work to back up and restore this data.

On a GUID Partition Table (GPT) disk, there's no equivalent unallocated area. Instead, on BIOS-based computers GRUB 2 uses a special partition called a [BIOS Boot Partition.](http://grub.enbug.org/BIOS_Boot_Partition) This practice minimizes the risk of problems with conflicting use of the space and makes it a little more obvious that there's something else that needs to be backed up.

---

### Post by Robbobden on 2011-02-01
Good info, thanks !   Lets say I have Ubuntu 10.10 in the 1st partition (16G).  That's /dev/sda1.  The remaining HD space, 60G, is free.   I'll create a 2G Swap afterwards from the command line.  That'll be /dev/sda2.  Grub2 gets loaded to /dev/sda during installation.  I'll get Ubuntu the way I want it with all packages etc and the Desktop GUI (I really like Macbuntu !! ) looks good.

Now, in case of a HD failure, I want to backup MBR and the 1st partition.   Using only Linux dd command, how would I proceed ?   Right after I do this, I'll want to wipe MBR and HD and using my backup data, restore everything the way it was.   How would you knowledgeable folks do this.   Try to make it simple for me, please !

Thanks !
RDL

---

### Post by Robbobden on 2011-02-01
When I do:  sudo fdisk -l   I see 1mb unallocated space before the 1st partition.   Grub2 data might be in there then ?   Well, I probably would be better off imaging the entire drive.   I found this link:

[http://www.ehow.com/how_4924091_clone-hard-drive-linux.html](http://www.ehow.com/how_4924091_clone-hard-drive-linux.html)

The hardest part of following the instructions in the above link was finding out how to 'apt-get install gddrescue'   'Course the Ubuntu LiveCD had to be in but in Synaptic Package Manager, in setting/repositories, you have to enable 'universe and multiverse', then close that window and 'reload' in the main window before you can get back to the terminal and get the gddrescue package.

Then:  sudo ddrescue -v /dev/source /dev/destination

In my case:  sudo ddrescue -v /devsda /dev/sdb

My sdb is an 8G USB stick.   Neat thing about this is that since I only had one partition for Ubuntu of 7G (I re-installed it with a smaller partition), the process only wrote HD space that was partitioned.   This HD is 60G, but only 7G of that 60G was copied to sdb.   Also, the USB is bootable if you can boot from USB.  I won't be able to with this ACER, but when and if I have to restore to a new HD, I'll reverse the process using the LiveCD and gddrescue again.   

RDL

---

### Post by Robbobden on 2011-02-03
Ahhh !  What I said above is not exactly correct.  Yep, you need to put limits to the operation perhaps by using the -s option.  In my case, the 1st partition is 7G.  So, to backup the MBR, unallocated space in front of the 1st partition, and the 1st partition itself, I tried this to make sure I got everything copied:  

sudo ddrescue -s7500000000 -v /dev/sda /dev/sdb  #(-s7500000000 represents 7.5G)

sdb is an 8G USB stick.   Instead of just wiping MBR and HD, then restoring with the USB stick, (to test whether the USB had everything), I installed Linux Plop boot loader and made an entry in the Grub2 menu for Plop.  After that, I inserted the USB stick, then chose Plop Boot Manager and then boot from USB.  

This got excellent results.  Ubuntu booted up from the USB stick and everything looked good and seemed to function well.  I know it looks like I'm carrying on a conversation with myself with this post.   Maybe someone will find this stuff useful.

BTW, here's how to get Linux Plop Boot Manager installed and an entry in Grub2 for it:

Visit:  [www.plop.at/](www.plop.at/)
click 'downloads' then 'Boot Manager downloads'.  I downloaded plpbt-5.0.10.zip to my 'Downloads' folder.    Then right-clicked the file and did an 'extract here'.Then threw away the zip file.  In terminal, I navigated to 'Downloads/plpbt-5.0.10' folder and did this:

sudo cp plpbt.bin /boot  #(plpbt.bin is the binary file in the plpbt-5.0.10 folder. You want to copy it to /boot)
 
Now, to add an entry in Grub2 menu:  sudo gedit /boot/grub/grub.cfg
Insert the text below:  My Ubuntu is in (hd0,1), yours could be somewhere else.  (Yep, I know.  Not supposed to edit grub.cfg.  Be careful or you could end up with an unbootable Ubuntu !)

menuentry 'Plop Boot Manager' {
     set root=(hd0,1)
     linux16 /boot/plpbt.bin
}

If you only have Ubuntu installed, Grub2 probably won't present itself.  If not, hold down the right-shift key just after your BIOS screen.  Keep it down until you see the Grub2 menu.  Plop Boot Manager should appear for you now.   PM for any additional info or to clarify something.

RDL

---

### Post by ticket on 2011-06-13
I found this:

> The version of Grub shipping with my Linux distro is Grub2, and it installs its equivalent of stage 1.5-2, core.img, into the remaining sectors on the first track after the MBR but before the first partition. 
[http://superuser.com/questions/101527/is-it-possible-to-have-grub2s-boot-img-in-the-mbr-and-have-it-load-core-img-from](http://superuser.com/questions/101527/is-it-possible-to-have-grub2s-boot-img-in-the-mbr-and-have-it-load-core-img-from)

So grub2 is not confined to just the MBR.
If one doesn't simply want to use dd to clone the whole disk, then this makes cloning a bit tricky.

I was planning on the scheme where I install Ubuntu onto a mem stick and backup my system disc to it using rsync: 

sudo rsync  -avx --delete /media/SYSTEMVOL/  /media/MEMSTICKVOL  

I found this works, but if a distribution upgrade updates grub2, then the MBR and the other altered tracks on the main system disk will have to be transferred to the mem stick by using dd with appropriate options.

e.g. if a track is 63 sectors and a sector is 512 bytes, then a track is 63 x 512= 32256 bytes,  so to transfer grub2 correctly may require two dd commands, one to transfer just the mbr (the first 446 bytes), then skip until 512 (i.e. skip the partition table) and transfer the 32256 bytes after offset 512 (will need to use the seek and skip options of dd).

My worry is that, even if this works, how future proof will it be?

I'm thinking now it might be best just to use the idea suggested in this thread, i.e. resize the partition of the main disk down to something small (~10Gb) and dd the first 10Gb (my data files are on another disk, not in /home).  That would take about 10 mins.  

Time to experiment.

---

### Post by Quackers on 2011-06-13
Apart from the first time I tried it, clonezilla backs up the mbr and restores it if you use a disk image (rather than separate partition images). The first time it failed to restore properly and I had to re-install grub(2).
Every other time I've restored from clonezilla disk images the mbr has been restored perfectly.
It may be another option for you.

---

### Post by coffeecat on 2011-06-13
> **ticket said:**
> So grub2 is not confined to just the MBR.

Indeed. The area between the partition table and the first sector of the first partition is called the embedding area and core.img does indeed go there. But legacy grub used to put stage 1.5 in the embedding area, so this is not a new problem. 

I don't believe core.img takes up the whole of the first 63 sectors, but it is larger than the old legacy grub stage 1.5. Which is why you are more likely to get problems with grub 2 than with legacy grub with certain badly-designed Windows utilities. Links:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable")

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

Interestingly that second link refers to the "extended mbr" when they refer to the first 63 sectors. I don't know whether that is proper terminology or not, but it explains the confusion about grub being "installed to the mbr". Does mbr mean the first 512 bytes (which includes the  partition table) or the first 63 sectors? Rhetorical question.

Whatever, I've always taken a robust and pragmatic approach to "cloning". I simply clone whichever partitions I want to copy and then re-install grub with a live CD or live USB which simply rewrites grub code to the mbr (sensu strictu) and the embedding area.

It would be interesting to know, from what Quackers says, which sense of "mbr" it is that clonezilla clones.

---

### Post by Quackers on 2011-06-13
sensu strictu......oh my :-)

From memory clonezilla uses dd to copy the "mbr" which is entered on the screen as 512 bytes, if I'm not mistaken.

---

### Post by coffeecat on 2011-06-13
> **Quackers said:**
> sensu strictu......oh my :-)

You might have corrected my faulty Latin while you were about it! As a quid pro quo, of course. :p It should have been sensu strict[SIZE=3]o[/SIZE]. :oops:

:wink:

---

### Post by ticket on 2011-06-14
I found that the following does work.

This is based on keeping user data on another disc, so that your home directory is small, and contains only user preferences and settings.

This means you only need a small system disc.  However, it is quite difficult these days to get hard discs smaller that 40GB.  You need no more than 10GB to install Ubuntu 10.1, which includes a fair sprinkle of apps (web browser, media players, office, etc).

With a small system disc, you can back it up to a USB stick.

My system disc was 80GB, so it needed shrinking. So after making a backup of it onto a spare 80GB disc, I loaded the 10.04 installation 'live' CD and started the GParted partition editor.  My USB stick is 16GB, so I needed to shrink my 80GB system down to 15GB (allowing some elbow room).

This took a little while, but I succeeded. Can't remember exactly what I did, but something like: 
- Resized sda1 to to 13GB
- Resized the swap space sda5 from 3GB to 2GB (have to disable swap to do this)
- Resized sda2 (logical partitions) to 2GB
- Moved sda2 next to sda1.

Result (screen shot) is attached.
I rebooted the system, just to check it was still ok.

I have to say that using GParted was very intuitive. Good piece of software.

I now have a system disc whose data only spans the first 15GB of the 80GB disc (the downside to all this is you lose a fair bit of disc space - but the disc was too large in the first place!).

To back it up onto the USB stick, you need to boot from a live CD again.  As we only need two basic commands, a knoppix live CD or similar is ok (it boots a bit quicker).

Insert the USB stick.

In a command shell, do a 
   sudo fdisk -l
just to confirm where all the disks are.

On my system, the system disc was sda and the USB was sdd.
I then copied the first 15GB of the system disc to the USB stick:

  sudo dd if=/dev/sda of=/dev/sdd  bs=2MB  count=7500
...................(source)..........(dest).......... 

The bs=2MB transfers the data in clumps of 2,000,000 bytes.
The count=7500 instructs how many clumps to transfer.
So dd will transfer 2,000,000 x 7500 = 15GB of data.

This took 19 minutes (avg 13.2 MB/s)
I noticed the USB stick got quite warm during this.

It might be worth trying to use clumps of 4MB, to make it quicker.  The dd options will then be:
   bs=4MB  count=3750

I restarted the system, removed the live CD, and yes, the USB stick booted fine!

Interestingly, as the USB stick booted, it showed the grub2 menu for the user to select which OS version to boot - this doesn't happen when I boot from the 80GB disc.

Now it only takes 19 minutes to clone my system using dd, whereas before it took 1 hour and 20 minutes.

If there is no distribution upgrade, (i.e. only software updates) then system backups can be made using rsync.  You still need to use a live CD to do this, since the system disc could be updating itself. So, using volume names of SYSTEM (HD) and SYSTEMBAKUP (USB stick):

sudo rsync  -avx --delete /media/SYSTEM/  /media/SYSTEMBAKUP  
......................................(source)................(dest).......... 

You will need to change the volume name of the USB stick from 'SYSTEM' to 'SYSTEMBAKUP' (or whatever you choose) for the above to work (the original cloning would have given the USB stick the volume name of 'SYSTEM')

---

