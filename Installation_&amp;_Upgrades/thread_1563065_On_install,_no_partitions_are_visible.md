---
title: "On install, no partitions are visible"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by ub-pir on 2010-08-28
I have a machine (Asus P4PE + 120GB SATA HDD) which has been running Karmic very successfully for a long time. I recently made the decision to upgrade to Lucid via the Update Manager. The upgrade seemed to go OK - no obvious errors - but the resulting version of Lucid had some weird problems: desktop messed-up, printers wouldn’t work any more, etc. So I concluded I had been unlucky - the upgrade had gone wrong – and I tried to install Lucid afresh from a CD.

  Every time I try this, the install gets to the page to specify partitions – but this page is blank. No partitions are visible. The buttons to create a partition, etc. are all greyed-out. I have tried various boot options like removing “quiet splash—“, setting noapic/nolapic, etc. but nothing seems to work. I can happily run Lucid from the CD, no problem. I have also checked I have not got RAID accidentally installed, as mentioned elsewhere on this forum.

  I am able to reinstall Karmic so I know there’s a filesystem there but the Lucid installer cannot see it. Any suggestions on how to proceed very welcome! 

  At the moment my only option seems to be to regress to Karmic.

---

### Post by srs5694 on 2010-08-28
See [my Web page on this issue.](http://nessus.rodsbooks.com/missing-parts/index.html) The cause of your problem might or might not be the same, but it's worth checking.

---

### Post by Sef on 2010-08-29
1) What does the command ```
sudo fdisk -l
``` give you?  (Copy and paste the results here.)

2) Can you get GParted and take a screenshot?

---

### Post by ub-pir on 2010-08-29
> **srs5694 said:**
> See [my Web page on this issue.]("http://nessus.rodsbooks.com/missing-parts/index.html") The cause of your problem might or might not be the same, but it's worth checking.

This link is broken!

In frustration, I have now installed Debian Lenny - absolutely no problems. Lenny sees the HDD fine.

Thinking about it, I have anecdotal evidence that Lucid does not  like older hardware. My motherboard is 5-6 years old (?) and the Lucid install fails. I have tried updating a very old laptop to Lucid and that failed. (Had to clean install Karmic.) I have a work colleague who tried to install Lucid on an older PC with no success. But on the positive side, I have successfully updated Lucid on my pretty new desktop at work and clean installed on the very new laptops of my two kids. I think I read that Canonical spent a lot of time making sure Lucid booted quickly - I wonder if support for older hardware has slipped as a side-effect of that optimization? Just a thought... Regardless, I now have a working system, albeit Debian!

Edit: Have now gone back to Karmic! Lenny is not a patch in terms of usability. But I ain't gonna mess with Lucid until I update the hardware!

---

