---
title: "exporting"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by tonab on 2007-03-05
hi ,i want to put my xubuntu onto a diffrent pc,how will it be transported.
example, I wish to put my xbuntu and all its settings  onto a bigger HD , faster PC,.

---

### Post by peabody on 2007-03-05
Reinstall xubuntu on the new computer, create a user with the same username, delete that new user folder and copy over your user folder from the older computer.

That's probably the most straight forward way.  Can't say they're won't be problems.  If you changed anything in /etc, you'll want to copy over those settings too.

You'll also want your installed packages from the old computer to be the same on the new machine; you'll probably want to copy over the /etc/apt/sources.list from the old machine and do something like the following on the old machine:

```

dpkg --get-selections > package_list

```

Then copy package_list to the new machine and run the following commands as root.

```

sudo apt-get update
dpkg --set-selections < package_list
sudo apt-get dselect-upgrade

```

I am no expert.  By all means, if someone has a better way, please speak up and correct me.

---

