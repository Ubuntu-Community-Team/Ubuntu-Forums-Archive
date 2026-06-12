---
title: "Resizing partition..."
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by sporkubus on 2008-07-16
Hi guys,

I used to have Ubuntu on my old laptop but switched back to Windows after I couldn't really get it working with my hardware. Now I have a new laptop and I want to try Ubuntu on it. I am attempting to install Ubuntu from the LiveCD and I am resizing my 220GB hard drive using the partition manager. For some reason, the "Resizing partition..." window is just sitting there and sticking at 0% (even though it has been working for a couple of hours now). I have other work to do with my laptop so I'm wondering if I should just reboot, but I'm afraid that it will permanently damage my system. On the other hand, if I wait and let it do its thing, how long should I wait?

---

### Post by Steveway on 2008-07-16
> **sporkubus said:**
> Hi guys,

I used to have Ubuntu on my old laptop but switched back to Windows after I couldn't really get it working with my hardware. Now I have a new laptop and I want to try Ubuntu on it. I am attempting to install Ubuntu from the LiveCD and I am resizing my 220GB hard drive using the partition manager. For some reason, the "Resizing partition..." window is just sitting there and sticking at 0% (even though it has been working for a couple of hours now). I have other work to do with my laptop so I'm wondering if I should just reboot, but I'm afraid that it will permanently damage my system. On the other hand, if I wait and let it do its thing, how long should I wait?

Last weekend I resized the partitions on my external 250GB drive.
The whole procedure lasted about 3-5 hours.
I had 2 Partitions on it, moved all data from the old fat partition to the newer ext3 partition, deleted the fat partition and resized the ext3 to fit the whole disk. That's a pretty heavy task especially if there is data on it that should not be deleted. So expect a long partition-time.
(That drive is now plugged into my server so that can access it from everywhere here as long as I have connection to my router. I set it up as an NFS drive. The setup took me only less than an hour even though I never did it before, yay Linux!)

---

### Post by sporkubus on 2008-07-16
Well, that's a bit of a relief. It still hasn't done anything, but I'm going to leave it for now and hope for the best.

This might be a dumb question but, if I resized my old hard drive, the data that was already there isn't going to get formatted, right?

---

### Post by Steveway on 2008-07-16
> **sporkubus said:**
> Well, that's a bit of a relief. It still hasn't done anything, but I'm going to leave it for now and hope for the best.

This might be a dumb question but, if I resized my old hard drive, the data that was already there isn't going to get formatted, right?

If nothing happens during the  process then nothing should get deleted. At lest this was the case for me. Just be careful when using gparted because a wrong click could possibly kill your data, read carefully through everything and don't forget to backup important data.

---

