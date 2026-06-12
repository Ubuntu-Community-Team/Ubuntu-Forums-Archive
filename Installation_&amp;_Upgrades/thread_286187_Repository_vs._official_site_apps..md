---
title: "Repository vs. official site apps."
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Armagguedes on 2006-10-27
[SIZE=2][FONT=Tahoma]Greetings.

I was wondering about installing (and the method of installing) applications in Ubuntu.

I know that the versions available on the repositories are official, they have customized artwork/icons and they are tested for stability for the current version of Ubuntu.

However the 6 month dev. cycle gets the apps outdated pretty quickly (especially annoying when the new version of an app gets released 1 week prior to/after the release).

So, what are the disavantages (other than those above) of removing/purging an app (say Firefox 2.0) from the system and installing a new version from a binary/source tarball/.deb from the official site?

(Having to manually add the new program to the K/Start/GNOME menu doesn't count.)

[/FONT][/SIZE]

---

### Post by warjowuch on 2006-10-29
Wel, let me tell you my experience:
When app's are delivered in deb-format, it's most of the times no problem: they just appear in synaptic.

But Firefox-updates via the method 'gksudo firefox', and then using the internal updater messes it up pretty badly. Then you can't control firefox via apt-get anymore :-( When I removed all firefox-related things from my harddrive, it still wouldn't work out. A friend of mine- a very skilled linuxer - solved this problem for me with quite in depth actions...

My 2 cents, what do others tell?

---

