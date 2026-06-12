---
title: "Nautilus default version after reverting upgrade"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by marouane87 on 2016-05-16
Hello,
I tried to install Gnome 3.20 on Ubuntu Gnome 16.04 using the following commands:
```
sudo add-apt-repository ppa:gnome3-team/gnome3-staging

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt update
sudo apt dist-upgrade
```

I didn't like that luch and wanted to revert back to default Gnome of the distribution, so I ran the following commands:
```
sudo apt install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3-staging
```

But, I got Nautilus version 3.18 which does not ship by default with Ubuntu Gnome 16.04.
Is there anyway to get the default package please?

Thank you!

---

### Post by deadflowr on 2016-05-16
Need to also purge the gnome-3 ppa.
You added both the gnome-3 and gnome-3-staging ppas.
gnome-3 has 3.18 in it.

---

### Post by marouane87 on 2016-05-16
Thank you very much :) !
Just for the record if someone else reads this thread: Why reverting back. Some application are not yet ready for Gnome 3.20 (Firefox included), so the rendering is not exciting ;)
(Yes, and I didn't like the "other location" to access my disks instead of just accessing them from the side bar)

---

