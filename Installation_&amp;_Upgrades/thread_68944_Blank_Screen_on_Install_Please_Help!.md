---
title: "Blank Screen on Install? Please Help!"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by nihila on 2005-09-24
Hi, I am installing Ubuntu on a brand new Dell Inspiron 9300. When I first bought this machine, I set Ubuntu 5.04 up without any problem. Unfortunately, an unrelated problem forced me to wipe my hard drive and reinstall everything.

For some reason, I am no longer able to install Ubuntu. When I boot off of the CD, I get to the screen that prompts for expert of standard install - once I press enter, a lot of text whizzes by and then my screen goes black - immediately following a mention of a "daemon" or something to do with "buffer".

I've tried installing both Ubuntu 5.04 and 5.10 without success. Also, I can no longer get the live cd to work on my system. I've even tried reformatting my machine and installing from scratch.

Can anyone suggest anything that I might try??? Thanks!

---

### Post by fordfan753 on 2005-09-24
Try flashing and upgrading the BIOS, if it installed before there is no reason why it shouldn't now...

---

### Post by nihila on 2005-09-24
Thanks for the speedy reply!

I flashed my BIOS, but I am pretty sure that I already had the most current upgrade (A04 6/29/2005). At any rate, it didn't help - I am still getting the same blank screen.

However, I did find a forum thread that seems to be about this same problem - [http://ubuntuforums.org/archive/index.php/t-6835.html](http://ubuntuforums.org/archive/index.php/t-6835.html). 

The poster says that the lines immediately before the hang are:

> Starting system log daemon: syslogd, klogd.
Trying to enable the frame buffer...


I'm pretty sure that's what I'm running too. But he seemed to resolve his problem by typing "linux debian-installer/probe/usb=false" or "acpi=off" at the install screen. Neither of those commands seemed to do anything for me :(

PS - This person may also have had the same problem - [http://www.ubuntuforums.org/showthread.php?t=64400](http://www.ubuntuforums.org/showthread.php?t=64400) . I've tried "noapic" and "noapic nolapic" without any luck.

---

### Post by nihila on 2005-09-25
Is there some way to install Ubuntu directly from my C drive? Might that circumvent the issue?

---

### Post by nihila on 2005-09-26
I'm posting this in case anyone else has the same problem and wants to know how I resolved it. 

I found info on the Inspiron 9300 here - [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron9300](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron9300).

The problem is resolved by netbooting with "linux vga=771" at the prompt.

See the info on netbooting at [https://wiki.ubuntu.com/Installation/WindowsServerNetboot](https://wiki.ubuntu.com/Installation/WindowsServerNetboot)

---

