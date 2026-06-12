---
title: "[SOLVED] Why are my two Ubuntu PCs not updating to same version"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by MaxMax on 2008-06-08
Hello, I installed 8.04 on my two computers (one desktop and one laptop). When I am notified to upgrade either of them, I do. However, the laptop is always a few digits behind the desktop, and stays that way until the next upgrade cycle. It never catches up to the desktop's latest version. Currently :

**Laptop**:
[INDENT]Release 8.04 (hardy)
Kernel Linux **[COLOR="Red"]2.6.26-16[/COLOR]**-generic
GNOME **[COLOR="Red"]2.22.1[/COLOR]**[/INDENT]

**Desktop**:
[INDENT]Release 8.04 (hardy)
Kernel Linux **[COLOR="Red"]2.6.24-18[/COLOR]**-generic
GNOME **[COLOR="Red"]2.22.2[/COLOR]**[/INDENT]

Is there a reason for that? Is there a way to force the laptop to upgrade to the ACTUAL latest version?

Thanks for any help/info -- Max

---

### Post by tonym on 2008-06-08
Check the /etc/apt/sources.list files on the two machines.  Are they the same?

---

### Post by Sef on 2008-06-08
> Is there a way to force the laptop to upgrade to the ACTUAL latest version?

Applications > Accessories > Terminal

then type in this code:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by MaxMax on 2008-06-08
Thank you Tonym, Thank you Sef,

I compared the two /etc/apt/sources.list files. The one on the laptop had all but one line commented out. Here is an excerpt:

```
# Line commented out by installer because it failed to verify:

# deb http://security.ubuntu.com/ubuntu gutsy-security main

# Line commented out by installer because it failed to verify:

# deb-src http://security.ubuntu.com/ubuntu gutsy-security main

# Line commented out by installer because it failed to verify:

# deb http://security.ubuntu.com/ubuntu gutsy-security universe

# Line commented out by installer because it failed to verify:

# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

# Line commented out by installer because it failed to verify:

# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse

# Line commented out by installer because it failed to verify:

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe

# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

So I made a backup copy and then I copied the /etc/apt/sources.list from the desktop. 

After a reboot, nothing seemed to change, so I ran the first part of the command suggested by Sef: 

[INDENT]sudo apt-get update[/INDENT]

I then ran the second part of the command:

[INDENT]sudo apt-get dist-upgrade[/INDENT]

It offered to upgrade a bunch of software, which I didn't want to do right away, so I replied no to the prompt. 

However, somewhere along the way, one (or all) of those steps fixed the problem, because shortly after, the GNOME update notice appeared and now both Laptop and Desktop are running the same version.

Thanks!

---

