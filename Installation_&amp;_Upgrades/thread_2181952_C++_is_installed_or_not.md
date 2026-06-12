---
title: "C++ is installed or not?"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by Muhammad_Mudassir on 2013-10-19
i have installed c++ by these commands.
[h=5]sudo apt-get update
 sudo apt-get upgrade
 sudo apt-get install build-essential
 gcc -v
 make -v[/h]now i want to chesk whether c++ is installed or not? how will i check?

---

### Post by steeldriver on 2013-10-19
You can check whether the GNU C++ *compiler *is installed with

```
g++ --version
```

---

### Post by Muhammad_Mudassir on 2013-10-19
i entered command in terminal the following comes.
The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected packages>

---

### Post by steeldriver on 2013-10-19
So try

```
sudo apt-get install g++
```

---

### Post by Muhammad_Mudassir on 2013-10-19
it comes.
Unable to correct problems, you have held broken packages

---

### Post by mörgæs on 2013-10-21
Please run again

```
sudo apt-get update
sudo apt-get upgrade

```
and post the complete output in CODE tags.

---

