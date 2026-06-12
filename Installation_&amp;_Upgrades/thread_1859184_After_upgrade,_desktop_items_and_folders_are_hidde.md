---
title: "After upgrade, desktop items and folders are hidden"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by pefty on 2011-10-13
I just upgraded to Ubuntu 11.10 (32-bit) and had a smooth transition, except for one glitch. When my desktop appeared, nothing was on it. I tried to open my home folder and it refused to open. Through application dialogs, I can see that all my files are exactly where they used to be, including the ones on my desktop -- it's just that they seem to be hidden for some reason!

I wasn't using any special desktop app that I was aware of, just whatever came with the Ubuntu distro by default. Please let me know if you understand what happened to my file visibility and how I might restore it. 

Thanks!
 pefty

---

### Post by ezramorris on 2011-10-13
> **pefty said:**
> I just upgraded to Ubuntu 11.10 (32-bit) and had a smooth transition, except for one glitch. When my desktop appeared, nothing was on it. I tried to open my home folder and it refused to open. Through application dialogs, I can see that all my files are exactly where they used to be, including the ones on my desktop -- it's just that they seem to be hidden for some reason!

Hi,
Welcome to the Ubuntu forums!

I don't believe that there's any way to see items in the Desktop folder on your desktop with the new Unity interface, but as you pointed out you can still access them by browsing to them.

The "Home Folder" item in the launcher should take you to your home folder.

If not, launch Terminal and type:
```
nautilus "$HOME"
```
and see if that works.

Ezra.

---

### Post by pefty on 2011-10-13
Thanks for the suggestion, Ezra, but Ubuntu threw an error when I tried it:

> Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
Trace/breakpoint trap

Any other ideas? Or how else can I get my new Home folder into my Launcher?

Thanks!
pefty

---

### Post by BazookaAce on 2011-10-13
Install Dconf Editor 

```
sudo apt-get install dconf-tools
```

Run it and navigate to: 

org->gnome->desktop->background

Enable "show-desktop-icons"

---

### Post by ezramorris on 2011-10-13
> **pefty said:**
> Thanks for the suggestion, Ezra, but Ubuntu threw an error when I tried it

Weird. It could be that some packages are at incompatible versions.

Try checking for any updates and installing them:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

If that doesn't find anything or fix it, post the output of:

```
apt-cache policy nautilus
```

---

### Post by pefty on 2011-11-21
Thanks all, it fixed itself on reboot!

---

