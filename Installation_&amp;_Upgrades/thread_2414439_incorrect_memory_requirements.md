---
title: "incorrect memory requirements"
date: 2019-03-10
forum: Installation &amp; Upgrades
---

### Post by zulan2 on 2019-03-10
I just tried to install Lubuntu 18.10 on an old system with 512 MB RAM.

The installation fails stating it requires 1 GB of memory.

All documentation I could found indicate that general use with 512 MB RAM should be fine, e.g.

[https://lubuntu.net/lubuntu-18-04-bionic-beaver-released/](https://lubuntu.net/lubuntu-18-04-bionic-beaver-released/)
[https://docs.lubuntu.net/lubuntu_installation_on_old_computers](https://docs.lubuntu.net/lubuntu_installation_on_old_computers)

This is really frustrating.

Now I try to report a bug at [https://bugs.launchpad.net/lubuntu/+filebug](https://bugs.launchpad.net/lubuntu/+filebug)

but it only lists the projects LxFind and LxScreenshot.

I'll leave this here in the hopes that it may help someone in the future.

---

### Post by CatKiller on 2019-03-10
[https://lubuntu.me/cosmic-released/](https://lubuntu.me/cosmic-released/)

> The installer enforces a minimum of 8GB free drive space and 1GB free RAM, but these are not truly the minimum requirements. Remove the “storage” and “ram” lines from the “required” section of /etc/calamares/modules/welcome.conf before running the installer and everything will proceed like normal.

---

### Post by zulan2 on 2019-03-11
Thanks alot!
I didn't expect that given the clear error message.

---

### Post by CatKiller on 2019-03-11
They've decided - correctly, in my opinion - that their focus shouldn't be primarily on old and terrible hardware, and should instead be on making a great, lean, operating system. The main driver of higher requirements isn't the operating system itself, but rather getting good performance out of current websites.

---

