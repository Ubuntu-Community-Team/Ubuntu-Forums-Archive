---
title: "trying to install on 2nd drive, GRUB wont install"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by sgietler on 2006-03-12
hello

I have a windows XP computer with a 80gig hard drive. I installed a second 160gig hard drive to install Ubuntu on. I created an ubuntu install disk, booted with that disk,  partitioned the 160gig slave drive, and installed Ubuntu on the second drive. It installed the basic package and the additional file. However, near the end of the install it did not try to install GRUB like I thought it would, it instead tried to install a LILO booter, but that didn't work...

I would like my system to dual boot and give me a choice of windows or linux. I did not change my partitions at all on my 80gig Windows XP hard drive (the master), is there a step that I need to do to get GRUB installed and my system to dual boot?

Right now it wont install GRUB, and it only boots into windows XP. Any ideas what I need to do?

thanks alot!
Scott

---

### Post by FredSambo on 2006-03-12
well your BIOS is set to boot from the master drive, so you'll probably have to install GRUB on your windows drive and set it to dual boot linux and windows, i think.

---

### Post by sgietler on 2006-03-12
[QUOTE=FredSambo]well your BIOS is set to boot to the master drive, so you'll probably have to install GRUB on your windows drive and set it to dual boot linux and windows, i think.[/QUOTE]

hey Fred
yes, I know that, but I chose "install GRUB" and I couldn't install it on my windows drive for some reason, I can't remember the exact problem, do I need to change the windows drive's partitions at all to get this to work? Let me try it again and I will let people know the exact problem....

Scot

---

### Post by FredSambo on 2006-03-12
all you need to know about installing GRUB is here:

[https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29](https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29)

---

### Post by FredSambo on 2006-03-12
you could also create a boot floppy and just pop it into your drive when you want to boot linux.

---

### Post by FredSambo on 2006-03-12
did you check your boot.ini file in windows?

---

### Post by sgietler on 2006-03-12
thanks fred

ok, I rebooted with the install disk
it asked me for the country, computer name, etc.
then I got the "partition disk" menu
I hit "back", chose "install grub", and it brought me again to the partition disk menu

(note - I had earlier today partitioned my 2nd drive and installed ubuntu on it)

I chose "manually edit partitions", and here is what it displayed:

IDE1 master (hda) 80GB
  #2 primary 3.9GB (darkened smily face) fat32 /media/hda2
  #1 primary 76.1 GB (lightning bolt) (darkened smily face) ntfs /media/hda1
  pri/log 8.2 MB - FREE SPACE

IDE1 slave (hdb) 160GB
  pri/log 160BG FREE SPACE

I'm not sure why its not showing the /ext and /swap partitions on hdb that it created before... 

anyways, any idea what to do next?

thanks,
scott

---

### Post by cotcot on 2006-03-12
You can redo the grub install (for instance following this : [http://www.ubuntuforums.org/showthread.php?t=76652&highlight=MBR+messed](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=MBR+messed) ) to see exactly where the installation of grub was different as expected.
It works also with the floppy. That is the way I do the dual boot on my PC1. Floppy in is Breezy, floppy out is XP. (make XP partition active again afterwards with fdisk or so)

---

### Post by FredSambo on 2006-03-12
it looks like the easiest way would be to go with a boot floppy, indeed.

---

### Post by confused57 on 2006-03-12
This thread may help

[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)

---

### Post by FredSambo on 2006-03-12
the search function r00ls.  :p

---

### Post by sgietler on 2006-03-12
thanks everyone,

everything installed fine, I have ubuntu up and running now, GRUB installed and worked fine. 

all I did was choose "manual partition", and manually partitioned the slave drive. it then reinstalled ubuntu. I never had an option not to format the drive, it seems like the previous partitions and install I did on the drive never "saved", I don't know why.

Scott

---

