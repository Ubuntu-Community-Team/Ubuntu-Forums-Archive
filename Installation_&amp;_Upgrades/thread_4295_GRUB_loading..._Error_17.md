---
title: "GRUB loading... Error 17"
date: 2004-11-13
forum: Installation &amp; Upgrades
---

### Post by ITLogic() on 2004-11-13
I have read another thread concerning this error. It means that the partition was there, but the file system was not recognized. So, now I know the problem, but not sure of a solution.

I booted with a Win 98 boot disk because, after that error theres nothing I can do but reboot. I checked fdisk and noticed this:

Partition 1: Ubantu
Partition 2: Windows ME
Partition 3: Ubantu Swap

Partition 1 was set active. I don't know if that means anything, but it looked funny.

It may be important to know that I was trying to install Mandrake before Ubantu, but was have problems with video cards. Anyway, I used Partition Magic 8 in Windows ME to delete the 3 partitions created by Mandrake.

This left me with 5 gig for Windows ME and 5 gig unallocated. During the install I told Ubuntu to automatically partition the 5 gog unallocated for it.

Everything was going smoothly until the reboot.  ](*,)

---

### Post by sfw5000 on 2004-11-14
Try checking out this thread: [http://www.linuxforums.org/forum/topic-19999.html](http://www.linuxforums.org/forum/topic-19999.html)

Hopefully you can do some kind of re-install of grub/ubuntu. I've never had this problem, but it seems to happen when you do a dual boot of windows. Also, search throught he mailing list thread. A bunch of people have had issues with dual booting into windows.

---

### Post by ITLogic() on 2004-11-14
Ok, I got it. It seems that when I was trying to install Mandrake something went wrong. It was funny because I started with a full 10 gigs. I partitioned the drive into two 5 gig partitions. Afer Mandrake f***ed up, I could no longer see the second 5 gigs with DOS fdisk or Partinion Magic in Windows. I tried to delete all partitions and reformat. I reloaded Windows ME first, hoping I woudl be able to see all 10 gigs again. But, now I only saw 3. WHAT? I checked the BIOS and saw that the HDD detection was not set to auto anymore and set to User with 3 gig space specified. How did that happen? Anyway, I changed that back to auto and started Windows ME and Partition Magic. I created a partition out of the 7 gigs that it now saw and then merged the 7 and 3 gig partition. Then I had one 10 gig DOS partition again. When installing Ubuntu, I repartitioned 5gig and 5 gig and all worked fine this time. thanks.  \\:D/

---

