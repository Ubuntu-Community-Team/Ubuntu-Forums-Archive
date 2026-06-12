---
title: "Upgrading Cream (Vim)"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by LeeU on 2007-05-08
Does anybody know how to get the latest version of Cream for Vim? The Synaptic Package Manager is showing .331 and yet the latest is .37.

Does anyone also know where to get some documentation for Cream itself?

Lee

---

### Post by bukwirm on 2007-05-08
You should probably look at the project's [webpage]("http://cream.sourceforge.net/home.html") for both the latest version and it's documentation.

---

### Post by LeeU on 2007-05-08
The link to update for Ubuntu is broken and there is no documentation. I was wondering if there was a way to get the SPM to update it, automatically.

---

### Post by LeeU on 2007-05-09
Also, how do I upgrade to a newer version of Vim than listed in the Synaptic Package Manager?

---

### Post by bukwirm on 2007-05-10
All packages currently installed should be updated by Synaptic automatically.

If you want a newer version of vim, you'll need to download it from the [vim website]("http://www.vim.org/") and install it yourself. Look for a debian package which you can install with *dpkg,* or a RedHat package, which you can convert to a debian package with *alien*, then install with *dpkg*.
If you can't find either of those, you'll probably need to compile it from source.

---

### Post by LeeU on 2007-05-10
Yeah, for some reason, it doesn't show the new release for vim. I recently switched from Windows and liked the Synaptic way of installing/upgrading. Guess I'll have to learn how to compile.

Thanks.

---

### Post by bukwirm on 2007-05-11
It takes a while for newly released software to find it's way into the repositories - that's probably why the latest vim release isn't there.

---

