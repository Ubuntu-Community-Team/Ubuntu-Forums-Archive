---
title: "Gigabyte mobo + Jmicron + Feisty Fawn H4"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by mpan3 on 2007-02-28
Anyways, I was under the impression that 2.6.20+ kernels have the proper ICH8 and Jmicron drivers for some of the 965 chipset mobo, but I just downloaded Xubuntu FF Herd 4 (dated feb 2007), which i assume have the latest kernel.

...But still no luck installing straight from a CD.  It freezes right after the bootsplash Anyhelp please?   

My setup:

single IDE Optical drive plugged into Jmicron IDE channel (jumper position unknown)
single SATA HDD plugged into Jmicron SATA port (jumper position unknown)
Gigabyte S3 with F8 bios  (SATA mode is set to IDE, not AHCI or raid)
USB keyboard/mouse, usb storage, are set to disabled in the BIOS

Is there any other CD i should try?

---

### Post by mpan3 on 2007-03-01
anyone?

---

### Post by juice99 on 2007-03-06
ihave the same problem and i tried 6.06, 6.10 and alpha 4 or 5.

---

### Post by tommcd on 2007-03-06
You might try zenwalk: [http://zenwalk.org/](http://zenwalk.org/) The current version, 4.4.1, uses the 2.6.20 kernel. It is light and fast, and only a 400mb download. I would be interested if it would run on your motherboard.
You could try posting your question here:
[http://www.phoronix.net/forums/](http://www.phoronix.net/forums/)
Forum admin Michael is very knowledgeable about new hardware and linux, and answers many of the threads posted there. Good luck. I've been keeping an eye on ICH8/Jmicron compatibility for a while now. It seems some motherboards, like Asus p5b work, but others don't. 
Phoronix seems to be down for maintainence atm. If you can't get through try later.

---

### Post by tmak on 2007-03-26
Hi,

i also just bought the Gigabyte S3 (firmware F10 from January 2007 i think..) with 2 GB of RAM and a Core 2 Duo processor (E6400).

I didn't succeed booting the Herd 5 install cd, it always hung up after the splash with "/sbin/modprobe sbnormal exit". Then i tried to boot the alternate install cd and was able to install the system from that. Interestingly enough, i wasn't able to boot the alternate cd every time but it also hung up every now and then, in different parts of the installation.

Nevertheless, i was able to install a Feisty system now from the alternate cd. But this still needs some optimization, since the apps don't start as fast as i'm used to on my old system. Furthermore the generic kernel doesn't start up the X Server with my nvidia 7600GT drivers installed. I still have to dig into that in the next couple of days..I guess some of these problems are also simply bugs because of the beta-status of Feisty.

Maybe you can try the alternate install cd and report if you still experience problems.

EDIT: in the meantime this problem was discussed on launchpad and the nightly versions of the boot cd are supposed to fix this bug. It was indeed a problem with the drivers for the JMicron chipset. My system is running now without problems, my performance problems were "selfmade" because i forgot to install the nfs-common package for mounting my nfs shares.

Good luck,
tmak

---

