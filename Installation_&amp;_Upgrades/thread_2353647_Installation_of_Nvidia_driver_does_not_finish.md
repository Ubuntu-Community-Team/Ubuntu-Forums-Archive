---
title: "Installation of Nvidia driver does not finish"
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by DB4711 on 2017-02-23
Hello,

I installed Ubuntu 16.04.2 on my XMG C405 with GTX 965m.

When I try to install any Nvidia drivers the installation stops at about 95%. I cannot abort this. Rebooting does not "repair" this problem. E.g. when I want to install any other software I get this error:
```

E: Could not ge lock /var/lib/dpkg/lock - open (11: Resource temporarily
unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
I tried to install the drivers directly after Ubuntu installation via "Additional Drivers utility" and after reinstalling Ubuntu with:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
```
and then "Additional Drivers utility"

Tried it now for 10 times without success...

Does someone has an idea where the problem could be?

Thanks for your help!

---

### Post by lisati on 2017-02-23
Check that you don't have something like Software Centre or Update Manager running, closing them if necessary. If that doesn't help, rebooting sometimes helps.

---

### Post by Autodave on 2017-02-23
Agree w/lisati: sounds like an update is running.  You may just want to leave the machine on and running for 1/2 hour and try again: that should let the updating get completed.

You can also go into SETTINGS -> SOFTWARE & UPDATES -> ADDITIONAL DRIVERS and let that search for the latest one. I believe that 375.39 is the latest version and is what I am using.

---

### Post by DB4711 on 2017-02-24
Hello,

thanks for your help!

Do I understand it correct that I should leave the machine on and running for a while directly after initial installation and then begin to install drivers and so on?

I tried to install gparted directly after initial Ubuntu installation. It was installed without any problems. But Nvidia driver does not install as described whenever I try it.

---

