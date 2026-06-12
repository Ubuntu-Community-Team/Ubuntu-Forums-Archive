---
title: "Restore GNOME login?"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by palz2015 on 2010-04-05
I am trying Xfce in my Ubuntu Karmic installation. I just logged out and I get the Xubuntu login screen. I prefer the GNOME one, and xubuntu-desktop sets Xfce as default. I tried editing /etc/x11/default-display-manager and it already says /usr/sbin/gdm.

Help please

---

### Post by Simian Man on 2010-04-05
Xfce doesn't have its own login manager, so you are still using gdm.  You just switched to the Xubuntu gdm theme when you installed 'xubuntu-desktop'.  This is why these metapackages are a bad idea, but everyone always tells people to install them.

---

### Post by palz2015 on 2010-04-05
How do I switch it back? And why does Xfce duplicate desktop environment names (in the 'session' menu it has Xfce session and GNOME listed twice)?

---

