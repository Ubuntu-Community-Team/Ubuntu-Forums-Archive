---
title: "Live CD works, Installation does not"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by spatton8 on 2013-01-26
I am currently running off the live CD. I have tried twice to install to the hard drive without success. It takes a very long time to boot and gets stuck right after typing in my login password. Switching to the console, it's the same

I am trying to install over the whole hard drive

My computer is a Lenovo Ideapad Z570
CPU: Intel Core i5-2410M
GPU: Nvidia GeForce GT 520M/Intel HD Graphics 3000
RAM: DDR3
Motherboard: Intel HM65
Hard drive: Western Digital Scorpion Blue                                                                 

Any ideas? I'm thinking about trying another hard drive

---

### Post by kc1di on 2013-01-26
this problem seems to be related to the graphics card in most machines.  one way that has worked for many is to use the nomodetest kernel command when booting.  [here is a page]("http://askubuntu.com/questions/207175/what-does-nomodeset-do") that will help with that. 

and here is a[ thread]("http://ubuntuforums.org/showthread.php?t=1613132") that speaks to it also.
good Luck.

---

### Post by spatton8 on 2013-01-26
Thanks, this is very likely to be the cause. I had similar issues when I tried clean installing Windows 7.  Couldn't get the graphics driver to work but I remembered Ubuntu working on this computer before when I had it dual booted so I decided to try it again.

My problem now is that grub is also loading extremely slow and when it does I can only press enter.  Pressing e or c does nothing even after waiting 5 minutes for a response.

---

