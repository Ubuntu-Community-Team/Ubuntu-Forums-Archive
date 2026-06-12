---
title: "unable to add repository using synaptic - Ubuntu 24.04.1"
date: 2024-09-21
forum: Installation &amp; Upgrades
---

### Post by lee48 on 2024-09-21
I'm unable to add a repository using the Synaptic->Settings->Repositories->Other Software->Add. I enter the following in the box but the "Add Source" remains greyed out. I followed the instructions at [https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html.en](https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html.en). I use to just manually add this to /etc/apt/sources.list but it appears things have changed in Ubuntu 24.04.1

deb [arch=amd64 signed-by=/usr/share/keyrings/oracle-virtualbox-2016.gpg] [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) noble contrib

---

### Post by 1fallen on 2024-09-21
They Love keeping us on our toes don't they....LOL
```

wget -q -O - http://download.virtualbox.org/virtualbox/debian/oracle_vbox_2016.asc | sudo apt-key add -
```
Will add the Key, next add the PPA
```

sudo sh -c 'echo "deb http://download.virtualbox.org/virtualbox/debian noble non-free contrib" >> /etc/apt/sources.list.d/virtualbox.org.list' 
```

---

