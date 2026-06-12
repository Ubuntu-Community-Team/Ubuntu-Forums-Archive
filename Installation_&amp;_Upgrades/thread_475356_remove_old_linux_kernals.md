---
title: "remove old linux kernals"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by shickidyshade on 2007-06-16
Hey guys im looking to delete some of my old kernels so that my grub menu is shorter so i can switch between ubuntu and windows faster. I think the last time i did this it was through the synaptic manager. 


Thanks

---

### Post by 5-HT on 2007-06-16
Yup, you can remove any given kernel image and restricted modules if applicable using synaptic. If you want to keep the kernels but hide them in grub, you can always move the entries below the automagic update line and comment them out.

---

### Post by shickidyshade on 2007-06-18
And how would you remove them using the synaptic

---

### Post by OzzyFrank on 2007-06-18
What's "the automagic update line"?? Sounds interesting...

---

### Post by 67GTA on 2007-06-18
I always keep one old kernel installed in case the new one gives me trouble. You can hide it in the menu list by commenting(#) them out. You can boot with the old kernel if the new one doesn't agree with you.

---

### Post by merlinus on 2007-06-18
> **shickidyshade said:**
> And how would you remove them using the synaptic

Search for linux-headers and linux-image, and select the ones you want to remove.

Best to keep two, however, in case the most recent one fails for one reason or another.

-merlin

---

### Post by OzzyFrank on 2007-06-18
I've read a few posts about people having massive problems after updating the kernel, so was glad to hear you could boot to an earlier one if you still had it... and I was very please to see in the kernel update after Feisty release that the old one was already saved, and the GRUB menu modified to accomodate both. I think that is awesome, coz if I have a problem after a kernel update, I can reboot and choose another. I'm updating the kernel again right now, and feel safe doing so coz of this. But yeah, eventually when my menu becomes too long, hehe, I can edit out some entries, or even remove the old stuff. Beats any rollback feature after updates in Windows! (God, wasn't System Restore a vast joke!!)

---

### Post by saxuntu on 2007-06-20
I'm a complete and total newb and am paranoid about screwing up.  In Synaptic i have three things checked when i did the headers search and they are all listed as the current version. Should i have something else marked somewhere?

---

