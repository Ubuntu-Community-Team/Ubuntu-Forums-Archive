---
title: "I am BEGGING to the developers of Ubuntu!!!!!!!!"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by el3ktro on 2006-10-17
Please please please some developer of Ubuntu read this. A single, simple config option in the kernel prevents Ubuntu from even installing on my machine. It's not something exotic, it's an Intel Centrino based machine. It's an Averatec 2460, Intel 945GM chipset, Intel GMA 950 graphics, RealTek RTL8139 network adaptor.

There's ONE SINGLE kernel config option preventing Ubuntu from running or even from being installed on my system, the kernel option is

8139TOO_PIO

This kernel module hard crashes the system. I've now installed Gentoo with a custom kernel where this option is not set and it works PERFECTLY - but damn I want my loved Ubuntu back!!

Come one guys, one such single option prevents the owners of a whole hardware series from installing Ubuntu and NO ONE listens - I've filed so many bug reports, posted to this forum so often and I never even got an answer - am I the only one using Centrino hardware with this network adaptor???

Can please SOMEONE of you Ubuntu developers at least confirm this bug, at least give a sign of live, write me if this can be fixed and if not, why it can't be fixed. I just at least want an answer please!!

Sincerely
Tom[RIGHT][/RIGHT]

---

### Post by MetalMusicAddict on 2006-10-17
Ubuntu developers dont hang out here.

---

### Post by Kateikyoushi on 2006-10-17
Unfortunately the devs aren't active on the forum, but there are initatives to inform them about matters of importance.
Contact your local forum ambassador. [LINK]("http://ubuntuforums.org/showthread.php?t=278375")

---

### Post by skymt on 2006-10-17
You can't just blacklist (/etc/modprobe.d/blacklist) the module? Or does the install CD hard-crash?

---

### Post by bettlebrox on 2006-10-17
Try opening a bug report:

[https://launchpad.net/distros/ubuntu/+bugs]("https://launchpad.net/distros/ubuntu/+bugs")

---

### Post by AgenT on 2006-10-17
As a tip: begging will not help you solve the problem. You need to file a bug report in launchpad (or contribute to an already open bug). You need to be brief and helpful (stating what causes the issue and possible ways of fixing it). And as others have pointed out, no developer reads the forums (that would be wasted time on their part). And a topic title like you chose is very poor and would result in getting dismissing your bug by most (or at least a demand to change it - delaying fixing the bug).

The very first thing you should do is SEARCH. Search this forum for answers and then search [launchpad]("https://launchpad.net/distros/ubuntu/+bugs") for a bug that already discusses this problem.

As someone pointed out, if your problem is booting your computer, then blacklist the module. If it is with the LiveCD, then either try passing a kernel option to disable the loading of this module or install using a minimum CD and/or doing a custom boot. If this does not work, then just do a [network install]("http://www.ubuntuforums.org/showthread.php?t=276532"). No need to boot a CD. There are a lot more options available for you, but they tend to require more Linux skills (ex. using any Debian based LiveCD that works, like Knoppix, and using chroot).

---

### Post by jazzfan on 2006-10-22
Hello,
I just bought the same laptop, so the same problem...
The install hangs/freeze at the ethernet driver load like explain the author of the thread.
How is it possible to bypass the realtek 8139 to be load at the installation ?
Thanks
Stephane

---

### Post by az on 2006-10-22
I wonder if you can dissable the ethernet card in your bios before you install?

I also wonder if there is an option you can use before youo boot.  Try the F keys at the bottom of the screen when you boot.  There are some funky parameters there for you to play with.

---

### Post by gn2 on 2006-10-22
Maybe just try different Distros, till you find one that works?

PCLinuxOS maybe?

I've found it to be more advanced than Ubuntu.

---

### Post by Kulgan on 2006-10-22
> Maybe just try different Distros, till you find one that works?

PCLinuxOS maybe?

I've found it to be more advanced than Ubuntu.

IMO, PCLinuxOS is a vista that works worse, though quicker, than vista. And it didn't get my hardware right. If you can't get ubuntu right, try [mepis]("http://www.mepis.org/") or [sabayon]("http://www.sabayonlinux.org/") - at least for me they worked fine. (Almost as well as ubuntu :P )

-K

---

### Post by jazzfan on 2006-10-22
Hello,
Thanks for your ideas.
But :
1) no ethernet disabling option in bios
2) other distro : i try Mandriva Live, Knoppix 5.0 and they  freeze too at the network step.
3) F options . I think you are talking about the F3/4/5/6 options. I try lot of them : noacpi, nolapic, pci=bios, irqpoll but none was able to prevent the freeze.
other ideas are welcome ;) 
Stephane

---

### Post by jazzfan on 2006-10-22
Hello,
Thanks for your ideas.
But :
1) no ethernet disabling option in bios
2) other distro : i try Mandriva Live, Knoppix 5.0 and they freeze too at the network step.
3) F options . I think you are talking about the F3/4/5/6 options. I try lot of them : noacpi, nolapic, pci=bios, irqpoll but none was able to prevent the freeze.
other ideas are welcome ;) 
Stephane

---

