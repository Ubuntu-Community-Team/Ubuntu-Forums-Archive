---
title: "Can I install 12.04 Xubuntu by ....."
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by jbuczek on 2012-10-20
I've got a diskless mini-box, spec's below.  It makes a CF flash drive  look like an IDE HDD.  It will not boot from a USB stick or anything else that I have.  I'm trying to do this on a new 8gb CF.

Is there some way I can do this:

1 - use another computer to partition the new 8 gb CF into, 
    lets say, P1 = 3gb and P2 = 5gb.
2 - somehow put the Xubuntu install iso on P2 and make it bootable
3 - put the CF in the m-computer and boot the install
4 - install Xubuntu on P1
5 - reformat P2 and make it /home

...... or is there another way?

The only thing I don't know how to do is step 2.  Seems the problem would be the bootloader....GRUB2 for Ubuntu.  As I understand it... and odds are I'm wrong.... the GRUB2 files are inside a previous OS install partition and I ain't got one of them. Is there someway to make the loader stand alone? 

This box used to run Ubuntu 10.04 just fine on a 2gb CF.  I installed it using an external IDE drive that I hooked up just for the install but I don't have one any more.

TIA

P.S. I assume in this case (i.e. flash drive) noswap would be best.

Spec:
Mini-box M200 chassis
Jetway J7F2WE1G2E mb w/ Via C7 CPU @ 1.2 ghz
     VIA Unichrome Pro OnBoard GPU
     Video Memory 	Shared Memory up to 128MB.
1 gb DDR2 RAM

---

### Post by 2F4U on 2012-10-20
Since Xubuntu detects the hardware on every boot, except if you install something like proprietary drivers, I would create a liveCD or liveUSB and boot a "normal" machine" with it. You would need a card reader in this machine. Then it should be possible to install Xubuntu on the CF card as if it is a hard disk. Make sure that the boot loader is installed on the CF card and not on the machine you boot of. My concern would be that 8 GB is not that much for a modern Linux distribution.

---

### Post by jbuczek on 2012-10-20
Never thought of that.  I figured the hardware differences between a dual core AMD machine and an old VIA box would create huge problems.  I guess I was thinking Windows.  Never imagined that every Xubuntu install carries drivers for all hardware setups. 

Yesterday I used the CF as a Live CD to try Xubuntu 12.04.1 and it worked like a charm even without special drivers.

RE the 8 gb.... apparently that's not going to happen.  I tried it yesterday as a live CD and the mini-box couldn't see it even at the BIOS level.  I guessing either the IDE emulator can't handle that much or the micro-micro power supply can't.  So I'll be going back to the 2 gb CF card but this machine did everything I wanted for two years with Ubuntu 10.04 on that card.  My demands are minimal... this is for internet activities only with Firefox and Pidgin plus Abiword for an occasional homework assignment.  Trying to solve this I did more reading and I'm going to go with the Alternate install CD which, they say, can still install on a 2 gb drive.

Got a party to go to today.  I'll try it tomorrow and let you know how it works.

---

