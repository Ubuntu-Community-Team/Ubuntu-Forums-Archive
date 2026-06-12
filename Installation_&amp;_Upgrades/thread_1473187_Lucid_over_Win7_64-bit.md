---
title: "Lucid over Win7 64-bit"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by dbaugh on 2010-05-04
Hi.  I have an i7-980x on a Gigabyte UD7 MB running Win7 Professional 64-bit.  I have an application that was written in C++ to run on a Unix box.  How complicated is it to install Lucid so that when I boot my machine I have the option to come up in either Win7 or Ubuntu?  If I choose Ubuntu I want to run the exe from the compiled C++ app.  I am hoping the answer is "trivial".  Thank you.

---

### Post by timothydonohue on 2010-05-05
> **dbaugh said:**
> Hi.  I have an i7-980x on a Gigabyte UD7 MB running Win7 Professional 64-bit.  I have an application that was written in C++ to run on a Unix box.  How complicated is it to install Lucid so that when I boot my machine I have the option to come up in either Win7 or Ubuntu?  If I choose Ubuntu I want to run the exe from the compiled C++ app.  I am hoping the answer is "trivial".  Thank you.

if you already have windows 7 installed, using a live cd to install ubuntu is as simple as resizing the windows partition and following the installation instructions (read them as you go).  once that is done, then you will have the option of choosing which OS you boot into at startup, right after bios screening, courtesy of grub.  just make sure you're paying attention as it boots, because there is a time limit, and it will boot into a default OS unless you choose otherwise (mine boots into ubuntu by default, i have to choose to boot into w7)

the live cd will help you along.  just boot from disc.  from there, you can create a new partition, resize windows, and install ubuntu

---

### Post by dbaugh on 2010-05-05
Thank you.  Just what I wanted to hear.

---

### Post by Mark Phelps on 2010-05-06
Two things ...

First, do NOT use the Ubuntu installer to resize the Win7 OS partition; use the Win7 Disk Management utility.  That will prevent the problem of corrupting Win7 partitions.

Second, you are most probably NOT going to run your compiles C++ program in Ubuntu.  It can not execute MS Windows .exe files.

---

