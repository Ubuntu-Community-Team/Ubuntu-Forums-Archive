---
title: "Missing Root oassword request in LTS 8.04  install program"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by sin83scg on 2008-04-28
:(I downloaded and burnt ubuntu LTS 8.04 from a ubuntu mirror.  The CD was checked and certified error free during first steps of install process.

During install of th above Ubuntu OS, there was no request for an entry of the Root password!  I reinstalled the o/s twice with same result.  Now I cannot access any application or file requiring root privileges.  Can any one help me?
Thanks. 
sin83scg

---

### Post by Herman on 2008-04-28
Use the word 'sudo' placed before your command for root priveledges in Ubuntu.
For example,
```
sudo mkdir /media/mountpoint
```Ubuntu is similar to Debian, but with Debian and probably many other Linux distros you would have been asked for a root password, Ubuntu uses 'sudo' and you only need your administrator's password.

Regards, Herman :)

---

