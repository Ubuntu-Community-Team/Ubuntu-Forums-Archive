---
title: "lockups during install"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by ~llama on 2005-08-03
Hey, first off lemme tell you that I love Ubuntu, and I've been running Hoary since May on my Compaq Evo laptop. I decided, with the purchase of a Powerbook tomorrow, that I'd finally take the leap and go windows-free, installing Ubuntu on my main PC. here are the specs:

Pentium D 820
Intel D945PSN motherboard (i945 chipset)
1GB (2x512MB DIMMs) DDR2-400 (samsung, i think)
Sapphire X600 Pro PCI-Express x16 video
Seagate Barracuda 7200RPM 200GB Serial ATA hard drive
Linksys WMP11 PCI wireless card

and that's it. At first I was going to install the 64-bit Ubuntu but the CD i burned was a coaster... I ordered some pressed CD's so I'm going to wait for them to arrive to install 64bit. I then tried the Hoary CD that I've used to install Ubuntu on about five other systems, so I know the CD isn't the problem.

Installation goes fine until it's time to partition the drive. When it gets to this point, the installer says "preparing the partitioner" or something to that effect, and then freezes when the progress bar is at 41%. Every single time. The drive access LED stays on and the drive makes strange noises until i turn off the computer. A warm reboot leaves the drive in this state, but turning off the switch on the power supply and leaving it for a minute and trying again gets me back to the 41% stage again.

I did manage to get to the partition manager once, but when it was time to write the table back to the disk, the same freeze-up happened.

I think this could be one of three things: (1)weird/new chipset causing issues with Hoary, and I should maybe try Breezy, (2)bad hard drive, or (3)some paramater I need to set or something else I need to try that I don't know about.

Any ideas? I would love to have no more Windows systems in my house, but if Ubuntu won't load on this hard drive I might not have a choice for a while.

Thanks for all the work you guys do... ubuntu is truly amazing.

---

### Post by MrCheese on 2005-08-03
> Installation goes fine until it's time to partition the drive. When it gets to this point, the installer says "preparing the partitioner" or something to that effect, and then freezes when the progress bar is at 41%. Every single time. The drive access LED stays on and the drive makes strange noises until i turn off the computer. A warm reboot leaves the drive in this state, but turning off the switch on the power supply and leaving it for a minute and trying again gets me back to the 41% stage again.

I did manage to get to the partition manager once, but when it was time to write the table back to the disk, the same freeze-up happened.

I think this could be one of three things: (1)weird/new chipset causing issues with Hoary, and I should maybe try Breezy, (2)bad hard drive, or (3)some paramater I need to set or something else I need to try that I don't know about.


I'd say a dodgy hdd - the strange noises you mention are usually a sign that patr of the surface is defective so the drive tries to re-read the area. If the noise is something like "clunk clunk" then I'm afraid it's new HDD time. Try & download some hdd diagnostics - most manufacturers do there own, so check the maker's web site - which will confirm if it's "hasta la vista - I won't be back" (to mis-quote Arnie) for your disk.

Paul.

---

### Post by ~llama on 2005-08-03
Ouch. That's what I was afraid of.

Kind of offtopic, how is support for the i945/Pentium D combo? Everything working OK besides my HDD? I'm assuming the AMD64 build is the one I need for Intel's EMT64, right?

---

### Post by JayTee on 2006-10-20
I'm running a Pentium D 940 with the D945PSN mobo and I've had no hardware compatibility issues so far. Installing Dapper was breeze and all the hardware was detected.

---

### Post by Kateikyoushi on 2006-10-20
If possible check the drive's SMART, that might indicate if the drive is about to pass away.

---

