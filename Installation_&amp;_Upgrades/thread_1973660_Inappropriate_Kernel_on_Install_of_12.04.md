---
title: "Inappropriate Kernel on Install of 12.04"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by Lenny212 on 2012-05-05
Hi, Attempting to install 12.04 on Lenovo T41.
On boot up - I get the error message "This kernel requires the following features not present on the CPU: pae; Unable to boot - please use a kernel appropriate for your CPU."
How do I use a different kernel? Please keep answer simple, I am not very technical. Thanks

---

### Post by prshah on 2012-05-05
The SIMPLEST solution;

a) Install Lubuntu 12.04, it includes a non-pae kernel
b) If you are not comfortable with LXDE environment in Lubuntu, you can then install the Ubuntu environment```
sudo apt-get install ubuntu-desktop
```

This is a suggestion only, I have not tried this.

---

### Post by dino99 on 2012-05-05
[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more)

---

### Post by Lenny212 on 2012-05-06
Thanks prshah and dino99 for your clear replies, tried prshah's option and it worked.

---

