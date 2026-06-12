---
title: "[SOLVED] Unable to install Ubuntu : /bin/sh: can't access tty; job control turned off"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by Levure on 2007-09-07
Hello !

I have a problem while trying to launch the Live CD 7.04

The Kubuntu blue bar is displayed, and after a few moment, I have a console with that error :

/bin/sh: can't access tty; job control turned off
(initramfs)

Is my configuration uncompatible for Ubuntu ?

- ASUS P5K-E-WIFI-AP
- 2 Go RAM Corsair Dominator (2x 1Go)
- Intel Core2Duo E7650 
- Barracuda SATA 250Gb (Hard-Drive)
- Samsung SH-S183A SATA (DVD/CD writer)
- Nvida EN7600

What can I do in order to install successfully Ubuntu on that computer ?

Many thanks in advance for your tips !

---

### Post by be4truth on 2007-09-07
If you want to install Ubuntu why do you use the Kubuntu CD? My expience is that the Kubuntu CD makes more trouble than the Ubuntu. I always install Ubuntu and then add the KDE desktop afterwards. My experience is that Kubuntu desktop alone is not grounded in Ubuntu. The OS runs well when KDE is installed on Ubuntu.

---

### Post by mxg01 on 2007-09-07
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=544141](http://ubuntuforums.org/showthread.php?t=544141)

---

### Post by Levure on 2007-09-07
re-Hello !

I've read the thread, so : :-k

- That's a fully new computer, so the hard-drive is really empty
- The hard-drive and the CD/DVD writer owns their own SATA cable, there isn't any possibilities to set one as 'slave', so I assume they are both considered as 'master'
- I don't have a floppy drive in that computer, so the trick to boot by putting a floppy in the floppy drive won't help me.

I just see two things to try :
- Retry with that LiveCD and remove the splash screen to see what it is failling exactly because it seems that error can have many different cause(s).
- Try using the "Alternate" 7.04 CD (which is text-based and can skip some graphics card problem).
- Try using the Ubuntu 6.06 CD

So, i try that and I will say what later !

Thanks for the thread's link !

---

### Post by be4truth on 2007-09-07
definitely try the altenate CD. I had already a number of installations which went fine on alternate CD install but no chance on LiveCD. To be honest; I don't download the LiveCD anymore. For what?

The other thing you could try just for the fun of it. Can you pass a boot option? 
Try to type 

```
linux=pci=nomconf ide0=0x1018,0x1010
```

Just see if that is the problem. If it doesn't help just forget it.

---

### Post by Levure on 2007-09-08
Hello from.... Ubuntu 7.04 !

Many thanks for your help ! 

The Ubuntu 7.04 Alternate CD was the answer !

I used synaptic after to add the kubuntu-desktop package and everything is now perfect !

Thanks again ! :-)

---

### Post by be4truth on 2007-09-09
Nice! Please mark this thread 'solved' - Go to the top of this page and use Thread Tools.

---

### Post by Levure on 2007-09-09
Done ! :-)

I was looking to edit the title yesterday, but I didn't saw the "Thread Tool".

---

