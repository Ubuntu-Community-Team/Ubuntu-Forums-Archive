---
title: "Crash during 2.6.31-20 kernel update..."
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by tangobravo on 2010-03-08
Feeling quite lost, here -- been using Ubuntu for quite some time now, and never ran into a problem I couldn't tackle - but I've never seen anything like this, so I don't even know specifically where to start / what info to provide.
 
Running Karmic on my laptop, I get very occassional kernel panics (suspect it has something to do with the Broadcom WiFi because it only seems to happen with heavy network traffic or HDD access), but just my lucky, this time it Panic'd on me during my recent update -> linux-kernel 2.6.31-20. My system still 'works', but I get the following when doing any other updates, now:
 
```

sudo dpkg --configure -a
[sudo] password for tango: 
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-generic
 linux-generic

```
 
Now I cannot seem to get rid of that, and of course, I am stuck in the prior version. Granted everything 'works' - but it bothers me. What's the best way to go about tracking down and hashing out a problem like this?

---

### Post by michaelenstone on 2010-03-09
I had the same problem.  Turned out to be an issue with GRUB.  

Try reinstalling grub-pc:

```
sudo apt-get remove grub-pc
sudo apt-get install grub-pc
```

then reconfigure packages:

```
sudo dpkg --configure -a
```

---

### Post by emptythevoid on 2010-03-16
Ran across this bugaboo after updating a clean install.  I really appreciate the help!!  :D

---

### Post by tangobravo on 2010-03-17
I hate to say it... but this didn't do it for me =(   Any other thoughts?

---

### Post by Nissan_350Z on 2010-03-21
> **tangobravo said:**
> I hate to say it... but this didn't do it for me =(   Any other thoughts?

i have to agree.. it didn't do it for me either.. did anyone find a fix for this?

---

