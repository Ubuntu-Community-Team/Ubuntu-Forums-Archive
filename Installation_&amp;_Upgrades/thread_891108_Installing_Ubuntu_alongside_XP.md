---
title: "Installing Ubuntu alongside XP"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by JBD88 on 2008-08-15
Sony Desktop from 2004
Pre-installed C drive 15Gb which has the O/S, program files, and little else.  I just added SP3 and it barely fit.

D drive is 165 Gb with about 75 Gb free.  I am defraging it as we speak.

My question is, when I boot up the Ubuntu CD and it asks me about partitioning, will it give me the option to make the C drive bigger without disrupting the XP install?  I want to have dual boot capabilities.  Was just sort of hoping it would give me the chance to make C bigger as it's basically full.  Could not even defrag it because it was less than 15% free space.  I've deleted all I can.

My plan would be to put Ubuntu on the the D drive, or at least on a new drive that I steal space from D to make.  I assume that's how it works.  20 Gb enough for my Linux?

Appreciate any comments.  I've very new to this.

Joe

---

### Post by Pumalite on 2008-08-15
Better 'shrink' XP ahead of time with Gparted Live CD (less chance of errors):
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Right click on XP and choose 'resize' from the menu.

---

### Post by JBD88 on 2008-08-15
what does the shrink do?

---

### Post by Pumalite on 2008-08-15
Gives you fre unallocated space for Ubuntu. You can continue and on that space create 3 'New' partitions:
10 GB for '/'
The rest minus the amount of your RAM for /home
The amount of your RAM for /swap. Remove Gparted . Plug in your Ubuntu Live CD, install, go 'Manual' at the partitioner and use the already prepared partitions.

---

### Post by JBD88 on 2008-08-15
This seems to be working.  I had to shrink down the big D drive, then move it to the right.  And then I think it will let me move the C to the right with the space created moving D.  I also left about 50 Gb on the end for Linux.

I'll create the 3 drives you mention.  Which type?  I know it's not NTFS, right?

Thanks for the help.  I would have done this a while ago had I just asked.

Joe

---

### Post by Pumalite on 2008-08-15
You can format it ntfs, but making the partitions I told you about would be better. Having a separate /home allows you to keep your data and settings in case of a reinstall.

---

### Post by JBD88 on 2008-08-16
Ok, so far so good.  I shrunk and moved my D drive.  but the C Drive is apparently not moveable, so so much for making it bigger.  At some point, I probably won't be able to add updates to XP, but maybe I'll be a full time Linux user by then.

For the 3 mounts you suggested, which filesystem do I choose?  ext2, ext3 or the others?  I noticed one type is called Linux-swap.  Is that what I use for the /swap?

Almost there.  Thank you.

---

