---
title: "Install Gnome desktop into KUbuntu from CD"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by xlinuks on 2007-04-21
Hi all,
I have both CDs (Ubuntu & KUbuntu 7.04) downloaded and installed KUbuntu, but I also wanna have the Gnome desktop (to have installed all default Gnome apps and libraries fast and easy). Is there a command/option in KUbuntu to install the Gnome desktop not from the internet but from the CD? Please help!

---

### Post by chinocracy on 2007-04-21
I asked the same question for putting Kubuntu Dapper into Ubuntu Dapper. Aysiu said I should use the alternate CD, not the live CD. Hope that helps.

---

### Post by chinocracy on 2007-04-21
Follow up. I think I got the same problem as I had with Baelfael in the other thread.  Installed KDE-Core, then I installed kdm and kde-theme for good measure. What I get is at startup is Kubuntu and its colors when loading modules, but when I login, the same old Gnome interface pops in. No selection of KDM or GDM (Wait, while I installed gdm, it made me select a default DE, and I chose GDM). I wonder how to bring up the menu selection for the DEs?  Perhaps my loading of extra packages did something to such effect. Thanks.

Edit: I tried ```
cd usr/share/xsessions
```, and what I get is 'No such file or directory.'

---

### Post by chinocracy on 2007-04-21
Hold on, the session picker is at the lower left after all, disregard my post above about it. I got KDE to work! Beautiful! All I need to do is fix the resolution now. I couldn't run above 800x600 since my monitor gets triple images at high res. Thanks!  :KS

---

### Post by xlinuks on 2007-04-21
Ok, thank you, I will download and try the alternate CD!

---

