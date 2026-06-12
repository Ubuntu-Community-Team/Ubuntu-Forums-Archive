---
title: "problem on installing"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by nayere on 2011-08-03
Hello;
I have a problem when installing this package through synaptic package manager.
this is : 
libpng12-dev
the error is:
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.42-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.42-1ubuntu2.1_i386.deb)
  404  Not Found [IP: 91.189.92.167 80]

my distribution is ubuntu 10.4.

---

### Post by Beacon11 on 2011-08-03
What happens when you run the following?```
sudo apt-get update
```

You may need to change which mirror you use. To change that, open up Synaptic Package Manager, hit Settings > Repositories. In the Ubuntu Software tab, change the Download From drop-down to Other, which will cause another window to pop up. In the new window, hit Select Best Server. This will select the one to which you have the fastest connection.

---

