---
title: "Is it Possible to Connect a Wired USB Xbox 360 Controller in Ubuntu?"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by sting547 on 2009-11-14
I have ubuntu and I have an Xbox 360 wired controller. Is it possible to play games in ubuntu using the controller? Thanks in advance

---

### Post by skatinjj on 2009-11-14
Not sure but you can always google around or just plug it in and see if it works.

---

### Post by Kreaper on 2009-11-14
I'm not sure but i know on windows when you plug it in it automatically downloads something from microsoft, so you may need a driver for it.

---

### Post by sting547 on 2009-11-14
I tried plugging it in and the light turned on on the controller, but Ubuntu didn't do anything.

---

### Post by oboewan on 2009-11-14
This tutorial should help you:
[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

---

### Post by sting547 on 2009-11-14
I put in all of the commands, but the same thing happened.

---

### Post by skatinjj on 2009-11-18
Did you get eny errors at some point?  If so, which commands gave the error(s)?

---

### Post by echotone on 2009-11-20
I cant download the jscalibrator package. It says not found.

---

### Post by sting547 on 2009-11-24
> **skatinjj said:**
> Did you get eny errors at some point?  If so, which commands gave the error(s)?

I had the same problem.

---

### Post by John Forseti on 2009-12-06
I got too;

> 
**Compiling and installing the drivers**

  
Assuming your current directory is your working directory ("xpad"), all you need to do is to execute the following commands: 

make
sudo make install
sudo modprobe -r xpad
sudo depmod -a
sudo modprobe xpadThis will compile the module, install it, remove the old one, and load the new one. If the process return errors, you probably missed a step. Otherwise, check the [Testing and Troubleshooting]("https://help.ubuntu.com/community/Xbox360Controller#Troubleshooting") section. 
I use "make";

forseti@Forseti:~/xpad$ make
make modules -C /usr/src/linux-headers-2.6.31-16-generic SUBDIRS=/home/forseti/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
scripts/Makefile.build:44: /home/forseti/xpad/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/forseti/xpad/Makefile'. Stop.
make[1]: *** [_module_/home/forseti/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2

---

### Post by Kreaper on 2009-12-08
Does the directory " /home/forseti/xpad/Makefile" exist and contain a makefile?

---

### Post by axldavis2012 on 2010-10-02
i tried to use the instructions from that link and did not work

---

### Post by Kain000 on 2010-10-06
I also got the same error after giving the command make.. any ideas?

---

