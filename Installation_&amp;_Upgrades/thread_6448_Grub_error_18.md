---
title: "Grub error 18"
date: 2004-11-28
forum: Installation &amp; Upgrades
---

### Post by TheEHMan on 2004-11-28
I've partitioned this 6Gig hard drive to have a 32MB /boot drive at the beginning of the drive (as suggested by the troubleshooting guide) and allowed Ubuntu to partition the balance as needed.  Installation goes OK but when I reboot I get the GRUB ERROR 18 message.  What am I missing here?

---

### Post by thread_killer on 2004-11-28
Grub error 18, as I recall, is the selected cylinder exceeds the maximum cylinder value supported by the bios.   Can you place boot partition somewhere in the first 1023 cylinders?  That should oughta fix it.

---

### Post by TheEHMan on 2004-11-29
That's what I've been doing.  During the partitioning I put the /boot partition at the beginning of the drive then let it partition the rest as it wants. :?

---

### Post by wallijonn on 2004-11-30
If you installed to its own boot partition did you set the bootable flag for that boot partition?

---

### Post by TheEHMan on 2004-11-30
[QUOTE=wallijonn]If you installed to its own boot partition did you set the bootable flag for that boot partition?[/QUOTE]


Just for laughs I tried installing again.  Set the /boot partition at the beginning of the drive, set it bootable, let Ubuntu partition the rest of the drive as needed.  Install went fine, rebooted, same Error 18.

---

### Post by foal on 2004-12-07
You migh want to give some more information about your harddisk. One alternate option I can think of is trying to set your harddisktype in the bios to LBA. I'm having this problem right now aswell, but I'm reinstalling Ubuntu as we speak. So if I succeed you'll hear it  8-)

---

### Post by Nathanael Reveal on 2004-12-07
TheEHMan --

This may turn out to be a variant of the problem I struggled with. Here's what I did:

1. Set the drive up in LBA mode in the BIOS. That should give disk geometry data with 255 Heads, probably 63 sectors.

2. Install Ubuntu normally. Never mind the /boot partition at the beginning.

3. After the core is installed, Ubuntu reboots the machine. At this point, I set the BIOS settings to "Normal" which gave my 4GB drive a disk geometry of about 8800 cylinders, 15 head, and 63 sectors. It rebooted the machine and...

4. GRUB started up fine and the Ubuntu installation finished.

If this does work I really don't know why. But I'd love to know what kind of hard drive you have and what your LBA and Normal disk geometry was.

Best of luck!

---

### Post by orion_114 on 2004-12-14
[QUOTE=Nathanael Reveal]TheEHMan --

This may turn out to be a variant of the problem I struggled with. Here's what I did:

1. Set the drive up in LBA mode in the BIOS. That should give disk geometry data with 255 Heads, probably 63 sectors.

2. Install Ubuntu normally. Never mind the /boot partition at the beginning.

3. After the core is installed, Ubuntu reboots the machine. At this point, I set the BIOS settings to "Normal" which gave my 4GB drive a disk geometry of about 8800 cylinders, 15 head, and 63 sectors. It rebooted the machine and...

4. GRUB started up fine and the Ubuntu installation finished.

If this does work I really don't know why. But I'd love to know what kind of hard drive you have and what your LBA and Normal disk geometry was.

Best of luck![/QUOTE]
 I managed to get it working the same way ... had my drive set on LBA when I installed Ubuntu then when I rebooted it said Grub error 18, I changed the BIOS settings for the HDD to Auto and now it seems to be booting just fine.

---

### Post by TheEHMan on 2005-01-30
Looks like it was a problem w/ my hard drive.  I looked at it in BIOS and it was listed as 495M instead of 6.1G.  I tried a smaller drive and it installed but couldn't boot to a GUI because of lack of space.  I ordered a new 20G drive tonight so when it arrives I'll try it again.

---

### Post by jalapeno on 2005-02-26
[QUOTE=TheEHMan]Just for laughs I tried installing again.  Set the /boot partition at the beginning of the drive, set it bootable, let Ubuntu partition the rest of the drive as needed.  Install went fine, rebooted, same Error 18.[/QUOTE]

