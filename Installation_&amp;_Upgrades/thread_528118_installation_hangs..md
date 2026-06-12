---
title: "installation hangs."
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by chekha on 2007-08-17
hi,

when i try to install unbuntu, it seems to hang forever at 91 %.
i tried to install two times with the same results.

it hangs at the message:
> [I][B]Detecting hardware, please wait.
Loading module 'aec62xxx' for 'IDE chipset support'.[/B][/I]

can someone help me? :confused:

my PC specs:
> Asus A7N8X-X nForce2 400/MCP (5 PCI, 1 AGP Pro, 3 DIMM) 
AMD Athlon XP1800+ 1.53 GHz 266 MHz bus (Thoroughbred) 
DDR-DIMM PC3200 512MB DDR CL2.5 184-P (DDR-PC400MHz)
DDR-DIMM PC3200 512MB DDR CL2.5 184-P (DDR-PC400MHz)
Creative Audigy Platinum eX (with Firewire) (PCI)
Asus V7100 PRO nVidia GeForce2 MX-400 32MB (AGP, SDR) 
NEC DVD-Writer ND-3550 IDE Black OEM DVD+R/+RW/DVD-R/-RW (Dual layer)
Sony RW CRX225E 52x-24x-52x CD-writer 
HighPoint RocketRAID 100 2P ATA100 

---

### Post by lgambett on 2007-08-17
While installation is hanging at 91 % try to press Ctrl+Alt+F1. This will open a virtual terminal session; probably in this session you will see messages explaining what is going on. Anyway it is pretty normal for the installation to "stop" for 10-15 minutes near the end, at 91 % - 93 %.
One question; are you installing from the Live CD or from the alternate CD ? The alternate one is better in order to solve installation problems.

---

### Post by lgambett on 2007-08-17
Sorry, seems I have found the solution **here**
[https://answers.launchpad.net/ubuntu/+question/10952](https://answers.launchpad.net/ubuntu/+question/10952)

---

### Post by chekha on 2007-08-17
hello!
thank you for the fast reply.
i tried that out. but it did not help me.

i am installing ubuntu using: ubuntu-7.04-desktop-i386.iso (livecd).
the md5 hash is correct.

i tried "Start Ubuntu in safe graphics mode", but got the same result (hangs at 91%).

then i press ctrl+alt+f1, i get this:
[[IMG]http://img293.imageshack.us/img293/8678/dsc01210resizevq4.th.jpg[/IMG]](http://img293.imageshack.us/my.php?image=dsc01210resizevq4.jpg)

dont know what to do now... :(:confused:

---

### Post by chekha on 2007-08-17
and where do i get the alternate cd? :confused:

---

### Post by merlinus on 2007-08-17
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by chekha on 2007-08-18
hi.
i tried to install from that alternate cd.
md5 hash is correct.

but it still hangs at :

> ***Starting System log daemon: syslogd, Klogd***

have waited for about 30 minutes. :confused:
should i suppose to write some commands or?

---

### Post by chekha on 2007-08-19
i tried once again to choose "install in text mode" from the alternate cd.

this time it hangs for over 1 + 1/2 hours at this point:
[[IMG]http://img502.imageshack.us/img502/5361/dsc01214resizegv6.th.jpg[/IMG]](http://img502.imageshack.us/my.php?image=dsc01214resizegv6.jpg)

why is it so difficult to install it? :confused: :(

---

### Post by chekha on 2007-08-22
anyone? :confused::(

---

