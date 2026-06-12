---
title: "Installing Oneiric via Netboot GTK"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by dmouck on 2012-02-10
Hi everyone,

I have configured a PXE boot environment on our network so that people can install Ubuntu over PXE boot. I have configured the text-based install and it works without any problems. I thought that I would setup the graphical gtk-based install as newcomers to Ubuntu might be a bit more at ease using the graphical interface to install. I configured the server to use the appropriate files in the gtk subfolder of the netboot subfolder. However, when first graphical screen comes up, all the text is squares! It looks like there are fonts missing from the install. 

I also noticed that one of the menu files (menu.cfg) calls for some files that are non-existent: gtk.cfg and adgtk.cfg .

Does anyone have any suggestions? Has anyone successfully used the gtk netboot?

Thanks in advance!

---

