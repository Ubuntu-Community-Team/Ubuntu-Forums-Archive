---
title: "Problem after update to kernel 5.4.0.62 in 20.04"
date: 2021-01-15
forum: Installation &amp; Upgrades
---

### Post by srope01 on 2021-01-15
I usually use Software Updater to get the latest updates. Recently there was a kernel update (to 5.4.0.62) which caused a strange problem after reboot and login. I get the following message as soon as I login:
```
Unable to lock 
Lock was blocked by an application.
```
The laptop then immediately goes into sleep mode. The message and sleep mode happens every time I login.

As I do system backups regularly, I have managed to go back to the version just before the kernel update so I am ok at the moment. However, I'd like to get this debugged so that I can move forward with the updates. Does anyone know what I should do?

---

### Post by ajgreeny on 2021-01-15
At the login screen use Ctrl+Alt+F4 to get to a command line and see if you can login there.
I am running the 5.4.0-62 kernel without a problem so this may relate to your hardware; please let us know what hardware you have in as much detail as you can.
From command line you could run command ***inxi -Fzx*** and tell us what it says as much as possible, though I realise that you will not be able to easily copy that output and post it back here.

---

### Post by srope01 on 2021-01-15
It looks like this problem has solved itself or perhaps it has gone into hiding. Starting from the backup version previous to the latest kernel, I decided to update one package at a time to find out which package was causing the lock problem. With some trial-and-error and several attempts in changing the order of installing packages, I managed to get 5.4.0-62 installed.

The appearance of this hardware problem remains a mystery, but I will change the status to Solved. Apologies for the bother.

---

### Post by bcschmerker on 2021-01-19
**What class of CPU does your laptop run?**  I'd run into a hardware problem on the currently-down Hot Rod gPC under 16.04.3-LTS Trusty, viz., random program crashes, and eventually traced it to the CPU - the original-build Advance Micro Devices® Athlon 64® X2 5600+ blew out its memory manager; the "downgrade" AMD Athlon 64® 3500+ ran stably through 20.04.1-LTS Focal until the GIGABYTE® GA-MA78GM-S2HP would no longer recognize an i8042 keyboard after 15 January 2021.

---

