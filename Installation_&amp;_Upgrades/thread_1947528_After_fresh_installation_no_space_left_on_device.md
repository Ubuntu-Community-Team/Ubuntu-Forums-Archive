---
title: "After fresh installation: no space left on device?"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by AussieGuy on 2012-03-26
I have recently installed Kubuntu 11.10 on a machine with a 300Gb HDD.  All went well; I did a basic installation (just accepting all the default settings, except that I allowed the use of the full disk, thus removing Windows), and then copied the home directory from my old machine using "scp -r", which was less than 3Gb of material.

However, now when I attempt to add more things, I get a "No space left on device", and df produces the following output:

Filesystem    1K-blocks Used Available Use% Mounted on
/dev/sda1     303867232 288837784    0 100% /  

I don't know whether this is a related or different issue, but I also now can't start X as it claims "XKB: Failed to compile keymap", and "Failed to activate core devices".

Does anybody know what's likely to be going on here, and how I can fix it?  I suppose I can do a fresh install, but how can I prevent this happening again?

Thanks,
-A

---

### Post by AussieGuy on 2012-03-26
Seems that my .wine directory (from my old computer) kept getting recursively copied into itself onto the new computer, until du reported a usage of something like 272Gb for that one directory.  I'm currently deleting it...

-A.

---

