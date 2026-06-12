---
title: "Menu.lst Issue after kernel upgrade"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by concord on 2006-08-04
My laptop has a 1280x800 screen.  The screen used to have two of everything on the screen as it was booting.  Once it went into the gnome desktop everything looked fine though.  I searched the newsgroups and found that I could get the screen to look normal by adding

vga=792

to the kernel options in the menu.lst file.  This works great except each time I do a kernel upgrade ...

1) the new kernel line does not include this perameter
2) it removes the perameter from all the kernel lines

I manually put the line back in, so it's not a big deal.;)   My question is why can't the upgrade process check for "special perameters" and just add them to the new kernel line?  Other people must have other different perameters, are they having this same issue?

Thanks.

---

### Post by zxee on 2006-08-04
This is probably more of a grub issue than a apt or synaptic problem. After thinking more about this I wonder if someone has already created a script to deal with this?
Grub2 is being developed to replace the current grub.
Perhaps this feature is included? You might want to check the grub website. Hope that's helpful.

---

