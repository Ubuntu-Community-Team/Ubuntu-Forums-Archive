---
title: "dual booting with windows 7 ultimate"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by jameslogan on 2010-07-06
Hi,
    this is more of a query than anything else so apologies if im covering old ground here.  a couple of years ago i used to dual boot windows xp with freespire and had no issues at all (followed the usual rule of installing windows first and then linux afterwards).  
  recently i started using windows 7 on my laptop and up until a couple of days ago was quite happy with that.
   i have however as part of a project of mine been looking for a linux distro to use with a driveless thin client and i came across the ubuntu netbook distro.  didnt run too well on the thinclient but its revived my interest in linux again.

   basically my query is am i likely to encounter any problems with dual booting ubuntu with windows 7, im assuming the grub bootloader will do the needfull with regards to the dual boot (as was the case previously with xp and freespire).

many thanks

Jim

---

### Post by scott1541 on 2010-07-06
I have been dual booting windows (xp, vista and 7) and ubuntu on and off for a while now and i have only ever encountered one problem, and that was caused by removing the active flag from my linux partition and putting it back on the windows partition, that was an attempt to make windows able to hibernate again, however grub didn't like it and messed up, I know it was my fault and not that of grub or any of my operating systems.

So yeah, I'd say if you don't start messing around with grub too much it will be just fine.

---

### Post by jameslogan on 2010-07-06
thanks, looks like ill be having a busy night tonight then, appreaciate the response

thanks

Jim

---

### Post by Mark Phelps on 2010-07-06
> **jameslogan said:**
> ... basically my query is am i likely to encounter any problems with dual booting ubuntu with windows 7, im assuming the grub bootloader will do the needfull with regards to the dual boot (as was the case previously with xp and freespire).


Would do two things to help protect your Win7 setup from damage and to help recover it:
1) Use the Backup feature to create and burn a Win7 Repair CD
2) Use the Win7 Disk Management feature to shrink the Win7 OS to make room for Ubuntu.  Leave the unallocated space as empty select that when installing Ubuntu.  Do NOT use the Ubuntu installer to shrink the Win7 OS partition.

---

### Post by jameslogan on 2010-07-07
***update***
installed ubuntu netbook last night, no issue what so ever, installed and running in less than half an hour, windows 7 still bootable and working well.  the one thing that surprised me was the number of updates that came through after the reboot but thats merely a formality.

alls well that ends  well

---

