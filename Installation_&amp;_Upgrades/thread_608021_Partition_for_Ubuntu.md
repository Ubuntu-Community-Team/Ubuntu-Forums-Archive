---
title: "Partition for Ubuntu"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by coasterfanryan on 2007-11-09
I have my live CD for Ubuntu and I want to install it on my 80 gig hard drive with Windows Vista. How Can I make a partition for Ubuntu? Do I do it from the Ubuntu installer? Thanks for replies =)

---

### Post by rsambuca on 2007-11-09
If you are going to add a partition, it is important that you use Vista's own Disk Management system to first "Shrink" the Vista partition.  You can then install Ubuntu into that free space.  Defrag your drive a few times and then Shrink it.  After, that, load up Ubuntu and you should be good to go!

---

### Post by dabl on 2007-11-09
Yep, what rsambuca said.

Also, free up at least 20 - 30GB, if you want to have room for some data. In the space that you free up, you will need to use GParted and make 2 partitions (this will make a total of 4 primary partitions on your hard drive, since Vista already uses 2).

One of the new partitions can be small, like 0.5GB, for Linux "swap".  Then the other one can be the rest of the available space, and you can install Ubuntu in that.  :guitar:

---

### Post by Pumalite on 2007-11-09
Maybe there is a way to set Page File to '0' in Vista. (later you restore it to original setting. This could give you more space)

---

### Post by coasterfanryan on 2007-11-10
ok, thanks for the help =)

---

### Post by mattchess on 2007-11-10
new here - hello everyone

The only Ubuntu experience I have so far is in a virtualbox on my laptop

As I type this, I am formatting a shiny new 500 gig drive that I have made two partitions on so far, and then left 40 gig of unallocated space.  Currently my machine is XP.  I am loading up vista into one of the new partitions, the other giant partition is for data.  The unallocated space is for Ubuntu.

Do I need to make the exra swap partition in that unallocated space with gparted, or will the install process make the partitions I need?  I thought the install/live cd already had gparted in it and it would do that automatically.

Also...the order of operations is to get vista working properly as a dual-boot...then get Ubuntu loaded.  

What do I need to do to make sure I have no boot loader problems?

Thanks...currently reading up in the forums but thought I would tag onto this thread.

---

### Post by Pumalite on 2007-11-11
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by dabl on 2007-11-11
> **mattchess said:**
> new here - hello everyone

Do I need to make the exra swap partition in that unallocated space with gparted, or will the install process make the partitions I need?  I thought the install/live cd already had gparted in it and it would do that automatically.

Also...the order of operations is to get vista working properly as a dual-boot...then get Ubuntu loaded.  



Yes, you'll want a 0.5GB partition for Linux swap -- that can be a primary partition.

Then for your fourth primary partition (Vista uses 2, and swap makes 3), you'll need to make it "Extended", so you can put 2 logical partitions in it, one for the root filesystem "/" and the second for your "/home" partition for data and settings.

Sounds like you've got the right sequence, doing Vista first.  I haven't done dual boot with Vista but with XP you definitely want Linux to be the last OS installed, so the bootloader works correctly.  :)

---

### Post by coasterfanryan on 2007-11-12
I want to partition my hard drive what do I do?  *Screen shot below*




[IMG]http://i149.photobucket.com/albums/s42/coasterfanryan/Screenshot.png[/IMG]

---

### Post by mattchess on 2007-11-13
Well all is working.  I already had XP on raid 0 array.  I added a 500 gig drive, and made four partitions - one for vista, one for ubuntu, a swap, and one big one for data.  Installed vista, then installed ubuntu 64 bit from a livecd (note that I needed to change splash to nosplash using F6 options, or I would get a blank screen after the menu).  When installing Ubuntu,used the advanced tab to tell it to install the bootloader to the right drive and partition (in my case hd2,1).  Then once installed I used easybcd edit to modify the vista bootloader to create an entry for ubuntu pointing to the right place.  I checked the box indicating the grub bootloader was not installed, and then on the neo-grub tab, clicked the button to configure the neo-grub menu file.  On that I needed to replace the references to an old kernal with the correct kernal number (three places I think).  Saved...and then everything ran just fine.

Took a few tries and a lot of reading up on the forums to piece that all together...hopefully those notes are of help to someone.

---

