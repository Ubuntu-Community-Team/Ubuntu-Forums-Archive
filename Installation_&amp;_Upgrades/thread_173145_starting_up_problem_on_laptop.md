---
title: "starting up problem on laptop"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by deesarge on 2006-05-09
i installed ubuntu on my hp,when it reboots ,it asks for my username and password. i give the nothing happens. the only thing that comes up is my username@computername:~$

---

### Post by aysiu on 2006-05-09
Maybe you accidentally did a server install?

Try typing ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by rdtran1 on 2006-05-10
I had that same problem where it only shows the black screen and you can type the user name but the password could not be entered.
I just reloaded it and it works fine, but I'm trying to install ubuntu onto my asus laptop and while loading it stops at "loading hotplug subsystems" I have no idea how to bypass this, any help would be appreciated.

Thanks.

---

