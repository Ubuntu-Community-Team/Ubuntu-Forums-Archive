---
title: "Reinstalling Windows Help!!!"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by Zuul47 on 2010-09-28
my friend did a full installation of Ubuntu 10.04 LTS 64bit...he doesn't want it anymore and wants windows 7 back. he tried to put in the MS disk and reinstall but the optical drive wouldn't read the DVD-R. he tried a CD-R with windows xp sp3 but it wouldnt load at startup either. Ubuntu and Xubuntu CD-Rs work fine on the laptop. I found a tool called Bootit NG,which is a partition manager, and there is a volume called Linux Swap/Solaris...do i need to mess with that and change it to another type,it had other choices for the volume like ntfs, fat-16,fat32,extended, and so on. The primary partition i know has to be NTFS.

the partition tool also mentions MBR



Please Help

---

### Post by PRC09 on 2010-09-28
When you try and boot from the win7 disk do you get any errors if so what does it say? Is this a self burned win7 disk or is it factory? Was this a dual boot or just Ubuntu? I asume your machine is set in the bios to boot from the dvd drive first.....

---

### Post by Zuul47 on 2010-09-28
> **PRC09 said:**
> When you try and boot from the win7 disk do you get any errors if so what does it say? Is this a self burned win7 disk or is it factory? Was this a dual boot or just Ubuntu? I asume your machine is set in the bios to boot from the dvd drive first.....


no errros the drive just slows down and the black screen with the white line shows for a bit and then it loads up ubuntu. no dual boot its all ubuntu.

my partitions are displayed like this:

EMBR entry 0 -                           149 gb-                 Linux Native            
EMBR entry 1-                            some megabytes-  Extended
Volume                                    -some megabytes   -Linux Swap/Solaris 


its a selfburn DVD and i set the optical drive to boot first.

---

### Post by PRC09 on 2010-09-28
If you are using Bootit then you can just delete all the partitions and leave it as unformatted space.Then select view mbr and set the one large partition as active and if its the latest version of Bootit set the mbr as win7 click apply and thats all you need to do with that.As for not booting from the dvd I am not sure why it doesnt boot other than a bad burn.May have to do it again at a lower speed.Hope that helps.....Maybe the original win7 has a problem.....

---

### Post by hansdown on 2010-09-28
Hi Zuul47.

Your friend should reformat the drive to NTFS.

Then the windows disk should load.

---

### Post by Zuul47 on 2010-09-28
so i don't need the volume called linux swap/solaris and the extended partition?

i'll try to burn another DVD and see if that helps....if not i was going to do a USB install.

the weird thing is that linux distro cds work but windows dvds and cds dont

i appreciate you helping me...THANKS!!!:guitar:

---

### Post by Zuul47 on 2010-09-28
> **hansdown said:**
> Hi Zuul47.

Your friend should reformat the drive to NTFS.

Then the windows disk should load.


When i use bootit Ng it has the NTFS and another word next to it. thanks for the help:guitar:

---

### Post by hansdown on 2010-09-28
> **Zuul47 said:**
> When i use bootit Ng it has the NTFS and another word next to it. thanks for the help:guitar:

The only other thing that springs to mind is, if this is a system restore disk, it will be looking for the restore partition, which may have been overwritten.

---

### Post by Mark Phelps on 2010-09-29
Boot from the Ubuntu CD but run in LiveCD mode.

Open the Partition Editor.  IF any partitions are mounted, unmount them.

Remove ALL of the partitions.  Remove the Ubuntu CD.

Insert the Win7 DVD (if this IS a DVD, then it's most probably an Installation DVD). Since the drive has no partitions, you should then be able to install.

However ... if this is a CD (not a DVD), then it's most likely a Recovery Disk, and without a partition on the drive containing a Win7 Image file, you're not going to be able to get win7 back -- since this is NOT an installation DVD.

---

