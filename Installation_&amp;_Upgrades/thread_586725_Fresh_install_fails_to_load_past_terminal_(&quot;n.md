---
title: "Fresh install fails to load past terminal (&quot;no resume image&quot;)"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by scottevan on 2007-10-22
I've just done a fresh install of Gutsy on my desktop PC which was previously running Feisty without issue.

I'm having a weird problem where Ubuntu starts to load, getting all the way through the splash screen, but doesn't load gnome and instead drops me on a terminal. The only text on screen is the following:
```
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/22733170-f5c2-4a90-9aab-a5c503ef45b1) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/22733170-f5c2-4a90-9aab-a5ac503ef45b1
kinit: No resume image, doing normal boot...

Ubuntu 7.10 scott-desktop tty1
```

I can then get gnome to start by typing "/etc/init.d/gdm restart" - but it won't load automatically!

Any suggestions on what might be going wrong? I tried reinstalling twice without success. Any advice would be much appreciated. I am somewhat unsavvy with regards to *nix troubleshooting.

---

### Post by ddrichardson on 2007-10-22
Does [this]("https://bugs.launchpad.net/ubuntu/+bug/103148") bug report look similar?

---

### Post by scottevan on 2007-10-22
> **ddrichardson said:**
> Does [this]("https://bugs.launchpad.net/ubuntu/+bug/103148") bug report look similar?
The similarity is striking, but it looks like this bug simply causes a delay in the loading of gdm where I am not having it load automatically at all. Maybe a sister problem? I also have 2 sata drives.

I'll try disabling the splash in "/boot/grub/menu.lst" as someone suggested.

---

