---
title: "Cryptswap1.. (endless failure)"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by weber-h3x on 2013-12-12
yep.... i know it has been posted about 398475032 times everywhere else, but i CANNOT seem to solve this... 

I recently had my Ubuntu 12.04.3 system crash & then when re-installing, it says cryptswap and swap setup just fine, but once the system tries to load, i get the message above.
I scoured the web high and low, trying everything from terminal commands, to GParted, to punching kittens... nothing seems to work.
3 pots of coffee and a whole day later, i find this:

[http://askubuntu.com/questions/341979/what-to-do-about-the-disk-drive-for-dev-mapper-cryptswap1-is-not-ready-yet-or](http://askubuntu.com/questions/341979/what-to-do-about-the-disk-drive-for-dev-mapper-cryptswap1-is-not-ready-yet-or)

I tried that, and everything went well... then upon reboot, it still gives me the same god-forsaken message!  
...then G parted says the swap area is broken... again...

WHAT IN THE F**K!??!

-------------------

As for a solution, I've seen a few suggestions of people saying, "DO NOT encrypt your home folder" and everything will be fine...  

.... I don't know what to do... aside from pull my hair out and drink more coffee...

---

### Post by weber-h3x on 2013-12-12
Specs:

Ubuntu 12.04.3 (64 bit)
4096 linux-swap (primary)
remaining area = ext4 (primary)

AMD quad-core
8g dual-chan memory
two 8800-gts-512 (SLI)
160g HDD (main)
320g HDD (backup)

---

### Post by PaulBx on 2013-12-14
Do you really need swap? Try swapoff -a. Buy some more memory.

---

### Post by weber-h3x on 2013-12-14
Re-install >

4096 swap (beginning + primary)
remaining /ext4 (beginning + primary)

DO NOT Encrypt /home 
DO NOT update during install

complete install > add indexes > update system > set drivers > profit

---

