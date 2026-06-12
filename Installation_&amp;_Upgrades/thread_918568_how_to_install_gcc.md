---
title: "how to install gcc"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by parvathy on 2008-09-13
hi,

i have ubuntu installed on my laptop. i want gcc to be installed. i downloaded gcc.4.3.2 from ftp.gnu.org/gnu/gcc.

can anybody help me and say what to do next?

---

### Post by iaculallad on 2008-09-13
You'll only be needing one file w/c is currently in the repository:

```
sudo apt-get install build-essential
```

This includes GCC version >= 4:4.1.1.

---

### Post by Shippou on 2008-09-13
Don't forget to first run an update before running the command above. 

```

sudo apt-get update

```

Also, do not forget to run the code everyday. I think software updates are released everyday, as there hardly comes a day when I don't update my computer.

Also, patch up your DNS. (techie stuff.. Not so important anyway)

Does the ISP of ubuntuforums patched up their DNS already?

---

### Post by iaculallad on 2008-09-13
> **Shippou said:**
> 
```

sudo apt-get update

```

Also, do not forget to run the code everyday. I think software updates are released everyday, as there hardly comes a day when I don't update my computer.


Actually, you don't have to manually run the code (sudo apt-get update) everyday. The Update Manager does that task automatically for you.

---

### Post by parvathy on 2008-09-13
i can't do that since i don't have a driver for my modem. to install the modem i have to have gcc compiler

---

### Post by iaculallad on 2008-09-13
> **parvathy said:**
> i can't do that since i don't have a driver for my modem. to install the modem i have to have gcc compiler

Make sure you have your Ubuntu CD at hand, place it on your CD/DVDROM drive and issue the commands below on your terminal:

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
gcc -v

```

That's one command at a time.

---

