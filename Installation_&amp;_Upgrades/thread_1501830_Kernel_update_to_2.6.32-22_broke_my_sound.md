---
title: "Kernel update to 2.6.32-22 broke my sound"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by sripplinger on 2010-06-04
I just updated my kernel from 2.6.32-21 to 2.6.32-22 today.  Now I am getting no sound.  I have checked my mixer levels with both kmix and alsamixer.  Nothing appears to be amiss.  I tried rebooting with the old kernel and still no sound.  Help?!

---

### Post by sripplinger on 2010-06-05
SOLVED!!!

If anybody else is having this problem here is the solution.  Unplug the audio jack for your speakers from the input jack on the back of your motherboard and then plug it back into the output jack.  It's really amazing that a kernel update can actually move audio jacks around now...

Boy do I feel sheepish.

---

### Post by nss0000 on 2010-06-05
> **sripplinger said:**
> SOLVED!!!

If anybody else is having this problem here is the solution.  Unplug the audio jack for your speakers from the input jack on the back of your motherboard and then plug it back into the output jack.  It's really amazing that a kernel update can actually move audio jacks around now...

Boy do I feel sheepish.

Same thing happens with printers. The low_beta Ubuntu updating software is untested and deeply "flawed"

---

