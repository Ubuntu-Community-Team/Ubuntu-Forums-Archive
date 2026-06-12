---
title: "Ubuntu 10.10 Nvidia Drive help!!!  o.O"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by Sobster on 2010-11-24
I just install Ubuntu 10.10 to a external hard drive on my laptop. 

It was a pain, but after messing with it all night i finally got it. We im having a problem updating my Nvidia drivers. Everytime i go to System > Administration > Additional Drivers, and try to active the one it says is recomended, it fails right at the end. But now all of a sudden, its activated.

So now i went to System > Administration > Nvidia X server settings, i get this error message saying, 

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."\

Dose anyone know how i may fix this problem. I am some what new to Linux and ubuntu, i wouldnt say i was a green, but i do have a basic understand of it, and i want to learn all i can. 

Windows is starting to make me angry >.< i might just go full Ubuntu ](*,)](*,)](*,)](*,)

---

### Post by skillet-thief on 2010-11-24
> "You do not appear to be using the NVIDIA X driver.  Please edit your X  configuration file (just run `nvidia-xconfig` as root), and restart the X  server."\

This means that you have to open up a terminal and type in the command, like this:

```
$ sudo nvidia-xconfig
```

"sudo" means that the command will be run as root.

---

### Post by Sobster on 2010-11-24
cool, worked. 

Thank you for the help and fast reply:KS

I guess i need to read up on my terminal skills

---

### Post by skillet-thief on 2010-11-24
You will learn to love the terminal.

---

### Post by Sobster on 2010-11-24
Lol indeed. Have any good fourm post or guides on Terminal 101 :D

---

