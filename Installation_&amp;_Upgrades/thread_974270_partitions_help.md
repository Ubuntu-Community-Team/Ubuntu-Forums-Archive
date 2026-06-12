---
title: "partitions help"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by putnam on 2008-11-07
Okay, well I have a HP Pavillion dv6000 laptop, and i need help with partitions. i try doing the guided partition junk and it asks me if I want to format my HD. I have Vista, and want Ubuntu 8.1 as an alternative. If it helps, it also has a window popping up that says 'Aperture beyond 4gb. Ignoring'

Any help? Oh and in the try ubuntu part, wireless dont work

---

### Post by dabl on 2008-11-07
You need to boot Vista and use the Vista hard drive partitioning tool to shrink the larger of the two Vista partitions that are on the drive.  Then you will install Ubuntu on the empty space that is left.  You need to free up at least 10GB for Ubuntu and its swap partition.

---

### Post by putnam on 2008-11-07
I did that, but it still wants me to format it, or it says sumtin like no root file selected

---

### Post by dabl on 2008-11-07
OK, you use "guided" and then you choose (checkmark) the partition that you freed up with Vista.  That one will be for "/" -- the root filesystem.  It's OK to let it format it -- it will need to do that.

Did you make a swap partition also?  You need a swap partition -- equal to RAM size is usually a good choice.

---

### Post by putnam on 2008-11-07
if I format it, will it remove Vista? I don't want to do that, if it does. Do I need to make a new partition?

---

### Post by dabl on 2008-11-07
It will only format the partition that you mark for "/" -- not the entire hard drive.  So you just need to be double-damn sure that you are marking the correct partition, and not one of your Vista partitions.

And yes, swap needs to be a separate partition.  So you will have four partitions total -- the two Vista partitions, plus a small one for swap (maybe 1GB or more, depending on how much memory your system has) and the rest of the drive for the Ubuntu filesystem.

---

### Post by putnam on 2008-11-07
okay, thanks, now I have to figure out how to dualboot and install wireless driver...



But Thank You!

---

