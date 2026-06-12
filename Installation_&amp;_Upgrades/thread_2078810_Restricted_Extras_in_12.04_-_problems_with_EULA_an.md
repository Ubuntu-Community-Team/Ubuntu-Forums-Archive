---
title: "Restricted Extras in 12.04 - problems with EULA and /var/lib/dpkg/lock"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by Loerie on 2012-10-31
During 12.04-1 installation, when running

> sudo apt-get install ubuntu-restricted-extrasit gets stuck at a Microsoft EULA, "Configuring ttf-mscorefonts-installer".
It says <Ok> but nothing makes it accept the EULA. Terminal has to be closed in order to do anything.

Running

> sudo apt-get install -fresults in:
> 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?Anyone else having issues with accepting the EULA?
Please help me to get rid of the lock, it is messing up the installation.

Should anything fail, can one "undo" the installation of restricted extras?

 Thanks!

---

### Post by howefield on 2012-10-31
> **Loerie said:**
> During 12.04-1 installation, when running

it gets stuck at a Microsoft EULA, "Configuring ttf-mscorefonts-installer".
It says <Ok> but nothing makes it accept the EULA. Terminal has to be closed in order to do anything.

Use the tab key to highlight the OK button and press enter.

---

### Post by Loerie on 2012-10-31
Great, but The problem is right now that I am locked out and cannot get back to the EULA window. 

What ever I do in terminal, the 
> 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?> 

message appears.

---

### Post by howefield on 2012-10-31
Generally means another apt-get instance is running, close all running package installers or might be easier to restart the machine.

---

### Post by Loerie on 2012-10-31
I restarted several times...  no change

---

### Post by howefield on 2012-10-31
Try these commands in a terminal one at a time.

```
sudo rm /var/lib/dpkg/lock
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

---

### Post by Loerie on 2012-10-31
It did it!

Your suggestion to get out of the EULA through TAB  ENTER would have probably prevented the lock problem. I mention it for  others who might experience the same problems in the future.

Thanks!

---

### Post by howefield on 2012-10-31
You're welcome.

Glad you got it sussed.

---

### Post by hans12345 on 2012-11-01
Thanks!

I had exactly this problem.

---

