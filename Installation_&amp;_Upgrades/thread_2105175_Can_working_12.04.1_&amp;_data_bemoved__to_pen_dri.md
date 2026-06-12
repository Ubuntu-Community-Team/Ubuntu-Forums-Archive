---
title: "Can working 12.04.1 &amp; data bemoved  to pen drive?"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by PiersCart on 2013-01-15
Been away from the Forum for several years.
Now have 12.04.1 partitioned on laptop with Vista. Is it possible to copy the Ubuntu and its data and **have it working** from a usb? If so, how can it be (simply)  done?

---

### Post by ronparent on 2013-01-15
One way of probably many - simply use the live CD to copy the contents of you current install on your HD to an empty partition you created and formatted on that pen drive. You have to then edit the /etc/fstab of the target to change the UUID to agree with that of the target partition on the pen drive. Same for a swap. 

The next step is determined by how you would want a grub on the pen drive to work. While in the live session I would simply mount the pen drive partition (ie to /mnt) and install grub to the /mnt/ as the root-directory and the /dev/sd? as that of the pen drive MBR. It would get more complicated if your computer uses UEFI.

This is I think the simplest answer but there are other ways.

---

### Post by PiersCart on 2013-01-15
Thanks, Ronparent. I was hoping to do it all with mouse clicks...Suppose I had better sort out my fingers from my thumbs, mug up on  typing commands and have a try.
Cheers,
PiersCart

---

### Post by ronparent on 2013-01-15
Mouse clicks will work - but leave you with a system with split personality problems. Using gparted you can simply copy the HD partition to the pen drive. But they will both have the same UUID and you will probably never know which is booting when both are present on the system.:)

I've done it and it works fine - except that you will probably pay hell to track any changes you make to whichever system boot. Have fun.

---

### Post by PiersCart on 2013-01-17
Thanks again. 
It seems to me that it would be simpler to download a new copy of the OS to the pen drive and then copy the existing data to it. Would you agree?
Or is this too blindingly obvious to be true??

---

### Post by ronparent on 2013-01-17
There is always a fly in the oitment. You are right. The problem is in how the data is copied! I have done it in a separate /home for instance. But then I have to change 'ownership' to have full access to it. Very simple to fix with a couple of terminal commands - which I have forgotten and would need to find again to proceed. 

But, I digress. A copy of the Linux based OS (containing all hidden files as well) installed for the hardware you intend to operate the pendrive on is completely workable! So is copying the existing data! If ownership problems crop up they are fixable. Enjoy.

---

