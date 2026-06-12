---
title: "upgrade to 14.04 with broadcom card"
date: 2015-02-09
forum: Installation &amp; Upgrades
---

### Post by mringer on 2015-02-09
Dell Inspiron, L-Ub 12.04, people have persuaded me I should upgrade to 
14.04. I want to use the live CD because it is easier to back out if things go 
wrong.

The most obvious problem is that it has a Broadcom card and I see that these 
cards are still giving any amount of trouble. The only way I could get mine to 
work was to install wicd and ndiswrapper. So I want to start by downloading
them. Please:

What are the package files for wicd and ndiswrapper for L-Ub 14.04?
Where can I find them?

Please dont anybody tell me I should do XYZ instead unless XYZ is very
reliable & comes with clear instructions.

---

### Post by Rex Bouwense on 2015-02-09
I also have a Dell Inspiron.  Mine is a very old 1000.  The easiest way to install the correct drivers and firmware is to follow the "How To" in Ask Ubuntu  
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
It is a pain to have to do that every time you change Operating Systems, but at least someone now has placed all the required information in one location.

---

### Post by mörgæs on 2015-02-10
> **mringer said:**
> The only way I could get mine to work was to install wicd and ndiswrapper.

This is unusual for a Broadcom card. Mostly they are easy to get to work without these tricks:

[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by mringer on 2015-02-11
Thank you who replied and especially for the advice to run lspci and
identify the card (done). 

Essentially you said "use firmware-b43-installer "
so how can I download the package for L-UB 14.04 while I still have a
working network i.e. before I start to upgrade from 12.04 ? 

Thank you

---

### Post by mörgæs on 2015-02-11
Don't upgrade. Do a fresh install of 14.04 using wired internet access.
When that works you use the advice in the link to get the Broadcom card running.

---

