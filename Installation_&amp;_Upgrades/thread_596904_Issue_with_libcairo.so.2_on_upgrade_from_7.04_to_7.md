---
title: "Issue with libcairo.so.2 on upgrade from 7.04 to 7.10"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by derekweber on 2007-10-30
Howdy,
I think this is a new issue but I might be off-track as I'm not too familiar with how shared libraries work in linux.

I upgraded my Dell Inspiron 6000 laptop from Kubuntu (yes, I know, I'm still waiting for Kubuntuforums to send me a registration activation email, several hours on!) 7.04 to 7.10 using the built-in update manager. Woot, looks sweet, however when I run firefox and try to save an image it dies completely - just disappears. I notice I can't run gnome games like /usr/games/sol too. I try running them from the commandline and get complaints about /usr/lib/libpangocairo... not having the right symbols in it.

After much faffing around (including uninstalling and reinstalling cairo2 and pango libs) I discover that /etc/ld.so.conf includes a reference to /usr/local/lib but not /usr/lib. In /usr/local/lib is another libcairo.so.2 which is old but is surrounded by a whole lot of Eclipse SWT libs. I back it up and create a link to /usr/lib/libcairo.so.2 (which is the new, up-to-date version, with the needed symbols, etc) and now my apps run again (although with a strange old looking font).

I'm wondering at what point does /usr/lib get onto the LD_LIBRARY_PATH, or if it does, or if it should. Where might I have got this /usr/local/lib/libcairo.so.2? If libcairo.so.2 is updated by the Adept Manager in /usr/lib why don't think seem to look there for it?

As I say above I'm not too familiar with how all this works, so I'm very happy to be corrected on anything. I'd just really prefer to find not just a solution (as I have) but the _correct_ solution without having to completely rebuild my laptop.

Oh, I did check the other related posts suggested by the forum page but they seemed to refer to libfreetype issues which I _think_ are unrelated (I may be wrong, please let me know).

Thanks in advance.

Derek (Adelaide, Australia).

---

### Post by derekweber on 2007-10-30
To see if the font issue was to do with libfreetype I put a link to it in /usr/local/lib from /usr/lib but it didn't change anything. The font is the old very thin one used in previous years, rather than the new thicker anti-aliased one used now.

---

