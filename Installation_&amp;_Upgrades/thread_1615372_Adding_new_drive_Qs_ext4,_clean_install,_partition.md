---
title: "Adding new drive Qs: ext4, clean install, partition"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by openprivacy on 2010-11-06
I currently have two 640 GB drives in software RAID-1 on my home Ubuntu 10.04 workstation and after three years I need more space.  I love the drives (quiet western digital caviar greens and good price point) so I bought two more.  I was planning to simply add them as a second pair of RAIDed drives, but I came up with some options/questions and am looking for some suggestions:

1) I'm running EXT3 - would it be OK to format the new disk as EXT4 and have a mixed system?

2) I'm thinking maybe I should unmount (remove) the current disks, install a whole new system (EXT4, clean of cruft) on the new disks, and then mount the old disks, transfer all my files and reformat the old disks.  This has the added benefit of placing / and /boot on the new disks.

2a) If I install a whole new systems, I'll have the opportunity to switch back to 32-bit (I'm currently running 64-bit).  I've had some Java & Flash issues, but I've mostly been able to solve them.  But it is a little more difficult and I don't do the kind of large audio/video conversions and giant compiles that 64-bit is supposed to be best for.  So I'm wondering if I should switch back to 32-bit... though it feels a bit like a cop-out given that I'm running an e8400 64-bit CPU.  Any thoughts here are appreciated.

3) How to partition?  The machine will be both my web site development workstation (running Drupal/MySQL development websites for 10-30 clients) and my personal web server (running about 10 live sites with low traffic but lots of content).  So I'm going to want 300+ GB for web space so I'm thinking of mounting the new disks as /var.  Anything wrong with a 640 GB /var?

This machine is my livelihood as well as my family web and mail server.  It works fine now, so part of me thinks I should just add the new disks as EXT3 and be done with it.  But all these options...

Thanks!

---

