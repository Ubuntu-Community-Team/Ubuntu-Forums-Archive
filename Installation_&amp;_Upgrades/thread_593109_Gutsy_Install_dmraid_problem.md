---
title: "Gutsy Install dmraid problem"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by sdhog2002 on 2007-10-26
I successfully updated my Feisty to Gutsy on my Dell 720 dual boot XP/ubuntu with RAID1 (I needed to add the initrd line to menu.lst, as described in numerous posts).  I had previously set up the RAID using the fakeRAIDHowTo, without too much difficulty. I am now trying to do a clean install of x86 64bit using an installation CD (I want 64 bit to get a sound driver - X-Fi driver only available in 64bit).  I can see my RAID mirror when I do dmraid -r, but dmraid -ay does not activate the RAID and I cannot go further. I get no error message when I do dmraid -ay, just nothing - after typing 'dmraid -ay' it just goes straight back to the prompt.:confused:

---

### Post by pjman on 2007-11-07
Hi, I'm in the process of doing pretty much the same thing. I found that nothing will show up under /dev/mapper/ if you still have your swap partition. Try sudo swapoff -a and deleting it with fdisk or parted.

---

### Post by sdhog2002 on 2007-11-08
Thank you, pjman. I will give that a try, out of interest, and let you know. The issue has become less important (prompted mainly by no suggestions how I could overcome it) as I am using my onboard sound instead of X Fi.

---

