---
title: "&quot;Unmountable boot volume&quot; error msg when loading XP (dual boot)"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by dpatel304 on 2006-10-29
I am trying to set up a dual boot system with ubuntu and xp.  My main problem seems to be in the partitioning.  I understand how much space to put for each partition and what it will roughly be used for.  My problem lies in what settings to use for each partition.  The guides I used are pretty out dated, and was wondering if there was a current dual boot guide for the newest version of ubuntu.

Anyway, Linux works fine, but when I try to load XP from the GRUB menu, it starts the win xp loading logo (xp logo with a progress bar underneath), then goes to a blue screen which says "Unmountable boot volume"

Any help would greatly be appreciated.

---

### Post by Splittor on 2006-10-29
Typically an unmountable boot volume is fixed easily by a chkdsk.  Boot up a Windows cd, go to a Repair console, and run chkdsk.

I don't think this will replace GRUB as the boot manager (i highly doubt it) but be aware if necessary you may have to repair GRUB if that occurs.

---

### Post by dpatel304 on 2006-10-29
thanks for the reply.  I tried this and it gave me the message
"there are one or more unrecoverable problems"

..or something to that effect.  It sounds like I can't fix it, and will need to redo my installation.

---

### Post by Splittor on 2006-10-29
What about a chkdsk /r ?

I think that's it...I know in the approx. 10 times I got that error this year (i'm a tech at my college), a chkdsk /r always fixed it.

If you can't repair it, or force repair it, then I'd say you're out of luck.  You could use a boot cd to recover files or something to that extent.

---

### Post by dpatel304 on 2006-10-29
I did try chkdsk /r, and that was the message it gave me.  I guess I am out of luck.  Not a big deal, since my PC has nothing of importance on it.  Thanks for the help, anyway.

---

### Post by Splittor on 2006-10-29
I apologize.  Best of luck!

---

