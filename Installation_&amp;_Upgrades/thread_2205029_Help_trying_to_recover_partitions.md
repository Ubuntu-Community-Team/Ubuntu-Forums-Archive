---
title: "Help trying to recover partitions"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by ctgcwiqc on 2014-02-11
I have an HP 2000 laptop (WIN7) that I wanted to install Ubuntu 12.04LT alongside.  I have 4 total machines to install on.
[LIST=1]
[*]I booted WIN 7 
[*]defragged 
[*]shrunk the volume by 512000MB to create 50GB unallocated space 
[*]I rebooted and Ubuntu did not see the unallocated space as Edubuntu did, it stated it was "unusable", where I ***believe*** Edubuntu detected and was able to format/write to this space on the first laptop i did this on. 
[*]So I rebooted windows and extended C:/ to reclaim unallocated space. 
[*]Booted Ubuntu from LiveUSB created with Y.U.M.I 
[*]selected install Ubuntu 
[*]selected "something else" to create partition 
[*]I selected the WIN 7 partition and entered 512000MB as the desired partition size (this is where I believe I mad the mistake) maybe I entered 512000MB as the desired size that I wanted to reduce the drive, however it appears this actual **shrunk the volume TO 512000MB** 
[*]I realized after returning and looking at the partition table I screwed up. 
[/LIST]

I havent done much other than attempt a few recovery options from third party groups.  I plan to create a recovery disk tomorrow from another laptop (exactly the same) and see what happens when I enter recovery.  I see that i screwed up partition table, and cross platform the table appears different, so it is difficult for myself to figure out what is what and how to fix manually.

  I have attached a link to 3 photos of the partition table, [https://drive.google.com/folderview?id=0B51jsxUX7e2ob2ktR1NwLURTRTA&usp=sharing](https://drive.google.com/folderview?id=0B51jsxUX7e2ob2ktR1NwLURTRTA&usp=sharing) one from windows after i shrunk volume, one of ubuntu prior to shrink, and another of ubuntu post shrink.  I want to create iso of disk, but since the free space is unallocated it will not select this space to copy.  I tried clonezilla FYI.  So i would like to restore to working order if possible, perform full backup, then retry installation.  I know I should have performed this step first, but I had no recovery media to write to.  

**THanks in advance** for the help I am sure I will receive.  Let me know if I need to post the pictures in a more trustworthy/approved manner.  I couldnt get them attached using the attachment option within the forum for some reason, so I added them to my google drive and shared them via link which is included.

---

### Post by ctgcwiqc on 2014-02-11
Well I booted Ubuntu off a live usb, and looked at disk options.  To my surprise, the built in utility posses the ability to create a disk image.  This is great news because the image it is creating is the complete 320GB disk, not just the recognized partitions as clonezilla was trying to do, ignoring the "unusable" space.  This should mean if any recovery option i try fails, the data I will attempt to recover should still be accessible via the disk image.  I still have a huge problem, but its nice to know the data is potentially somewhat safe.

---

### Post by oldfred on 2014-02-11
It looks like you had the standard HP Windows 7 that uses all 4 primary partitions with MBR(msdos). You have to delete one partition, so you can create a new extended partition for all the Linux partitions.

Testdisk may show old partitions. Usually it shows all old partitions and if you changed several times you may have various versions. You have to pick only one set that does not overlap. Best if you really know old partition table structure or had backup of partition table.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by ctgcwiqc on 2014-02-16
Testdisk failed to detect all partitions.

Parted failed to run the "automated" processes it was designed to, possibly due to me not knowing the partition areas exactly, which would make the process not very automated.

Gpart did nothing.  

I attempted a restore with Win7 rescue disk, but it failed with error "recovery partition full" after about 2-3 hours.  I canceled the restore, and booted Hiren's Boot CD, investigated free space issues, and determined my son had switched the backup location from our 3TB NAS to the recovery folder.  This is why I have no backed up files to begin with, HAHA, but there was not enough free space in that volume to store the backup, so its worthless.  So I am currently restoring from the disc image I created with ubuntu live usb, which is taking FOREVER.  320GB HDD takes 1.2-2 days to write image back to drive?!?!  I this normal?

My next plan is to restore image, boot into WINXP from Hiren's Boot CD, extend two of the four partitions to capture the unallocated spaces, then run data recovery utility, probably "recuva" as I have success with this program in the past, and I can run it from the WINXP mode within Hiren's Boot CD.  Hopefully this will capture alot of the lost files.

I have another laptop excatly the same as the one with the screwed up partition table.  What could i do to mirror the partition/MBR or would this not be a good route travel?  I think this would be ideal, it is the same laptop, same HDD, same OS.  

Next step may be to image the "GOOD" laptop, restore image to "BAD" laptop, then restore to factory settings, that way the MBR & partition table are as they were intended, then attempt to rearrange/delete primary partitions to create room for Ubuntu.

---

### Post by oldfred on 2014-02-16
If your other system was identical down to the same sectors you can copy partition table. But if sectors are off it will not work and may make things worse.
 
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt


Using sfdisk to fix partition table problems - not without risk
 [http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 

Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

   Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by ctgcwiqc on 2014-03-23
I was able to "backup" my partition table from the good twin laptop, but i am not skilled enough to write it to the laptop with the screwed up partition table.  

I may attempt to recover again but for now I cloned the good laptop and wrote image to bad one.  Restored to factory settings and all is well.  

Really good info about the 4 primary partition limit, i do appreciate that.  I plan to use the instructiuons from the full circle magazine link you provided to remove a primary partition.  I cant believe HP would ship HDD from a factory essentially maxed out as far as partitions go without tweaking that is.  THanks again.

---

