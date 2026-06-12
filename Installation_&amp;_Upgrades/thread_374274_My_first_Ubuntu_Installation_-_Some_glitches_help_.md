---
title: "My first Ubuntu Installation - Some glitches help wanted"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Kwag on 2007-03-02
My environment: 

Dell Dimension 4700 
2.8 Ghz CPU, Multi-threaded
512 MB DDR II RAM
80 GB SATA Hard Drive

My original 3 primary partitions:

3 GB, Primary, PC/M Concurrent DOS  (this is an image of the disk at shipping time for restore)
47 MB, Primary,  FAT   (This is for the boot menu, provided by Dell)
72 GB, Primary NTFS  (This has my Windows XP SP 2 OS)

I used the Edgy Eft Live CD to install Ubuntu as a dual-boot alongside my Windows XP SP2 OS and opted to set up my partitions manually. 

I shrunk the NTFS partition down to 50 GB  (My computer is pretty well defragged because I have diskeeper running on it all the time as a service within XP).

I created an extended partition with the left over 22 GB and broke it out like this:
  1 GB linux swap
  10 GB ext3 to /
  11 GB ext3 to /home

GParted gave me some error saying my fat partition had errors in it, do I want to continue and leave as is or go back?  But I never touched the FAT partition, so this confused me.  Going back didn't help.  Plus, since I didn't touch the FAT partition, I wasn't to worried, so I said continue as is.

The installation seemed to go pretty well.  Near the end the monitor blacked out.  I was expecting it to eject the CD, and tell me to press "Enter" (like what happens during the live session).  However, everything froze.  I could not eject to CD.  I tried Ctrl-Alt-Delete.  So, I did a hard shut down and restart with the power button.  

Forgive me, but my first priority was to make sure Windows XP was not damaged.  The GRUB menu came up correctly, and I chose Windows.  A blue screen came up, and I got the message "Cannot detect filesystem of Volume /???/<bunch of letters>."  Chkdsk started up.  It completed in about 5 minutes, and then windows proceeded to boot, but more slowly than usual.  A lot of CPU crunching.  Several messages saying "Detecting new hardware".  But finally it was done, and everything seemed functional.  I rebooted next into Ubuntu.  Everything over there was fine too.  I went back over to Windows again, to see what would happen the second time.  The same error message came up, chkdsk started, but in a second or two the process finished, and windows proceeded to boot.  However, windows still boots much more slowly than usual (lot of crunching at the beginning), but I don't get the "detecting new hardware" message.

I used the Windows Recovery Console and ran chkdsk on C: and fixed any errors.  (there was only one).  Then I rebooted windows.  No change. 

How do I fix this problem?  I have a GRUB Super Disk, but there are so many tests and options in there, I don't know what to do.

Thanks.

---

### Post by Karstadt on 2007-03-02
i am afraid I cannot give an answer but is Diskeeper running?  I should think it would not like all the changing on the hard disk.

---

### Post by GoingDown on 2007-03-02
It might be because new Ubuntu partitions you have created are visible to Windows, but it cannot determine what is the file system type on those, and that will cause slowdown.

Try to start Windows, and then go to the "Disk Administrator" (Control Panel/Administrative tools/Computer Management) and remove DRIVE LETTERs of all ubuntu partitions you can see.

---

### Post by Kwag on 2007-03-02
Diskeeper shouldn't be the problem since it is a service that only runs within Windows (i.e. it is only active when Windows OS is running).  

As suggested, this evening sometime,  I will try to remove the visibility of the Ubuntu Partitions in Windows (using the Disk Administrator in Windows).  

I will report back here with the results.  Thanks for everyone's help so far.

---

### Post by Kwag on 2007-03-02
Oh well.  I looked at the partitions in the Disk Management application within Windows XP.  I do see all my Linux Partitions in there.  They are listed as Healthy (Unknown Partition), and the app thinks they haven't used any space.  There are no drive letter paths assigned to these partitions.  The only option this tool gives me for these partitions is to delete them, which of course I don't want to do.

Any other ideas anyone?

Thanks.

---

### Post by Invictious on 2007-03-03
^ same questions as above. It's pretty annoying now..

---

