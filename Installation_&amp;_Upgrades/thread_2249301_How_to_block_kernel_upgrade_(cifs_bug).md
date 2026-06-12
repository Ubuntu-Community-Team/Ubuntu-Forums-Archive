---
title: "How to block kernel upgrade (cifs bug) ?"
date: 2014-10-21
forum: Installation &amp; Upgrades
---

### Post by fdelente on 2014-10-21
Hello,

I have xubuntu 14.04 installed with the 3.13.0-32 kernel, and CIFS works correctly; if I upgrade, I get kernel 3.13.0-37 in which CIFS is broken and can't mount my network drives. How can I stop 3.13.0-37 to install, I want to keep 3.13.0-32 as my kernel.

Thanks.

---

### Post by ibjsb4 on 2014-10-21
If you manually upgrade in terminal, the kernel will remain the same.
```
sudo apt-get upgrade
```
Update manager uses dist-upgrade which also updates the kernel.
```
sudo apt-get dist-upgrade
```
If you use synaptic to update/upgrade it can also be set to standard upgrade and will not update kernel.

---

