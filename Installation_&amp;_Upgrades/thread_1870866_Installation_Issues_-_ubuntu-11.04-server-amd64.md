---
title: "Installation Issues - ubuntu-11.04-server-amd64"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by Bengalaas on 2011-10-28
Hello,

Hopefully someone will have some advice or some input into a way to resolve this as I am not the most savvy person with Ubuntu. I obtained some older hardware for free which I am looking to install Ubuntu server 11.04 x64 onto. The system specs are as followed;

Motherboard: TYAN - S2720 Tunder i7500
Raid Controller: Adaptec 2200s
Hard Drives - x4 SCSI 250's
Memory: x4GB
Processor: x2 Intel Xeon 2.4GHZ Dual Core

When attempting to start the installation disc I get the Ubuntu logo and then nothing for about 5 minutes. After that five minutes a line shows up in the middle of the screen pink/green/white with artifact coloring and some of the menu selection for the installation, IE check desk, install Ubuntu the sort. I left this as is for about another 2 hours to see if maybe it was just really sluggish which it was not completely frozen. Numlock is locked no response from anything keyboard and system is hosed.

I am running Raid 0 with the four drives, and can detect them in bios along with all other required hardware. I have also checked the md5sum and verified the disk was good on my other tower by launching and checking contents and launching live mode. Also I was previously running x64 bit windows 2003 on this machine.

Currently at a loss please help me out on this one would be cool to get this free hardware to run. Oh and thanks in advanced.

---

### Post by Bengalaas on 2011-10-28
Bump

---

### Post by MAFoElffen on 2011-10-28
> **Bengalaas said:**
> Hello,

Hopefully someone will have some advice or some input into a way to resolve this as I am not the most savvy person with Ubuntu. I obtained some older hardware for free which I am looking to install Ubuntu server 11.04 x64 onto. The system specs are as followed;

Motherboard: TYAN - S2720 Tunder i7500
Raid Controller: Adaptec 2200s
Hard Drives - x4 SCSI 250's
Memory: x4GB
Processor: x2 Intel Xeon 2.4GHZ Dual Core

When attempting to start the installation disc I get the Ubuntu logo and then nothing for about 5 minutes. After that five minutes a line shows up in the middle of the screen pink/green/white with artifact coloring and some of the menu selection for the installation, IE check desk, install Ubuntu the sort. I left this as is for about another 2 hours to see if maybe it was just really sluggish which it was not completely frozen. Numlock is locked no response from anything keyboard and system is hosed.

I am running Raid 0 with the four drives, and can detect them in bios along with all other required hardware. I have also checked the md5sum and verified the disk was good on my other tower by launching and checking contents and launching live mode. Also I was previously running x64 bit windows 2003 on this machine.

Currently at a loss please help me out on this one would be cool to get this free hardware to run. Oh and thanks in advanced.
Welcome to Ubuntu!

Nice board.  the hardware setup is nothiing out of the ordinary for a server install.  Even the graphics is a standard chipset for most servers. (Most of mine here have the same chipset.

You say that when you boot from that disk on that machine, it gets to the Install menu, but the graphics are scrambled with a pink/green/white lines?  

I'm assuming you burnt the CD from your tower... Did you burn on slowest speed possible?  Have you tried booting any other bootable CD's that were burnt from your tower / from your server canidate? (Suggestion Server 11.04 or 10.10)... Have you tried the 11.10 disk on your tower to see if the Intall menu comes up?

The point it is having a problem is "basic" vga graphics and before the user has any chance to change any graphics options for the install.  <<EDIT- This milestone is before querying the RAID so it didn't come into play yet = don't belive this is an issue in this. What is in play at that point is CPU, onboard chipsets, BIOS, keyboard, video, casper/isolinux. >>

I've been testing dev branches of server since 10.04... I noticed at 11.04 that even though the sever edition is "text" based, that graphics chipsets do get queried for modes and the graphics mode is VGA/Vesa... In 11.04 they added some VGA theming capabilties (console and terminal)... which adds some quirks to some, needing just a workaround- but yours "should" have been fine with that.

The reason I asked the above questions and had you try the above- is that sometimes there is just enough differences in CD/DVD drives from one-to-another, that they won't boot right. Burning at the slowest speed possible helps with that... but some drives are still too much of a difference between the 2.

I did notice a quirk on the 11.10 install disk and multiple CPU's, but I'll stop here to get some feedback before going on.

---

### Post by collisionystm on 2011-10-28
> I am running Raid 0 with the four drives

I know this does not entirely help your situation, but aren't you a bit nervous about doing that?

I would take advantage of the raid controller and the 4 drives and do a raid 10. Its only 500gb when you are done, but at least your chances of losing data are greatly minimized.

---

### Post by MAFoElffen on 2011-10-28
> **collisionystm said:**
> I know this does not entirely help your situation, but aren't you a bit nervous about doing that?

I would take advantage of the raid controller and the 4 drives and do a raid 10. Its only 500gb when you are done, but at least your chances of losing data are greatly minimized.
On this sidenote- I agree whole hearted on that.  I had that same curiosity and concern... Personally, I try to stick with RAID 5 or RAID 10... Some redundancy with speed.  I don't really mind the loss of some storage for the trade-off of keeping my data.  "He who laughs last, had a good backup."

---

### Post by Bengalaas on 2011-10-31
> **MAFoElffen said:**
> Welcome to Ubuntu! 
I'm assuming you burnt the CD from your tower... Did you burn on slowest speed possible? Have you tried booting any other bootable CD's that were burnt from your tower / from your server canidate? (Suggestion Server 11.04 or 10.10)... Have you tried the 11.10 disk on your tower to see if the Intall menu comes up?
 
The point it is having a problem is "basic" vga graphics and before the user has any chance to change any graphics options for the install. <<EDIT- This milestone is before querying the RAID so it didn't come into play yet = don't belive this is an issue in this. What is in play at that point is CPU, onboard chipsets, BIOS, keyboard, video, casper/isolinux. >>
 
[SIZE=2]Hello MAFoElffen,
 
Wanna say a good thanks for the suggestion and taking a look and/or trying to help. After long Holiday weekend I went back to this box and looked into this futher. I did attempt to burn a new CD at slowest speed from my tower which was x16. I have the same drive in my server case as my main tower so this was not the issue. Also I tested the disk after it failed on my server back on my tower which worked fine. I believe the issue is with the graphics langauge selector that comes up in which case iv read something about an alternative install? I was wondering if you know of a way to do a text based install or command line install to kick off the installation process. If I am right the drivers are not being pulled correctly for the VGA card. The ISO that I am using is from [/SIZE][[SIZE=2]http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/11.10/[/SIZE]]("http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/11.10/")[SIZE=2] under the [/SIZE][SIZE=2]Alternate install CD section 64bit.[/SIZE]

---

### Post by Bengalaas on 2011-10-31
Bump

---

