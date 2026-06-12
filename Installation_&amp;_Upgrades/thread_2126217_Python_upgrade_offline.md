---
title: "Python upgrade offline"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by Dracco on 2013-03-16
Hello. I have desktop pc running Ubuntu 10.04, without internet connection and want to upgrade python on it. I downloaded sources on another pc, configured, installed, it shows me python 2.7 binaries, upgraded 2.6 as well from 2.6.5 to 2.6.8, but when i try installing wicd-gtk it says that my python version is 2.6.5. Any idea how to make it see changes?

Thanks in advice,
Dracco

---

### Post by dino99 on 2013-03-16
well, thats exactly whats devs are doing when they fix dependencies and/or API/ABI
so if you are a coder, then you can dive into the package sources to update the required version; but also resolve the headhaches due to difference introduced by the new python version.

or download the good deb package into an empty folder, then apply from there :  ```
sudo dpkg -i *
```
[http://launchpad.net/ubuntu/+source/wicd](http://launchpad.net/ubuntu/+source/wicd)

---

