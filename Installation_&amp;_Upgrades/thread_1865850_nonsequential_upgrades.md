---
title: "nonsequential upgrades"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by nanog on 2011-10-20
GDM  is borked in 11.10 and breaks non-sequential upgrade via apt/dpkg. You should remove it and its deps before upgrading from lucid, maverick, etc..

Upgrading with the iso fixed the broken deps and also worked well with a vanilla lucid install. I have not looked at the installer script but I am willing to bet that it's removing stuff prior to package install.

---

### Post by arpanaut on 2011-10-20
Do you know that lightdm is replacing gdm in OO?

See: [https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes](https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes)
go down to Updated Applications

Could this be the root of your issues?

---

### Post by nanog on 2011-10-22
yes, i've been testing 11.10 since day 1. 

 i've been doing non-sequential upgrades since breezy. this is the first time i've had a major issue. i confirmed that the deps could be nuked via chroot, which is in essence what the installer is doing.

---

