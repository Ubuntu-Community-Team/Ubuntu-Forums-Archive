---
title: "Jaunty, 16gb SDHC card not detected."
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by frkingz on 2009-04-09
Hi,

Problem. After installing the most recent version of Jaunty 9.04 on my Dell Mini 9 my 16gb SDHC card is not detected when inserted. A 2 gb card I have works fine.

Prior to this the 16gb card and card reader worked fine with Intrepid 8.10. 16gb card still works fine in my other computers. Tried formatting it, no change.

The 9.04 install was not an upgrade. I totally wiped out hard drive and started fresh. So far I've done it twice. Still does not recognize 16gb card.

Any help appreciated. Searched for awhile online but can't seem to find an answer to this problem.

Otherwise 9.04 works great on the Dell Mini. Much improved battery life.

Thank you.

Francis K.
[email]frkingz@adelphia.net[/email]

---

### Post by ytsejam1138 on 2009-04-10
I am having the exact same problem.  Although, my 9.04 was an upgrade from 8.10.

---

### Post by ronacc on 2009-04-10
see if gparted sees it .

---

### Post by ytsejam1138 on 2009-04-10
Gparted cannot see the 2GB SDHC card or the 16GB SDHC card.  Even when the 2GB is mounted and accessible from the desktop.  Here is the what I get for the Jmicron reader after running 'lspci -vnn' in terminal:

02:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
	Subsystem: Dell Device [1028:02b0]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0100000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 88000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci


02:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381] (prog-if 01)
	Subsystem: Dell Device [1028:02b0]
	Flags: fast devsel, IRQ 16
	Memory at f0100400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

02:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
	Subsystem: Dell Device [1028:02b0]
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at f0100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>


And here is what the output looks like from [www.ubunutmini.com](www.ubunutmini.com) when they ran it on a fully functioning Dell Mini9 system:

02:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
Subsystem: Dell Device [1028:02b0]
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at f0100000 (32-bit, non-prefetchable) [size=256]
[virtual] Expansion ROM at 88000000 [disabled] [size=64K]
Capabilities:
Kernel driver in use: sdhci-pci
Kernel modules: sdhci-pci

02:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381] (prog-if 01)
Subsystem: Dell Device [1028:02b0]
Flags: fast devsel, IRQ 16
Memory at f0100400 (32-bit, non-prefetchable) [size=256]
Capabilities:
Kernel modules: sdhci-pci

02:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
Subsystem: Dell Device [1028:02b0]
Flags: bus master, fast devsel, latency 0, IRQ 7
Memory at f0100800 (32-bit, non-prefetchable) [size=256]
Capabilities:



I'm thinking the Capabilities: <access denied> line is what is causing my problems, but I'm unsure how to correct this.  

Hey, ronacc Narcoosee, is just down the road from me.  I'm live on the east side of Orlando near UCF.

---

### Post by ronacc on 2009-04-10
yes the access denied looks suspicious . Is your cardreader built in ?  I see it is on the pci bus . Hmm I just ran lspci -vnn on my sys and also got alot of "access denied"s  then I ran it with sudo and they disapeared , try it with sudo .

---

### Post by ytsejam1138 on 2009-04-10
Yes, my reader is built in and yes running lspci -vnn with sudo removes the access denied.  The reader is working, just not with a 16GB card only the 2GB card. Both worked before the upgrade.

---

### Post by ronacc on 2009-04-10
I have no Idea why it wouldn't see the 16gb card when you can see the 2gb , unless there is a bug in the driver for the card reader in jaunty , I used my external usb reader and gparted the other night to format an 8gb card to put jaunty on for my eee so if gparted don't see either card there is a definate problem , do you have a 4 or 8 gb card you could try ? anything over 2gb is sdhc , if it don't see those it might tell us something .

---

### Post by ytsejam1138 on 2009-04-11
This bug has now been confirmed:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359323)

---

### Post by klange on 2009-04-11
My 16GB SDHC card is working fine in my Mini with 2.6.28-11.38. I'll make note of this on the bug report.

---

### Post by ytsejam1138 on 2009-04-11
How do I get kernel 2.6.28-11.38 to try out?

---

### Post by ronacc on 2009-04-11
try the 2.6.29 kernel , search the forum , there is a link to the ppa for it somewhere , your problem may be with the jmicron controler , I remember a couple of releases back they had problems with jmicron and sata  . My external usb reader reads sdhc cards fine and so does my eee 701 , infact I have jaunty installed on an sdhc for my eee .

---

### Post by ytsejam1138 on 2009-04-11
I tried the 2.6.29.1 kernel and even the 2.6.30-rc1 and neither will recognize my wireless card or my my card reader with the 16GB SDHC.  I went back to an old kernel 2.6.27-7 and everything is working now.

---

