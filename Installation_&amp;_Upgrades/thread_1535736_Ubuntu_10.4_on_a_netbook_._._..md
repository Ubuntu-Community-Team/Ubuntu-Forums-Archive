---
title: "Ubuntu 10.4 on a netbook . . ."
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by ThePossum on 2010-07-21
Have a problem with my current installation of 10.4 on my netbook.  Seems the netbook has suddenly run out of HD space.  In terminal it is only showing like 7GB of HD space total but the netbook actually has a 40GB drive.

So I want to reinstall 10.4 on it again hoping that it will fix my problem.  My question is can I safely install the decktop version or should I install the Netbook Edition.  I do like the on screen desktop of the Decktop version much better than the one on the Netbook edition.

Which should I use to possibly avoid the full disk problem?

---

### Post by tommcd on 2010-07-21
> **ThePossum said:**
> 
Which should I use to possibly avoid the full disk problem?
Neither one will avoid this, because we don't even know why you have run out of disk space.
To try to find out where all of your space went, try running in the terminal:
```
sudo du -csh /*
```
This will take a bit of time to run. You can run that command without sudo, but you will get "permission denied" messages on files belonging to root. If you see that a certain directory, like /var for example, seems to be unusually large, you can run:
```
sudo du -csh /var/*
```
This will help you drill down to find exactly what directory is eating up space.
To see a summary of your partitions and how much space has been used, and how much is available, run:
```
 df -h 
```
Have you been running the system as root??? Have you enabled the root account???

Otherwise, you can install the desktop or the netbook version. It is always your choice.

---

### Post by ThePossum on 2010-07-22
Will give that a try.  Thanks

---

