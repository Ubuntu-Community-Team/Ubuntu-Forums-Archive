---
title: "Making a partition for a dual boot?"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by Quan Chi2 on 2007-02-23
Hi, I'm new to partitioning and I have a question.  I have chosen to Resize SCSI1(0,0,0), partition #1 (sda) and use freed space.  I gave the new partition 30.8Gb.  I clicked "Forward" and now nothing is happening...  I have been on the same screen for a long time (about 20 minutes).  Does this take a long time usually?  Did I do something wrong?  I canceled two times before this because it was not doing anything different.  Nothing is showing me any progress or anything.  So, did I do anything wrong?  Is Ubuntu making the partition?  I have a Windows OS installed already as my main OS.  I would like to make a dual boot.  I hope I'm doing it right.  How long does it usually take to partition?

---

### Post by logos34 on 2007-02-23
no, it shouldn't take that long.

Some things to try:
-defrag windows and run error-checking w/correction (chkdsk /r).  Also, temporarily disable your paging/virtual memory and hibernation files (those green bands you see in defrag window).  Try install again
-try Gparted live cd to shrink windows
-use the text-mode alternate install ubuntu cd

---

### Post by Quan Chi2 on 2007-02-23
Alright.  So first I should defrag my windows partition, right?

---

### Post by logos34 on 2007-02-23
> **Quan Chi2 said:**
> Alright.  So first I should defrag my windows partition, right?

yep.

---

### Post by Quan Chi2 on 2007-02-23
Alright.  I think that while it was stuck on the screen it was doing something.  I came to this assumption because when I canceled and restarted to boot Windows, Windows started doing a CheckDisk.  So I think that Ubuntu was doing something after all.  Heh, I just want to be correct in every step I take because I don't want to mess this main partition up.  My parents use this computer, so I can't erase Windows and start using Linux, I don't like using a VM for any OS really, so that leaves me no choice but to make a dual boot.

Thanks for the help.  I hope this works.  If anyone else has any other suggestions, please feel free to post in response to my first post.  If I have any problems I'll post here again. :)

---

