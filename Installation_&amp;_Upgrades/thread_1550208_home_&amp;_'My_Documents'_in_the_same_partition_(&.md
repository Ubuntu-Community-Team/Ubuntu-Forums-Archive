---
title: "/home &amp; 'My Documents' in the same partition (&amp; encrypting it)"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by leo738 on 2010-08-10
Hello All,

I've been running Ubuntu for a while now & had my laptop as a dual boot as follows (drive space is approx):

C: Windows XP (25GB)
D: 'My Documents' (80GB)
E: Ubuntu (15GB)
F: /home (38GB)
G: Swap (2GB)

The system was running fine but I'd like to encrypt the whole drive (as per [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=761530](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=761530) ) and while preparing the laptop I thought I'd reconfigure the partitions to reduce redundant space & simplify things:

C: Windows XP (25GB)
 D:  /home with a 'My Documents' folder (118GB)
 E: Ubuntu (15GB)
 F: Swap (2GB)
 
What I'm wondering is if anybody has successfully tried this? I'll probably use (as before) [http://fs-driver.org/](http://fs-driver.org/) & ext3 with an I-node size of 128. Besides this any downsides? As mentioned I'll probably encrypt with Truecrypt (running on both XP & Ubuntu) so I should be able to access the D drive from both OS's (I think!)

Thanks for any info/ pointers,

Leo

---

