---
title: "someone please help me out"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by sidheart on 2008-06-26
I by mistake updated my 8.04 with some feisty mediubuntu repos

Now when I go to synaptics package manager i get the following error

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

please someone help me out

---

### Post by tamoneya on 2008-06-26
lets just take a look at the file and edit manually.  Run all the following commands in terminal.

1. Backup the file in case we really screw up:```
sudp cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bak
```

2. Post the contents of the file to the forum:```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```Then copy out of gedit and into the terminal so we can help you find the errors.

Also a title of "someone please help me out" is very useless.  Next time make it something more like: "E: Type '<!DOCTYPE' is not known"

---

### Post by wolfen69 on 2008-06-26
do this:
```
gksudo gedit /etc/apt/sources.list
```then just remove every line that has medibuntu in it. save file and ```
sudo apt-get update
```

---

### Post by sidheart on 2008-06-26
I went and manually removed the medibuntu lists using the terminal.It worked.
anyways thanks
and yes will be careful

---

### Post by sidheart on 2008-06-26
I went and manually removed the medibuntu lists using the terminal.It worked.
anyways thanks
and yes will be careful about the title in the future

---

