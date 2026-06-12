---
title: "ATI 9550 Radeon"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by psp219 on 2008-03-07
When i try to enable the drivers for my ATI card in restricted drivers manager, it says please fix broken packages first, i have all the updates for ubuntu i dont know wut to do

---

### Post by empthollow on 2008-03-07
there are a couple of ways to do this.  you can goto the 'fix broken packages link in synaptic, or you can type the following in a terminal:
```
sudo apt-get -f install
```

---

### Post by psp219 on 2008-03-07
> **empthollow said:**
> there are a couple of ways to do this.  you can goto the 'fix broken packages link in synaptic, or you can type the following in a terminal:
```
sudo apt-get -f install
```
I did all that and it still wont work wut to do now?

---

### Post by psp219 on 2008-03-07
still same error message

---

### Post by empthollow on 2008-03-07
please run the command in the terminal and post the output.  alot of times you have to manually remove a particular package in order to get rid of this error.  the trick is figuring out which package.

---

### Post by psp219 on 2008-03-07
kevin@kevin-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kevin@kevin-desktop:~$

---

### Post by psp219 on 2008-03-07
i also did the synaptic package manager thing you told me to do

---

### Post by empthollow on 2008-03-07
interesting.  apt-get is not returning any errors.  I'm not sure why it would be telling you to fix broken packages when there are none.  I can however provide a workaroud.  all the restricted driver manager does is install the package xorg-driver-fglrx, so if you type the following it will yeild the same result as using the restricted drivers manager.
```
sudo apt-get install xorg-driver-fglrx
```
If you get any errors on that command, post them here.

---

