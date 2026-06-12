---
title: "[SOLVED] How to prevent automatic kernel upgrade?"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by valmi on 2008-06-19
I'm a new convert to (X)Ubuntu, and a very enthusiastic one, except for the fact that since I first installed Synaptic or update-notifier or whoever is responsibled for that insisted on installing a new kernel about once every week.

Now, it's not a major hassle. It takes a little time to download, a little time to make menu.lst look as I want it to, a little time to reboot, and it adds an nth additional kernel image that I'm not too sure what to do with.

But for what little hassle it is, I don't see any benefit. As far as I'm concerned, I'd be very happy to roll back to a more stable build and stick with it, without update-notifier continually harrassing me. Is there a way to do this?

Thank you very much!

---

### Post by grim4593 on 2008-06-19
Not sure if you can do it this way in xubuntu, but in gnome you can go to System -> Administration -> Software Sources. On the updates tab, just uncheck "Check for Updates". That way it won't bug you until you manually go into Synaptic and check for updates.

I did the same thing back in Windows: disable the Automatic Update service until I wanted to check for updates. No point having it secretly downloading and installing everything making everything slower.

---

### Post by valmi on 2008-06-23
Thank you. I was able to do the same thing in Xubuntu, through System -> Software Sources.

Sadly I didn't find a way to still update everything but the kernel, which would have been my first choice, but at least that'll bother me less often.

---

### Post by grim4593 on 2008-06-23
Well... Open Synaptic and search for "linux-". Then hit the column header above the checkboxes to put the currently installed packages at the top and then highlight the kernel, headers, modules, image, and the metapackages. Then go to Package -> Lock Version. That way they won't get upgraded at all until you unlock them.

---

