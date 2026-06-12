---
title: "[SOLVED] Help me get 8.04 on my Laptop"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by Vryko Lakas on 2008-06-14
So I've been using 7.04 in a dual-boot configuration (with XP Pro) on my laptop for a while now. I'd like to put Hardy on it. I'm not worried about losing any of the data on my Feisty partition at this point, got backups of my essential stuff. 
The issue I have is that during the first install of Feisty, I seem to have messed something up, so I started again after the process was already underway. Doing so, I wound up with two Feisty partitions instead of one. 
Well, everything seemed to work okay. But now I'd like to get rid of both Feisty partitions and have just the XP Pro and Hardy on here. So I need to 
-be able to make sense of and use GParted on the Hardy live cd, 
-get rid of the stuff I don't want, and 
-set up a partition for Hardy so I can do a clean install. 

I have a screenshot of what my laptop's hard drive looks like as of now. There is a 40GB Windows partition in front, a rather large unallocated block, and what looks like the two Feisty partitions after that. I think the laptop also has a hidden partition where the Asus backup utility stores stuff in the background. 

What I'd like is to leave the Windows partition alone for now, use all the other partitions except the Asus backup to create one new partition, and install Hardy in that. Can someone give me a newb-friendly walkthrough to help me make this happen?

---

### Post by Pumalite on 2008-06-14
Boot your Live CD. Go to the Terminal:
sudo gparted
Delete everything right of the unallocated space and have a merged 'free space'.
In that space, create 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.
Install Ubuntu, go Manual and use the already prepared partitions. Let grub install to MBR and you'll have dual boot.

---

### Post by Sef on 2008-06-14
Why do you have two swaps?

---

### Post by housam on 2008-06-14
+ pumalite advice , after you get the big unallocated space , format it to be an extended partition and create the new three partitions inside it as a logical partitions. this will avoid the limitation of creating more than 4 primary partitions in a single HDD as you already have 2 of them.

---

### Post by Pumalite on 2008-06-14
He has two /swap because he installed the OS twice and apparently, each time he added a /swap.

---

### Post by Vryko Lakas on 2008-06-19
Thanks for the advice. 
Unfortunately I'm not clear on how to move the partitions or merge the free spaces. I right-clicked on /dev/sda5, but I got the following error message:
Unable to delete /dev/sda5! Please unmount any logical partitions having a number higher than 5
But all the drive partitions have the option to unmount greyed-out. As far as I can tell by the Information menu, all the partitions ARE unmounted. I tried turning off all the linux-swap partitions, refreshed, and still nothing worked.

---

### Post by avtolle on 2008-06-19
You are booting from the Live CD here, correct? If so, you may have run into a problem with Gparted on the Ubuntu 8.04 (at least) Live CD. Minimize the Gparted window, see if there is a "volume" mounted on the desktop; if there is, right click on the icon, select "Unmount Volume", when icon disappears, maximize the gparted window and right-click the partition.

---

### Post by housam on 2008-06-19
> **Vryko Lakas said:**
> Thanks for the advice. 
Unfortunately I'm not clear on how to move the partitions or merge the free spaces. I right-clicked on /dev/sda5, but I got the following error message:
Unable to delete /dev/sda5! Please unmount any logical partitions having a number higher than 5
But all the drive partitions have the option to unmount greyed-out. As far as I can tell by the Information menu, all the partitions ARE unmounted. I tried turning off all the linux-swap partitions, refreshed, and still nothing worked.

Try to use the [[COLOR="Red"]_Gparted live cd_[/COLOR]]("http://gparted.sourceforge.net/livecd.php") , boot from it and do the partitioning task as you want . no partitions mounted

---

### Post by Pumalite on 2008-06-19
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779&release_id=592033](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779&release_id=592033)
Choose the iso.

---

### Post by Vryko Lakas on 2008-06-19
Thanks, avtolle. That is exactly the problem. I think that came up when I put in a thumbdrive and didn't remove it before going into GParted. 

I have deleted everything to the right of the XP Pro partition, as per pumalite and housam, and things are really moving along quickly now. 
I've got a new screenshot showing the partitioning scheme. I didn't see any options to label the new drives with names, so I just assumed that I was supposed to format the 1GB partition as linux-swap right now, and during manual install I will see the option to set the"/" and "/home" to their respective partitions? Or should I got back and delete the swap to let the installer handle that?

---

### Post by Pumalite on 2008-06-19
Follow post # 2

---

### Post by Vryko Lakas on 2008-06-19
Everything went smoothly! Thanks very much for the patience and help.

---

### Post by Pumalite on 2008-06-19
Good luck.

---

