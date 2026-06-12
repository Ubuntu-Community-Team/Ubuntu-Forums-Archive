---
title: "Need help to replace 9.04 partition with 10.04!?"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2010-05-20
Hello There!:)

Posting this thread using the DEMO variant of 10.04, congrats to the developers that it didn't fail like that of 9.10 for all those who have configured their Modems & Routers to work in 'Bridge Mode'!

Here's my concern:::

I wish to immediately replace my 12GB partition, currently kept aside for 9.04 with 10.04.How to accomplish the same? 

Installation screen does comes up with 'Manual' preference, but it is confusing & am unable to make any decision owing to great excitement!?

Guys..please help me...Its becoming irresistible to use 10.04 in its full strength!:guitar:

---

### Post by darkod on 2010-05-20
If you have data to save from that partition, obviously do that first. If not just proceed with the installer.

Select Manual Partitioning. That will list all your disk(s) and partitions. Click on the 12GB partition where you want to install 10.04. Then click on the button Change on the bottom.

Change the filesystem from Not Used into ext4. Tick the format box to format the partition so there are no remains from 9.04. Select the mount point as /.

If you have separate /home partition currently, you will need to do the same for it, just DON'T FORMAT it, and select the mount point as /home.

The new install of 10.04 should automatically pick up your swap partition and use it.

That's it.

---

### Post by ratcheer on 2010-05-20
If you want to replace it with a fresh install of 10.04, you select the partition and tell it to format it and then choose it as the mount point for / (which is root). If you do this, you will lose everything you had in Karmic, so make sure to back up anything you need before you do it.

If you want to upgrade it, keeping what you had before, you need different instructions.

Tim

---

### Post by Saurabhdua on 2010-05-20
Hello again!

Now posting this one through 'Full-Installation' of 10.04.I simply made use of common sense to 'Right Click' the 12GB partition & choosing 'Delete'.It got converted to 'Free Space'.Then made the necessary changes, very much like you told so. For every drop-down menu,I chose the very first option & that's it!

Finally Mr. BEAN has installed 10.04 alongside Windows XP. Woalla..!
The BEST part:::'Internet Works & without any hassles.

One more thing Darkod:::?? What do you mean by /home partition?

---

### Post by Hampshire Hog on 2010-05-20
I hope you don't mind but I have a similar problem.  I want to replace Ubuntu 9.04 with Ubuntu 10.04.  I downloaded the ISO file and burnt it to a CD using Brasero Disk Burner.  This completed successfully.  After placing it into the CD-Rom drive I switched on the PC, But it failed to boot.  I have made the CD-Rom drive as the first drive seen at Boot-up.

Any ideas of what the problem may be.  Your words of wisdom would be greatly appreciated.

Many thanks

HH
:confused:

---

### Post by Saurabhdua on 2010-05-21
Absolutely No Idea, I got hold of the latest version through "Ubuntu Ship it".

Mine was a smooth sailing except the last stage where, despite 100% installation & popping the disk out(automatically), screen got struck with some "Weird" I/O Error!?

Nevertheless, I gave it a 'Forced' shutdown & am very much using it!

I have even made an immediate transition to 'Google Chrome' as my default Browser.Even better smooth sailing......!

---

### Post by Hampshire Hog on 2010-05-21
Hi All .............. I have now managed to get the Ubuntu 10.04 CD to boot up eventually, after many attempts.  This is the disk I burnt from the ISO file download I did yesterday.  I then ran the Live CD version and took a look around.  It looked very impressive.  I will be having a go at installing Ubuntu 10.04 in the next day or so.  Hopefully the installation will run as smooth as it did for me with Ubuntu 9.04.  I will be doing a completely clean install so if I run into any problems I may be back.  However, in the mean time may I thank you for your help/advice/info'.

Regards

HH
:popcorn:

---

