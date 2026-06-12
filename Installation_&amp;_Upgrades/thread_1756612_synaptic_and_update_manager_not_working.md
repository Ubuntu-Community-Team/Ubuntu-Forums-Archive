---
title: "synaptic and update manager not working"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by poision_heart on 2011-05-12
hi

i have successfully install natty on my dell inspiron laptop.
when i tried to load synaptic or update manager or ubuntu software center i am getting following error and its not allowing me to open any of above application

error is:

[COLOR="Red"][B]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
[/B][/COLOR]

please help me to resolve this error.i need to install restricted drivers and compiz for best use.

---

### Post by matt_symes on 2011-05-12
Hi

Try this from the terminal.

```
sudo rm -f /var/lib/apt/lists/*
```

Enter your password. It will not be echoed to the screen. This is normal. Then type

```
sudo apt-get update
```

Kind regards

---

### Post by poision_heart on 2011-05-12
hi matt
thanks its working now

---

### Post by bailey07 on 2011-05-13
Thank you so much.  I too have a Dell Inspiron and was having the same problem.  Will I have to do this every time I want to update?

Thanks again!

---

### Post by matt_symes on 2011-05-13
Hi

> Will I have to do this every time I want to update?


I hope not. I should not think so. Was this a fresh install or upgrade ?

Kind regards

---

