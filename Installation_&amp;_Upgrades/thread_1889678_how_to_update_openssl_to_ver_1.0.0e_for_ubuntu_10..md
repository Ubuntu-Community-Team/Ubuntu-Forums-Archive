---
title: "how to update openssl to ver 1.0.0e for ubuntu 10.04"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by creatxr on 2011-12-01
how to update openssl to ver 1.0.0e for ubuntu 10.04  i downloaded source from openssl.org  compiled and "sudo make install"  but it still shows "0.9.8k" version.  thanks.

---

### Post by vangop on 2011-12-02
Did you remove the old version prior to doing that? If you had the old one installed via the package manager, you should have removed it first.

---

### Post by creatxr on 2011-12-03
it seems it's hard to update by self.
it has many packages depend on openssl, i cannot only remove openssl and install new one from source.

---

### Post by raja.genupula on 2011-12-04
sudo apt-get install --reinstall <app_name>

this will do as updating only specific application .

---

