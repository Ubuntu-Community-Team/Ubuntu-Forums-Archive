---
title: "Grub Crash on Boot loader with keyboard"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by palmor on 2010-02-26
Hi! I have post this in linux mint forums too, but I can't solved, this is the issue:


I have installed Linux mint and it failed on grub, if I press something grub crash, tired of that I install Ubuntu but my surprise was the same problem on grub, I was thinking if grub2 was the problem, so I tried grub legacy and was the same x_x

I remember use a old version of ubuntu with lilo (or was opensuse) but it works! but neither last ubunt nor mint with grub :(

The problem is:
   Grub loader: select OS
   If I press ANY key it crash, if I wait the 9 seconds it enter to default OS (first option)


Note: It is neither PS2 nor USB keyboard, it's a laptop keyboard, a Compaq presario 2100

Note 2: I don't speak english very well ^_^

Any help?

Thanks!

---

### Post by mgcarley on 2010-03-10
> **palmor said:**
> Hi! I have post this in linux mint forums too, but I can't solved, this is the issue:


I have installed Linux mint and it failed on grub, if I press something grub crash, tired of that I install Ubuntu but my surprise was the same problem on grub, I was thinking if grub2 was the problem, so I tried grub legacy and was the same x_x

I remember use a old version of ubuntu with lilo (or was opensuse) but it works! but neither last ubunt nor mint with grub :(

The problem is:
   Grub loader: select OS
   If I press ANY key it crash, if I wait the 9 seconds it enter to default OS (first option)


Note: It is neither PS2 nor USB keyboard, it's a laptop keyboard, a Compaq presario 2100

Note 2: I don't speak english very well ^_^

Any help?

Thanks!

Hi,

I had the same problem on a Compaq nx9005 (Finnish Keyboard) - both with grub 1.97 installed (as supplied with (K)Ubuntu 9.10) as well as with all 4 of the 9.10 bootable CD's (Ubuntu Desktop, Alternate and Kubuntu Desktop, Alternate).

**Solution: Enter the BIOS and turn *off* the USB legacy support.**

Although it seems somewhat counter-intuitive, for some stupid reason it worked for me - I stumbled upon this solution completely by accident.

Hope this helps.

(K)Ubuntu and Grub Developers: I think Grub 1 was better. Grub 2 is unnecessarily complicated. Yes, I know it's elegant or whatever but... it's stupid. And obviously Grub 1 was more stable.

---

