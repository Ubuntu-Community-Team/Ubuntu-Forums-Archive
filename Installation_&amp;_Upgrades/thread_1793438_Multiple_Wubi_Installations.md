---
title: "Multiple Wubi Installations"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by pcwiz11 on 2011-06-29
Could you tell me if it is possible to have more than one Wubi installation on a single PC. For example could I have both Ubuntu and Kubuntu installed at the same time or can you only have one at a time?

Thanks in advance!

---

### Post by bcbc on 2011-06-29
You can only have one at a time. While it's possible to work around this, it's not very straightforward. 

But by default, Wubi will uninstall the existing one before installing the new one.

PS [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by Rubi1200 on 2011-06-29
As bcbc pointed out, this is not really feasible.

One idea might be to download and burn to CD both the Gnome and KDE versions.

Run them as a LiveCD, decide which one you prefer and then install that version, keeping the other to use as a LiveCD.

---

### Post by pcwiz11 on 2011-06-29
> **bcbc said:**
> You can only have one at a time. While it's possible to work around this, it's not very straightforward. 

But by default, Wubi will uninstall the existing one before installing the new one.

PS [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Thanks very much for your help bcbc. I didn't realize that you can install the KDE desktop separately though. That might come in handy as I could run Ubuntu with KDE installed if I needed that.

---

### Post by bcbc on 2011-06-29
> **pcwiz11 said:**
> Thanks very much for your help bcbc. I didn't realize that you can install the KDE desktop separately though. That might come in handy as I could run Ubuntu with KDE installed if I needed that.

Hey, you're welcome :)

Just note the warning that you'll get your menus filled with apps from gnome as well as kde. 

If you want to play with it, back up the virtual disk (\ubuntu\disks\root.disk) within Windows first. You can always copy it back if you don't like the result.

---

