---
title: "Move Ubuntu to new HDD controller?"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by Mugendai on 2006-06-23
I have Ubuntu installed in this old dual celeron mobo that has standard DMA IDE ports, and two extra Ultra DMA ports.  I'de been running it on the standard DMA ports, but I got a new hdd for the system, and I've already transfered ubuntu to it, and have it running on the new hdd using the dma controller.  But I want to move it to the Ultra DMA controller.

The controller is handled seperately, its not like modern ones... It is a Highpoint HPT366.  When I connect the ubuntu drive to the HPT366 controller it starts booting, gets through grub, it times out on mounting the root filesystem.

I'm thinking either it ends up with different drive letters(note I've tried with only it connected, no other drives, still didnt go).  Or that some hardware driver needs loaded to support the controller before it can mount the FS.

Could someone please help me to get ubuntu to run off the hdd on the hpt366 controller?

---

### Post by rowanparker on 2006-06-23
I would think doing something like that would need a reinstall but am I right somebody?

---

### Post by MetalMusicAddict on 2006-06-24
Watch out about installing a new controller. It looks as though Dapper is enumerating drives on the PCI IDE controller 1st and causing no end of problems for people with PCI controllers. Im dealing with this now. Look [HERE]("http://www.ubuntuforums.org/showthread.php?t=191885").

---

### Post by Mugendai on 2006-06-24
FYI, this is an onboard controller.  Though I think it likely functions very similar to the PCI version.

---

### Post by Mugendai on 2006-07-04
Can someone suggest any other forum, maybe one with more advanced users?  This forum never seems to be able to help me with anything...

And I still dont have an answer to my issue.

---

### Post by ezsit on 2006-07-05
One way to start would be to attach your hard drive to the controller you intend to use and boot from the live cd. Once booted, take a look at the fstab file and see where the filesystems are located and note the device names for each filesystem.

Chroot into your / on the hard drive and edit the fstab to match and you might be done. I vaguely remember there is another file that controls mount points, but you'd have to look into this further. I hope I've given you some ideas on how to possibly get started.

---

### Post by ezsit on 2006-07-05
Forgot to mention that you would also have to edit your /boot/grub/menu.lst file on the hard drive when you're chrooted to change the root filesystem to point to the correct device. I'm trying to do this from memory, so bear with me. Look at the /etc/mtab file as well, this file may also need to be edited with the new device info. Also, the /boot/grub/device.map file may also need editing.

Also, look at the newsgroup alt.os.linux.debian

---

### Post by Mugendai on 2006-07-10
Thanks for the info ezsit.  I have one question though.  I was to understand that there is some difference in the way Breezy and Dapper sort the hdd's.  I haven't found a live CD for Dapper, is there one?

---

### Post by rowanparker on 2006-07-10
The normal Dapper CD is the live CD, it has the GUI installer on the Live CD or you can use the alternate CD for text-based installation.

Rowan.

---

### Post by mssever on 2006-07-10
> **Mugendai said:**
> Thanks for the info ezsit.  I have one question though.  I was to understand that there is some difference in the way Breezy and Dapper sort the hdd's.  I haven't found a live CD for Dapper, is there one?

Go to [http://www.ubuntu.com/download](http://www.ubuntu.com/download), select a mirror, and grab an iso from the desktop section.

---

### Post by dev3d on 2007-10-18
can you activate hardware raid 1 on this HPT366 ?

i am about to install ubunto 7.10 on my old BP6 dual vceleron box and i would like to have raid 1 on 2 250 gig drives

thx

---

