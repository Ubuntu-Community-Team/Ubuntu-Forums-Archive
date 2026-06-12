---
title: "update manager wont  work"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-04-12
i tried to use the following command to fix

 sudo dpkg --configure -a

didnt work i still get the error

Archive directory /var/cache/apt/archives/partial is missing.


any idea how to fix

---

### Post by drs305 on 2009-04-12
Try creating the partial folder, since it is reported missing. If there is something specific dpkg is looking for in the folder then it will probably issue another error message but may give you an idea of what app is not properly installed:
```
sudo mkdir /var/cache/apt/archives/partial
sudo dpkg --configure -a

```

---

### Post by rburkartjo on 2009-04-12
when tried that got the following error

ray@ray-desktop:~$ sudo mkdir /var/cache/apt/archives/partial
mkdir: cannot create directory `/var/cache/apt/archives/partial': No such file or directory
ray@ray-desktop:~$

---

### Post by nandemonai on 2009-04-12
> **rburkartjo said:**
> when tried that got the following error

ray@ray-desktop:~$ sudo mkdir /var/cache/apt/archives/partial
mkdir: cannot create directory `/var/cache/apt/archives/partial': No such file or directory
ray@ray-desktop:~$
```

sudo mkdir /var/cache/apt/archives
sudo mkdir /var/cache/apt/archives/partial
```

---

### Post by bumanie on 2009-04-12
Try > sudo mkdir /var/cache/apt/archives/partial
> sudo apt-get update> sudo apt-get install ipcalc

---

### Post by rburkartjo on 2009-04-12
nan tks for the help in remaking the directories but now i get the error

E: /var/cache/apt/archives/acroread_9.1.0-7jaunty1_i386.deb: trying to overwrite `/usr/share/man/man1/acroread.1.gz', which is also in package acroread-debian-files

---

### Post by drs305 on 2009-04-12
> **rburkartjo said:**
> when tried that got the following error

ray@ray-desktop:~$ sudo mkdir /var/cache/apt/archives/partial
mkdir: cannot create directory `/var/cache/apt/archives/partial': No such file or directory
ray@ray-desktop:~$

Barring a typo, the only way that error message should appear is if the path is not correct. Do you have a /var/cache/apt/archives folder?

---

### Post by rburkartjo on 2009-04-12
drs yes i do this again could be bug in 9.04 beta

---

### Post by rburkartjo on 2009-04-12
who ever moved this thread tks i was not sure if it was just an update manager problem or a 9.04 beta problem thats why i posted on beg board first. but since the update manager seems to be working must be a bug

---

