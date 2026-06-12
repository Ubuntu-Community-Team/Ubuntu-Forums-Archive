---
title: "NVIDIA driver instalation problems"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by warlorddagaz on 2006-10-23
After searching the forums, I found a way to stop the x-server to allow the install of the NVIDIA driver for my geforcegraphics card. However, after finally getting past the first problem, I get errors saying about kernel problems, it then asks if I want to try and download new ones, which didn't work, so it said it would compile it. However, it then said that gcc or cc wasn't in the path variable - I imagine these are c compilers, but I have nop ideas how to install them/add them to the path variable.

It would also be good (as is is presumably the same idea) to know how to add javac to the path variable

Thank you in advance - sorry for my lack of technical info.

---

### Post by at0mic on 2006-10-23
hi.

i went through this entire mess too. see below. the script envy mentioned in the below thread might fix ur prob right off the bat. very simple to use and very awesome 


[http://www.ubuntuforums.org/showthread.php?t=281358](http://www.ubuntuforums.org/showthread.php?t=281358)

ops might wanna sticky one of these

---

### Post by warlorddagaz on 2006-10-23
Looks useful - thank you!

---

### Post by at0mic on 2006-10-23
Ok, let us know how your experience goes.

---

### Post by warlorddagaz on 2006-10-23
It went very well - ot took about 5 or 10 minutes to install, and now google earth works (hooray), along with (I presume) many other apliations that will now be able to get that added graphics boost (or whatever you can get from a 64mb geforce 2 graphics card!!!

Just out of interest, does anyone know why it is so much harder to install the driver on Ubuntu than Windows - I have only been liberated in the lat month or so, and so far have really like Ubuntu, along with many of it's features, but at times, it does seem harder to do some tasks that Windows does relatively easily.

---

### Post by bulldog on 2006-10-23
You can install the driver with synaptic although it's not the latest.
```
sudo aptitude install nvidia-glx
```

Easyer as in windows I suppose :D

---

### Post by at0mic on 2006-10-23
the problem is mostly with x64 kernels. its a custom kernel and therefore needs custom compilation. if you had the i386 version it wouldnt be so troublesome. im going to install the i386 tonight. far less problems with compatability and im too noob to handle most of them without some serious help from the great ppls here. do you have the x64 version warlorddagaz?

---

### Post by bulldog on 2006-10-23
> **at0mic said:**
> the problem is mostly with x64 kernels. its a custom kernel and therefore needs custom compilation. if you had the i386 version it wouldnt be so troublesome. im going to install the i386 tonight. far less problems with compatability and im too noob to handle most of them without some serious help from the great ppls here.

Wise decision :D 

Had the 64 first time around and had only trouble,after 14 days I setup i386 and it's running ever sins.

---

### Post by warlorddagaz on 2006-10-23
[LEFT]It was x86 (I think)
[/LEFT]

---

### Post by at0mic on 2006-10-23
maybe the recompliation of the nvidia drivers is required for all ubuntu versions then. im not sure. only 2nd day of ubuntu ! :)

---

### Post by warlorddagaz on 2006-10-23
I'm coming up to a month tommorow - maybe I should have a party.

---

