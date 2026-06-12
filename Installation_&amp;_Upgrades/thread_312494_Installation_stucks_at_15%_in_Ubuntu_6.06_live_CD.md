---
title: "Installation stucks at 15% in Ubuntu 6.06 live CD"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by sundar80 on 2006-12-04
Hi,

I managed to install the ubuntu 6.06 live CD by having "/" root in hda5 parition of  9.96 GB and ticked "reformat" option. I have XP installed in hda1 and my other files in hda6. So iam trying to install ubuntu in hda5 partition. After the installing progress bar starts, it says a "swap" partition needs to be created for better usage of physical memory. Since i have 10 GB for ubuntu i clicked "continue" option. It says installing and progresses to 15% after which the dialog box goes off and nothing happens..
What can be the problem.? If creating swap is the problem, how to i create it?
C: drive - 10 GB - hda 1 - Windows XP
D: drive - 10 GB - hda 5 - planning to install ubuntu
E: drive - 18 GB - hda 6 - other files.

Should I have to format my hard disk to have to create one more parition for swap? But this I dont want to do as I need windows also..

Please advise....

---

### Post by stanna on 2006-12-04
you need a partition for the swap, thats how it works, instead of like windows having a file for swap, linux uses a partition. you could try shaving off 1gig from your ubuntu install partition and then using that 1gig for the swap partition. it could easily be done in the live cd during installation to resize the 10gig then creating another 1 gig..

i hope this helps you.

---

### Post by sundar80 on 2006-12-05
Hi

thanks stanna for the reply..I am ok to parition 1GB for swap..but how wud i do it?  If iam right on the "partition" menu, I had to resize the hda5 allotted for ubuntu installation to 9GB. Would that do..?  Because when i select "/", hda5, "reformat" and "swap", hda5, it says cannot create swap...
Could you be elaborate as iam at sea when it comes to computers

---

### Post by sundar80 on 2006-12-05
Does dual boot work even though I have Windows XP in primary drive C:/ and ubuntu in logical drive D:/ ?? Or is it that ubuntu must also rest in primary drive C:/ along side Windows by choosing to install ubuntu in free space by selecting option 1 in partitioning? pls advice...

---

