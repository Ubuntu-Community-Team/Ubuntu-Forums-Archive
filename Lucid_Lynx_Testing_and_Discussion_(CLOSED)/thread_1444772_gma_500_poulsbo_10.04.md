---
title: "gma 500 poulsbo 10.04"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xeemo on 2010-04-01
Is there currently any support in the 10.04 beta for the gma 500?  I've got it working in 9.10, and I'd like to upgrade, as it fixes a few of my other problems, but I can't get the GMA 500 working.

---

### Post by overdrank on 2010-04-01
Moved to Lucid Lynx Testing and Discussion  :)

---

### Post by Mulenmar on 2010-04-01
[None that I've found]("http://ubuntuforums.org/showthread.php?t=1440310"), sorry. :( But this is going to be an LTS release, hopefully Intel will update the IEGD driver to support it.

And hopefully somebody will port the Arch Linux 915resolution-static package to Ubuntu -- at least with that, I can set up the fbdev driver to have a full 1366x768 framebuffer. :(

The biggest thread on here about this accursed chipset under Lucid Lynx seems to be [here]("http://ubuntuforums.org/showthread.php?t=1428736"), but there are no solutions there either.

The main problem atm is that both drivers for this chipset only work with the old version of the graphics server (Xorg 1.6) while Lucid Lynx uses version 1.7.

If somebody put together a PPA with the older Xserver and the IEGD and Poulsbo drivers, I'm sure that would make a lot of people happy, too. :-\"

---

### Post by Ibidem on 2010-04-02
What about [grub2-915resolution]("http://wiki.archlinux.org/index.php/Acer_Aspire_One#Using_intelfb_without_an_initrd")?
Same thing, but it sets the graphics mode before you boot Linux.
Here's [the patch]("http://aur.archlinux.org/packages/grub2-915resolution/grub2-915resolution/grub2.patch"), but it requires recompiling grub2...

---

### Post by last1 on 2010-04-06
Wish I'd read this before trying for so long to get it to work. I'm going to update the wiki.

---

### Post by nekr0z on 2010-04-11
Ibidem, thanks A LOT for the hint. And the best thing about it is that ubuntu comes with 915resolution module compiled in grub2, so no recompiling is actually needed.

Is there any way to make this framebuffer setting survive suspend? On my system, with this framebuffer workaround enabled, suspend-to-ram effectively kills X and makes it reload with VESA that can't keep the desired resolution.

---

