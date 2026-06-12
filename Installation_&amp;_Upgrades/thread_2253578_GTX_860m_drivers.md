---
title: "GTX 860m drivers"
date: 2014-11-20
forum: Installation &amp; Upgrades
---

### Post by Evil Larney on 2014-11-20
Hi there, 

I recently bought a new laptop with the GTX 860m gfx. Now I wanted to install the drivers for it but I have no clue how to do that. I have tried several methods to install it and none of them worked. 

When I try to install it through the terminal ctrl + alt + F2, I get the message that I have no video card that supports the drivers. After that I get the message that my X server is running and I should close it. 

I tried many other ways I found when I googled, but none of them worked. Can someone help me?

---

### Post by oldfred on 2014-11-21
Is it an ultrabook with dual video or just the nVidia?

If dual video you may be booting with the Intel driver and the nVidia is not seen?

       [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
Getting hybrid graphics to work nvidia-prime GT650M - but you want most current nVidia driver available
[http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-nvidia-prime-gt650m](http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-nvidia-prime-gt650m)
Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)
Bumblebee - allows both nVidia & Intel to be used, nVidia Prime is just nVidia:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04](http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

