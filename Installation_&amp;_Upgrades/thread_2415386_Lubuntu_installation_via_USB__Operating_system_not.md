---
title: "Lubuntu installation via USB : Operating system not found."
date: 2019-03-25
forum: Installation &amp; Upgrades
---

### Post by confusedkoala on 2019-03-25
Hi all

I have an old Sony Vaio laptop that gives the operating system not found perpetually after I tried to install windows 10.

I gave up and tried Lubuntu instead. In the first installation I saw the actions taken were to wipe all 4 partitions and end up with 1 Lubuntu.  I proceed and I did manage to boot normally.

As it was a new system for me and I was doing some exploring, I tried to reinstall a clean start.
This time the installation showed me that 1 partition will be wiped and 4 ( or 3 ) will be created. I proceed and the operating system not found issue is back.

How can I get the 1 partition style of installation again? Now it all defaults to the multiple partitions kind .. :(

---

### Post by yancek on 2019-03-25
> I have an old Sony Vaio laptop that gives the operating system not found perpetually after I tried to install windows 10.

Was there any operating system existing when you tried to do this?  I ask because later in the post you indicate when you installed Lubuntu the first time, it wiped 4 partitions?  What partitions?

Did you re-install Lubuntu and are now back to the operating system not found error is back?  How is the boot priority set in the BIOS?  Have you changed it so the drive on which you installed Lubuntu is set to first boot priority?

If you have nothing on the drive, you could try installing again with the manual method (Something Else) and create your partition beforehand with GParted.  You could create a new partition table first which will eliminate any data on the drive for all intents and purposes.

---

