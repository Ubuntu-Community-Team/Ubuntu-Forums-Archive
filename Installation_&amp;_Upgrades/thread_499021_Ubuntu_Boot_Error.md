---
title: "Ubuntu Boot Error"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by D0P3F15H on 2007-07-12
Im brand new at Linux, installing it because i got sick of my windows corrupting itself and therefore Ubuntu was the first choice.

First I tried the Live CD but being an extremely old system (900MHz Celeron, 160MB RAM) it didnt work. So I downloaded the Alternate CD and installed again partitioning my 160GB HDD into 20GB for the OS and 10GB swap space leaving 130GB free.

About 80-90% into the main installation it had an error and put me back at the install menu so I just went back into the main installation where it picked up from where it left off and finished. At reboot Grub Boot Manager  had 'Error 17' and the pc wont boot any further. I tried reinstalling with the same results and the CD says that its okay.

Any ideas?

---

### Post by gizmoarena on 2007-07-12
Your CD might be corrupted. Get another copy of it.
If you want to recover your windows boot up. use your windows XP cd (I'm guessing you use XP)
boot the CD, goto recovery console, type "fixmbr". your windows boot will be fixed.

now download the alternate cd again. and try to install ubuntu :D

---

### Post by merlinus on 2007-07-12
You do not have enough RAM to run ubuntu.  Try the xubuntu alternate install cd.

Or buy more RAM....

-merlin

---

### Post by gizmoarena on 2007-07-12
and I forgot to tell you. you dont need 10GB partition for SWAP space. For your computer 300MB would be more than enough.

yes, merlinus is right, try xubuntu instead.

@merlinus: with alternate CD, he's supposed to be able to use ubuntu on slower computers, right?

---

### Post by merlinus on 2007-07-12
The alternate install cd needs less memory (RAM) for installation.  It also bypasses potential video problems since it is text-based.

The system requirements are available on the various ubuntu websites.  xubuntu is the least resource-intensive version.

Here are its requirements:

To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only required you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").
 To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.


-merlin

---

### Post by D0P3F15H on 2007-07-12
Thanks, ill download Xubuntu tonight and see how that runs. Id get more RAM but its the oldschool SD stuff which is really hard to find

---

### Post by gizmoarena on 2007-07-12
> **merlinus said:**
> The alternate install cd needs less memory (RAM) for installation.  It also bypasses potential video problems since it is text-based.
-merlin

I didn't knew that. thanks :)

---

