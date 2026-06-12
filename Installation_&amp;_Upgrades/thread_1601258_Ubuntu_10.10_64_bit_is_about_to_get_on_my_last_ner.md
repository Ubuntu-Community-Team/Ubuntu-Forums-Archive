---
title: "Ubuntu 10.10 64 bit is about to get on my last nerve"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by DarkDancer on 2010-10-20
I have never had this much trouble getting Ubuntu installed. Forget the busy box errors. Forget the disk that worked twice (sort of) and then would no longer complete the install and made me go into windows and redownload and burn it, Forget the fact that it reformatted some of my drives for no apparent reason. I have made peace with that.

Let me tell you where I REALLY REALLY need help now. When I finally got into Ubuntu it suddenly told me that the Home directory only had 60 k left in it. So I figured I must have accidentally put it on a tiny partition. So I reinstalled and picked a nice big Home partition that was over 100 GB. I had it reformat the Home Directory so it would be nice and empty. When I finally get back into Ubuntu I get the warning that the home Directory only has 49kb available. Oh, and it remembers the web pages that I had opened before I reinstalled. 

So, how do I get it to actually use the Home Directory I chose for it? Or is there something more going on here?

---

### Post by linux-hack on 2010-10-20
Your problem is rely strange. can you post your partitions ?

---

### Post by mjh_ca on 2010-10-20
> **DarkDancer said:**
> Oh, and it remembers the web pages that I had opened before I reinstalled. 

Something is not right.  Do you have multiple copies of ubuntu installed in different partitions?  Maybe you installed a new copy on a second partition and then booted to the previous copy.

If you have no other data on the drives, nuke all the partitions and start with a totally clean drive before running the install again.

---

### Post by autark on 2010-10-20
I suggest you post the contents of /etc/fstab and the output of the df command.

---

### Post by TBABill on 2010-10-20
Did you reformat that home partition? Sounds like it was not and I'm wondering if it is somehow (no idea why!) retaining info from the size it was previously? I have never seen it but it seems very odd. Formatting it may at least remove remnants of anything that went wrong the first few times.

---

### Post by DarkDancer on 2010-10-21
Ok, so I fixed it. Here's how. I looked at gparted and yes it was showing that the home directory and the root had been placed on 2 different and much smaller partitions than I had selected for them. Basically where the old Ubuntu had been installed. So I pulled out my 10.04 disc, reinstalled with that. It put them EXACTLY where I had chosen, then since it was a fresh install, did an upgrade to 10.10. All is right with the world.

---

