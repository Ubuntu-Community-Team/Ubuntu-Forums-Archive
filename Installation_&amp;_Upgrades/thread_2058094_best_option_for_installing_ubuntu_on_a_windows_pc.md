---
title: "best option for installing ubuntu on a windows pc"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by DeezyFaReal on 2012-09-14
What is the best option for running Ubuntu and Windows 7 on an used Desktop? It already has Windows 7 on it.

== Install Ubuntu with wubi.exe
== Ubuntu on live a USB
== Ubuntu in a virtual box
== Dual boot
== Windows 7 in a virtual box

Specs:
Dell ultra small form factor, 2 GB memory, Intel Pentium, 75 GB HDD, Windows Vista era

Things to consider:
This is my old desktop computer that I don't spend much time on, so I want to keep things low maintenance on the Ubuntu side. Is Ubuntu on a live usb the best option? Say maybe Ubuntu 10.04.4 on a 4 GB flash drive with only security updates.

---

### Post by critin on 2012-09-14
Virtual machine, (vmware is easy)  is the safest and easiest if you haven't run ubuntu before.  You can open it from your Windows desktop, so there's no need to mess with booting and possibly corrupting both OS's.  

After you learn more about ubuntu, you will want to install side-by-side, but give it some time first.  (Wubi or partition install.)

With Live usb , any changes you do or adding anything will not be saved when you remove the usb, unless you install it and make it persistent.

Wubi is good, but read up on it.
Dual boot when you're sure you want the version you're running.

---

### Post by Bucky Ball on 2012-09-14
*Moved to **Installation & Upgrades ***

... but a toss up with 'Recurring Discussions'. A lot depends on what you want to do with the machine and your machine specs. If you have 512kbs of RAM you could pretty much forget a VM. Wubi for trying it out, not a long term solution. If you mostly use Windows and are intending Ubuntu to be a drop-in replacement to use Windows apps, dual-boot or don't bother with Ubuntu. 

I'd decide what it is you require from the Win and Ubuntu installs and take it from there. Good luck. ;)

---

### Post by jerrrys on 2012-09-15
Whatever you decide, but 10.04 is on its way out (End of Life April 2013).  You may want to go with [Ubuntu 12.04]("http://www.ubuntu.com/download/desktop") and if your old box isn't up to the task; [Xubuntu]("http://xubuntu.org/getxubuntu/").

---

### Post by DeezyFaReal on 2012-09-15
I appreciate the input. I will have to go with a virtual machine. I like virtualbox, but I'll try out vmware if it's "safer and easier". I'm just going with this option because I don't want to mess up Windows and I know with a virtual machine I can back ubuntu up as a virtual disk image and install it again on another PC or the same machine any time.
Thanks!

---

