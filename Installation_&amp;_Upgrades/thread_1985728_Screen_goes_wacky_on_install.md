---
title: "Screen goes wacky on install"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by atomicspin on 2012-05-23
Trying to install Xubuntu 12.04 on a Toshiba Satellite (Sorry, model numbers are worn off, but it's older).  
After I hit "Install Xubuntu" the screen either a) goes blank and stays blank or b) goes crazy and throws weird graphics all over it.

I've already tried installing with nomodeset and I get the same problem.  

Thanks in advance for any help.

---

### Post by kc1di on 2012-05-23
can you open a terminal and and enter the following command then post the result here.

```
sudo lspci
```
the l is a lower case L not #1

---

### Post by atomicspin on 2012-05-23
> **kc1di said:**
> can you open a terminal and and enter the following command then post the result here.

```
sudo lspci
```
the l is a lower case L not #1

Thanks for responding.
This is a fresh install on a new hard drive, so no OS is currently on there.  Is there a way to get to Terminal via the install disc?

---

### Post by kc1di on 2012-05-23
yep go to the live boot and bring up a terminal and run the command
it will still find the info I'm looking for.

---

### Post by atomicspin on 2012-05-23
> **kc1di said:**
> yep go to the live boot and bring up a terminal and run the command
it will still find the info I'm looking for.

Unfortunately, same problem happens when I try to run the live boot.  It just keeps rebooting.

---

### Post by kc1di on 2012-05-24
> **atomicspin said:**
> Unfortunately, same problem happens when I try to run the live boot.  It just keeps rebooting.

and you already tried the nomodtest option?
here are a couple things you can try.

[http://askubuntu.com/questions/139437/ubuntu-12-04-live-cd-wont-boot]("http://askubuntu.com/questions/139437/ubuntu-12-04-live-cd-wont-boot")
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

