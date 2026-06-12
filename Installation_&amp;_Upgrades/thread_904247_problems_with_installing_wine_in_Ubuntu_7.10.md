---
title: "problems with installing wine in Ubuntu 7.10"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by ajaxmehta on 2008-08-29
Here's what Synaptic Package Manager says when I try to install wine:-

wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed

Thanks for your help in advance. I am a complete newbie to Ubuntu, so please excuse if this is the wrong place to be posting this.

---

### Post by Cresho on 2008-08-29
you can install wine from add and remove.  do a search.  Also, before you go this route, you should change a few things.

piece of my notes.

fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.  add 3rd party stuff for source files.  refresh with button on top.  in add and remove programs, under show, select "all available applications"

after this, try in synaptic to install wine, if not, add and remove but remember that it is not the latest.

---

### Post by ajaxmehta on 2008-08-29
Thanks Cresho, but Add/Remove is not working either. Here's what it says:

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

---

### Post by Cresho on 2008-08-29
"sudo apt-get update" then "sudo apt-get upgrade"  list any problems if it encounters any.  THen try installing wine.  If it does not work, there is also a few more tricks available.  THis method ensures that your updated and of course upgraded.

---

### Post by ajaxmehta on 2008-08-30
Add/Remove programs says:


"Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

Synaptic is still not marking Wine for installation. Here's what it says:

Could not mark all programs for installation. 
The following packages have unresolvable dependencies.
Make sure that all required repositories are added and enabled in the preferences.
wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed

---

