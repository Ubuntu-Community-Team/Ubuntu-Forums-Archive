---
title: "The Applications menu does not appear on my new Ubuntu Gnome desktop"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by Ludwin on 2006-10-22
I just installed Ubuntu from Xubuntu ( sudo apt-get install ubuntu-desktop )

The Xubuntu Xface desktop does still work. But if I choose the ubuntu gnome desktop, the place where the word "applecations" should appear is empty. If I click on it, nothing happens.

Why this? Some hints:

I had to fix a bug with slocate: a beta version of slocate was lying in /var/cache/apt/archives/ . To install the non beta slocate, I had to remove the file /etc/cron.daily/find . Then I could install slocate and ubuntu was configurated.

Then I was asked several times if I wanted to keep so configuration files or replace them with new ones. The default choice was to keep them. I had no idea what these files were. I just chose to replace them all.

Could this be the cause of the problem?

Does anyone know a way to fix this?

---

### Post by Kateikyoushi on 2006-10-22
Right click on the bar, add to panel and from the utilities group select menu bar.

---

