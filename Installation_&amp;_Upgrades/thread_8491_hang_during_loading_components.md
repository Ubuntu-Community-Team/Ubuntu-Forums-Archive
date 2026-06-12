---
title: "hang during loading components"
date: 2004-12-17
forum: Installation &amp; Upgrades
---

### Post by Moooink on 2004-12-17
the install is hanging at loading components 34% 
"retrieving nic-extra-modules-2.6.8.1-386-dI"

any ideas? I've tried two different cds so it is unlikely that it is the cd that is bad.

Nic

---

### Post by jdong on 2004-12-17
How 'hung' is it?

Can you move around the consoles with ALT+Fn?

---

### Post by ilex on 2005-03-29
[QUOTE=jdong]How 'hung' is it?

Can you move around the consoles with ALT+Fn?[/QUOTE]
 I have the same problem.
installer chooses "low memory mode"
after some questions we get to "loading additional components"
retrieving and unpacking nic-extra-modules-2.6.8.1-386-dI starts about ten times and then it gets quiet. 
Ctrl-F2 gives shell 
Ctrl-F3 last entry: insmod /lib/modules/3.6.10-4-386/kernel/isofs/isofs.ko
Ctrl-F4 ongoing debug output, the same over and over again:
 main menu [17503}: DEBUG: resolver xxx mark
xxx= lilo installer, cdebconf-prio, cdrom-checker,  menu item loadcdrom selected, config loadcdrom status 2, and many more

system is HP omnibook 2100 laptop mem= 31MB hdisk=  4,1GB
On other system it installs perfectly.

Ilex

---

### Post by ilex on 2005-04-04
I've just tried the latest installer:
 hoary-rc-install-i386.iso            30-Mar-2005 02:59  597M  Install CD for Intel x86 computers (standard download)
no luck.

Ilex

---

### Post by ilex on 2005-04-04
Same type problems with debian sarge netinstall after loading cdrom drivers. A mini-ISO with debian woody > OK.
Lets try warty...

Ilex

---

