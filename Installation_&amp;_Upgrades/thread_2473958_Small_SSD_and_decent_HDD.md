---
title: "Small SSD and decent HDD"
date: 2022-04-19
forum: Installation &amp; Upgrades
---

### Post by ChrisOfBristol on 2022-04-19
A friend has just bought a reconditioned desktop. It has IMHO a stupidly small SSD of 120GB. She also has a decent sized HDD. I haven't seen the computer yet, so can't be sure there will be room for both disks, but I thought of putting the OS on the SSD so the computer starts and loads software quickly, it would be plenty big enough for that. The data which takes up a lot of room would go on the HDD, speed is perhaps less important as most files are small.
I'd like comments on this plan - or suggestions for a more optimal use of the two drives.

---

### Post by oldfred on 2022-04-19
I upgraded my old BIOS system in about 2011 with a 60GB SSD when price dropped below $100 as OEM.
I was able to have two / (root) partitions of almost 30GB including /home. And then created data partition(s) on HDD so each install could use same data. 

I now use Kubuntu as it does not require quite as much system as Ubuntu. I also have converted to newer UEFI systems with larger SSDs and HDD more for backup and storage that is not used as much. HDD also used for test installs even though noticeably slower than SSD.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

### Post by Impavidus on 2022-04-19
If an SSD and an HDD fit together in the computer, putting the OS, applications and frequently used files on the SSD and media files and maybe other documents (or the entire /home partition) on the HDD makes sense. I don't know how your friend uses her computer. For me, 120GB of storage total would be enough.

Main options are:
- Put the root partition on the SSD and the /home partition on the HDD. That will waste quite a bit of SSD space.
- Put the root and /home partitions on the SSD, then a separate partition for large media files on the HDD.
- Put the root partition on the SSD, don't create a separate /home partition, but create symlinks in the home directory pointing to directiories on the HDD, replacing the default directories like ~/Documents, ~/Videos etc.

What is best depends a bit on how your friend uses her computer.

---

### Post by ChrisOfBristol on 2022-04-19
> **Impavidus said:**
> I don't know how your friend uses her computer. For me, 120GB of storage total would be enough.
Thanks for reading my query properly before answering. You have suggested some good options, but of course the first thing would be to ask her how much data she has! I was thinking in terms of my own usage which isn't much help. I think she mainly uses it for purchases (virtually no data) typed documents (not much) and photos (not a vast amount). I'll check with her.

---

### Post by GhX6GZMB on 2022-04-19
A partition of 20...30 GB for / (the OS) is enough. (SSD)
The rest can be allocated to the /home partition. (also SSD)
If further storage is needed, more partitions (HDD) can be mounted under the /home subdirectories. It's flexible.

---

### Post by ChrisOfBristol on 2022-04-19
> **ml9104 said:**
> A partition of 20...30 GB for / (the OS) is enough.Agreed, I used to use about 20GB. I think I've got 40 now, I did it to have plenty of space for Flatpaks and for creating the one I've written as I suspect something gets put there rather than /home. 20GB on my friend's disk would leave 100GB for photos which would be 
~30 000 ~3MB ones, probably plenty. To be done on Thursday for obvious reasons :).

---

### Post by ActionParsnip on 2022-04-20
120Gb is plenty for Ubuntu
[https://ubuntu.com/server/docs/installation](https://ubuntu.com/server/docs/installation)
States that you need minimum 2.5Gb disk (2% of the drive).
Ubuntu isn't Windows. Its not a massive beast. Its trim and small so I don't see where you are getting "stupidly small" from.....

---

### Post by ChrisOfBristol on 2022-04-20
> **Impavidus said:**
> For me, 120GB of storage total would be enough.
She has a total of **16GB** of data. So a 120GB SSD is plenty! 
> **ml9104 said:**
> If further storage is needed, more partitions (HDD) can be mounted under the /home subdirectories. It's flexible.
if she starts doing something that creates loads of data I can do this. I remember doing it for someone else's computer.

This was a good reminder to always ask the obvious questions and consider something simple first, thanks guys.

---

### Post by ChrisOfBristol on 2022-04-20
> **ActionParsnip said:**
> 120Gb is plenty for Ubuntu
But not necessarily for the data.
> I don't see where you are getting "stupidly small" from.....
i don't do video or anything else that creates lots of data, but my 500Gb disk is half full.

Impavidus was spot-on when he said: > **Impavidus said:**
> What is best depends a bit on how your friend uses her computer.

---

