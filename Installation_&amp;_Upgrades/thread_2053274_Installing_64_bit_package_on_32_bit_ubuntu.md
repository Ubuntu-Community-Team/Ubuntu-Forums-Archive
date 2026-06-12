---
title: "Installing 64 bit package on 32 bit ubuntu"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by rollyah on 2012-09-05
i have 32 bit ubuntu running.
i need to install mysql-server-5.1 amd64 on it.

This system is already running linux-image-2.6.26 amd64

i can't seem to find that package in any current repo so i'm thinking of force installing it using dpkg but i don't know how to solve dependencies (especially libraries)

Any advice?

---

### Post by lincoln32 on 2012-09-05
normally you cannot install a 64 bit program on a 32 bit operating system
but your linux Kernal is 64 bit so you would be fine if you really have a 64 bit system. If that is a typo and you really have a 32 bit system just install the 32bit mysql-server

---

### Post by rollyah on 2012-09-05
thanks for the quick reply.

well ubuntu is 32 bit but i've installed linux-image 64 bit
and i have the same exact setup working on another system (ubuntu 32 bit, kernel 64 bit, mysql 64 bit) but there's no documentation on how it's setup.


> **lincoln32 said:**
> normally you cannot install a 64 bit program on a 32 bit operating system
but your linux Kernal is 64 bit so you would be fine if you really have a 64 bit system. If that is a typo and you really have a 32 bit system just install the 32bit mysql-server

---

### Post by lincoln32 on 2012-09-05
Ubuntu is availible in 32 and 64 bit you have a 64 bit system based on the Kernal image and not 32. Also 64 will not install on a 32 bit hardware system. I suspect you installed the 64 bit version originally.
general guideline is if you have less than 4 gb of ram to use a 32 bit operating system on 64 bit hardware and if you have more than 4 gb of ram then use the 64bit operating system on a 64 bit hardware. I do run several servers on 32 bit operating systems on 64bit hardware
with more ram due to other issues but I am starting to use more 64 bit operating systems since 64 bit servers are getting very stable the last few years

---

### Post by rollyah on 2012-09-05
Thanks again for taking interest in helping out with this.

I seem to have trouble explaining myself.

i have the follwing :
HArdware supports both 32 and 64
Ubuntu **32 bit installed** 
i have installed using apt-get   linux-image **64 bit**
System now boots to 64 bit image even though it's 32 bit
i need to install mysql server 64 bi on a 32 bit ubuntu.

This entire setup is done on 4 separate and distinct servers which are currently running.

I need help to setup the 5th to be identical as the first 4.




> **lincoln32 said:**
> Ubuntu is availible in 32 and 64 bit you have a 64 bit system based on the Kernal image and not 32. Also 64 will not install on a 32 bit hardware system. I suspect you installed the 64 bit version originally.
general guideline is if you have less than 4 gb of ram to use a 32 bit operating system on 64 bit hardware and if you have more than 4 gb of ram then use the 64bit operating system on a 64 bit hardware. I do run several servers on 32 bit operating systems on 64bit hardware
with more ram due to other issues but I am starting to use more 64 bit operating systems since 64 bit servers are getting very stable the last few years

---

