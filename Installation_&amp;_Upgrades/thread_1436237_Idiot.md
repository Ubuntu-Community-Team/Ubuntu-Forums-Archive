---
title: "Idiot"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by steven_horn on 2010-03-22
Let me start by saying I know nothing about Linux. However, I had a brain fart and bid on one of these Hong Kong brand 7" netbooks that came loaded with WinCE 5.0. This thing is just TERRIBLE! I've been told that it would probably run substantially faster if it were loaded with Linux instead. I researched and it appears that the Xubuntu is the best choice. I cannot use the bootable thumb drive because this thing doesn't even have a bios. It is an [SIZE=2][FONT=Verdana]**[COLOR=#ffffff][FONT=Arial][COLOR=#000000][FONT=Arial][FONT=Arial][FONT=Times New Roman][COLOR=#000000][COLOR=#ffffff][COLOR=blue][FONT=Constantia][FONT=Verdana][COLOR=#ffffff][COLOR=#000000][COLOR=blue][FONT=Constantia][COLOR=#ffffff][COLOR=#ffffff][FONT=Arial][COLOR=#000000]*ARM926-AKCHIP*[/COLOR][/FONT][/COLOR][/COLOR][/FONT][/COLOR][/COLOR][/COLOR][/FONT][/FONT][/COLOR][/COLOR][/COLOR][/FONT][/FONT][/FONT][/COLOR][/FONT][/COLOR]**[/FONT][FONT=Verdana]**[COLOR=#ffffff][FONT=Arial][COLOR=#000000][FONT=Arial][FONT=Arial][FONT=Times New Roman][COLOR=#000000][COLOR=#ffffff][COLOR=blue][FONT=Constantia][FONT=Verdana][COLOR=#ffffff][COLOR=#000000][COLOR=blue][FONT=Constantia][FONT=Arial][COLOR=#000000][COLOR=#ffffff][COLOR=blue][FONT=Constantia][COLOR=blue][FONT=Constantia][FONT=Arial][COLOR=#000000]CPU[/COLOR][/FONT][/FONT][/COLOR][/FONT][/COLOR][/COLOR][/COLOR][/FONT][/FONT][/COLOR][/COLOR][/COLOR][/FONT][/FONT][/COLOR][/COLOR][/COLOR][/FONT][/FONT][/FONT][/COLOR][/FONT][/COLOR]**[/FONT][/SIZE], 2gb NAND Falsh Hard drive, and 128mb DRAM. Can anyone tell me if it is possible to load linux on this thing, and if so, point me to the appropriate instructions on installation of the OS and drivers?

---

### Post by 2hot6ft2 on 2010-03-22
You might try Lubuntu. I installed it last night to play around with and it's very light and snappy.
[http://lubuntu.net/](http://lubuntu.net/)
The beta 1 for lubuntu 10.04 seems very stable. Here's a thread you may be interested in:
[Put in list from lightest to heaviest: ubuntu, xubuntu, lubuntu, and jolicloud]("http://ubuntuforums.org/showthread.php?t=1427709")

For more info and system requirements
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
> A Pentium II or Celeron system with 128 Mb RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. It should be possible to install and run Lubuntu with less memory, but the result will likely not be suitable for practical use.

There are other distros like Tiny Linux which I'm sure others can tell you more about.

EDIT: I just looked and Lubuntu is using 1.74 GB of space so you may want something even smaller.

---

### Post by pricetech on 2010-03-22
There's always Puppy and Damn Small Linux.

You don't say how you plan to install though.  I take it you have no boot options at POST ???

---

### Post by steven_horn on 2010-03-22
That is correct, there are no boot options. There is an update screen at bootup, but nothing that takes you to a bios where you can set the boot device priority. 
 
When I say I know nothing about Linux, I literally mean nothing. What I want to do is completely do away with WinCE and load linux as the primary and only OS. After reading and reading and reading, I believe this is called a debian install (install to the hard drive)? Damn Samll Linux did sound like the most viable option for this, I dare call it a netbook, cell phone with a full size keyboard. It says you can install Damn Small Linux to the hard drive, but I have not been able to find the instructions to do so, or how to install all of the drivers once the OS is installed.

---

### Post by lykwydchykyn on 2010-03-22
I saw these and almost bought one, but I did a search first to see what the prospects of loading Linux on the thing were.

Glad I did.  Apparently there is work in progress to get a Linux running on these, and potentially there are distros out there that work; but it's not straightforward.

And before anyone else suggests the usual litany of "low-spec computer" distros, these netbooks use ARM chips, which is a totally different cpu architecture from x86/x86_64.  This means that the vast majority of desktop Linux distros will not run on them.

Have a read through this thread for more detailed information:

[http://ubuntuforums.org/showthread.php?t=1349626](http://ubuntuforums.org/showthread.php?t=1349626)

---

### Post by lisati on 2010-03-22
I'm not familiar with the model mentioned by the OP. As I was reading through this thread, the term "embedded system" came to mind. If this is the case, it could be problematical (but not necessarily impossible) to install a Linux system.

---

### Post by snowpine on 2010-03-22
Buyer beware. There is a zero percent chance you will have a satisfying X/L/Ubuntu experience on that **toy** that looks kind of like a computer. The Windows CE operating system is flashed to ROM and cannot be replaced with Linux (at least not by anyone without an engineering degree and substantial experience with embedded systems). :(

---

