---
title: "Drive locked after installer crash"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by Lars Gottlieb on 2011-04-07
Hey experts!

I need help rescuing my machine after an unfortunate incident with what I assume is a faulty thumbdrive. It's a bit of a tale; please bear with me. 



The other day I bought a used HP 2140 netbook; which had a 1.6GHz single core Atom, 2G mem and a  tiny little harddrive. I got it home, put my ssd in it, and within an hour had a nice clean ubuntu netbook edition installed on it. 

And everything was joy, mostly, for a couple days. But Netbook edition was not as fast as expected, and I wanted to try another distribution. 

So I put Xubuntu on a new thumbdrive, and tried to install it. Some time during the file copying process, it stalled. I left it on overnight, then turned it off. 


And now we have it ...


I've tried a few distribution iso's; Ubuntu desktop, xubuntu, linux mint. Same thing every time: Installation hangs after clicking next at the screen that checks for specs, space and online status. 

I can boot from another thumb drive with little trouble, but cannot install from there either. 

I've tried running GParted, but running it from the meny leads to it crashing. Running it from the terminal still crashes; running it with 'sudo gparted /dev/sda' it runs, and from here I can do most things; I can remove and create partitions, and format to my hearts content. But trying to change flags brings up this error: 'Failed to mount "Uden Navn" The enclosing drive for the volume is locked'. When I close that popup, this comes up in the terminal: 'udevadm settle is not permittet while udev is unconfigured'

I've tried asking google for help with both those texts, without finding a solution. 
I understand that the drive could be locked somehow because of the crash. So I took it out, connected it to another machine, removed the partitions and changed to a guid partition table, and made absolutely certain that the drive had finished ejecting before disconnecting it. Nothing. 

I tried another harddrive: Nothing

I've reset and flashed the bios: Both nothing. 

I've tried updating GParted; it tells me I have the current version. 

I've let Xubuntu run thru its updating process from the thumbdrive, and even though it gives me a couple errors underway, it gets thru. But it doesn't help


I'm fresh out of ideas: Please help!

---

### Post by Lars Gottlieb on 2011-04-07
Right; Tried putting an OpenSUSE on it, in the hope that it could sort out the drive settings - and much to my surprise, it simply installed; no real problems. 

It didn't sort the drive problems, though; after, Xubuntu still flat refuses to install.

---

### Post by Lars Gottlieb on 2011-04-07
Still trying to get Xubuntu on the machine, I tried various versions of Linux Mint. And lo and behold - Linux Mint hopped in with no trouble at all; and I could run GParted from that installer.

Is there a way to roll the GParted from the Linux Mint usb to the Xubuntu one? And would that fix my problem? I have the feeling it Might, but ..

---

