---
title: "'Linux headers no longer required' when installing Skype"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by MrsUser on 2012-10-03
When I want to install Skype via terminal on a fresh Ubuntu 12.04.1 64-bit install, then, before a long list of what will be installed, I get this message:

```
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic
```This sounds suspicious to me, as if it will break something. After all, it's a fresh install of Ubuntu. So why does it want to remove stuff?

Do I have to worry?

---

### Post by ajgreeny on 2012-10-03
This is probably because you are now using the 3.2.0-31 kernel and headers which appeared in updates recently, but still have the 3.2.0.29 kernel and its headers installed.

If that is so, and you can check which kernel you are using with ```
uname -a
```in terminal, you can remove those -29 headers, but they take up little disk space, so it is not too important.

---

### Post by Bucky Ball on 2012-10-03
To deal with this, run:

```
sudo apt-get autoremove
```

Then try again. Nothing suspicious here ... ;)

---

### Post by MrsUser on 2012-10-03
Thanks. I'm not worried anymore :p

Edit:
Yes, it's the 3.2.0-31 kernel. So it's because of the update I ran directly after install, I suppose.

---

