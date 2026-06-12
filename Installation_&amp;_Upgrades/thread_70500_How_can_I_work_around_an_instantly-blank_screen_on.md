---
title: "How can I work around an instantly-blank screen on LiveCD startup?"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by Blueshell on 2005-09-30
I've got a pair of SGI 1600SW flat panel LCD displays which work perfectly under Ubuntu Hoary using an xorg.conf file I modified from a previously-working XF86Config file under Debian Sarge.  I succeeded in doing this by bootstrapping via an install on a more-common display and video card, then modified the xorg.conf file, swapped display hardware, and rebooted.  Fine so far.

However, I'd like to be able to use my Hoary LiveCD as a rescue disk, but it can't seem to figure out how to drive these displays (they're using the SGI Revolution #9 driver cards, which are rare).  I get the normal VGA-mode "boot:" prompt asking me for "install", "live", or "expert", but typing "live" instantly blanks both screens, and even C-A-F1 doesn't give me a non-X login.  Is there some way of telling the LiveCD -not- to try to enable X, but just to dump me into a shell?  GIven that I'd really like a rescue CD that's the same OS as the normal machine (so things like support for LVM and maybe an encrypted filesystem will already be on the CD---the idea being that I can use the LiveCD to resize the filesystem -without- having to have a spare root around), it'd be nice if I could get the LiveCD to actually work on this machine without swapping display hardware around.

(My other options are (a) taking up space with a secondary emergency partition that's not normally mounted, or (b) making my own bootable CD, something I haven't yet attempted.)

Thanks!

---

### Post by Blueshell on 2005-10-01
Okay, I've figured out a workaround.  On my hardware, booting with the framebuffer off (e.g., "live debian-installer/framebuffer=false") works IN BREEZY ONLY and gets all the way up, yielding a usable LiveCD session.  (And thanks to the Ubuntu developers     for making this one of the suggested boot options in one of the CD's help screens!)

In Hoary, OTOH, booting that way gets much farther---instead of instant blank screen, it finishes loading & initializing everything---but still doesn't work---because as soon as it's done initing, the screen BLOOMS SOLID WHITE, taking a few seconds to do so, and stays that way.  I presume it's being misdriven with the wrong sync rate once X starts.

So -something- changed (for the better) in guessing monitor parameters between Hoary & Breezy (well, the preview of last week), but I have no idea what.

---

