---
title: "Dual boot MBR intact"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by Lowrie on 2007-06-10
Sorry if this question has already been asked. I briefly looked through the forums but found nothing. So if i missed something please forgive my incompetence.

To the problem at hand. I am currently attempting to dual boot by Dell inspiron 640m laptop with windows and Kubuntu. I am reading Matthew J. Miller's guide to dual booting without changing the MBR. [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("Here") is the link. Everything has worked perfectly to plan until installation step 8. 
> Now, we're going to use the Linux System Rescue CD to dual boot using Window's bootloader. Start by making a mount point for the OS Share partition:
mkdir /mnt/osshare
Then, mount the partition:
mount -t msdos /dev/hda6 /mnt/osshare
If you're not sure which device (e.g., /dev/hda6) your OS Share partition is, you can use QTParted to see the device number. Finally, we'll create a file that Windows can use to boot Linux:
dd if=/dev/hda2 of=/mnt/osshare/ubuntu.bin bs=512 count=1
Where /dev/hda2 is the device for your Linux partition (again, use QTParted to find the device number if you're unsure).
When i use the System rescue CD mount the partition i get the error that says something along the lines of "file or location does not exist". When i read that i automatically thought i had the wrong hard drives. So i when into Kubuntu's QTParted partitioning tool to see the directory files. Nothing was wrong.

Sorry for the inconvenience, any help is greatly appreciated.

---

### Post by merlinus on 2007-06-10
This seems unnecessarily complicated.  Ubuntu will set up grub, which will allow you to boot either windows or ubuntu.

This may help:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Good luck!

-merlin

---

