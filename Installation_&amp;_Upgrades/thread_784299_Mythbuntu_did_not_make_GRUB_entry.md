---
title: "Mythbuntu did not make GRUB entry"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by p-stone on 2008-05-06
Good morning

I have a machine running Ubuntu hardy heron. Yesterday I loaded mythbuntu hardy onto another partition on the same machine. The install ran fine, giving me no errors and from my ubuntu install I can see the other partition and it looks fine. However there's no entry on my GRUB menu for the mythbuntu install. I can't figure out why, I'm wondering if I should just reinstall or can I just make a menu entry for mythbuntu and save myself the install hassle?

Thanks

---

### Post by MountainX on 2009-10-28
bumping...

does mythbuntu use grub? or lilo?

---

### Post by tommcd on 2009-10-29
> **p-stone said:**
>  I'm wondering if I should just reinstall or can I just make a menu entry for mythbuntu and save myself the install hassle?

When you installed Mythbuntu, did you let the Mythbuntu installer install grub? If so, where did the Mythbuntu grub go, to the MBR, the Mythbuntu root partition, or somewhere else?
If Ubuntu's grub is still booting the computer, you can easily make an entry for Mythbuntu in Ubuntu's grub. To add an entry to Ubuntu's grub for Mythbuntu follow the advice in the 4th post in this old thread:
[http://ubuntuforums.org/archive/index.php/t-393379.html](http://ubuntuforums.org/archive/index.php/t-393379.html)
Hardy uses grub legacy, so that thread is still relevant for your situation.

---

