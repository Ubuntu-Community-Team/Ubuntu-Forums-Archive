---
title: "ubuntu 13.04 installer shows no partitions"
date: 2013-12-29
forum: Installation &amp; Upgrades
---

### Post by masridhar on 2013-12-29
I'm trying to install Xubuntu 13.04 on an HP Envy h8-1414 desktop  computer running Windows 8. I would like to set it up dual-boot. I  downloaded the 64-bit AMD desktop ISO onto a USB device and booted from  it. I am able to "try ubuntu" just fine - in fact I am writing this  message from within Firefox while trying it. But when I try to install  it, the installer shows me this when trying to select a partition, see  screen shots here: [https://sites.google.com/site/masridhar/xubuntu-install-problems](https://sites.google.com/site/masridhar/xubuntu-install-problems)  When I click any of the buttons in the empty partition list, the installer crashes.

I used gparted to carve out some space for Ubuntu, and it shows me the  partition list just fine. I also read in other threads on askubuntu and ubuntuforums that  I should try using gdisk to check for errors in the GPT disk. But that  seems to show that everything is fine. 

I'd love to get xubuntu going on this machine. Thanks in advance for your help!

---

### Post by masridhar on 2013-12-29
Answering my own question: Found this on one of the threads on askubuntu.com:

Remove RAID settings from the drives:

sudo dmraid -E -r /dev/sda 

That did the trick, and the installer can now see all the partitions. I was able to install xubuntu.

---

### Post by oldfred on 2013-12-30
That would indicate you have an Ultrabook with Intel SRT. 
You may also have video issues and need bumblebee.
See link in my signature for more info.

---

