---
title: "Uninstalling Apps in 12.04.1 LTS"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by ooleyguy on 2013-01-29
As the title says, I have Ubuntu 12.04.1 LTS installed and I'm liking it a lot. However, there are many apps installed by default that I don't think I need.

I safely uninstalled several of them but there are a few that I am scared of removing. Here is a list:

1. Bluetooth - I don't have bluetooth devices, but when I look to remove it, it tells me It will remove gnome-shell and gnome-user-share as well.

2. Language Support - I only speak English and don't use a non-standard keyboard, but it says the package contains the GTK+ frontend and I don't know what that means.

Is it safe to remove those or am I stuck with em forever and ever?

---

### Post by howefield on 2013-01-29
If in doubt, leave well alone. :)

Are you stuck for space ?

---

### Post by dino99 on 2013-01-29
the default apps list is dealt by the metapackage ubuntu-desktop. If you uninstall it, then you are able to remove some more apps; but take care of the messages you get while removing apps due to cross dependencies.
Then to also remove the unneeded libs left behind, you can run gtkorphan or bleachbit (set it carefully)

About the unwanted languages, install localepurge

---

### Post by ooleyguy on 2013-01-29
No, I have 4.5 TB total. I just don't like having non-necessary programs and files on my computer. Especially if they might be running and taking up RAM.

---

### Post by dino99 on 2013-01-29
> **ooleyguy said:**
> No, I have 4.5 TB total. I just don't like having non-necessary programs and files on my computer. Especially if they might be running and taking up RAM.

inside the menu : System Tools -> Pref -> Apps at startup
you can select which process to load at startup.

---

### Post by ibjsb4 on 2013-01-29
If you want more control over whats installed and whats not.  It is better to build up instead of tearing down.  Start with the mini.iso, do a terminal only install and then install the ubuntu-desktop without the recommend packages.

The "red dots" must be installed; the "green dots" are recommends and will not be install with the below command.

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)

Once you have the terminal install complete (with the mini.iso) just enter:

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

And your done :)

[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+mini+iso&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+mini+iso&ie=utf-8&oe=utf-8)

---

### Post by Bucky Ball on 2013-01-29
> **ooleyguy said:**
>  I just don't like having non-necessary programs and files on my computer. 

If you have that much space you might like to make a 10Gb partition and try going the other way, then, by having a play with a minimal install. That way, you get only what you ask for and can create a custom list of apps during the install. Rocket fast depending on what you drag in. Don't install a *buntu-desktop but only the desktop environment, like xfce4 or lxde or whatever; add that to the list of things you want during install along with a package manager, synaptics perhaps, firefox and thunderbird. You need to research some other essentials.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

