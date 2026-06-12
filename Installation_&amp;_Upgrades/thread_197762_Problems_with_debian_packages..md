---
title: "Problems with debian packages."
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by Lcrusher on 2006-06-16
Hi, I'm new to Ububtu and linux in general. I find this a great OS. I have encountered some problems during my driver and software installation, I managed to solve them using search.:D  But there is one problem that I still can't solve - I can't create debian packages using "make".  When I enter "make" it gives out

```
gcc  -O2 -g capt.c -o capt
make: gcc: Command not found
make: *** [capt] Error 127
```

I found some similar posts in this forum, I have tried out the sollutions given in them, but if didn't help.
Can someone tell we what do I need to create debian packages.

Thanks. :)

---

### Post by loell on 2006-06-16
do this..

sudo apt-get install build-essential

for compiling stuff, i would remind you though that

"make" command is for compiling and "make install" is for installing the compiled stuff.. this does not create a deb package..

---

### Post by Lcrusher on 2006-06-16
```
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


It was already installed...:(

---

### Post by Lcrusher on 2006-06-16
Is there a solution to my problem? Without "make" I can't install the my printer drivers. :(

---

### Post by Lcrusher on 2006-06-16
I solved the problem by uninstalling and installing the gcc and build-essential (the simple reinstallation didn't work).

I couldn't make the printer work though.

---

### Post by loell on 2006-06-16
what's your printer brand and model?

---

