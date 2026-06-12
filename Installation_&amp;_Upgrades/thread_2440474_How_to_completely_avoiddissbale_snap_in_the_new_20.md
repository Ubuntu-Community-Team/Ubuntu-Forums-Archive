---
title: "How to completely avoid/dissbale snap in the new 20.04 Ubuntu"
date: 2020-04-11
forum: Installation &amp; Upgrades
---

### Post by asen-christov on 2020-04-11
How do I completely avoid snap on my system if I install 20.04 Ubuntu? Preferably some way to disable/remove it already during installation.

---

### Post by The Cog on 2020-04-11
This does the trick:
```
sudo apt purge snapd
```

---

### Post by webaake on 2020-04-11
Well, that's after install isn't it? ;)

---

### Post by ajgreeny on 2020-04-11
> **webaake said:**
> Well, that's after install isn't it? ;)
Yes, it certainly is, but as far as I'm aware there is no way to stop the installation whilst you install the OS, in the same way that you can not choose other things to exclude from the installed system.  Is there a specific reason that makes you want to make life harder for you than it should be by stopping all snap packages from installing?

Be warned, however, that there are some applications that are only available as snaps, the obvious big one being chromium-browser.  There have been some comments about using a ppa repo in order to add it as a .deb package, but I've not searched that any further so far.

There also talk at [https://askubuntu.com/questions/1204571/chromium-without-snap](https://askubuntu.com/questions/1204571/chromium-without-snap) of using the debian buster repos for chromium but I have no experience of that either.

---

### Post by mikewhatever on 2020-04-11
> **asen-christov said:**
> How do I completely avoid snap on my system if I install 20.04 Ubuntu? Preferably some way to disable/remove it already during installation.

Well, you can always modify the installer, just learn to program, get the source, and dig in. It is up to you to decide if it's worth the effort.
Good luck.

---

### Post by Impavidus on 2020-04-11
You can also try the minimal installer, which will only install the things you ask for.

A standard install of regular Ubuntu has some snaps nowadays. I don't know about all flavours.

---

### Post by Tadaen_Sylvermane on 2020-04-11
> [COLOR=#000000]Be warned, however, that there are some applications that are only available as snaps, the obvious big one being chromium-browser.

Indeed. And it will only move more towards snaps as that is their path forward barring any major downfalls. If you really really want to avoid snap then Debian might be more your speed. I would guess though that ultimately many distros will move to either snap, flatpak or appimage. Universal packages make a lot of sense. Generally I don't like any of them either myself but I do see benefits. It's nice having the exact same version of LXD on any distro that supports snap. I've already had issue where my apt installed lxd didn't match one done via snap. Containers wouldn't migrate. In the case of LXD snap is their only planned release method from here on out.

Change happens whether or not one likes it. [/COLOR]

---

### Post by webaake on 2020-04-12
What's the future for Google's repos? [https://www.google.com/linuxrepositories/](https://www.google.com/linuxrepositories/)

---

### Post by grahammechanical on 2020-04-12
In 20.04 Ubuntu Software is itself a snap app.

Some years ago Ubuntu experimented with something called Ubuntu Personal. It was a snap based Ubuntu. The OS kernel was a snap. It used the Mir display server and Unity 8. It was more of a proof of concept experiment and the underlying Ubuntu code was not upgraded to the next release of Ubuntu.

I think it points the way that the owner of Ubuntu is thinking. In fact Ubuntu core is also a snap OS. It makes sense to confine as many apps as possible to secure the OS. 

[https://ubuntu.com/core](https://ubuntu.com/core)

Regards

---

