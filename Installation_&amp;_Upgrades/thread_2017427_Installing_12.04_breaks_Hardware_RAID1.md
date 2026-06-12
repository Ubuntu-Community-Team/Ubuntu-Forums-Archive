---
title: "Installing 12.04 breaks Hardware RAID1"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by truesdk on 2012-07-05
I recently decided i would try installing 12.04 on a server with a RAID1 hardware raid. (first attempt at this)

I installed the hardware RAID1, and everything was working great (because there was no OS on the machine), but when i go through the 12.04 server install, it gets to the step where it asks if you want to configure an iSCSI, so i click no and decide to setup the server using the entire disk with LVM.

Now, in my mind, i would think Ubuntu would only see one drive (my RAID array), but it still sees 2 drives, so i install it on the first drive which then degrades my raid array.

Is there a way to fix this from happening?

---

### Post by darkod on 2012-07-05
And if you say Yes on the iSCSI question? You might need that so that it "understands" the controller and the array.

Yes, it should see one single disk.

---

