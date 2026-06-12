---
title: "Updating additional drivers."
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by Dr. div11 on 2011-05-07
hey .. any idea how to update addtional drivers using terminal......i want to update to NVIDIA accelerated graphics drivers.. using terminal... which command to use can u please tell me....

i am using ubuntu 10.10...!!!

---

### Post by Dr. div11 on 2011-05-07
hey .. any idea how to update addtional drivers using terminal......i  want to update to NVIDIA accelerated graphics drivers.. using  terminal... which command to use can u please tell me....

i am using ubuntu 10.10...!!!

---

### Post by dino99 on 2011-05-07
you mean there is no system menu to get that activation ? its on a server ?

---

### Post by Dr. div11 on 2011-05-07
> **dino99 said:**
> you mean there is no system menu to get that activation ? its on a server ?


no no... there is ...but i want to upgrade using the terminal

---

### Post by dino99 on 2011-05-07
try something like:

sudo jockey-gtk -e nvidia-current

note: dkms need to be installed for the new kernel

---

### Post by alphacrucis2 on 2011-05-07
> **Dr. div11 said:**
> hey .. any idea how to update addtional drivers using terminal......i want to update to NVIDIA accelerated graphics drivers.. using terminal... which command to use can u please tell me....

i am using ubuntu 10.10...!!!

[URL="https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"]https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia
[/URL]

---

### Post by howefield on 2011-05-07
Duplicate threads merged.

---

### Post by Dr. div11 on 2011-05-07
the problem is ..whenever i update nvidia using additional driver..and restart ...my ubuntu always restarts in 

tty1 mode...and after that i am not able to go back to ubuntu screen its like m stuck..
so i need a command line to update the driver using terminal..
please help..

---

### Post by jramshu on 2011-05-07
Looks like you need to restart in recovery mode. Then work from there in low res.

EDIT: Going to have to find out what model graphics card you have.

---

### Post by jramshu on 2011-05-07
Has anyone found a solution to this. I'm still waiting to find out what model and such the card is.

---

### Post by MAFoElffen on 2011-05-07
> **dino99 said:**
> try something like:

sudo jockey-gtk -e nvidia-current

note: dkms need to be installed for the new kernel
Then run:   
```

sudo nvidia-xonnfig

```@dino99:
Whatt's the difference in using jockey-gtk and:
```

sudo apt-get install nvidia-current

```Jokey-gtk is the GUI version of the driver manager right?  And if you didn't have a GUI running it would do what?

---

