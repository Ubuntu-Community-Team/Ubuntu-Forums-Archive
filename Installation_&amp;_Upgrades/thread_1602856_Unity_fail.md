---
title: "Unity fail?"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by Infinis on 2010-10-22
Followed the following guide to install a 64 bit version of Netbook Remix 10.10 on my amd64 nettop (MSI U210) (AMD Athlon Neo 64)(MV-40).

[https://help.ubuntu.com/community/UbuntuNetbookEdition/amd64](https://help.ubuntu.com/community/UbuntuNetbookEdition/amd64)

Followed all those steps and verified it twice. Logged out and loged into the netbook remix. When I logged in there are no menu visible.. I can see a plain black bar on the top and a plain purple (same color as the wallpaper) on the left side. When i hover with my mouse the left bar, a plain black box appears over. Both bars are clickable, I can guess where which buttons are. 

If I login back into the desktop edition - everything is fine.

Somebody encountred something familiar?

---

### Post by kerry_s on 2010-10-22
you need to have 3d vid drivers working before you log into to netbook. the new netbook is 3d.

that guide is long winded, if you install regular ubuntu 64, you only need to install "ubuntu-netbook", it will install everything you need.

---

### Post by kWahab on 2010-10-29
Facing the same problem. 
Installed ubuntu-netbook from apt-get. I just "see" (more like feel) transparent left and top bars when I choose the Netbook session at login. The links are there . I can click and launch firefox, rythmbox etc. Can't see anything though. No icons, no tooltip text etc. 

If I click the top left corner I see the second screenshot.

Configuration:
Dell Inspiron 6400/e1505, with ATI X1400 256MB. 
Ubuntu 10.10 desktop 64. all updates as of Oct 28. Default ati/radeon open-source drivers.

---

### Post by kWahab on 2010-10-29
Just booted from a Netbook Live CD. Same issues here. 
I guess it's an issue with Mutter and the ati/radeon driver. Will have to do more research.

---

