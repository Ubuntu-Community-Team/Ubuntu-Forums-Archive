---
title: "Installed 10.04 LTS on ACER Aspire One but no Gnome"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by JerryF on 2010-08-09
I installed Lucid Lynx on my new Acer Aspire One. In general everything seems to be working (except possibly sound but I have not checked that yet). My Windows manager appreas to be Metacity using the GDM display manager, but I would have expected the standard Gnome desktop. I do have the netbook-launcher running, but If I recall I installed the full 10.04 not the netbook remix. When I try to install gnome from Synaptic package Manager it complains either that it could not install 'epiphany-extensions' or 'swfdec-mozilla'. From the terminal using 'apt-get install gnome'
The following packages have unmet dependencies:
  gnome: Depends: swfdec-mozilla but it is not going to be installed
E: Broken packlages

If I install swfdec-mozilla, then I get the same message except with 'epiphany-extensions'.

---

### Post by mörgæs on 2010-08-10
If it is a new install, you could just reinstall to fix the problem. Remember to have wired internet access while dong so.

If you want to fix the broken packages, this might help:
[http://ubuntuforums.org/showthread.php?t=965882](http://ubuntuforums.org/showthread.php?t=965882)

---

