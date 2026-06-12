---
title: "Redundant files on boot partition?"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by DadsArmy on 2011-06-15
Hello!

My boot partition doesn't have any space left, rendering me unable to install any updates.
Most space in the boot directory (85 MB) is taken by the following files:

initrd.img-2.6.32-24-generic
initrd.img-2.6.32-26-generic
initrd.img-2.6.32-27-generic
initrd.img-2.6.32-28-generic
initrd.img-2.6.32-29-generic
initrd.img-2.6.32-30-generic

It seems to me that I´d need at most one of these. What exactly do (or did) these initial ramdisks do, and is it safe to delete them? :confused:

Thanks in advance.

---

### Post by mörgæs on 2011-06-15
If you need more space, have you tried 

```
sudo apt-get clean
sudo apt-get autoclean
```

?

---

### Post by DadsArmy on 2011-06-15
Thanks[COLOR=Black] [/COLOR]mörgæs, but I'm afraid that didn work.
Installing a small, selected set of updates does work (there is still some space left).
The initrd's are still there though, does this mean they shouldn't be removed?

---

### Post by mörgæs on 2011-06-15
I wouldn't bother with removing them, unless you are running out of space again.

---

### Post by plucky on 2011-06-15
> Thanksmörgæs, but I'm afraid that didn work.


It is best to use **Synaptic Package Manager** to remove old kernels.

Search for **linux-image** and **linux-headers** and mark the old kernels for "complete removal", then **Apply**.

It is recommended to keep at least one older kernel,just in case you mess up the current kernel,then you will still have something to boot into to fix the problem.

**Make sure you don't remove the current running kernel.**

This will free up space in the /boot partition.

Some people recommend using "Ubuntu Tweak",but I prefer to use SPM. 

Good Luck

---

### Post by mörgæs on 2011-06-15
This is just a minor issue:

When things change, it is better to write a new post rather than editing an old one. My #4 refers to your #3, in which you initially stated that everything worked. You and I know the connection, but it is confusing for a new reader, who later finds the thread while searching for a solution.

---

