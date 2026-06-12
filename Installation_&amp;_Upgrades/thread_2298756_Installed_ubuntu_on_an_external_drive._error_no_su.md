---
title: "Installed ubuntu on an external drive. error: no such device, grub rescue problem."
date: 2015-10-13
forum: Installation &amp; Upgrades
---

### Post by chill_is on 2015-10-13
Hi everyone. I have lets say beginners knowledge on ubuntu. I installed ubuntu on my laptop with USB stick on my external hard drive and set the grub loader to be installed on my internal hard drive where windows were installed. Now everytime I start my laptop or restart it from both of OSes it pops up this: "error: no such device: 632fsd-23rvsf-....
Entering rescue mode...
grub rescue>:_....
I've seen and searched many threads about this issue but none of them refers to an external hard drive. Any suggestion ?
Thanks in advance and sorry for bad English.

---

### Post by yancek on 2015-10-13
> error: no such device: 632fsd-23rvsf-....

That error message means Grub is looking for a device partition with that UUID and it doesn't exist.
It's always useful to post the version of windows you are using because they've been selling operating systems for 30 years and they're not all the same.
Could you clarify where you installed Ubuntu.  You said you used a usb stick with the Ubuntu installation medium/Live CD on it and installed to:  an external drive?  on a partition on an internal drive of the laptop?

Since you obviously have access to another computer, go to the site below and download the Boot repair software and burn it to a CD and boot your laptop with it in the drive.  When it is booted, you should see an option to Create BootInfo Summary, select that and when it is finished post the output here for someone to review.  Make sure you read the page first before trying it so you understand what is happening.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2015-10-14
Some systems now boot too quick for USB powered external drives to come up to speed and be available. Is drive USB powered or has separate power brick? Even if separate make sure it is on and working.

Also how large is / (root) partition on external drive. Some BIOS will not boot external USB drives if boot files are beyond a certain point like over 100GB. Better then if / is 25GB and rest of drive is /home or data partition(s).

Post link to summary report as suggested by yancek.

---

