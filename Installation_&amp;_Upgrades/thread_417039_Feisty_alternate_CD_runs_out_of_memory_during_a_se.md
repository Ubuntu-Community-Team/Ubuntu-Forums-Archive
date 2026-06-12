---
title: "Feisty alternate CD runs out of memory during a server install"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by dobuntu on 2007-04-21
Hi,

I'm trying to do a server install of ubuntu 7.04 using the alternate CD on my old machine. My goal is to install a lightweight desktop using fluxbox or openbox.

The install process goes on until the partition editor is about to start, after the successful configuration of the network. At this time I get a blank screen with the "Killed" message. Switching to the console output with Alt+F4, I see a message like this:

**Out of memory: killed process** (frontend) [rescheduled].

Processes get killed on and on, and the partition editor never comes up.
Looking at the console, I also see that the 

My computer is an old Pentium 90MHz with 80Mb of RAM and a 4GB HD (no boot from CD but I made it with a SmartBootManager floppy - thank you guys on the wiki).

I had installed xubuntu before on this machine, although I had some trouble in making X work (DRI not supported) and setting up my RS-232 mouse (no USB, no PS/2), but finally I got it working (although slowly).

Note: this is my very first post in my very first forum although I'm not a kid (44yo) and I've been using  computers since 1982.

Thank you all for reading!

---

### Post by heimo on 2007-04-21
I think 80MB is just not enough - even if you could get Xubuntu installed, it might not run well enough to be usable. I'd try DSL or Debian (very flexible distribution), or searching something for older computers in Distrowatch.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://www.debian.org/](http://www.debian.org/)
[http://distrowatch.com/](http://distrowatch.com/)
> 
Note: this is my very first post in my very first forum although I'm not a kid (44yo) and I've been using  computers since 1982.
That's three years more computers than I've done. :) Started -85, Linux based operating systems for last eleven years. Windows from early 90's. We're not old, we're experienced. ;D

---

### Post by dobuntu on 2007-04-21
Hi, "experienced" heimo,
thank you for your reply.

80Mb should be enough to run a lightweight window manager, it is reported to run in 64Mb or less.
But I get a hang during a server install (no GUI to be installed!).

Before installing xubuntu (6.10, I forgot mentioning the working ubuntu version), I installed DSL but it's essentially a live CD and although it can be installed on the HD it is not a true installation (e.g. no upgrade method is supported).

I'm also looking for a way to make my existing swap partition used by the installer, so not to get memory errors anymore. Is there anybody who knows how this can be done?

---

### Post by heimo on 2007-04-21
> **dobuntu said:**
> 
80Mb should be enough to run a lightweight window manager, it is reported to run in 64Mb or less.

I remember my whole Debian installation being under 100MB (kind of thin X client), so yes, definitely possible. And just for fun, I just tried running my virtual mail server (Feisty) with 48Mb and then 32MB of RAM. 48 boots up, 32 doesn't.

I remember some threads from these forums couple releases ago, where it was instructed to enable swap partition early on the installation process. As you may know, you can change to virtual console during install and run commands like "swapon /dev/whatever".

Thumbs up for trying to install on original Pentium. :) I could send you couple memory sticks, I'm sure I've couple DIMMs nearby. :D

---

### Post by dobuntu on 2007-04-21
> **heimo said:**
> Thumbs up for trying to install on original Pentium. :) I could send you couple memory sticks, I'm sure I've couple DIMMs nearby. :D

This is very kind from you, but my PC only supports SIMMs. ;) 

> **heimo said:**
> I remember some threads from these forums couple releases ago, where it was instructed to enable swap partition early on the installation process. As you may know, you can change to virtual console during install and run commands like "swapon /dev/whatever".

I've read some posts which suggested activating a swap from a menu coming up during a "server-expert" install mode, but it seems to be no more available in Feisty.

I didn't try the virtual console, but I'm afraid it will not be available before the install error (text-mode install, before partitioning). I'm gonna see it anyway, thank you :)

(I would like to emphasize that it is a server install - no GUI installed - only a command line system - and it runs out of memory before partitioning the HD. The help on the boot screen of the alternate CD says it requires 32Mb of RAM for using this ubuntu installer -- and I have more than double.)

---

### Post by dobuntu on 2007-04-21
Hi, heimo, I did it! :guitar: 

> **heimo said:**
> I remember some threads from these forums couple releases ago, where it was instructed to enable swap partition early on the installation process. As you may know, you can change to virtual console during install and run commands like "swapon /dev/whatever".

Thumbs up for trying to install on original Pentium. :) 

During the hardware detection stage, I've accessed the virtual console with Alt+F2 and I got a BusyBox console, saying "type help for a list of built-in commands":

I've typed, but no "swapon" command listed, nor "free", nor "df", nor many other essential tools. At first I was discouraged, but the commands where there, although not listed

 I typed "free" and I saw zero swap space available. Then I did "swapon /dev/hda2", but got an error: "could not stat /dev/hda2: no such file or directory". In the meanwhile, the hw-detection phase had finished, so I retyped the swapon command, and it succeeded! :) Then I typed "free" and I saw the swap partition available! :cool: 

The install process this time brought up the partition editor, no more memory faults!
It's still running...

I will let you know if it will terminate successfully.

Many thanks for your tip and for having incouraged me to install ubuntu on my old Pentium.

Ciao,
dom

---

### Post by heimo on 2007-04-21
> **dobuntu said:**
> 
I will let you know if it will terminate successfully.

Many thanks for your tip and for having incouraged me to install ubuntu on my old Pentium.


Excellent! :) I hope it goes well, let us know.

---

