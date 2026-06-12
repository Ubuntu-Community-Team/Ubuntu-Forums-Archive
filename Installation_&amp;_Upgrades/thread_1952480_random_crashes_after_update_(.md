---
title: "random crashes after update ("
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by AlmaTlust on 2012-04-04
After performing an update I get weird random crashes in different DEs (KDE, XFCE). programs crash (both kde and gnome ones, although the latter ones seem to be a bit more "long-lasting"), plasma crashes, sometimes at login it tells me some weird message about consolekit not being able to connect to somewhere etc.

I tried to use muons history to see what packages have been updated, but it shows rubbish stuff, even updates of programs I haven't installed at all. One of the updates was a new kernel version (3.0.0-18 from proposed repository), and others were packages of xorg-edgers ppa (I have an intel card and the standard intel drivers shipped with ubuntu caused loads of problems).

Any clues anyone? I'd appreciate any hints.

==============
Update: the reason seems to be the kernel update. The problems don't appear with kernel 3.0.0-17.

---

### Post by crackers8199 on 2012-04-05
i too am seeing random nonsensical crashes since the update.  haven't tried rolling back to the older kernel yet, i'll give that a shot.

---

### Post by crackers8199 on 2012-04-05
seems there's something drastically wrong with the .18 kernel.  roll back to .17 has solved my issues as well...

---

