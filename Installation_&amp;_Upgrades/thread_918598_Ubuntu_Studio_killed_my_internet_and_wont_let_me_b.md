---
title: "Ubuntu Studio killed my internet and wont let me bring it back"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by scenkner on 2008-09-13
I have an odd internet setup.  I had previously installed usb-rndis-lite. a little program which allows me to share my internet from a Windows Mobile smartphone with my desktop running linux.  All was going well until I installed the studio package. After installing the internet stopped working.  So I tried to reinstall usb-rndis-lite but am getting a strange error which I never got before. It was unable to find lib/modules/2.6.24-19-rt/build.  What is this and why is it no longer there?

---

### Post by Sef on 2008-09-13
> It was unable to find lib/modules/2.6.24-19-rt/build. What is this and why is it no longer there?

It's part of the kernel.   What is your kernel?  If you don't know, then do this:

Open the terminal (it could be Applications > Accessories > Terminal), then paste or type in this code:

```
uname -r
```

---

### Post by scenkner on 2008-09-15
Kernel is 2.6.24-19-rt, there just isn't any build folder.
BTW, the terminology I am using probably isn't correct.  I dont think that usb-rndis-lite is actually a program, I think its a driver.  Also, this error is occurring during the make command.

---

### Post by scenkner on 2008-09-17
I really hate being a bumper, but im sure that somebody knows why this has happened and I really like to have internet.  Can someone help as to why the build folder is no longer in the kernel?  How do I get it back?

---

### Post by scenkner on 2008-09-17
If anyone is interested, I have fixed it myself! :)
I noticed after some looking that lib/modules/2.6.24-19-generic/build was still completely intact.  So, I installed usb-rndis-lite using the generic kernel.  Then with the internet up, I downloaded the linux headers for 2.6.42-19-rt which is the default kernel that my system loads into.  Then I was able to log in using 2.6.42-19-rt and install usb-rndis-lite.
I was able to find that the build folder that was missing was directly related to these header files which somehow disappeared.  Or when I installed Ubuntu Studio, it created this "rt" which I hadn't been using all along. (I never noticed what I was using before).
Anyway, it is fixed and if anyone else ever runs into a similar problem, here is the solution.  GET THE HEADERS!

---

