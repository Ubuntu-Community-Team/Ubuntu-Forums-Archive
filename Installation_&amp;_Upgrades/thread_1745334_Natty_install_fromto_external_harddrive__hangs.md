---
title: "Natty install from/to external harddrive  hangs"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by marius311 on 2011-04-30
I'm trying to install the desktop 64bit edition of Natty to an external harddrive. Using the Startup Disk Creator, I put the LiveCD in a partition on my external harddrive, and I can boot into and use that no problem. Now, from that, I try to install Natty. I select the manual partition thing, and choose my root partition to be on the external harddrive as well. That works, but a few screens later, during the slideshow, the installation just hangs. The bottom progress bar is full and it stopped on "detecting filesystems...", but otherwise there are no other messages. 

Any ideas whats going on?

---

### Post by Hedgehog1 on 2011-05-01
To be sure I understand, You have the ISO on the very same hard drive you are (unsuccessfully) installing Ubuntu onto, right?

If this is the case, I believe that you will need to be running the LiveCD/LiveUSB from a separate device that the one that is the install target.

In my testing of natty installed a few weeks back, the unmounts that happen as part of the install are (I believe) confused by the source and target being the same device.

Can you move the ISO to the internal hard drive, or, more traditionally, use the ISO to make a LiveCD/LiveUSB?


***The Hedge***

:KS

---

### Post by marius311 on 2011-05-01
Yeah that's exactly what happens. There is a cryptic error message
about being unable to unmount /cdrom, which I now realize is referring to the LiveUSB partition, but you can ignore it and continue. I might file a bug report since that error message is really confusing, or it should not be ignorable, since it will hang the installation later. 

Install to the external harddrive from a CD did work, by the way.

---

