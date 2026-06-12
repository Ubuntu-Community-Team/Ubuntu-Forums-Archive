---
title: "Corrupt kernel"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by dhavalbbhatt on 2007-10-17
All,
I have been playing around with Gutsy for a while now, however, there have been updates to the kernel files on almost a daily basis. A couple of things have happened - I was on version 2.6.20-15-generic when I first installed Gutsy from the CD. Within a few days they moved it up to 2.6.20-16-generic and in that version, my internet connection and the sound card did not function (which I haven't used at all since I started noticing that problem). Subsequently, the kernel has moved to 2.6.22-14-generic version. However, when I try to boot from the latest (2.6.22-14-generic) kernel version, I get a "File not found" error. 

My questions are:
1) How do I fix that - I have tried using the Grub CLI method, and it seems the Grub can't find the latest kernel versions in the /boot folder (even though I am able to see the files). 

2) If I don't update to the latest kernel, how does that impact the upgrade to Gutsy (official version)? Will I have to completely reinstall Gutsy or is there a way for me to remove the kernel versions that are not working and just hope that when I upgrade to the official version, the upgrade will take care of everything (yeah - I am playing naive).

Thanks,
DB

---

### Post by Pumalite on 2007-10-17
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by dhavalbbhatt on 2007-10-17
Thanks Pumalite, but what are we looking for?

My grub currently points to the older Kernel - I have commented out the latest kernels, so that I don't have to go through the trouble of scrolling down and hitting the right kernel and avoid getting the "File not found" error during boot up.

Is there a way I can remove the newer kernels and just do a proper upgrade when Gutsy is released tomorrow?

DB

---

### Post by Pumalite on 2007-10-17
You can remove a kernel through Synaptic. Make sure is one you don't need.

---

