---
title: "No desktop manager after upgrade to 12.10"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by The Foz on 2013-01-30
I have just (yesterday) upgraded my main system (a desktop system which I also use a a server) from Ubuntu 12.04 to 12.10. Now I have no desktop manager when I log-in.

Instead of the desktop manager, it is running lightdm, which is enough for me to do server admin tasks, but not much more.

Directly before upgrading to 12.10, I ran updates on 12.04, so it is possible that the problem came from the updates, rather than the upgrade. I used the GRUB menu to boot into the previous version, and had the same issue.

Does anyone have a suggestion for getting my system working again?

I have tried removing and then installing again the "ubuntu-desktop" package, but it made no difference.

---

### Post by The Foz on 2013-01-31
I could probably fix this myself, if I could find out where the Desktop Manager is started, and what the correct command is to start the Desktop Manager. There is no user level .loginrc file, and nothing relevant in the /etc/default directory.

---

### Post by The Foz on 2013-01-31
So, I managed to make some progress. 

Using [this link]("http://news.softpedia.com/news/Install-Alternative-Desktop-Managers-in-Ubuntu-48586.shtml"), I found out how to set which desktop manager runs after login.

I am now able to log-in and get the gnome desktop manager (GDM), but when I set the selection back to the default (unity) desktop manager, it doesn't start and I am back to lightdm.

---

