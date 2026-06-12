---
title: "Ubuntu freezes before the install begins T.T"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by dummy1234 on 2007-09-06
I'm new to the Linux OS, and it's the first time I install it on my PC. I Want to make it a dual-boot with Windows XP Media Center so I could still use the old software until I get used to Linux. My problem is:  (Ubuntu 7.04)  after I press "Install/Start Ubuntu", the loading screen freezes even before starting the installation. I really need some help and I've tried to look on the internet and help files, but I didn't find anything. And in the IRC help channel, I didn't even get any suggestions. If someone can help me, I'll be really grateful. My system specifications are:
Motherboard: ASRock 775i65GV
CPU: Intel Celeron (2,53gHz)
VGA: Gigabyte ATI Radeon 9200 AGP (128mb, pixel shader - 1.4, vertex shader - 1.1, TV out, ViVo) (I also have an on-board VGA card - Intel extreme graphics 32mb)
Sound: C-Media (on board)
RAM: 1024mb DDR
HDD: Maxtor 40gb + Seagate 160gb (both not SATA)
CDVD: LG Dual Layer DVD-RW 16x24x16
Floppy: IBM standard floppy
Keyblard: Compaq standard keyboard (no multimedia functions or buttons)
Mouse: Genius PS2 laser mouse
Monitor: Compaq S720 color Monitor
USB1: Hercules Deluxe Web Cam
USB2: Trust T1400 Wireless Tablet
USB3: All in one memory-card reader

P.S.
Partition settings - Maxtor HDD -> Windows XP (all 40gb. file system = fat32). Seagate HDD -> data (downloads, games etc.) 114gb (file system = fat32), Linux 10gb (file system = ext3), Linux (don't know why it made it in 2 instead of 1) 20gb (file system = ext3), Linux SWAP 500mb

if you want to contact me personally, I use MSN: [email]devianart.dummy1234@hotmail.com[/email] or Skype: dummy1234. Thanks to everyone who try (or succeed) to help me.

---

### Post by merlinus on 2007-09-06
Video card problem.

You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

Once installed, you can change the driver to vesa from a command line to get to a gui, where you can search for and install the correct drivers.

-merlin

---

### Post by dummy1234 on 2007-09-06
> **merlinus said:**
> Video card problem.

You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

Once installed, you can change the driver to vesa from a command line to get to a gui, where you can search for and install the correct drivers.

-merlin

well, I'm a newbie to the Linux based system, and the "text-based" installation is not included in the book I'm following =/ is there any other way?

---

### Post by merlinus on 2007-09-06
You can try removing your ATI card.

-merlin

---

### Post by dummy1234 on 2007-09-06
> **merlinus said:**
> You can try removing your ATI card.

-merlin

and if I just use the on-board one, will it work? (but I'll need to use my ATI card eventually)

---

### Post by merlinus on 2007-09-06
Give it a try.  As I said earlier, once ubuntu is up-and-running you can search for and install the ATI drivers.

-merlin

---

### Post by dummy1234 on 2007-09-06
> **merlinus said:**
> Give it a try.  As I said earlier, once ubuntu is up-and-running you can search for and install the ATI drivers.

-merlin

Thanks you so much! That really worked perfectly! I've posted my problem all over the net and only you gave me a solution! Thanks, I really appreciate it!

---

### Post by merlinus on 2007-09-06
Great news!  Glad I could help.

-merlin

---

