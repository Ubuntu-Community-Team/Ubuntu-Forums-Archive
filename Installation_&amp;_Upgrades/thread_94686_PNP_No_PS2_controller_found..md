---
title: "PNP: No PS/2 controller found."
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by Sudokan on 2005-11-24
There is probably an obvious fix to this, but I searched the forums and I cannot find a thread describing this. I am somewhat new to Linux, and this error stumps me. When trying to install (K)Ubuntu or run either Live CD, the system hangs at the same location, as follows:

....
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
PNP: No PS/2 controller found. Probing ports directly.

and...nothing. It just hangs there.

I have tried various boot options, like noapic nolapic or pci=noacpi, to no avail. I also tried plugging in my USB mouse and keyboard into the respective PS/2 slots, but this doesn't help either. I am running Ubuntu on my laptop with no problem, and I would like to install it to my 8 Gig secondary hard drive on my desktop as well. Anyone have any ideas?

---

### Post by yesplease on 2005-11-24
Perhaps somebody can help you when you post you hardware specs.

---

### Post by Sudokan on 2005-11-24
Ahhh, yes, I forgot about that. As you can tell, my desktop is rather old, but it still works for most things:) 

1.7GHZ Celeron
ECS M921LR Motherboard, VIA P4X266 (VT8753) rev. 01 Chipset, Award Bios (release date 10/15/2002)
Kingston SDRAM PC133 - 512 MBytes
ATI Radeon 9200 AGP Video Card
Soundblaster Live Platinum soundcard
Realtek Fast Ethernet onbaord NIC Card
Logitech Multimedia Keyboard (USB)
Microsoft Wireless Intellimouse Explorer (USB)
Western Digital 120 Gig hard drive (Master) (Windows XP in 9 Gig NTFS Partition, 7 FAT32 Partitions)
Maxtor 8 Gig hard drive (Slave) ( Presently contains PCLinuxOS)
Memorex CDRW (Master)
Generic CD (Slave)
Internal 4 port USB hub ( has Lexmark printer, Gamepad, Zodiac handheld cradle attached)
No floppy (disconnected and removed it; disabled it in bios...no need for it)
SBC DSL Modem (attached via NIC Card)

Thanks for reminding me, yesplease, I forgot to list this stuff...I hope this is sufficient.

---

### Post by Sudokan on 2005-11-25
Well, I finally solved this one...seems kind of obvious in hindsight, but then again, don't they all? I simply changed the bios setting:

USB Keyboard Support   Enable/Disable

from Enable to Disable. I then made sure my USB keyboard was still plugged into the PS/2 port, and restarted the system. This allowed the Live CD to boot up, and I am currently installing Ubuntu with ease.;) 

I think this might be a slight bug, although probably an unimportant one, in the Ubuntu and Kubuntu install routines. I had PCLinuxOS installed on this drive already with no problems, and I have booted up the Knoppix Live CD several times with no problems. Ahh, well, thats what makes Linux interesting...I learn something new every day...

---

### Post by marshcast on 2008-05-31
I'm having this same problem, but don't have a ps/2 port to plug into :(

Anyone offer any ideas?

---

