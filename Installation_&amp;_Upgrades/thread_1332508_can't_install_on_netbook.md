---
title: "can't install on netbook"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by a_z1_9scores on 2009-11-20
Okay, so now I have a netbook and I want to dual-boot kubuntu and XP for gaming. KNR is nice, but it won't install on my netbook, giving me and error message telling me to check my cd, except I'm using a jumpdrive. Naturally I thought corrupted installation so I reburned it to my flash drive and same thing, so I tried a Wubi install. It froze on "creating the virtual drives" so I looked online and saw That the creating virtual drive freeze was a documented error but there was no solution. I also read that you can just install the nbr desktop on a normal cd installation so I downloaded the desktop cd and burned it to my jump drive using unetbootin, which by the way was the same thing I used for the nbr and I still couldn't install. I'm using a Compaq Mini netbook with a 15 gb harddrive with two partitions. The partition I'm installing on is 4.6 gb and XP is already installed

edit: adding that the version I'm installing is 9.10

'nother edit: I deleted my i386 files thinking I had backed them up but didn't so there's no way I can reformat or otherwise touch the Windows installation.

yet another edit: I used the partition manager on kubuntu which split my hd into 3 partitions (1 windows 1 ubuntu and 1 swap). To fix it, I went behind that and used a third-party partition manager to merge the swap and ubuntu partitions and shrink the Windows partition to increase the size of the Ubuntu partition (a mouthful I know). Maybe this has something to do with it?

---

### Post by a_z1_9scores on 2009-11-20
I tried a different jumpdrive and the kubuntu desktop cd just now and got the same message about a corrupted hard drive. I'm going to defragment the hard drive.

---

### Post by a_z1_9scores on 2009-11-23
Okay, after days of trying to find an answer, I finally just installed Ubuntu 9.04 using Wubi 9.04 and moved it using LVPM. I'm going to upgrade to 9.10 then install the plasma netbook packages now.

---

