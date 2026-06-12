---
title: "Fakeraid RAID 0 works, but only once. Then &quot;Offline Member&quot;"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by BFG on 2013-03-14
This is an odd problem.  As an experiment I built a machine with Ubuntu 12.10 64 bit on RAID 0 using 2x identical HDDs. 

The system boots perfectly and runs just fine.  However, when it's shut down and re-started, both drives are announced as "Offline member".  If I then boot the machine using a liveUSB, the RAID 0 array is visible.

After booting with the liveUSB, I make no changes, simply re-boot. And the machine starts normally.  Restart again - back to "Offline member".  Very odd.

Any thoughts on what this could be?

---

### Post by MAFoElffen on 2013-03-14
Experiment? LOL! I've never had much luck with fake RAID and Linux. I played with that years ago, then gave up. There were other more dependable methods, like mdadm (software RAID) and LVM. 

The problem? Just my guess from my past experimentation... I think it has to do with that motherboard manufacturers never really standardized on how it worked (each had their own), so each had their own special drivers for Windows OS's, where I can see that driver support for those has fallen out for a lot of those older boards (with newer Win). Then Linux... having specific driver support for those minor differences...? Maybe how the arrays are reported through BIOS as ready or not? 

I know even with real RAID and software RAID, sometimes during the modprobe at bootup, you sometimes have to add a pause or wait to give "time" for them... for the disks to spin up and build the array, before it can pass a flag saying it's good. This still happens to me sometimes with software RAID, if I assign a logical arrray that is separate and starts after root // added in at the fstab. But those same arrays have no problems if mounted later... Frustrating debuging that.  That's just my guess and feelings on that.

---

### Post by darkod on 2013-03-14
I know it doesn't answer your question directly, but if you plan to have only ubuntu on that machine forget about fakeraid and use mdadm SW raid.

You would only involve fakeraid if you plan to dual boot with windows.

---

### Post by MAFoElffen on 2013-03-14
+1 w/ darko.

To expand on my earlier post. I always thought/felt FakeRAID was a Windows gimmick type feature that needed special windows drivers to work... and even then I found it didn't work reliably. Compared to real hard RAID and Software RAID, FakeRAID seemed to be a failure in the market-place and in the industry. Just my thoughts.

While you are experimenting- I think you would be happier experimenting with mdadm.

---

### Post by BFG on 2013-03-15
Thanks guys.  Some interesting points.  Though I'd like to solve this puzzle before starting again with mdadm.  I'll see if I can post a screenshot

---

