---
title: "error when running sudo"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-10-07
just noticed this error

ray@ray-desktop:~$ sudo apt-get update && sudo apt-get dist-upgrade
sudo: /etc/sudoers is mode 0777, should be 0440
Segmentation fault

what is the easiest way to fix and how. tks

---

### Post by MacUntu on 2009-10-07
Guess I'd try to boot in recovery mode, drop to a root shell and type:
```
chmod 440 /etc/sudoers
```

---

### Post by taavikko on 2009-10-07
> **rburkartjo said:**
> just noticed this error

ray@ray-desktop:~$ sudo apt-get update && sudo apt-get dist-upgrade
sudo: /etc/sudoers is mode 0777, should be 0440
Segmentation fault

what is the easiest way to fix and how. tks

Did you try to edit sudoers file in some unorthodox way?
As this would suggest it: [http://ubuntuforums.org/showthread.php?t=1285061](http://ubuntuforums.org/showthread.php?t=1285061)

---

### Post by rburkartjo on 2009-10-07
mac tks worked like a charm

---

### Post by rburkartjo on 2009-10-07
taa yes

---

### Post by taavikko on 2009-10-07
> **rburkartjo said:**
> taa yes

ok, always edit that file with "sudo visudo"
To not make it go haywire.

---

### Post by rburkartjo on 2009-10-07
taa wont forget tks again

---

