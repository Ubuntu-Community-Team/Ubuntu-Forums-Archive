---
title: "Compile Vim with GTK GUI"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by bertilow on 2005-10-16
I've done a Breezy Kubuntu install from scratch since upgrading from Hoary gave lots of miserable errors.

The basics seem to be running well now after a few initial strange glitches.

Now I've tried to compile Vim 6.4 (just out of the door) with support for GTK GUI, but the compiler can't find any GUI support. I just tried it with versin 6.3, and the same thing happened. Vim 6.3 compiled and installed just fine with a GUI in Hoary, as did version 6.4.

It seems that some package is missing, but which one?

I've already read that I need "gnome-core-devel" and "libgtk1.2-dev". I've already installed both, but there is no change for the better. (I did wipe the old vim code, and unpacked it fresh before trying again.)

I've read that the compiler needs to see "gtk-config" (it should be in the PATH). It is, but still no luck.

Any ideas?

I just found that the precompiled "vim-gnome" package is a lot better than older prepackaged GUI vims that I've tried (e.g. it has multi-byte support compiled in), so I could almost go with that. But I'd like to try the latest version 6.4. It should be possible to compile it, no? If not, why not?

---

