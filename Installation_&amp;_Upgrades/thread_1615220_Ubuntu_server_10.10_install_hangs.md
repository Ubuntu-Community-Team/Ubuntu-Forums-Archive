---
title: "Ubuntu server 10.10 install hangs"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by faisalsadaf on 2010-11-06
I am trying to install Ubuntu server 10.10 (AMD64) on my new custom built machine (specs below). I boot with the Ubuntu server CD, select advanced options remove quiet mode install, and 

Here's what happens:
0 - On the machine, I currently have Ubuntu desktop 10.10 installed.
1 - Boot machine with Ubuntu server CD
2 - select english language
3 - F6 to select Expert mode, backspace the quiet parameter from the command line
4 - System starts to recognize hardware, and stops at the following line:
    >  [   4.334453] scsi 2:0:0:0 CD-ROM      LITE-ON DVDRW  SHW-160P6S PS09 PQ: 0 ANSI: 5At this point, the machine just sits at this last message, and does not do anything.

I was able to install Ubuntu desktop on this system just fine, and just wanted to get rid of the desktop and install the server.

Any suggestions on what to do? 

I didn't think that I needed to remove the existing partitions before I install the server. Correct me if mistaken.

I'm not a professional Linux practitioner. Hoping to get some help here to get this going. Thanks for helping me out!

> Machine Specs
ASUS Motherboard M4A88TD-V EVO/USB3
AMD Phenom II X6 1055T Processor (hex core, 3248 MHz)
Installed Memory: 8192 MB
Boot Hard Drive: 160GB
500W Power Supply


---

### Post by faisalsadaf on 2010-11-09
To add to my thread;

- Ran MD5 checksum against the ISO that I downloaded. It checks out.
- When I check CD for errors, the same screen, nothing but a white horizontal cursor '-' appears on the top left corner of the screen.
- Have burned two CD's from the same ISO, with same exact outcome.
- So I also burned a bootable USB (using Universal USB installer), and exactly the same issue.

I really need to get going. Any suggestions??

---

### Post by strayhud on 2010-11-25
I'm having the same issues on a new system built with the same MOBO.  After scouring the web for a while I posted the following to a thread on an openSuse forum at: [http://forums.opensuse.org/english/get-help-here/install-boot-login/446101-unable-install.html]("http://forums.opensuse.org/english/get-help-here/install-boot-login/446101-unable-install.html")  

-------------------
Add one more user having issues with this same MOBO yet a different Linux distro. I just bought a M4A88TD-V EVO/USB3 today from Fry's with memory and a new CPU to upgrade an older ASUS/AMD based file server. The old server was working fine running Ubuntu 9.10 and recognized all the same devices - two sata drives, DVD drive, power supply, etc. The new system booted fine off the HD, but x-windows was a little screwy and I didn't have network connectivity. Since my plan was to eventually get rid of the desktop install of ubuntu and turn it into a true file server I decided I'd just reinstall the OS and not worry with trying to fix things. I dropped the same CD I used to install ubuntu on the old system into the same drive on the new system and it booted up fine (I assume this tells me the BIOS is recognizing the drive ok). But after a few screens into the installation it starts complaining about not being able to detect a common dvd driver. I've tried to manually mount it but nothing seems to work. Searching around for solutions led me here and now I'm thinking there is a real problem with the BIOS on this MOBO and/or the linux kernels I'm trying to use. I'm thinking of returning the MOBO tomorrow based on what I've learned as its not worth the hassle. Sorry I couldn't be of more help, but wanted to let you guys know there is more than a few people struggling with this MOBO under more than one linux distro.

---

### Post by faisalsadaf on 2010-11-25
Okay so my issue was that my CDRW/DVDRW drive had gone bad. As soon as I replaced it, things went back to normal. I was able to install from the same media.

---

