---
title: "Ubuntu 12.04.2 on Thinkpad T430 anyone?"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by t430 on 2013-03-18
Hi,

I recently bought a Thinkpad T430. Planning to move to a good, stable Linux. 

Has anyone installed 12.04.2 on T430 ? 

Hows the heat and battery life with it?

My primary goal is to have a good stable Linux system as a base OS on which I can install other stuff like VMWare (And inside it I will try out other OSes).

As mentioned before, battery life is important to me (With the preloaded Win Pro 7 I get about 5 hours). How will it be with 12.04.2 ? 

What about the heat? I want to try Linux without frying my laptop.

Hope I am not asking too much, but will the backlight keyboard work as well?

Anyone currently using it on a T430?

Please let me know.

---

### Post by Mr. Shannon on 2013-03-18
I can't say for certain since I have the T530 (a larger version of the T430), but it should work just fine. I run Linux Mint 13 on mine (which is a derivative of 12.04).

I have the largest battery and the time reads a little over 5 hours. I have not done a test to see if this is accurate but I would say that is about right. It may lean a little towards 4 hours. However, my T530 has a i7 quad mobile processor pulling that down. I have not really used my Windows partition for very long so I have no idea how long my battery lasts on Windows.

Linux "usually" won't fry your laptop. The reason for the "usually" is my previous laptop ran really hot under Linux. My HDD would exceed 50C and the processor would run at over 90C. However, if I remember correctly, it also ran pretty hot under windows Vista.  I think Lenovo had to replace the fan last time it was sent in so that could have been part of the problem.  In contrast, my T530 runs cool to slightly warm most of the time. For example, right now my HDD is at 37C and the CPU at around 40C-50C.

Yes the keyboard backlight works just fine on my T530. Also, the webcam and volume and screen brightness buttons, and lid close detection work as well.

What you need to be cautious of is if you got your laptop with the Optimus NVIDIA card.  If so, you will need to either turn it off in the BIOS and never use it, or use [http://bumblebee-project.org/](http://bumblebee-project.org/) as NVIDIA does not yet support Optimus under Linux.  I got it working on my laptop with only minor tinkering, but others have had less success.

---

### Post by t430 on 2013-03-19
Hi Mr. Shannon,

Thank you sir for such a detailed reply.

Thing is I am planning to dual boot. But as of now, the whole disk is allocated to Win 7.

Will try to find out some ways to may be shrink the Win 7 Partition and install Ubuntu 12.04 in the free space...

---

### Post by t430 on 2013-03-20
Hi,

I was able to successfully install Ubuntu 12.04.2 on my T430. Thank you very much.

Battery time is about the same as on Windows.

Followed an article on google - [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/) and was able to successfully dual boot :)

Currently downloading updates. 

I am more familiar with Fedora and this is my first tryst with Ubuntu. Hoping it will turn out to be good. 

The Webcam, Back light works, suspend also works correctly after closing the laptop lid.

---

