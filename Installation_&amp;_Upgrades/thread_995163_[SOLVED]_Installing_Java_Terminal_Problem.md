---
title: "[SOLVED] Installing Java Terminal Problem"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by konlord on 2008-11-27
Can anyone help me with installing java through the terminal when the terminal wont let you type in the password after typing su for the self extracting file?

---

### Post by Pumalite on 2008-11-27
Why don't you install through Synaptic or:
sudo apt-get install ubuntu-restricted-extras
?

---

### Post by konlord on 2008-11-27
Well because Im pretty new & have no clue what any of that is lol If you want to link me to a guide or something that would be great

---

### Post by taurus on 2008-11-27
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by Pumalite on 2008-11-27
Go to:
Applications>Accessories>Terminal
And in the Terminal; type:
sudo apt-get install ubuntu-restricted-extras
(copy and paste to be sure)
Press 'Enter'
It will install Java and codecs  and all kind of goodies for you.

---

### Post by konlord on 2008-11-27
it still asks me for a password & wont let me type anything in for it

---

### Post by Pumalite on 2008-11-27
The password is invisible while you type it. Just type it and then press 'Enter'

---

