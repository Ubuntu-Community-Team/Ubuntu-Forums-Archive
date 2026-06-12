---
title: "Error 22: No Such Partition"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by navegante911 on 2007-02-24
Hello,

I just restored a backup file of my previous Ubuntu but when I restarted the CPU I came across "Error 22: No such Partition".

I also have windows installed in a different partition that I have no access to right now.

Everything happened when I deleted the windows partition yesterday by mistake. Since I like ubuntu so much, I did the backup and formated the the whole drive to give more drive space to ubuntu on this new installation.   I have already installed windows in c, but again, no access to it.

Any Idea how to fix the ubuntu boot to show both OS and to log again into ubuntu?

Thank you!

---

### Post by ajgreeny on 2007-02-24
Try using a live cd and then use the terminal to find out your various partitions with:-
fdisk -l
You may then need to mount your ubuntu partition and edit the /boot/grub/menu.lst file to point to the correct partition.

Good luck.

---

### Post by navegante911 on 2007-02-24
Thanks for responding!

I am somewhat new to Linux in general, but I am sure I will find more information on these forums in regards to your suggestions.

Also, is it possible to restore my ubuntu backup with the live cd?

Thanks again!

---

### Post by ajgreeny on 2007-02-25
Maybe I misunderstood, but when you said you had restored a previous backup of your ubuntu, I assumed you meant of the whole partition.  Is that correct?  If so it is important that you restore it to a partition which is at least as big as the original or bigger; you can't restore it to a smaller partition, even if there is enough room for it, in theory.  Tell us in a bit more detail what you did, from the start, and we'll try to help.

OK, to start, run a live CD session and in a terminal type the command I told you:-
fdisk -l

Let us know what the output of that is, and if possible what your  /boot/grub/menu.lst listing at the bottom says, and we may be able to tell you how to get up and running again on both windows and ubuntu.

---

### Post by navegante911 on 2007-02-25
Thanks again for responding!   However, I decided to start all over again last night after I became frustrated with the whole thing.

What you are saying makes a lot of sense. I previously had Windows on the d drive instead of the usual c drive and I think that also had something to do with the issue too.

I really appreciate your interest but I have started allover again.   I am now working on installing Beryl to Ubuntu and trying that out.

Thanks again!

---

