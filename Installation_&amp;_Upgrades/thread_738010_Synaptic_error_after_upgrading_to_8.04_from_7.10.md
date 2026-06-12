---
title: "Synaptic error after upgrading to 8.04 from 7.10"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by elnamo on 2008-03-28
My upgrade to 8.04 seems to encounter error after finishing download. The system restarted and I have to reconfigure X, the error message in Synaptic is


[SIZE="1"]E: /var/cache/apt/archives/language-pack-gnome-en_1%3a8.04+20080317_all.deb: trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/shared-mime-info.mo', which is also in package language-pack-en
[/SIZE]

Has anyone seen this kind of error care to explain what I should do next? Thanks.

---

### Post by Wilfred on 2008-03-28
Think I had the same message after an update.  I unflagged the 'language-pack-gnome-en' from the update manager and after that all went well. (even updates the next day were processed just fine)

Hope this works for you as well!

---

