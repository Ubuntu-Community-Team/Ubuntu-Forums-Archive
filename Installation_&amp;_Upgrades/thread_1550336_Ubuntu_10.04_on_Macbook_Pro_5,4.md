---
title: "Ubuntu 10.04 on Macbook Pro 5,4"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by sandhuatub on 2010-08-10
Hi,

I have been trying to get Ubuntu installed on my Macbook Pro for a over a week now with no success.

Distro: Ubuntu 64-bit 10.04 LTS
Hardware: Macbook Pro 5,4 with firmware 1.8

I have tried almost all methods I could find by googling. I am trying to do a single OS install, that is, only Ubuntu and no OSX.

I have tried two methods:
1. Wipe disk, install refit on a 200MB partition and install Linux on rest of the disk. With this install, I boot into refit and then select Linux. Grub loads and then the system hangs at "Uncompression Error - System halted". The machine boots up fine with LiveCD so hardware issues are not a suspect. Refit sync fails with a message saying "Analysis Inconclusive, will not touch the disk"

2. Wipe disk and install Linux on the entire disk (sda1 for root and sda2 for swap). Results in the same "Uncompression Error". 

I tried to install Fedora and got the same "Uncompression Error" after finishing install and rebooting.

Will appreciate pointers or howto from anyone who has successfully done a single OS install on their MBP?

---

### Post by sandhuatub on 2010-08-10
As a reference, I have tried:
[http://regebro.wordpress.com/2008/11/16/installing-linux-on-a-macbook-without-os-x/](http://regebro.wordpress.com/2008/11/16/installing-linux-on-a-macbook-without-os-x/)

AND,

[http://mac.linux.be/content/single-boot-linux-without-delay](http://mac.linux.be/content/single-boot-linux-without-delay)

To fix any kernel issues in the original distro, I booted into a particular install in rescue mode, chrooted to the hard disk image and ran "apt-get upgrade" to install new packages. Did not help.

---

