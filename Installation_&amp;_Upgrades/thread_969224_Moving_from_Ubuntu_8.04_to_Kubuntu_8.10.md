---
title: "Moving from Ubuntu 8.04 to Kubuntu 8.10"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by daver94 on 2008-11-03
I have been using Ubuntu 8.04 since it came out.  I would like to move to Kubuntu 8.10.

I have a new hard drive on which I would like to install Kubuntu.  I would like to keep the /home directory from my old installation.  I did not partition my old drive, so I'm not really sure how to go about this.

[LIST]
[*]Can I just install Kubuntu on my new drive and then copy the /home directory?
[*]How do I recreate the users on the new installation?
[*]What would be a recommended partition scheme for the new installation?  My new drive is 1TB.
[/LIST]

Any other thoughts would be appreciated.

---

### Post by ajgreeny on 2008-11-03
> 
[LIST]
[*]Can I just install Kubuntu on my new drive and then copy the /home directory?
[*]How do I recreate the users on the new installation?
[*]What would be a recommended partition scheme for the new installation?  My new drive is 1TB.
[/LIST]
Yes you can do more or less what you suggest in your first two points to get your files and data to the new home folder or partition.  If you have the same username and password there may not even be any ownership problems, but if there are we can sort that out for you easily.

For the third query, I suggest you chose manual partitioning in the install, when it gets to that part.  10GB is enough for root, leaving plenty of empty space for future package installation, the rest, except for maybe 1 or 2GB as swap, can be your home partition.  Some people go for very complicated partitioning but I have yet to see a good reason for anything other than the three I suggest here.

If you are going to a KDE Kubuntu installation from gnome, there will be a lot of hidden files in your current old home that will not really be needed, such as .gconf, .gconfd, .gnome, .gnome2 .metacity and others that relate to gnome only, but with a disk of that size, I wouldn't worry about copying all of them; you never know, you might want to add ubuntu-desktop package on to your kubuntu install, in which case they would be very useful

---

### Post by urugTON on 2008-11-03
Daver,

I added Ubuntu 8.10 to my Vostro laptop this weekend.  Since I'm new to linux, I studied up on grub and researched having multiple linuxes (lunixi?) on the laptop.  One of the more helpful posts for me is at:

[http://www.go2linux.org/dual-boot-two-linux-distros-debian-and-mandriva](http://www.go2linux.org/dual-boot-two-linux-distros-debian-and-mandriva)

I do have my /home in its own partition.  I also had 30 GB free (Vista would only give back 80GB of the 160 GB drive - I'll see to that problem later). 

The actual installation was anticlimactic.  The only "tricky part" was selecting manual partioning, specifying the existing /home mount point and setting up a new partition for /.  

The 8.10 installation process took care of everything else.  I was pleasantly surprised at how smoothly the partitioning went and that grub needed no manual attention after the fact.  The two Ubuntus share the /home without complaint.  I booted Vista to see if it was upset.  It did a resume and proceeded to work happily after the upgrade.

FWIW, I have a 20 GB /home and 10GB each for my two /.  I'm thinking your 1 TB should be adequate.  :)

I have only one user on the laptop, so migrating users was not an issue for me.

So far, 8.10 has worked very well.  Much to my surprise it configured my wireless connection with only the passkey for my WPA connection.  All else seems to work fine, but I'm not a terribly demanding user either.

Hopefully all this praise applies to kubuntu.

Good luck.

---

### Post by urugTON on 2008-11-03
Moved to 8.10 Upgrade/Installation thread.  Transmit finger too fast. :(

---

