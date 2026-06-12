---
title: "error during ubuntu installation after vista"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by madeel on 2011-01-06
I installed windows Vista and then went on to install Ubuntu 10.4 with liveCD. However, when installation reached to 66%, a message came up that an irrecoverable error occurred. And took me back to Ubuntu trial environment. 

I had used this CD earlier to install Ubuntu. So I don't think so there is any error on the CD. I believe it is the installation with vista which is causing the problem. 

Some pages have suggested that I should first resize the vista from itself and then I should have gone for installing Ubuntu. The problem was that it wasn't clear whether I should create three partition (vista,ubuntu,swap). So I thought let Ubuntu do it. But now I am stuck. What should I do now?

I am scared to restart the system. Should I download ubunutu 10.10? What I am not sure whether live CD would allow me to burn it. I am imagining 10.10 may have resolved some issues which 10.4 has with vista.

---

### Post by fabricator4 on 2011-01-07
Actually, I think the problem is with the CD. As burners age there can be problems.  Problems like dust on the lens or faulty CD's/DVD's are a temporary irritation, but a burner that makes disks that aren't reliable is a major pain.  My desktop machines may get 2 or 3 new burners over the course of their lives.  One of them is ready for a replacement right now - the live CD I made with it couldn't be read in other drives.

Boot windows and see if you can read all of the disk by copying it to a directory on the hard drive.

Chris

---

### Post by Bucky Ball on 2011-01-07
Stick with 10.04 LTS. Latest is definitely NOT always the greatest and 10.10 is having some issues at the mo. 

How much free space have you got there? Is Vista on the whole disk? If so you need to resize it or install again (easier and safer) leaving free space for the Ubuntu install. V IMPORTANT: Defragment the Vista partition before resizing!!! Windows spews data all over the available disk space and if you don't defrag first you will get inaccurate info on how much you can shrink the partition.

If Vista not on whole disk and you already have free space, try again (although could be optical drive as mentioned) but this time choose to manually partition. It is wise to add a separate /home partition:

/ = root, where the OS lives, 15-20Gb is plenty;
/home = your stuff and settings, big as you like;
/swap = 2Gb should be fine, 4Gb if you intend using hibernate. 

This way if you screw the OS with experimentation or anything else your personal data is safely on a separate partition. ;)

Good luck.

PS: 10.10 resolved problems with installing with Vista? Ubuntu and Windows have nothing to do with each other and this is not your issue. Forget that line of attack. In fact, the Ubiquity installer in 10.10 is wiping Windows installs in some cases when trying to do side-by-side installs at the moment. _***AVOID***_ for now. Yours is another issue concerning not enough free space or faulty disk/optical drive. ;)

---

### Post by madeel on 2011-01-07
Many thanks both of you for insightful comments. It has improved my understanding. 

Before I read your response, I had tried once more. Now I see three OS installed side by side. I think, the best option is re-install Vista having two partition. 

By the way, how can I define the separate partitions like \root, \home as you have described. It is a very good idea.

---

### Post by Bucky Ball on 2011-01-07
Install Vista on a partition big enough for it and leave free space for the Ubuntu install.

Next install Ubuntu to the free space. You will eventually arrive at the partitioning section. Choose to manually partition. You will see the Vista partition clearly in the partitioning section so just leave it alone (it will be an NTFS partition, the only one there). The free space should be clearly visible also.

/, /home, and /swap are all there as default partition names (along with others) so all you need to do is create the partition and choose the default name. You can add others and call them want you want. It pays to sit down with pen and paper and plan exactly what you are going to set up by the way of partitions before you begin so you have a clear picture in mind of what's to be done. 

Format them as EXT4 (Windows can't read these so if you want to share data between the two OSs you will need to create an NTFS data partition. /swap does not need to be formatted, it will take care of itself. Put / first, /home next (and any other partitions you want to setup), and /swap last.

Take it slow and if you're not sure, you can cancel your partitioning and start again before you push the final button of no return. 

NOTE WELL: You can only have four primary partitions on one physical drive. BUT one of those four can be an extended partition inside which you can have 99 logical drives. Ubuntu will happily live on one inside an extended partition. 

Post back if you need any more help with it. :)

---

