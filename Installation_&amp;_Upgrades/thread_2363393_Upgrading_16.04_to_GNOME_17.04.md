---
title: "Upgrading 16.04 to GNOME 17.04"
date: 2017-06-09
forum: Installation &amp; Upgrades
---

### Post by Semn on 2017-06-09
Hello, I am having trouble with installing GNOME 17.04 from USB stick and wanted to install 16.04 , and then install GNOME 17.04 over it. Is it possible directly from download or running some script in 16.04?

Thanks

---

### Post by #&amp;thj^% on 2017-06-09
Sorry this  is not very clear to me?
Will 16.04 install? Or do you have 16.04 installed and want to upgrade to 17.04?
EDIT: And do you have any other OS's like Windows installed?

---

### Post by Semn on 2017-06-09
No other system on the computer. 16.04 installs from the CD, but 17.04 does not from the USB. So I install 16.04 from the CD, and then would like to install 17.04 from there using some sudo command?

---

### Post by #&amp;thj^% on 2017-06-09
Hmmm? This is not **not the preferred way to do this**, but seeing that it will will be a fresh install you could in theory, after 16.04 is installed and most importantly
_updated fully_.
So first run:
```
sudo apt update && sudo apt full-upgrade
```

You'll first need to make sure update-manager-core is present (it may already be installed):

```
sudo apt-get install update-manager-core
```

Next, run:

```
sudo do-release-upgrade
```

You may need to check /etc/update-manager/release-upgrades and change the line:

```
Prompt=lts
```

to:

```
Prompt=normal
```

for the release to show up.

---

### Post by Semn on 2017-06-09
thanks !

will try this

---

### Post by #&amp;thj^% on 2017-06-09
I'll be watching for a successful out come then.;)
Good luck...and post back any problems you encounter.
Cheers

---

