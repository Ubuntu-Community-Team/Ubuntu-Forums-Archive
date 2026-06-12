---
title: "installing planeshift"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by amyfan on 2007-08-06
i have been trying to install planeshift i have read all the forums on it but none help i do not get anything when i try to install it this is what i have downloaded /home/------/Desktop/PlaneShift_CBV0.3.019-x86.bin i can not find a way to install it or mount it as a iso image any help would be greatful thanks

---

### Post by ifeldt on 2007-08-08
Try running this
```
chmod +x PlaneShift_CBV*
sh PlaneShift_CBV*
```

This should get it installing.

What this does is take the .bin installer file and sets it to executable. This should allow you to run it as intended.

You may need to add a sudo before the sh command, and enter your password if you get an error.

---

### Post by kilgor3 on 2007-08-09
Im having the same prob as him/her...

I followed your advice got this error when trying to run sh with and without sudo

xxxx@xxxx:~$ sudo sh PlaneShift_CBV0.3.019-x86.bin
PlaneShift_CBV0.3.019-x86.bin: 1: Syntax error: "(" unexpected

---

### Post by easyease on 2007-11-30
> **kilgor3 said:**
> Im having the same prob as him/her...

I followed your advice got this error when trying to run sh with and without sudo

xxxx@xxxx:~$ sudo sh PlaneShift_CBV0.3.019-x86.bin
PlaneShift_CBV0.3.019-x86.bin: 1: Syntax error: "(" unexpected
same problem here.

---

### Post by mordiaky on 2008-01-06
Easy Install

Open Terminal

Type in:
```
chmod +x PlaneShift_CBV*
./PlaneShift_CBV*
```

Follow the on screen installation.

---

### Post by jakswa on 2008-04-11
Thanks to you!

---

