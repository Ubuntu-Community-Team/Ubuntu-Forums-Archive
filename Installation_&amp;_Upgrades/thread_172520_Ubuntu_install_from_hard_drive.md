---
title: "Ubuntu install from hard drive??"
date: 2006-05-08
forum: Installation &amp; Upgrades
---

### Post by Foreststorm on 2006-05-08
I downloaded the DVD iso and am looking to install ubuntu from my harddrive.

Now I have done this with several other flavors of linux but ubuntu seems to be different and I cannot figure out how to get it accomplished.  Other flavors would offer a mini iso that I would burn to a CDRW disc that would be bootable for installation and then I would just select to install from harddrive partition /dev/hdb2.  I don't see any of these options for ubuntu and I don't see any instructions on how to do this. (maybe I am just blind)

Some flavors I have installed before, I had to extract the files from the iso to get the harddrive install to work other flavors would install direct from the iso files.  I have the ubuntu dvd iso on a separate partition and I have also extracted all the files from the iso and have put them in that partition.

So I need to come up with a way of getting the installer to install from the files found on /dev/hdb2.

I did manage to get an installer to run by the following one of the following menu.lst items in my grub bootloader: ```
title Install Ubuntu
    kernel (hd1,1)/install/vmlinuz root=/dev/rd/0 vga=normal ramdisk_size=14972 rw --
    initrd (hd1,1)/install/initrd.gz


title Install Ubuntu 2
    kernel (hd1,1)/install/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
    initrd (hd1,1)/install/initrd.gz
``` I believe the second one got the installer to run but then it wouldn't install because it was looking for a CD that wasn't there.

Just some side notes I have 2 harddrives, CD-burner, floppy drive.  I have winxp pro installed as well as two variations of Suse Linux 10.1 RC3.  Grub is the current bootloader in the MBR.

---

### Post by Foreststorm on 2006-05-08
On second thought I think I will just download and install via the 1 CD installation instead of racking my brain over the dvd iso.  I'll just have to do some extra installations later to get all the packages I want installed.

But if anyone comes up with some ideas do let me know... heck I can always make room for another linux install.

---

### Post by Dr. Nick on 2006-05-08
[QUOTE=Foreststorm]On second thought I think I will just download and install via the 1 CD installation instead of racking my brain over the dvd iso.  I'll just have to do some extra installations later to get all the packages I want installed.

But if anyone comes up with some ideas do let me know... heck I can always make room for another linux install.[/QUOTE]

here are a few ideas.
You may have seen them, you seem to be using the same logic they are. 

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)
[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

I have done this in the past and it worked fairly well if I recall, but I might not be much help now :) Even though they are using grub for dos you can adapt that to a existing grub install on linux. The one cavet to this approach I have experienced is that if the install fails after writing a new grub or formating partitions you are screwed.

All that being said I just got the new Dapper live CD and preformed a install totally from the GUI, It was cool. If you dont want dapper yet then the breezy install cd would probably be easier then a hard drive install. If you want you can add the dvd iso to your apt sources so you wouldnt have to redownload anything.

---

