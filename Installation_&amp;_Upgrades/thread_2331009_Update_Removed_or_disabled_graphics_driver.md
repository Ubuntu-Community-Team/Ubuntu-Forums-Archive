---
title: "Update Removed or disabled graphics driver"
date: 2016-07-17
forum: Installation &amp; Upgrades
---

### Post by dfpd62 on 2016-07-17
Hi Folks,

done a normal update last night on my ubuntu 14.4 and shutdown the system afterwards.
before i shut down a box popped up asking me to create a password, something about  Grub and propriatry drivers,
I didnt really understand it, thought that not following the instruction would remove my propriatry ATI driver which it seems to have done.

so I cannot boot 14.4 to graphical mode, how do I reverse this update?

Any help appreciated 

Thanks,  D

---

### Post by grahammechanical on 2016-07-17
At the Grub boot menu select Advanced options for Ubuntu and then select a recovery mode kernel. At the recovery menu select Resume. That may get you to a working desktop and from there you can change video drivers.

Or, from the same Advance options sub-menu select a previous kernel to load. 

Regards

---

### Post by dfpd62 on 2016-07-17
Hi ,
Thanks, that got me back up running on 14.4 with the previous kernel on the list.
how do i undo the last update to restore the latest kernel?
I am ashamed to say that since ubuntu has been trouble free for 3 years I have got lazy and forgotten most of my command line knowledge :(
but this is something I have not had to do before.

regards

D

---

### Post by giga+bytes on 2016-07-17
Hmm.. last night I had almost the same thing happen, except it was to do with secure boot and the proprietary drivers, which disabling secure boot seems to have mostly fixed (still doesn't quite seem totally fixed). Could these issues somehow be related? They both involved the AMD/ATI fglrx drivers..

---

### Post by dfpd62 on 2016-07-17
Hi I must have been mistaking boot for GRUB, How did you disable secure boot? in the BIOS?

---

