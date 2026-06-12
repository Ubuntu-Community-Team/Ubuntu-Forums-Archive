---
title: "Windows / Ubuntu Partition"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by Outrager on 2006-07-08
I have a 120GB HD and 1.5GB of RAM. I split it up 50/50 so 56GB is for Windows XP (C Drive) and 56GB would be for Ubuntu (D Drive). I formatted both to NTFS. I put in the Ubuntu DVD and go thru the GUI installer. I get to the partitioning part and I'm pretty confused with it. I know to use the Manually partition option. I select the HDA1b partition, but the next page where it asks for mounts I don't understand. Could someone give me some recommendations as to how much of my partition I should use for each mount, the filesystem, and what each is for?

56GB Space (already partitioned from a larger 120GB), 1.5GB RAM

---

### Post by Dr. Nick on 2006-07-08
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

You shouldnt install ubuntu into the 2nd ntfs partition, Use native linux filesystesm, If you just delete the 2nd partition that doesnt have windows (D drive) then it will be free space and ubuntu can automatically split it up for you.

You can mount /home on its own partition if you want, makes backups easier since all your personal data is on a differnt partition then the rest of the system

Look here for partition info 

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

