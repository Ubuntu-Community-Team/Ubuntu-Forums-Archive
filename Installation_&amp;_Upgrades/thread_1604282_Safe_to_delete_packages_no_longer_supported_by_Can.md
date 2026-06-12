---
title: "Safe to delete packages no longer supported by Canonical?"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by Chariblaze on 2010-10-23
I've been trying to upgrade from a largely-untouched Lucid Wubi installation to Maverick, first uninstalling and reinstalling in Windows through wubi.exe. This led to another Lucid installation, instead of Maverick, which I understand is probably because Wubi is still being updated to include Maverick or Wubi is staying with Lucid because of the LTS release.

    I later tried burning the standard .iso file to a CD, and installing Ubuntu inside Windows. This worked, but anytime I tried to enter my password in for root privileges, the permission window stayed the same, albeit without the text field. This window was unresponsive, but closing it seemed to make everything work like normal. Since this first happened in the Update Manager, the updates all went through, but at the end there was a cryptic error message, which I know had parentheses. None of this seemed to actually harm anything, but I'd rather not have them. Reinstalling didn't seem to fix this.

    My actual question is this: if I were to upgrade Lucid through the Update Manager, should I remove all packages no longer supported by Canonical (13), since Ubuntu first installed them? I tried this through the Terminal, and for the most part, it seemed successful, though I couldn't get rid of the last one, xserver-xorg-video-v41. I understand that upgrading might lead to more problems since this is a Wubi installation, but I'd still like to know if deleting the first 12 packages is a suitable solution, and if there's any idea on how to delete the last one.

---

