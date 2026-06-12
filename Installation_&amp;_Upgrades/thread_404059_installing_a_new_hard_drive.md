---
title: "installing a new hard drive"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by 900donuts on 2007-04-07
heres the situation
i recently accuired some parts among the parts was a 160Gig hard drive (my current set up is a 10Gig and a 6Gig)
my computer case is restricted to 2 hard drives at a time
so i pulled out the 6Gig  and pluged in the 160 hopeing to find a way to transfer my installation. the computer reached the point of checking the file systems at boot then it screemed some thing about superblocks and i had the tell it to move on
i cant access the hard drive at all (though the disk manager sees it)

so i have 2 questions
1st how do i fix this?
2nd how do i transfer all my data to and settings to the new hard drive?

---

### Post by confused57 on 2007-04-07
You might want to burn a copy of the gparted live cd(30 mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

You could set up how ever many ext3 partitions you want, using the live cd...there's much more you can do with the live cd, move partitions, resize, check filesystem, etc.

Then to be able to access the partitions, you'd need to mount them:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

See the section on Mount Ubuntu(or Linux?) to be able to access the partitions and see the section on Partimage & Backing Up...there's a lot of useful info on this site that may help, including setting up a separate /home partition.

Another site to check out is the first link in my signature.

---

