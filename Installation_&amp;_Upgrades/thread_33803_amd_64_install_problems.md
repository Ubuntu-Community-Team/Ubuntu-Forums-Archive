---
title: "amd 64 install problems"
date: 2005-05-12
forum: Installation &amp; Upgrades
---

### Post by atysh on 2005-05-12
Hi,

I've been trying to install ubuntu-amd64 on my pc (amd64 754, MSI K8T NEO) and have some problem with it...

At first apt doesn't work properly (maybe because of the crapy on board Realtek gigabit LAN) so can't finish the installation and reports a lot of errors. I just don't understand why I have to have internet connection to install an op system? It got me grazy with Debian, too. 
I could find an unofficial add-on CD, but only for 32 bit versions. I may put a 32 bit system on my machine, and wait... but then there is no point of having a 64 bit processor...

So, is it possible to install ubuntu (or kubuntu) 64-bit without internet connection?

Thanks

---

### Post by futte on 2005-05-12
me too i have a old pci netkort i used in sted of my Gigalan ,Suse and MD is the only one that kan use gigalan  :roll:

---

### Post by atysh on 2005-05-12
Yeah, I did the same - using an 10/100 'old' card kubuntu's slipt on the machine. Now I hope that support for gigalan will pop up soon....

Thx for replying

---

### Post by chryz on 2005-05-12
As far as I could see this network adapter is supported by the "r8169"-module, and has been supported for ages. Modprobe the damn thing allready  :?

---

### Post by sneferu on 2005-05-12
I too had problems with installs, both debian and ubuntu... Fedora worked fine, but i do not want fedora... So i kept on struggling...

I have an MSI Neo 2 (brand new)
3.31 is bios version
Nvidia GeForce 5500 256 mb card
the realtech gig nic
1 sata drive on the board
2 ata drives on a maxtor card
1 dvd and 1 cdrw/dvd drive
2 GB of ram

I finally got ubuntu to install (using failsafe defaults and then turning options on one by one in the bios) and now my only problem is that when rebooting the system stops and tells me that fsck failed because my super block is corrupt or my filesystems are not proper ext2 filesystem... control d to continue and the system boots the rest of the way and works fine (except the nic card which is slower than xmas). My filesystems are ext 3.

the nic works fine with internet but it does not run at GB speed on local network... more like 10 base... told me 14 hours to copy 3 gigs... So i'm gonna turn that thing off and add a pci nic card... at least for now...

---

