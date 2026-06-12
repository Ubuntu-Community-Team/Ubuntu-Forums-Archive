---
title: "Reinstall Ubuntu 7.10"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by David 01 on 2008-03-07
I'd like to reinstall Gutsy. I have 2 hd's and am multiple booting Win2K and 7.10 between them. I sure don't want to lose my Win install even though I only use it occasionally or for historical purposes. Also I have 2 or 3 old Ubuntu or LinuxMint installs still on the drives.

I'd love to clean my machine up but for right now I just want to get Gutsy back to the defaults. i've been trying to get Samba networking going and have made many changes both manually and through interfaces.

Yes, I'm learning, but at least I'm not complaining.

Thanks to everytone who has made Linux and Ubuntu what it is today!

David

---

### Post by David 01 on 2008-03-07
To clarify, I want to reinstall and keep my present docs. I just want to reinstall the program.

---

### Post by zvacet on 2008-03-08
If you have separate home partition just reinstall on top of existing root partition.If you don´t have separate home you can [make](http://www.psychocats.net/ubuntu/separatehome) one.Good thing will be to back up your files in both options.**During install do not format home partition.**

---

### Post by David 01 on 2008-03-08
Thanks for your prompt reply and help. This is what I needed but unfortunately I still lost my data.

When manually partitioning my drives I formatted the / partition (as you know I had to). The problem was that since I had 11 partitions, I backed up the wrong one. I backed up hda1 which is the partition I resized, but I didn't backup hdb2 which was my / partition and where my current data was written.

I have some old data but lost everything for the last year or so. I need to move everything that I want to keep and get rid of the old partitions. Thanks to your help I have a better understanding of how to do this now.

Thanks,

David

---

### Post by David 01 on 2008-03-16
> **zvacet said:**
> If you have separate home partition just reinstall on top of existing root partition.If you don´t have separate home you can [make](http://www.psychocats.net/ubuntu/separatehome) one.Good thing will be to back up your files in both options.**During install do not format home partition.**

Did you do a little editing on me after the fact?. I don't remember the bold instruction being there originally, but that is only common sense that you don't want to format the data you want to save. My problem was that I was confused about where that data was since I had added a partition temporarily using your instructions. But the good news is that I **had** backed up my information (as you suggested) on a CD (I'd forgotten about it)  as well as moving things around on the hard drive and was able to restore what I needed. My only problem with that was that I had used Home User Backup and found that the restore did not work with Gutsy. After research I found that KDAR would work, but it was quite a project to research and then install everything (had to add repositories).

Bottom line, with your help I now have a separate /home partition and I like that very much. And with a lot of work and learning on my part, I am now down to 4 partitions between my 2 hard drives, 1 Win2k on 1 drive and /, /home and swap on my Linux drive. I went from confusion to organization

---

