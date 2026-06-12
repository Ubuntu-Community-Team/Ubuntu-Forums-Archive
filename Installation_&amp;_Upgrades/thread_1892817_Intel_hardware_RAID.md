---
title: "Intel hardware RAID"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by talbert.nh on 2011-12-08
Hello
New to Ubuntu. Setting up a file server with Intel S1200BTL mobo and Intel RS2BL080 RAID card, with 4 x 2TB WD SATA HDDs in a single RAID 10 array. I have installed 10.04.3 and 11.10 and get the same result: the installation sees the RAID volume, even calls the RAID card by name, and seems to install fine. The install asks to remove the DVD and reboot, which it does, then it boots to a grub rescue prompt. 
 
I have done an install to a single SATA drive and it booted fine, so I am missing something with RAID here. It is strange that the install sees the 4TB volume, but after rebooting it does not. 
 
Update: I did another install of 11.1 and now it boots fine. Should I be concerned with how hard it was to get a good install? Anything I am missing with Intel RAID?
 
Thank you, much appreciated.
 
Tom

---

### Post by megahertz on 2011-12-14
Did you use ubuntu-11.10-alternate or ubuntu-11.10-desktop?
The problem is that the Ubuntu desktop installation software comes with and loads the Raid manager software (dmraid), but it doesn't install it on target drive. The second main problem is that you're not able to install the boot loader (Grub), maybe because dmraid hasn't bean installed.
You _must _use ubuntu-11.10-alternate to install dmraid (raid manager) and install grub properly.

---

