---
title: "Can't boot Linux kernel 2.6.38-10"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by annet on 2011-08-03
I updated my kernel from 2.6.38-8 last week via the Update Manager.  Now my IBM Thinkpad Z60t just sits there with my Caps Lock indicator blinking below a black screen if I try to boot into Linux 2.6.38-10.  I can go to the "Previous Versions" sub-menu, click on "Linux 2.6.38-8" and it boots just fine.  I'm running Xubuntu Natty.  

Anyone else have this problem?  No kernel updates available since this happened...

---

### Post by coffeecat on 2011-08-03
Hi and welcome to the forum.

A flashing caps lock indicator means a kernel panic. Try booting into the 2.6.38-8 kernel and open Synaptic. Search for 2.6.38-10 - you should find three or four packages - and mark them all for re-installation. If you still get the same problem after re-installation then you'll have to conclude that some aspect of your hardware is not compatible with the -10 kernel. (The -10 kernel works just fine on the machines I've installed Natty to.)

You'd need to continue to use the -8 kernel until such time as a >10 kernel comes through the updates. I've done a quick google search for your particular machine and Ubuntu and I didn't find anything relevant, but you might want to try a more extensive search to see if you can find anything.

---

