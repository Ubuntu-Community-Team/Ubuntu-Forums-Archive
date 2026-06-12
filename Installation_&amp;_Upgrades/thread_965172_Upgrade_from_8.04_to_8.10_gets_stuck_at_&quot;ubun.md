---
title: "Upgrade from 8.04 to 8.10 gets stuck at &quot;ubuntu upgrade configuring base-files&quot;"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by blwegrzyn on 2008-10-31
I started the upgrade and it got stuck at
"configuring base-files"
the intrepid process was stuck doing nothing,
I killed that process and now when I go to update manager I don't see the option to do the upgrade anymore,
how do I restart the upgrade so all packages are installed correctly? Currently when I go to upgrade manager I see attached screen. Would clicking the partial upgrade finish the upgrade correctly?
thx

---

### Post by blwegrzyn on 2008-10-31
i run below commands to complete the upgrade:
dpkg --configure -a
sudo apt-get dist-upgrade

---

