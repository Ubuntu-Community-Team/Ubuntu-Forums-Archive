---
title: "No change logs/description when auto-updating new kernel..??"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by ampes on 2006-06-15
Hi,just want to ask some stupid newbie question..Today new kernel (2.6.15-25-686 and 2.6.15-25-386) and fglrx driver has been automatically updated,but can someone tell what are the changelogs or fixes for these upgrades??Window$ Automatic Update always put their description for every update so their customers know what have been changed and patched..it is nice to know what have been fixed..

As for the updates,now my GRUB lists 4 kernel to boot (plus 4 for Recovery) and I am using the 2.6.15-25-686 kernel..Is it ok to uninstall the unuse kernels (386 and old kernel) or just comment out other kernel from GRUB menu.lst ??

Edit: Ok...I realize some updates have their description...but why major update (kernel and fglrx driver) still doesnt show any description...

---

### Post by adamvert on 2006-06-16
Can't help with information about the upgrade - I'd like to know too! But it's definitely fine, advisable even, to remove unused kernels (assuming that your current kernel is working fine).  If you remove them using Synaptic, GRUB will automatically get updated.

Adam

---

