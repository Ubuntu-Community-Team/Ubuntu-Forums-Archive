---
title: "Upgrade problem 14.04"
date: 2014-09-07
forum: Installation &amp; Upgrades
---

### Post by tjjioc on 2014-09-07
I use 14.04 did the latest updates and it now boots into grub. Whichever option I click it still won't boot correctly

---

### Post by satnelav on 2014-09-07
Ubuntu Boot Repair has once helped me tremendously. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ibjsb4 on 2014-09-07
The next screen after boot is the login window.  Your not getting to the login window?

---

### Post by tjjioc on 2014-09-09
It boots into grub. No log in screen.
If I do ctrl, alt, f1. I get the log in screen but it doesn't stay long enough for me to log in

---

### Post by kansasnoob on 2014-09-09
Can you try booting an older kernel from the grub menu?

Do you happen to know what graphics chip(s) you have? I read that Optimus is broken:

[http://www.webupd8.org/2014/09/recent-update-broke-ubuntu-desktop-on.html](http://www.webupd8.org/2014/09/recent-update-broke-ubuntu-desktop-on.html)

---

### Post by tjjioc on 2014-09-09
I have tried an older kernel but it doesn't work.
No idea what my graphics chip is.

I can now boot if I click on advanced options for Ubuntu then click on first generic option. While the screen is waiting to load I type
Sudo apt-get update
sudo apt-get upgrade
It then boots up as normal. But it is a bit of a pain

---

### Post by kansasnoob on 2014-09-09
> **tjjioc said:**
> I have tried an older kernel but it doesn't work.
No idea what my graphics chip is.

I can now boot if I click on advanced options for Ubuntu then click on first generic option. While the screen is waiting to load I type
Sudo apt-get update
sudo apt-get upgrade
It then boots up as normal. But it is a bit of a pain

Once booted open the terminal and try:

```
sudo update-grub
```

```
sudo apt-get -f install
```

The latter may inform you of other needed actions or warn of broken packages, etc. If the latter seems to just ***go_to_work*** on completing part of the upgrade I'd run "update-grub" one more time when it's done.

---

