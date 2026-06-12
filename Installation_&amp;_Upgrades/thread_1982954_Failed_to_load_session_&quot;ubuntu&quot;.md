---
title: "Failed to load session &quot;ubuntu&quot;"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by Nick_C on 2012-05-19
Hi,

Just done a basic install of Ubuntu Server 12.04 without desktop.  Only Package selected was samba file server.
Then tried to add a minimal desktop and a few utilities:

aptitude install
[INDENT]xorg
gnome-core
gnome-system-tools
gnome-app-install
gnome-nettool
chromium-browser
gdebi
gcc[/INDENT]

Problem is when I try to logon I get:
> Failed to load session "ubuntu"

---

### Post by Nick_C on 2012-05-20
Just done a completely fresh install and followed instructions here:
[http://linuxblog.avserver.info/minimal-lightweight-gnome-desktop-for-servers-revisted/3/](http://linuxblog.avserver.info/minimal-lightweight-gnome-desktop-for-servers-revisted/3/)

Unfortunately same problem:
Failed to load session "ubuntu"

What am I doing wrong?

---

### Post by raja.genupula on 2012-05-20
at login screen press CTRL+ALT+F1 and then login from there
type as

```
sudo start lightdm
```
and let us know . 

:)

---

### Post by biocyberman on 2012-08-20
I faced the same problem: trying to switch from server install to desktop environment and got "failed to load ubuntu session". This is after I installed only "gnome-desktop-environment" package as the same practice I did on Lucid. But I failed, so after reading around, I installed lightdm and chose it as default display manager. 
I also then installed "ubuntu-desktop" virtual package which installed 266 additional packages. 
Problem solved !!!! :lolflag:

---

