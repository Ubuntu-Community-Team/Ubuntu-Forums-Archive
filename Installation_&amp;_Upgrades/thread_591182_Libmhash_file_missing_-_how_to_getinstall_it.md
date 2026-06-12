---
title: "Libmhash file missing - how to get/install it?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by thealmightyone on 2007-10-25
I have installed a language called scheme, which I have to use as part of my course (as well as linux). I installed it, and if I try to run scheme, I am told a file, libmhash.so.2, is missing. I have repeatedly downloaded and installed different variants of scheme, always end with being told the same file is missing.

So far, I have tried installing a mhash library, which looked like it installed properly, but hasn't solved the problem. Should it have?

Being new to linux doesn't help much, so I'm hoping to solve the problem once and for all with your help.

---

### Post by oldos2er on 2007-10-25
Open Synaptic Package Manager (System, Administration), search for libmhash. Mark for installation the two files that show up, then click Apply.

---

### Post by thealmightyone on 2007-10-25
That has already been suggested to me, and the libmhash files aren't in there.

Do I need to download updates? This is the 7.10 release, so I can't see me needing updates already.

---

### Post by oldos2er on 2007-10-25
They're there, you just need to make sure you've got all the repositories enabled. Check System, Administration, Software Sources, and see that there's a check in each box.

---

### Post by thealmightyone on 2007-10-25
So, do I need to connect to the internet and download updates?

I should add that I am not posting through the ubuntu computer, but a different computer.

---

### Post by oldos2er on 2007-10-25
No, updates won't change your software sources. You need to connect to the internet, check software sources like I told you before, go into Synaptic, click Reload, then search for libmhash.

---

