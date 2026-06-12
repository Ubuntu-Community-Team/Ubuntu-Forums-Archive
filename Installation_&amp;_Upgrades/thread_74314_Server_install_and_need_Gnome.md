---
title: "Server install and need Gnome"
date: 2005-10-11
forum: Installation &amp; Upgrades
---

### Post by Louisvdw on 2005-10-11
Hi 

I installed with the server option and wanted Xwindows/gnome as well.
After some long struggles I manage to get Gnome to boot up by installing with apt-get the xserver, Xorg, xterm, gnome and GDM packages. 

Now I boot up to the gdm logon screen and can logon, but if I want to run Synaptic, it first does not run and if I double click again, then I get error. 
"Failed to run /usr/sbin/synaptic: Child terminated with 1 status"

1. What is all the packages I need to install to get gnome running nicely and
2. Is there a way to see a list of packages available in apt-get?

PS. synaptic is installed (Apt-get tells me there are no newer version available)

---

### Post by mlomker on 2005-10-11
> 2. Is there a way to see a list of packages available in apt-get?


```

apt-cache search *packagename*

```

I'm not sure what might be going on for you.  You could always install **ubuntu-desktop** but it'll grab more packages than you might want.

---

### Post by Louisvdw on 2005-10-11
apt-cache search -> ah great! 

The size does not matter now. I'll check that when I know more. Just need to get it running first. 

I'll try it.
Thanks

---

