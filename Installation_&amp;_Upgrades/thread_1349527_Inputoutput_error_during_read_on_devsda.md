---
title: "Input/output error during read on /dev/sda"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by sseng_123 on 2009-12-08
Hullo,
 
I totally new to Ubuntu ie desktop Linux. I wanted a change from Windows.
However I have met the following challenges.
 
- When installing Ubuntu 9.10, I saw the an error when the installation process was detecting file systems. The error is Input/Output error during read on /dev/sda.
 
If any buddy has solved a challenge like this, I will be glad to wait for his/her assistance.

---

### Post by HarshReality on 2010-01-11
Guestimation would be bad drive. I had this on a Dell mini and it was due to a defective SSD

---

### Post by smithers3628 on 2010-02-04
I am having the same issue and i am running an Acer Extensa 4420 laptop. Just ran Killdisk and got rid of everything, yet the install still will not finish.  I get to about 15% of files transferred and I get the same eror message.

I am able to instal Windows XP and Vista with no problems what so ever, but ubuntu will not allow it.

Does anyone have a fix for this problem? i know the hardware is plugged in and working.


[LIST]
[*]Dimensions: 13.2 x 9.8 x 1.62 inches
[*]Weight: 5.4 lbs
[*]Processor: AMD Athlon 64 X2 TK-57
[*]Memory: 2 GB DDR2 RAM 667 MHz
[*]Optical Drive: 8X DVD ± RW / CD-RW DL
[*]Display: 14.1 inch WXGA TFT-LCD CrystalBrite Display, 1280 x 800 pixels
[*]Hard drive: Hitachi 160 GB SATA HDD, 5400 RPM
[*]Graphics: ATI Radeon Xpress X1250 graphics with 256 MB VRAM
[*]Speakers: 3D Sonic stereo speakers with HD audio support
[*]Operating System: Microsoft Windows Vista Home Premium
[*]Wireless: Acer InviLink wireless LAN (802.11b/g)
[*]Ports: 4 USB 2.0 ports, VGA out, S-Video out, Ethernet Port, Microphone and Headphone jack, Modem, 5 in 1 card reader, Kensington Lock slot, Optical Drive
[/LIST]
any help would be much appreciated.

---

### Post by dabl on 2010-02-04
That's probably a bad burn of the CD.  Burn it at your slowest speed, DAO mode.

---

### Post by smithers3628 on 2010-02-04
Nah i have 2 copies of 9.10 that both work as well as an older version which i have tried to install, all of which failed.

To prove they work, my friend installed ubuntu 9.10 with the same disc last night, and i am typing on another computer freshly formatted with the same disc.

---

### Post by alexeix on 2010-02-16
I have the same problem when attempting to install 9.10.

Whether I choose to automatically or manually set up the partitions, the following error is reported:

"Input/output error during read on /dev/sda"

Then..."failed to create a swap space...the creation of swap space in partition 5 of SCSI2 (0,0,0) (sda) failed".

As per the previous poster, I can install Windows on the same HDD without any issues.

Also, my Ubuntu install CD was burnt at slow speed.

The reason I'm doing a fresh install, is that I upgraded from Jaunty to Koala previously and have had many problems with hanging, crashing, etc.

I also had some issues with Jaunty and ran a diagnostic tool from my hard disk manufacturer (Samsung), which said the disk was fine, but I got it swapped out for a new one regardless.
However, I still had issues with Jaunty though, so I wonder if there may be a problem with some hard drives???

---

### Post by alexeix on 2010-02-16
Okay, on the 5th or 6th try, the install worked.

I really don't want to struggle like this before even running it, so I'll just see how it works and hope I don't have any further issues.

It <may> be an over-heating problem, since I'm using a Shuttle SFF PC and on this last attempt, I left the PC off for a while, then removed the case cover when doing the install.

---

