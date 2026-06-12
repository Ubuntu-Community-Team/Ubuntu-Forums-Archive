---
title: "Partition problem"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by vaniub on 2010-04-25
Hi,
 
Iam trying to install ubuntu 8 using live cd. When it comes to step where partition is being done, i have tried to change the partition suggested by ubuntu to the one i preferred i.e., 60% for the xp(which is already installed) and 40% for ubuntu. When i click forward, it says partitioning process failed for some reason. 
 
since, I cannot use whole disk space for ubuntu alone, i could not go forward with the option of "_Guided - resize the partition and use the freed space._", which was, i think, using the entire disk space. I have aborted the installation since i was not sure what to do next.
 
I want both xp and ubuntu in a  dual boot modes. 
 
Pls help me. Thanks a lot in advance.
 
regards.

---

### Post by avtolle on 2010-04-25
A few things. First, please defrag your XP if you have not already done so; more than once is my recommendation. Next, as I presume you have but one partition now (XP taking the entire disk), once the defrag is done, the Guided selection you referenced should work; you will need to specify, as I recall, the size you want for the XP. I have done the partitioning manually for so long, I really don't recall how it works.

Good luck.

---

### Post by vaniub on 2010-04-25
Thanks a ton for you quickest reply.
 
Do you mean running the 'Disk Defragmenter' option under 'Accessories/system tools' of Win XP?
 
Thanks once again.
 
regds.

---

### Post by avtolle on 2010-04-25
> **vaniub said:**
> Thanks a ton for you quickest reply.
 
Do you mean running the 'Disk Defragmenter' option under 'Accessories/system tools' of Win XP?
 
Thanks once again.
 
regds.
Yes, or another defrag program of your own choosing.

---

### Post by The Thunder Chimp on 2010-04-25
> **vaniub said:**
> Hi,
 
Iam trying to install ubuntu 8 using live cd. When it comes to step where partition is being done, i have tried to change the partition suggested by ubuntu to the one i preferred i.e., 60% for the xp(which is already installed) and 40% for ubuntu. When i click forward, it says partitioning process failed for some reason. 
 
since, I cannot use whole disk space for ubuntu alone, i could not go forward with the option of "_Guided - resize the partition and use the freed space._", which was, i think, using the entire disk space. I have aborted the installation since i was not sure what to do next.
 
I want both xp and ubuntu in a  dual boot modes. 
 
Pls help me. Thanks a lot in advance.
 
regards.


Do the defragmentation operation under Windows XP, then you might want to use GParted to change partitions on your drive out of the installer. Then when you'll install, you'll choose "Use most continuous amount of free space". That should do it. (GParted is available in the livecd. All you got to do is boot with the live cd without installing (Try Ubuntu without any changes to your computer) and start GParted from there.)

Tell us how it went!

---

### Post by avtolle on 2010-04-25
Good thought, Thunder Chimp.

---

### Post by vaniub on 2010-04-25
Thanks a lot.
 
Could you pls give me some more information about GParted. What it actually does?
I have only one partition(c:) on my hard drive currently. So, with GParted, i will have to do another partition for ubuntu? Or without actually doing the partition also, i would have ubuntu installed on my PC.
 
I already have ubuntu 9 installed on my pc using wubi. But since, it does not allow me to dual boot both the OS at a time, i again have to install ubuntu 8 which "i think" allows me to set up for dual boot.
 
Thanks a lot for all the help.
 
 
regds

---

### Post by avtolle on 2010-04-25
OK, some clarification is needed by me. First, dual boot does not mean booting **both** OS simultaneously; rather, as commonly used, it refers to the ability to boot (in your case) either XP or Ubuntu. That capability exists with all Ubuntu releases I've used (from 5.10 - 10.04). 

You may want to run XP from a virtual machine inside Ubuntu if you are desirous of access to either OS without exiting one and booting the other. That is what it seems you want, thus my confusion.

---

### Post by vaniub on 2010-04-25
Iam sorry! I think i have mis-understood the term dual-booting. Thanks a lot for the clarification.
 
You said, I can have Virtual machine installed in Ubuntu and with that i will also be able to access the applications in XP. Is it possible to have Virtual Machine installed in XP and access the ubuntu files(especially linux) from there. Because i have more other applications to work with, like(BO,Datastage etc) installed in XP and i would also need to use linux simultaneously, without rebooting the PC.
 
Thank you very very much. Its been a GREAT HELP.
 
regds.

---

