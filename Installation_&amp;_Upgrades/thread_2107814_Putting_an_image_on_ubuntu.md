---
title: "Putting an image on ubuntu"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by Elitenoname on 2013-01-22
I have installed ubuntu on my laptop and i was wondering if i were to re-partition the hard drive so i could put my windows 7 image on the hard drive if it would create any problems anyone knows of? the image was made when it was just windows 7 only so i dont know if it will mess grub or the boot up. has anyone tried this?

---

### Post by Lightning Dragon on 2013-01-22
Hello,

Do you mean reinstall Windows 7, or dual boot between Ubuntu and Windows 7?

---

### Post by Elitenoname on 2013-01-22
would be dual booting but i have an image that has everything pre-configured rather than clean install then having to configure and install all the applications

---

### Post by Lightning Dragon on 2013-01-22
Hello,

Do you mean you already have both the OSs installed and now you would like to be able to choose which to boot when you turn your system on? Or perhaps you mean you have Windows/Ubuntu installed alongside the other?

If you already have both OSs installed and you aren't getting a list of OSs to select from, enter into your BIOS and switch the boot to the HDD (harddrive) carrying the OS you want into.

---

### Post by Elitenoname on 2013-01-22
no i currently have ubuntu 12.04 install on my machine and i want to repartition the drive to put a windows 7 image on it almost like dual booting but i would not be installing windows 7 rather just putting a pre-configured image onto the laptop

---

### Post by Lightning Dragon on 2013-01-22
Hello,

In that case, I do not think you can do that. At least not the way you are hoping to. Perhaps staff or another member could clarify if I'm correct or not, but I have never heard of someone being able to put a pre-configured Windows 7 in with Ubuntu.

---

### Post by Herman on 2013-01-23
I have just been running a few experiments with Windows 7 and Ubuntu myself.

You didn't say what software you used to creating the image of your Windows 7 installation or what steps you took prior to creating the image.

The last time I used Partimage or similar methods of saving a copy of an operating system I was in the habit of removing all my regular files first and saving those separately. That allowed me to resize {shrink)  the operating system partition(s) first to a very small size.  That's important later, because when restoring we normally need to create a partition or partitions at least as large as the ones that were backed up in the image.  Unless your cloning/restoring software takes care of that for you somehow.

If you did shrink your Windows partitions first, or if the software you used did it for you, your image backups will probably fit in the now smaller amount of free space. 
Otherwise you may need to delete Ubuntu to get the free disk space for the same size partitions back again to restore to. 

Windows7 needs a primary boot partition to boot from. The operating system is restored to a logical partition it will still boot but you will need space for a 100MiB boot primary partition somewhere.

It's often necessary to run a file system check (CHKDSK) after restoring from a cloned backup . It's normal for Windows to run an file system at boot-up if you used GParted to work on it too. If Windows runs a file system check at boot-up it's best to be patient and wait for the file system check to run its course.

Sometimes if operating systems are not restored to the same partition number they were originally installed in they can need changes to various settings before they can boot and run properly. Windows XP needs boot.ini edited with the new partition numbers. Windows 7 will be able to fix itself automatically for you if you have your installation disk or a [system recovery disk]("http://ubuntuforums.org/How to Create a Windows 7 System Recovery Disc | eHow.com") so you can run Startup Repair'. **[Repair *Windows 7* Using the *Startup Repair* Tool]("http://www.google.com/url?sa=t&rct=j&q=how%20to%20use%20windows%207%20startup%20repair%20in%20system%20recovery%20disk&source=web&cd=4&cad=rja&sqi=2&ved=0CEYQFjAD&url=http%3A%2F%2Fpcsupport.about.com%2Fod%2Ftoolsofthetrade%2Fss%2Fwindows-7-startup-repair.htm&ei=MW7_UM3uKcKgkAWK6YCgCA&usg=AFQjCNGD9RhgA3LCUynWfjRQN94aMvtTww&bvm=bv.41248874,d.aGc")**

 Then back in Ubuntu you just need to run update-grub and your Windows 7 should be bootable from GRUB.

---

### Post by Elitenoname on 2013-01-24
Thanks herman that did help the imaging software i will be using is call R-drive what is does is it will take a complete image of your hard drive (or the partitions you select) and store it into a compressed .arc file then when you go to put the image back on to a new hard drive it will restore it the way it was save on the the new partition. i know it also will take the 100mb  partition with it and restore it as well in the process but do you know if it creates any problem when booting using grub or anything like that and will it be recognized or do i have to do something inorder for it to be recognized?

---

### Post by Herman on 2013-01-25
I have never tried R-Drive, but I googled it and in its web-page sales spiel it claims that data from a disk image can be restored on a free, unpartitioned space any place on the hard drive.  [http://www.drive-image.com/](http://www.drive-image.com/) It also says the size of the restored partition can be changed.
From a quick scan of that page I didn't notice any advice about emptying  user files and resizing partitions smaller prior to taking the backup  image. 

As a natural skeptic I am thinking they probably really mean the size of the restored partition can be changed later, after the partition has been restored. That would be normal, of course it can. 
I think just give it a try and see what happens, as long as you don't restore on top of your Ubuntu partition it won't likely hurt Ubuntu.
I imagine if it can't do it you'll be given an error message and it will stop without harming anything in your hard disk. 
Maybe you should take a backup of your Ubuntu files first just in case.

I still think you'll need a CHKDSK and then run update-grub and you should be okay if the R-Disk software is as clever as the website implies.
If you don't run CHKDSK yourself, it might be okay, but if it fails to be automatically added to your GRUB boot list after you run update-grub running CHKDSK might help.
Windows will likely run CHKDSK, (file system check) itself on boot up if you don't do it beforehand. In that case just be patient and wait for the file system check to complete and Windows should reboot as good as new.

---

### Post by Herman on 2013-01-25
Here's a thread from the R-Drive Backup Forums, [Destination Disk is too Small]("http://forum.r-tt.com/destination-disk-is-too-small-t6090.html").
Apparently there's a way to adjust the partition size on the Restore/Copy Parameters panel.

---

### Post by furything on 2013-01-25
Be careful restoring the image.

It should have 2 partitions like you say 100mb is the hard drive system restore. Then the system. Don't restore the MBR otherwise you will have to reinstall grub2 from a live cd which I found rather painful.

As another point if you wish to use windows backup it likes to be the primary partition so you have to move ubuntu first and make sure the mount point for it is the correct partition (guess you can do this from from livecd as well but never had to).

---

