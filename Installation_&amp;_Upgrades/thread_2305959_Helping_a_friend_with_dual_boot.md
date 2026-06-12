---
title: "Helping a friend with dual boot"
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by acefromspace on 2015-12-10
I am helping a friend setup a dual boot windows/ubuntu. She is not "computer literate" She is the manager at the small country store where I work. The computer is desktop sony vaio and currently running win xp and is a mess! Others have tried to help, but they don't really know what they are doing (and xp is not supported) I will repartion and then install ubuntu on free space partition (it's been years since I did this) In the past I let windows do the partition (if I do it wrong with ubuntu I might mess up mbr for windows. My issue is that she does not have data backed up, so if I mess up all will be lost. What is the best AND safest way to do this? Also, is win vista still supported? I will try to backup data (duh!) but might have to do this anyway (sick and tired of helping her with this system the way it is) She wants me to take over things like ordering, e-mail, ect. but I won't bother until I get ubuntu installed.

---

### Post by v3.xx on 2015-12-10
A business that cannot afford a computer upgrade?  As cheap as they are?

What kind of computer is this?  Whats the specs (cpu, ram, graphics)?

---

### Post by Irihapeti on 2015-12-10
Windows Vista is supported until 2017. However, if it's a typical XP machine, it may not have enough RAM to do the job. Mine was rather sluggish until I upgraded to 1.5 GB of RAM.

---

### Post by grahammechanical on 2015-12-10
There are some general principles that should be followed.

1) Use Windows utilities to defag Windows and do it more than once and restart each time
2) Use Windows utilities to resize/move Windows partition and restart each time
3) Ubuntu needs 2 partitions one for Ubuntu ( mount point / ) and one for swap ( mount point swap)
4) With MBR partitioning we are allowed a maximum of 4 primary partitions
5) If the 4 primary partition allocation is already used up then one primary partition has to be deleted.
6) The spare primary partition allocation has to be used as an Extended partition.
7) In the Extended partition create 2 Logical partition to use for Ubuntu. Or allow the Ubuntu installer to create the Extended partition out of the unallocated space and install Ubuntu into it.

Regards.

---

### Post by acefromspace on 2015-12-11
Computer is Sony Vaio PCV-RZ46G. Processor is about 4 gig and memory is 1 gig. By the way, the memory tested bad so need to replace anyway (before doing anything else) Might go for 2 gig. It has large hard drive with lots of free space to work with. Yes, I will defrag first... thanks for the tip on doing twice and restart between. I just remebered it has another partition (for windows?) Not sure how that's setup (or why) but will try to get details and post later. I know it sounds crazy (and is) but the company that owns the store has left us on our own (very little support and won't spend a dime on the store) They are a real estate co that only cares about the property for future plans. I hope to eventually convince my manager to ditch windows and just use linux. Our needs are simple, and the one thing "the company" does do for us is payroll.

---

### Post by yancek on 2015-12-11
Before beginning, it would be a good idea to post some partition information.  You could do that when you boot Ubuntu or whichever system you choose by opening a terminal once you get the installation medium booted and running this command and posting the output here:  sudo fdisk -l (Lower Case Letter L in the command).  If xp is a typical install, it will be using the entire drive and you will need to shrink a partition to make room for Ubuntu.  I don't think xp has that software in a default install so you may need to download some software.  If you change a partition in windows, you should also run chkdsk after.

---

### Post by acefromspace on 2015-12-11
My mistake... does not seem to have another partition. It does show C drive, and what confused me is it shows D drive, but all it had was a few megs of temp files. Not sure why... maybe from using ubuntu live disc before. Doesn't matter I will go as planned as soon as I get new memory. Is 1 gig enough for current ubuntu LTS (14)? By the way, this computer is my manager's own... she doesn't want to spend much. Can always add another 1 gig later. Maybe I will just buy the damned memory myself (only $40 for 1 gig) just to end this nightmare.

---

### Post by acefromspace on 2015-12-11
Just want to be sure I have this right. Defrag windows (several times), Shrink windows partition, leave rest of hard drive free space, then install ubuntu on free space (letting it setup partitions... what I normally do) or should I go ahead and create partition for ubuntu (using windows) and have it be free space (or this not necessary?)

---

### Post by sudodus on 2015-12-11
> **acefromspace said:**
> My mistake... does not seem to have another partition. It does show C drive, and what confused me is it shows D drive, but all it had was a few megs of temp files. Not sure why... maybe from using ubuntu live disc before. Doesn't matter I will go as planned as soon as I get new memory. Is 1 gig enough for current ubuntu LTS (14)? By the way, this computer is my manager's own... she doesn't want to spend much. Can always add another 1 gig later. Maybe I will just buy the damned memory myself (only $40 for 1 gig) just to end this nightmare.

No, 1 GB is not enough for the current standard Ubuntu. But it is plenty for Lubuntu and just enough for Xubuntu and Ubuntu MATE. These flavours of Ubuntu have lighter desktop environments (graphical user interfaces) so they need less RAM. I would say that you need at least 2 GB RAM for standard Ubuntu and Kubuntu (I would like to have 4 GB RAM).

Also for other reasons (the old Pentium 4 processor), it is a good idea to use a flavour with a lighter desktop environment. Let her try them live and decide what to use :-)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

Finally, there might be problems - different versions (12.04 LTS, 14.04 LTS, 15.10) might work differently with the graphics card, at least until you install a proprietary graphics driver. I suggest that you start with **14.04.1 LTS**

See also this link: [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by sudodus on 2015-12-11
> **acefromspace said:**
> Just want to be sure I have this right. Defrag windows (several times), Shrink windows partition, leave rest of hard drive free space, then install ubuntu on free space (letting it setup partitions... what I normally do) or should I go ahead and create partition for ubuntu (using windows) and have it be free space (or this not necessary?)

Defrag, shrink and check with Windows. Do ***not*** create partitions for Ubuntu using Windows, because it might create dynamic partitions, which do not work with linux. Use gparted in Ubuntu live or let the installer do it.

---

### Post by acefromspace on 2015-12-12
I understand that 2 gig would be better, but I have ran ubuntu 12.04 on several computers with 1 gig RAM and it seemed OK (don't do anything that requires intense graphic usage) Also, I have tried live disc (12.04) on this computer and it worked OK.

---

### Post by sudodus on 2015-12-12
When you have tested and it works for you, then go ahead :-)

---

### Post by Geoffrey_Arndt on 2015-12-12
Hmm, this install will be interesting.   Ace from Deep Space . . . . pls keep us updated.

---

### Post by acefromspace on 2016-04-01
Please disregard this thread. No longer work for this person, and not interested in helping her anymore.

---

### Post by lisati on 2016-04-01
> **acefromspace said:**
> Please disregard this thread. No longer work for this person, and not interested in helping her anymore.
Thread closed. If you change your mind, feel free to report this thread and ask the forum staff to reopen it.

---

