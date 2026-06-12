---
title: "Xubuntu install hangs during livecd boot up"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by snowboard975 on 2007-02-20
Hi there,
I am trying to install Xubuntu 6.10 on my computer that has celeron 1Ghz CPU and 412MB RAM.

But it hangs while live cd boot up when it showed a rat logo surrounded by ubungu logo. The bottom moving bar stops after 3 seconds since it shoed the logos. 
I tried the second boot option(safe graphic mode). but it also hangs my computer likewise. 

Any suggestions?

---

### Post by Ionix on 2007-02-20
Hmm... sounds like the same problem I am having.. Is your graphic card ATI?

---

### Post by snowboard975 on 2007-02-21
> **Ionix said:**
> Hmm... sounds like the same problem I am having.. Is your graphic card ATI?

No. It is from Nvidia. And I've finally got the solution. 
I pressed F6 key on the boot menu. And deleted "quite splash" from the kernel options. Then I could see where it hanged. It showed some errors that says hda has badcrc and dma problems. I googled the error and found the problem was aroused because I use 40pin IDE cable that cannot support UDMA function in contrast with 80pin IDE cable. So I disabled UDMA function from the CMOS setup. And I successfully installed Xubuntu!

---

### Post by TSBonLinux on 2007-04-17
Did you check the disk? mine did that too when I used a bad disk. try burning again with a better disk

---

