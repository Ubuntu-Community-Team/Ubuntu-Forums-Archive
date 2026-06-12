---
title: "Where to find package bugfix information?"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by nomiz on 2011-01-10
Hi there,

Could someone please explain where I could find bug-fix information about updated packages?

For example, recently *xorg-common* and *xserver-xorg-core* are updated to version 2:1.9.0-0ubuntu7.1. What would be fixed in this release?

Thanks in advance!

---

### Post by arpanaut on 2011-01-10
Go into synaptic, search for the package and select it, then in the info box below select "Get Changelog"

Sometimes a little cryptic, that should get you started.

---

### Post by nomiz on 2011-01-10
Allright thanks! Almost too obvious, but thats probably because I never use Synaptic. Is there also an apt-command? Where does Synaptic get its info from?

---

### Post by arpanaut on 2011-01-10
Check the changelog of the package in question. You can do this via  "Package > Download Changelog" in Synaptic, or "apt-get changelog  package_name", or by going to [packages.ubuntu.com]("http://packages.ubuntu.com/") and clicking "Ubuntu changelog" for the package you're curious about, or visiting the URL 

[https://launchpad.net/ubuntu/+source/](https://launchpad.net/ubuntu/+source/)[COLOR=DarkRed]package_name[/COLOR]/+changelog

---

### Post by nomiz on 2011-01-10
Alright, thank you!

---

### Post by nomiz on 2011-01-10
Only *aptitude changelog package_name* seem to work

---

### Post by arpanaut on 2011-01-10
Funny, both work for me?????

Use the tool that works best for you...:)

---

