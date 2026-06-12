---
title: "Ubuntu LiveCD Corrupted my Windows OS"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by stuh505 on 2006-07-17
I decided to install ubuntu from the live CD last night onto a spare 10 GB partition.  I used the manual partition setup mode.  I formatted the root partition for NTFS and the swap with linux-swap.  When I attempted to install, it got about 10% through the install process and then the install dialog box disappeared (failing).  When I restarted it said my windows partition had been corrupted.  I never touched my windows partition in the partition editor, and never said to mount anything to my windows partition.

While I now have ubuntu up and running, I am disgruntled that I lost my existing drive without warning.

Perhaps you are thinking, "it's your own stupid fault for choosing ntfs"...no, it's not my fault, because I am new to linux and I did not know.  If ntfs is not a supported format then the installer should have explained this or not made it an option, or not attempted to do a partial install...and in any case it should not have touched my windows partition!

---

### Post by x64Jimbo on 2006-07-17
Have you tried using your Windows install CD in recovery mode? One command I highly recommend is 
fixmbr
In the Windows install CD recovery mode, this command will restore your master boot record, which might possibly be the problem.

---

### Post by orb9220 on 2006-07-17
You said "I formatted the root partition for NTFS" you don't format the root 
If you only have one drive and one partition ntfs then the ntfs has to be resized to allow you to create a new patition / and one for swap.

EX: I have 60Gb xp hd. I resize the 60 down to 20 that leaves 40 unallocated.
I then create new partiton on the 40 gb of 39 which will be / root and then a 1 gb for swap with out touch the ntfs and do not format the ntfs unless you want to wipe out xp too.

So Ubuntu did Not wipe it out you did when you said it was ok to format ntfs partition.

---

### Post by stuh505 on 2006-07-17
orb,

Like I said in my original post I had a spare 10 gig partition that windows was not on before I attempted to install ubuntu.  I then split off 1G from it  and formatted that with linux-swap and reformatted the remaining 9GB as ntfs for the root.

---

