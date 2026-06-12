---
title: "Frugal install issues."
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by fealow on 2011-12-17
Hi there I'm new to Ubuntu 11.10 and trying to install it via a frugal install on my C drive (I currently have windows 7 installed). there are no problems with booting and the ubuntu desktop comes up. From there I click on the "install ubuntu" short cut on the desktop. after selecting the language It comes up with the partitioning section of the installer and tells me that i cannot install over the partition windows is on because the ISO image of ubuntu is on that C drive. Now thats fine, i understand that. So I select a free partition that has 277gb's free on it. it has no file system on it and ubuntu recognizes it as free space. i select this partition and go to format for ubuntu.

I choose the following options.

-logical
-ext3
-format partition -check-
- / (for the mountpoint)

when I go to install it tells me something a long the lines of there is no "root" and it fails. I'm at work so I cant give an exact report of the error that is given until i get home. but are there any known problems with frugal installs? or anything i haev to do partition wise to get it too work?

any help would be appreciated as i've been trying to install for days now. i first tried via making a live CD but the disk integrity checker fails every time and ive worked out it comes down to the brand of CD's I'm using (sony).

---

### Post by MAFoElffen on 2011-12-18
> **fealow said:**
> Hi there I'm new to Ubuntu 11.10 and trying to install it via a frugal install on my C drive (I currently have windows 7 installed). there are no problems with booting and the ubuntu desktop comes up. From there I click on the "install ubuntu" short cut on the desktop. after selecting the language It comes up with the partitioning section of the installer and tells me that i cannot install over the partition windows is on because the ISO image of ubuntu is on that C drive. Now thats fine, i understand that. So I select a free partition that has 277gb's free on it. it has no file system on it and ubuntu recognizes it as free space. i select this partition and go to format for ubuntu.

I choose the following options.

-logical
-ext3
-format partition -check-
- / (for the mountpoint)

when I go to install it tells me something a long the lines of there is no "root" and it fails. I'm at work so I cant give an exact report of the error that is given until i get home. but are there any known problems with frugal installs? or anything i haev to do partition wise to get it too work?

any help would be appreciated as i've been trying to install for days now. i first tried via making a live CD but the disk integrity checker fails every time and ive worked out it comes down to the brand of CD's I'm using (sony).
First, check md5sum of the ISO. On burning use the lowest speed possible. I don't know about Sony CD's. I use Imation's, because I get packs of 100 for really cheap. Enough that During dev-cycles, I go through a lot.  

Once you get a CD or USB going... If you select "Try" and get to the desktop, then get to the partitioner and delete the partition that was last created during the failed install.

Install from the desktop, that way ifthe installer freezes or errors, you can get to the /var/log/syslog... When the install gets to partitioner use the unused space.  

That sort of sounds like what you did.  But just to make sure.

The other way to do that is to create the partition from the LiveCD as extended on the unused space. Logical - 4GB's at ext4; Logical - Linux swap as the other 4GB... Install- When the partitioner starts up, use manual. Select the ext4 partition, mount @ "/", check the format box, continue ... Then I select the linux swap and continue...

I usually always do multi-boots the second way I mentioned. But I do all my partioning with a GParted LiveCD.  Just my preference.

---

