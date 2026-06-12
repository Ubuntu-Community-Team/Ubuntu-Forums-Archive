---
title: "Problems installing Ubuntu on Philips X56"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by Hrugaar on 2006-11-03
Hi,

I am having problems installing Ubuntu on my new Philips X56 laptop, i have tried using 5.04, 6.06 and 6.10, the desktop installs, and the alternative installs(for 6.06 and 6.10). It is getting to the point of detecting network hardware but then freezing. I have checked all of the cds for defects and they are all coming back fine. On my laptop there is a physical switch which turns the wireless capability on and off, i have tried all of the installs with the switch on and off. I have also tried installing as a server install but that does not work either. Could there be a hardware compatability issue? it is an Intel core 2 duo T5600 if i remember correctly. The wireless chipset is a 3945abg(?). Any help would be much appreciated as i have no idea what to try next?

Ru

---

### Post by Hrugaar on 2006-11-04
Hi

the network hardware is:
# Ethernet: Integrated 10/100 Mbps Ethernet
# Wireless: Intel® Pro/Wireless 3945ABG (802.11a/b/g) 
im completely stuck now.

Ru

---

### Post by Hrugaar on 2006-11-04
oops my bad, i have not tried 5.10 but 5.04, i cant find a download of 5.10.
ive tried booting with lots of options(although im not sure what all of them do):
hw-detect/start_pcmcia=false
pci=noacpi
irqpoll
noapci nolapci

still getting nowhere.

any help would be great

Ru

---

### Post by Hrugaar on 2006-11-04
hmm, would i be right in thinking that 5.04 does not recognaise SATA drives? as it reports that it cannot find and partitionable media...

thanks 

Ru

---

### Post by imy30 on 2006-11-16
Hi I am having the same problem. I have a philips x56.

I turned on debugging and it fails in the same place hardware detecting.

However the error message I get is that the network interfacen address is already bound.

By the way the philips x56 specs are
      - SATA hard drive
      - Intel DUO chip

Can any one help.

---

### Post by imy30 on 2006-11-16
Hi just to let you know I found this on another thread, I think these guys/gals have fixed the problem.

[http://ubuntuforums.org/showthread.php?t=287939](http://ubuntuforums.org/showthread.php?t=287939)

---

### Post by derjames on 2006-11-21
Please see 

[http://ubuntuforums.org/showthread.php?t=287939](http://ubuntuforums.org/showthread.php?t=287939)

if you still want to run Ubuntu on the Philips X56 (under Windows XP using VMware server).

---

### Post by phenest on 2007-07-03
Hmmm. I'm using Ubuntu 7.04 Live CD, but only gets as far as the scrolling bar. I'm guessing it's having trouble with hardware. I'm going to have a go with 6.06 to see what happens.

I'm damned if I'm using Ubuntu as a virtual machine. I want to get rid of Windows. I read on another thread, installing Dapper first and upgrading. Is it possible to get Dapper, and if so, can it be upgraded to Feisty?

---

