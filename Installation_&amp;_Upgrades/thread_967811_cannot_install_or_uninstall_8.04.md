---
title: "cannot install or uninstall 8.04"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by aboutTOpullmyhairout on 2008-11-02
when i run apt it tells me to run the  "apt-get -f install" command and when i do i get another terminal message saying 

root@phawker:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies...Segmentation fault

does anyone have any ideas what i should try to fix this ?
i have tried that command, purging all with unmet dependencys.

---

### Post by XDevHald on 2008-11-02
Should be "if you're set a root in terminal" **apt-get -f install package_name**

---