I was having this problem with 4.1 warty warthog, and re-tried similarly to this. However, I noticed that when you let Ubuntu set up the rest of the drive, it re-set a few options on the /boot partition that I just manually created! In particular, the /boot partition was no longer set to bootable, and it was set to not be touched (i.e. not formatted), nor to be mounted at /boot. I went back and fixed up these settings, and then proceeded. The system then re-booted normally.

Looks like the ubuntu installer needs a bug fixed.

For the record I have my BIOS set to LBA. I didn´t get any joy from setting it to Normal or Auto. My motherboard is an AX59Pro.

---

### Post by kenguard on 2005-03-26
[QUOTE=jalapeno]I was having this problem with 4.1 warty warthog, and re-tried similarly to this. However, I noticed that when you let Ubuntu set up the rest of the drive, it re-set a few options on the /boot partition that I just manually created! In particular, the /boot partition was no longer set to bootable, and it was set to not be touched (i.e. not formatted), nor to be mounted at /boot. I went back and fixed up these settings, and then proceeded. The system then re-booted normally.

Looks like the ubuntu installer needs a bug fixed.

For the record I have my BIOS set to LBA. I didn´t get any joy from setting it to Normal or Auto. My motherboard is an AX59Pro.[/QUOTE]
 Yep.  That was the problem on my installation as well.

I have and XP system that I'm loading Ubunto on a 2nd drive.

I rebooted off the CD and went through the install again, and looked at the partitions and they were not set up properly. 

During the original install, I choose the free space on my 2nd EIDE drive and let the install do the rest.  I normally hate wizards and want to see and do every detail, especially when I have a healthy bootable system that I can't afford to screw up on the other drive.   So I went as far as making sure Ubunto only used the free space on the drive and let it configure the partitions and do the rest. 

If anyone else installed their system and did some manual selections on their hard disk settings they may want to reboot off the CD and go through the install again and make sure to look at the partition's settings for the proper filesytem, bootable flag, and mount point and let it install again.  It should boot right up and still give you access to your other OS.

---

### Post by spanishfly on 2005-03-29
[QUOTE=Nathanael Reveal]TheEHMan --

This may turn out to be a variant of the problem I struggled with. Here's what I did:

1. Set the drive up in LBA mode in the BIOS. That should give disk geometry data with 255 Heads, probably 63 sectors.

2. Install Ubuntu normally. Never mind the /boot partition at the beginning.

3. After the core is installed, Ubuntu reboots the machine. At this point, I set the BIOS settings to "Normal" which gave my 4GB drive a disk geometry of about 8800 cylinders, 15 head, and 63 sectors. It rebooted the machine and...

4. GRUB started up fine and the Ubuntu installation finished.

If this does work I really don't know why. But I'd love to know what kind of hard drive you have and what your LBA and Normal disk geometry was.

Best of luck![/QUOTE]


thanks dudes... i tried and got the same problems with a 200gb HD, you guys helped so much.. ubuntu seems to be almost the perfect system for me... now if only RPMs worked worked...

---

### Post by kyriaap on 2005-03-30
[QUOTE=Nathanael Reveal]TheEHMan --

This may turn out to be a variant of the problem I struggled with. Here's what I did:

1. Set the drive up in LBA mode in the BIOS. That should give disk geometry data with 255 Heads, probably 63 sectors.

2. Install Ubuntu normally. Never mind the /boot partition at the beginning.

3. After the core is installed, Ubuntu reboots the machine. At this point, I set the BIOS settings to "Normal" which gave my 4GB drive a disk geometry of about 8800 cylinders, 15 head, and 63 sectors. It rebooted the machine and...

4. GRUB started up fine and the Ubuntu installation finished.

If this does work I really don't know why. But I'd love to know what kind of hard drive you have and what your LBA and Normal disk geometry was.

Best of luck![/QUOTE]

after step 1 my GRUB was starting fine... thnx a lot  8)

---

