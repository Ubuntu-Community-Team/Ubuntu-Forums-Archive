---
title: "unity crashed after installing cinnamon 2.0.2 on ubuntu 13.04 64bit"
date: 2013-10-12
forum: Installation &amp; Upgrades
---

### Post by anoopp on 2013-10-12
Hello All,

Today i installed Cinnamon 2.0.2 on my ubuntu 13.04 by using below commands

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
```

But after installing Cinnamon i am not able to login to system with Unity as it blanks after the login. In cinnamon as well i am getting Cinnamon is crashed error message while login.

Can anyone help me to resolve this. Let me know if you need any other details.

Thanks in advance.

---

### Post by dvergu|2 on 2013-10-21
I had the same Problem, I installed Ubuntu 13.10 64bit and Cinnamon 2.0.3 to night and kept getting "Cinnamon is crash error message"
At last I found this, and it fixed my Cinnamon issue.
All I did was to run apt-get update and dist-upgrade, even though I have the newest distro.

Hope this can be some help to you.

---

### Post by fantab on 2013-10-22
Don't use the ppa to install Cinnamon. Cinnamon is in the official repositories so:

```
sudo apt-get install cinnamon
```

should suffice, I think.

Uninstall Cinnamon, disable the ppa then run:

```
sudo apt-get autoremove
``` This should remove if there are any leftovers from the ppa.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

then try installing cinnamon.

---

### Post by thepisu on 2013-10-30
Another way to get back to Cinnamon 1.7 from official repository, should be using:
```
ppa-purge ppa:gwendal-lebihan-dev/cinnamon-stable
```

---

