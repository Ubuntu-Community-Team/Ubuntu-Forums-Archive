---
title: "Install, no root file system is defined, internal error"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by OpusX on 2013-02-09
Hey guys. I got a problem here, been bugging me for a couple weeks. Literally spent a lot of hours on trying to get my PC to run Ubuntu. 
I honestly just cant do it, without one of you guy's help. So here it is. Started off using Vista. It  came with the PC. I wanted to jump ship, and it's been a few years since I've used Ubuntu. Think my old PC ran Ubuntu 7.4, and that would be around the last time i touched Linux. So I downloaded Ubuntu 12.10. Before I go further, here are my specs... Got a gateway Lx6810-01, with the Intel processor Core 2 Quad Q8200(2.33GHz)64 bit Quad-Core, 8GB DDR2 memory and a 640GB Hard Drive. So I download Ubuntu 12.10 AMD 64 bit. I burn a .ISO, pop it in my PC and everything runs great til I try to install it. I get a message saying "sorry Ubuntu 12.10 has experienced an internal error. So I'm scratching my head, and think well I don't have an AMD, so perhaps I should do the i836.ISO... Thinning it should run on both 32 and 64 bit systems. Well turns out I had the same issue and error message as before. So I turn to the forums, and I the one response I had said to lower my burn speed . I'm pretty sure that's not whats wrong. So my next move I do, is to download 12.04... I and burn an image, pop it in the CD drive, run the live cd, everything is great, I can surf the net and what have you, its going. I click the install button... "I get a message No Root file system defined please correct in partitioning menu." So I do, I delete everything. I want to run Ubuntu, just Ubuntu. Still wont work, same error message. I come up with this idea. I download CentOS 6. Burn the .ISO, install it with a fresh partition, deleting everything. Cent runs great. I don't need a CD, boots right off the hard drive. I can get online, and when it comes down to it, that's 75% of what I want to do 
anyways. The problem is cent is ugly. I still want my Ubuntu. So here's the deal. This is what I need to fix.  I got the a Ubuntu 12.04 disk. (it's a good disk, I'm certain). I can run the thing live no problem. Here's what happens. CD is in the drive, start the PC up, Ubuntu dose it's thing, I can "try Ubuntu" or "install it", I wanna click install, I got more then 4.5 gigs, not a problem, got an internet connection too, click continue... Here's where it gets weird. I got options back, quit, and install. I cant click anything else at this point. Obviously I want to install. Click install now, error message " no root file system is defined. Please correct this from the partitioning menu." If I can remind you when I put live Ubuntu disk 12.10 in, it says internal error. But Cent works fine. I really am appreciative of any ones help on here. I'm really don't know what to do. Thank you!

---

### Post by dino99 on 2013-02-09
when setting the partitions, / (root) needs the "boot" flag  ):P

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by Mark Phelps on 2013-02-09
When you install Ubuntu, you either have to select the option to use the entire drive (in which case, the installer will do its own partitioning), or you have to select Something Else -- in which case, you have to do your OWN partitioning.

When you select the second, you have to define a ROOT ("/") partition -- it's an option in the partitioning screen.  IF you don't do that, you will get the error message you saw.

---

