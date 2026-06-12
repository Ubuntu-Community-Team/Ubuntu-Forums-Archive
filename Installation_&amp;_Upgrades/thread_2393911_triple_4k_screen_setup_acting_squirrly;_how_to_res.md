---
title: "triple 4k screen setup acting squirrly; how to reset display settings?"
date: 2018-06-09
forum: Installation &amp; Upgrades
---

### Post by dankegel on 2018-06-09
Hi all!  I'm experimenting with a Skull Canyon running a fresh minimal Ubuntu 18.04.
It works great when plugged into one 4k monitor (via any of the three
ports: hdmi, mini-dp, or type c; all three show up in xrandr as DisplayPort).

It even seems to work ok when I plug in two.  Doesn't matter which two.

[https://www.intel.com/content/www/us/en/support/articles/000005571/mini-pcs.html](https://www.intel.com/content/www/us/en/support/articles/000005571/mini-pcs.html)
claims that the Skull Canyon ( NUC6i7KYK ) can handle three 4k displays,
and indeed, if I do 'sudo systemctl start multi-user.target' and run startx, 
I see three nicely mirrored displays.
When I plug in all three, and boot to normal graphical.target mode with the usual gdm
greeter, one of the three screens does show gdm, and allows me to log in.

So far, so good.  But when I log in, all three monitors go black, and all
I can see is a mouse hugging the left edge of the right monitor.  It's
rather freaky.  This happens regardless of which user is logged in.

Unplugging any of the three monitors brings things back to a working-ish state,
with at least one of the two remaining monitors working.

I think it worked at first, then I clicked Something Wrong in display settings,
and now it's highly confused.  Alas, logging in as a different user doesn't seem to
rescue it.

Any suggestions for how to recover from this?  Where does the Display settings
widget store its data, and how can I reset that (ideally from the commandline)?

---

### Post by dankegel on 2018-06-11
Filed [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1776260](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1776260) for part of this.

---

