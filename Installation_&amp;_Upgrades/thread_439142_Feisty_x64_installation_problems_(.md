---
title: "Feisty x64 installation problems :("
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by ninjapig on 2007-05-10
Hi guys,

I'm a still a newbie to the linux and ubuntu movement.

My hardware is a Dell E521. 

An amd x2 3800+. 

I have installed the feisty i386 version easily with no problems. But when i come to the 64 bit version i'm having problems. I did some research and found that hitting f6 and changing "quiet splash" to "noapic "works for a lot of people. But for me unfortunately after typing 'noaipc' , i get errors like

SQUASHFS Errors
Buffer I/O Error

and things like logical block 28934



if anyone could help me out in this area, i would be extremely thankful.

---

### Post by SigmundL on 2007-05-10
Got it working by adding 'vga=792' to the end of the line in menu.lst

/Z

---

