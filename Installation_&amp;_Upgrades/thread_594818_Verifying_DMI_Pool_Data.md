---
title: "Verifying DMI Pool Data"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Jynx on 2007-10-28
I've read every thread on this issue and grub fixes as well.  However I didn't see something posted in any of these that I've noticed on mine so I'm starting this thread.

My setup is as follows :

HDA
      1 - Vista
      2 - Files
      3 - Files

HDB
      1 - Ubuntu 7.10

If I have HDA set to boot first Vista starts fine.
If I have HDB set to boot first it just hands on "Verifying DMI Pool data"

Oddly enough though if I boot to the Ubuntu CD and go to the very bottom and click "Boot first Hard Disk"  Grub starts up just fine and I can choose Ubuntu or Vista.

---

### Post by Jynx on 2007-10-29
Anyone?

---

### Post by dwasifar on 2007-12-07
I know it's been a while since you posted this question, but if you are still having trouble, maybe this will help.

I ran into this same issue on my main desktop yesterday, and it cropped up on a friend's machine today.  

In both cases, going into BIOS on startup and resetting to defaults eliminated the problem.  In my BIOS I selected "Load Optimized Defaults."  Yours may be different.

I don't know why it worked, but it did.

---

