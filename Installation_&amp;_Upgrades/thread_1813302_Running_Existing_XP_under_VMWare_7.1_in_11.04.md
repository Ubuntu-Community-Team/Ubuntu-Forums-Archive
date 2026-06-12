---
title: "Running Existing XP under VMWare 7.1 in 11.04"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by kw_martin on 2011-07-27
Why: 1) Ubuntu 11.04 with Unity interface and Libre appears the best of all worlds (assuming cheat sheet with workspace/windows short-cuts is kept handy). 2) Huge legacy of programs running under XP and 1-2 of them are not available in Ubuntu and I must run them often (example Viewdraw), and I didn't want to re-install XP and programs and I didn't have space.

Cautions: Need registration code for XP and no going back (easily). Also, you could possibly make some serious mistakes that could require a complete re-install to fix.

One Nice Thing: when it works as described, it's very quick to do.

Box: Dell Inspiron 550 with Serial ATA (I think)

VMWare Docs: minimal use, just takes time (it took me 1.5 work days total, all the time trying to find solutions at VMWare was mostly wasted - they appear to taking after Microsoft in approach to documentation)

STEPS:

CRITICAL: Before starting make (actually copy) a new profile in Windows and make sure profiles are not automatically chosen after a time-out. 

I suggest putting the Virtual Profile ahead of the Physical Profile.

In VMWare:

1) New Virtual Machine
2) Custom
3) Next
4) I will install the operating system later
5) Microsoft Windows
6) Edit name to change to something like "WindowsXPPro" (I don't like spaces)
7) Next
8) Next after adjusting memory to 1Gbyte (I assume you have at least 4Gbytes RAM).
9) Next (use default NAT)
10) BusLogic
11) Use a physical disk
12) for me, even though disk C was shown as /dev/sda1 in Windows, I had to specify /dev/sda. Otherwise boot locked up (I'm running GRUB in 11.04)
13) Use entire disk

Next edit WindowsXPPro.vmx (for me, I found this using Google, but not clearly explained)

and change 3 lines containing scsi0:0 to ide0:0 using
>sudo vi WindowsXPPro.vmx
The final lines look like:
ide0:0.present = "TRUE"
ide0:0.fileName = "WindowsXPPro.vmdk"
ide0:0.deviceType = "rawDisk"

Next edit WindowsXPPro.vmdk (sudo)
and change
ddb.adapterType = "buslogic"
to
ddb.adapterType = "ide"

Without these edits, I got the Blue Screen of Death (BSOD, STOP: 0x0000007B)

next run vmware (I had to use sudo)

>sudo vmware

After getting into Windows, you need supply registration code (I almost couldn't find mine - this would have been bad).

Next you need to need to install VMWare Tools before the machine is usable.

Caution: many places to go wrong, and since your machine will be different than mine, I'm sure there will be places that need to be different. Again, very difficult to go back (registration code runs out - you need to contact MSFT).

My final machine appears to be very usable (except in unity mode) including networking and now I can finally work in Unix (been going back and forth since early NEXT days - I really don't like Windows Registry approach, and I especially dislike Word - I like Excel).
-Good Luck (I took time to post this as it finally looks possible to get rid of running Widows exclusively and I think this is a good thing).

DISCLAIMER: if trying this hurts your box, I apologize, but take no responsibility or liability.

---

