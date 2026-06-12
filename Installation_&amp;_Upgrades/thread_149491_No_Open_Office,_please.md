---
title: "No Open Office, please"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by sameat on 2006-03-24
I want to do a fresh install of dapper (but this question applies to earlier versions of ubuntu as well).  

I don't want openoffice...I am perfectly happy with abiword and gnumeric, and I am not interested in dealing with openoffice bloat at all.

They way I see it, I have a couple of options:

1) Do a "server" install and apt-get install the desktop stuff afterwards
2) Do a regular install and apt-get remove openoffice

Are there other options?

Which option is the most efficient?

Thanks for your help.

---

### Post by dermotti on 2006-03-24
I went with the server install and install xubuntu-desktop right after. Went very smooth and my system wasnt cluttered with useless programs.

go server install.

---

### Post by megabyte405 on 2006-04-19
The xubuntu install (server, then install xubuntu-desktop) will also install AbiWord by default in place of OOo, so that looks to accomplish what you want.   The XFCE environment is a bit different than the default GNOME, however, so it might be less to your liking (or more, who knows?)

Otherwise, there's no real harm in removing OOo after installing the full install.  You can even install the regular install, remove OOo, add xubuntu-desktop, and pick which desktop (GNOME or XFCE) you want each log-in: just pick your session on the login screen.

Good luck, and thanks for using AbiWord!

-- Ryan, AbiWord dev

---

### Post by glaze on 2006-04-20
Install as server and then install gnome-core or kde-core. It will not install all the bloat.

---

