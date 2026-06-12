---
title: "Binary Is Whitelisted [At Live Cd Boot]"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by Kenposcholar on 2012-12-29
A frustrating problem occurred today. Installing via an Ubuntu 64 bit live cd, the installation is quickly stopped after choosing any option with the error "Binary is Whitelisted". There is no more information than that. I tried to install from wubi on W8, however, it appears that UFEI prevented that from working as well. It has to be a problem with the BIOS conflicting, but I am not sure what setting is the problem. ANY help would be appreciated. :o :o

SPECS: -ASUS Republic of Gamers G75VW-AS71
       -Intel Core_i7_2.7_GHz Processor 2.3GHz
       -16 GB DIMM RAM
       -1TB 7200rpm Hard Drive
       -Nvidia GTX 660M 2G GDDR5
       -Windows_8 x64

---

### Post by sejje on 2012-12-29
Had this same issue, same laptop.

Just now solving it, but need to add "nomodeset" in grub-it goes after the two dashes on the vmliniz line. Is related to video drivers.

PM me if you need more help, or email me-- [email]myusername@myusername.net[/email] ( fill in with sejje )

---

### Post by davelindberg on 2013-01-10
Has anyone figured this out?
 
I bought the below laptop from Best Buy...
 
SPECS: 
-ASUS Republic of Gamers G75VW-BHI7N07
-Intel Core i7 3630QM Processor 2.4GHz
-8 GB DIMM RAM
-1TB 5400rpm Hard Drive
-Nvidia GTX 660M 2G GDDR5
-Windows_8 x64
 
I got Ubuntu 12.10 installed under UEFI on a secondary internal hard drive, but when I boot from the hard drive under UEFI or "Launch CSM" I message that says "Binary is whitelisted". If I do nothing, Ubuntu loads in 30 seconds. I am just annoyed by the "Binary is whitelisted" message. Anyone knows what the message means?
 
The only way I got the Ubuntu to install from the Live USB was to boot from BIOS using "Boot > Launch CSM > Enabled" and "Security > Secure Boot Control > Enabled".
 
Any suggestions?

---

