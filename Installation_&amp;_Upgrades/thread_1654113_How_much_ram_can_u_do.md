---
title: "How much ram can u do?"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by Al Grant on 2010-12-27
I am thinking of going 64bit Ubuntu on my desktop PC. The main reason for this is so I can put a truck load of ram in and vbox more than one machine at a time.

I know 64bit Ubuntu can probably handle some extraordinary amount of ram (32G seems to come to mind).

The box is a oldish Core Duo HP machine with a ASUS branded mobo in it with DDR2. 

I am wondering if I am likely to not be ram limited by the OS but by the hardware itself?

Was thinking of going to 16G - anyone have any experience in this area on hardware of this vintage?

Cheers

-Al

---

### Post by presence1960 on 2010-12-27
Look up your mobo specs and it will tell you the max RAM supported for 64 bit OSs

---

### Post by carl801 on 2010-12-27
Al Grant:

This is my computer, built about 3 years ago (from hardinfo).

Computer Processor: 4x AMD Phenom(tm) II X4 955 Processor
Memory		  : 7224MB (2448MB used) DDR2
Operating System  : Ubuntu 10.10
Kernel		  : Linux 2.6.35-24-generic-pae (i686) 32 bit

I have no problem running several virtual machines at one time using Virtualbox v4.0.0.  Right now, I'm simultaneously running Windows XP, Linux Mint, and Natty 11.04.  My Asus motherboard is several years old, AM2+ socket.  The processor is relatively new, 4 core.  

But take a look at this test on a Core 2 Duo laptop using both 32 and 64 bit Ubuntu OSs. Clearly, memory aside (they used 4gb for all tests), there is a really significant increase in performance with the 64 bit kernal.

I'd say go first with 2x4gb sticks and a 64bit installation and see how it works.

Carl

---

### Post by carl801 on 2010-12-27
Sorry, forgot the link:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by akand074 on 2010-12-27
The limitation will be the OS, not the hardware. 64 bit hardware theoretically can handle 16 exabytes. Windows 7 (64bit) Professional and Ultimate can handle up to 198 GB of RAM. I imagine 64 bit Linux could handle more. You have nothing to worry about. Worry about getting a motherboard that can support that much.

---

