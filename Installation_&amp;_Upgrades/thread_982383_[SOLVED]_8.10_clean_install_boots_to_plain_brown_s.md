---
title: "[SOLVED] 8.10 clean install boots to plain brown screen"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Trevor4706 on 2008-11-14
I have an old Dell Inspiron 1100 with an Intel 82845GL integrated video card that has run Ubuntu versions 6.04 up to 8.04 without any problems.  I tried upgrading my 8.04 installation to 8.10 without success -- problems similar to those others experienced who took that route.  I've since tried unsuccessful clean installs with both the Desktop CD and the Alternate CD.  Both lead to the same result: I get the familiar Ubuntu log-in screen, enter my username and p/w, and then I go to a blank, brown screen and sit there.  It seems to be stuck somewhere between the log-in screen and the Gnome desktop.  I've tried re-starting X from the brown screen (Ctrl-Alt-Backspace) but nothing works.  Also tried various things from the recovery mode as well, but always end up at the same screen.

I'm about ready to give up and re-install 8.04, but want to give this forum a try first.  Appreciate any suggestions for resolving this.

---

### Post by Trevor4706 on 2008-11-15
Problem solved.  My video card couldn't handle compiz.  Used the root shell from the rescue mode and apt-get remove to uninstall compiz and compiz-core, then rebooted  and got into the Gnome desktop as advertized.:)

---

### Post by NIkonovT on 2008-11-30
Edit: Wow... That worked... Thanks for that!

---

