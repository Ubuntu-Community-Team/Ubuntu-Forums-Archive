---
title: "Problem with partitioning through the qtparted program in ubuntu"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by DaddyBuckshaw on 2007-06-22
I recently attempted to install ubuntu on my desktop which currently has windows xp. during the xp install, i created just one partition (ntfs) that occupies the entire drive. i was under the impression the the qtparted program would allow me to resize this partition so that i could install ubuntu. once i come to the partition screen during the installation, it does not give me the option to resize the drive. i even canceled the install and opened qtparted through the menu and it allowed me to resize but once i clicked apply on the pending processes, it gave me an error saying that it could not resize. is there an alternate method of changing my current partition size or am i just doing something wrong right now?

---

### Post by 67GTA on 2007-06-22
One of the first options should be to resize the existing windows partition and use the free space. You can just choose to manually install, and then resize it by hand. It will give you an error message if there is a problem so you can see what is happening. Read through the link for more info [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by DaddyBuckshaw on 2007-06-22
> **67GTA said:**
> One of the first options should be to resize the existing windows partition and use the free space. You can just choose to manually install, and then resize it by hand. It will give you an error message if there is a problem so you can see what is happening. Read through the link for more info [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

thats what the guide says but it did not work for me like that. when i got to the initial partition screen, it did not give me the option to do the "guided" resize. i found a guide that told me to go to "xterm" and use ntfsresize to change the ntfs filesystem. i then used fdisk to change the partition size. i went back into windows so that it would run chkdsk and then restarted once more so that it would write the journal entry (?) and then loaded back into ubuntu. i got through the partition portion fine but now, when i enter in my user name info and press forward, it just sits there working but nothing changes (i let it run overnight and it was still on the same screen this monrning).

---

### Post by rbmorse on 2007-06-22
The most expedient solution would be to go to Sourceforge.net and download the gparted liveCD. This is a self-booting to a minimal Linux and will run the gparted partition tool.  

Gparted is similar to Qtparted (i.e., a GUI front end for the Linux parted utility) but has received more development and will resize NTFS partitions. 

In theory, this function is still "experimental," but I have used it with much success as have others.  If you look at the bug list on Sourceforge you won't find anything particularly troubling for the current release. 

I would use the Gparted LiveCD to resize your existing NTFS partition (this will take a long time...perhaps several hours) and leave the unpartitioned space created on the drive as it is, empty, unpartitioned space.  

When you run the Ubuntu installer, tell it to put itself in the largest unpartitioned space available. It will create and format / and /swap automagically. Once the install is complete you can modify the installation as desired. 

If nothing else, this method is the one with which I have had the most success in having GRUB come up installed and configured correctly for both Ubuntu and XP.

---

### Post by DaddyBuckshaw on 2007-06-22
> **rbmorse said:**
> The most expedient solution would be to go to Sourceforge.net and download the gparted liveCD. This is a self-booting to a minimal Linux and will run the gparted partition tool.  

Gparted is similar to Qtparted (i.e., a GUI front end for the Linux parted utility) but has received more development and will resize NTFS partitions. 

In theory, this function is still "experimental," but I have used it with much success as have others.  If you look at the bug list on Sourceforge you won't find anything particularly troubling for the current release. 

I would use the Gparted LiveCD to resize your existing NTFS partition (this will take a long time...perhaps several hours) and leave the unpartitioned space created on the drive as it is, empty, unpartitioned space.  

When you run the Ubuntu installer, tell it to put itself in the largest unpartitioned space available. It will create and format / and /swap automagically. Once the install is complete you can modify the installation as desired. 

If nothing else, this method is the one with which I have had the most success in having GRUB come up installed and configured correctly for both Ubuntu and XP.

thanks for the info. im going to try this out right now.

---

### Post by DaddyBuckshaw on 2007-06-22
> **rbmorse said:**
> The most expedient solution would be to go to Sourceforge.net and download the gparted liveCD. This is a self-booting to a minimal Linux and will run the gparted partition tool.  

Gparted is similar to Qtparted (i.e., a GUI front end for the Linux parted utility) but has received more development and will resize NTFS partitions. 

In theory, this function is still "experimental," but I have used it with much success as have others.  If you look at the bug list on Sourceforge you won't find anything particularly troubling for the current release. 

I would use the Gparted LiveCD to resize your existing NTFS partition (this will take a long time...perhaps several hours) and leave the unpartitioned space created on the drive as it is, empty, unpartitioned space.  

When you run the Ubuntu installer, tell it to put itself in the largest unpartitioned space available. It will create and format / and /swap automagically. Once the install is complete you can modify the installation as desired. 

If nothing else, this method is the one with which I have had the most success in having GRUB come up installed and configured correctly for both Ubuntu and XP.

i just booted from the gparted live cd (turns out this is the same application i initially used in the ubuntu live cd) and it shows that i have 22 gigs left over. this means that i partitioned everything properly using ntfsresize and fdisk. i am still assuming that the installation will stall though since it was like this yesterday when i was tryin to install

---

### Post by rbmorse on 2007-06-22
The only thing I can offer is make sure you chose carefully when picking setup options.  You may have a problem with disk geometry that isn't immediately apparent, and that may be causing the installer to barf. Let us know how the next attempt turns out.

---

