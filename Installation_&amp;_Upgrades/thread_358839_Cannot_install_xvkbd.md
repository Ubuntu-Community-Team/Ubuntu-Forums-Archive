---
title: "Cannot install xvkbd"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by MasterOfMuppets on 2007-02-11
I'm trying to set up my MX510 Logitech mouse using this guide:
[http://ubuntuforums.org/showthread.php?t=65471]("http://ubuntuforums.org/showthread.php?t=65471")

But I can't install xvkbd...
[COLOR="Blue"]moshewe@moshewe-laptop:~$ sudo apt-get install xvkbd xbindkeys
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xvkbd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xvkbd has no installation candidate
[/COLOR]

Replaced my hard disk and now after reinstall I can't apt-get it :(.
Help?

---

### Post by Kateikyoushi on 2007-02-11
Did you enable other repositories ? Should be in the universe repository.
System > Administration > software sources

---

### Post by daou on 2007-02-11
Do you have multiverse + universe repositories enabled?

---

### Post by MasterOfMuppets on 2007-02-11
I have no idea what are these repositories you guys are talking about :(...
I went into Sofware Sources and the tickbox "Community maintained Open Source sofware (universe)" was off, so I ticked it. It downloaded some lists and that was it for now.

Installed the xvkbd and xbindkeys, thanks for helping a noob :).

Should these repositories always be enabled?

---

### Post by daou on 2007-02-11
Repositories are servers where you can download apps from.

By default, Ubuntu only enables it's own repositories which contain officially supported software. Multiverse and universe gives you access to thousands of more apps. You don't have to use them, but I suggest you do. They aren't "officially" supported apps, but perfectly working ones nevertheless.

You can either enable them by editing your /etc/apt/sources.list file, or use the frontend suggested by Kateikyoushi. The frontend is much easier and safer to use (System > Administration > software sources). But if you want to start learning more about how your box works, I suggest always looking at the actual configuration files and trying to edit them instead.

---

