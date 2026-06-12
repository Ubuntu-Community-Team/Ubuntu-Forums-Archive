---
title: "[SOLVED] Removing Win98, repartition hda &amp;amp; adding /home information"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by ali_bongos_dad on 2008-06-27
I'm presently dual booting Ubuntu Feisty Fawn and Windows 98 although I've not used Windows for over a year and I now want delete it and upgrade to Hardy.

My question is how do I delete Windows, keep the information held on Feisty's /home partition and repartition my hda so that / is at the beginning of the drive, where Windows used to be, then swap followed by /home,
then install Hardy and add the stored information in /home from Feisty?

Hope that's clear enough for everyone to understand.

Thanks.

---

### Post by housam on 2008-06-27
Boot from ubuntu live cd and  take a screen shot of Gparted image  and post it . it will help  putting the sequence of what you want.

---

### Post by Afkpuz on 2008-06-27
Well, I know this isn't the only way, but just back up your homefolder information to a jump drive, then reinstall hardy over everything.  However, there are other methods.  That method works well as long as you make sure you copy everything you want/need onto a usb drive.

---

### Post by ali_bongos_dad on 2008-06-27
Thanks for the quick replies.
Here's the screen shot

---

### Post by housam on 2008-06-27
If you already did backed up your data on /home partition sda4 then Use [[COLOR="Red"]_Gparted live cd _[/COLOR]]("http://gparted.sourceforge.net/livecd.php")to delete the fiest 3 partitions ( windows, swap & feisty ) leaving one unallocated space . 
then divide this unallocated space to 2 new partitions ( ext3 format for the root / and a smaller one for the swap -  swap = RAM if your ram is more than 1 GB )
during the installation choose the manual way and assign the / root partition.
Hardy will detect your /home partition during the installation.

---

### Post by ali_bongos_dad on 2008-06-27
Of course!!  It's blindingly obvious when you think about it. Thanks very much

---

