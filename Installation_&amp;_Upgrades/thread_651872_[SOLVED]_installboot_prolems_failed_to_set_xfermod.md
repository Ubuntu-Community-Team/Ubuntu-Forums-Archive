---
title: "[SOLVED] install/boot prolems: failed to set xfermode / exception emask....frozen"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by ImALittleTeaPot on 2007-12-28
I'm having install/boot problems with gutsy 7.10.  

The kernal version is 2.6.22-14 generic. Its a live cd that i downloaded (32bit). 

System:
abit IP-35 Pro Mobo
Lite On DVD RW
Seagate Barracuda 320GB
ATI Radeon X1950XT Video Card


I set BIOS to boot from cd, get as far as the UBUNTU screen with the orange bar going side to side. Then this error message. 
[ATTACH]54425[/ATTACH]

_UPDATE_:
After many attempts at booting from the live cd, I finally suceeded, but don't know why. So i tried it a few more times to see what would happen. Apparently my system will boot from the live cd RANDOMLY (like 1 of 7 attempts give or take). This is weird. Also....more problems occur. I was able to install, then this screen (splash screen?) will hang when Ubuntu tries to boot from the hard drive.
[ATTACH]54426[/ATTACH]

During the hang, I pressed ctrl+alt+F1 to get a little more info about errors. Here it is.
[ATTACH]54429[/ATTACH]

Notice that its telling me that a file is missing in my /dev/disk/by-uuid/xx-xxx.
I think that this is the UUIP address of my root partition. 

After tinkering around in grub (hitting 'e' and editing boot parameters), I've found that I can boot into Desktop if I add either the parameter "irqpoll" or "acpi=off" at the end of the kernel line:
/boot/vmlinuz-2.6.22-14-generic root=UUID=7eec31fb-03e9-40cd-861a-efe58a7aec56 ro quiet splash (append here)

But this doesn't really "fix" the problem. booting from the live cd is still random, and I am told that those boot parameters might hurt performance.

Any insight into this would be greatly appreciated.

---

### Post by ImALittleTeaPot on 2007-12-28
tried alternate 64bit cd. Same error messages after 1st update of new install.

---

### Post by ImALittleTeaPot on 2008-01-04
found the problem

> **US41 said:**
> I found the solution to getting past it. Apparently on motherboards, such as the Abit IP35 Pro, the Sata controllers 1-4 are double-booked and the OS cannot read them. 

To fix the problem:

1. Open your PC box
2. Unplug your SATA cables from SATA ports
3. Plug them into the highest numbered ports you have (I moved mine from SATA 1/2 to SATA 5/6)

Viola. The live CD runs and I have installed Ubuntu.

---

### Post by slayer^_^ on 2008-03-09
to me the solution was unplugging the SATA data and power cables, substituting the data ones and switching the power ones... maybe a simple contact mechanical error, due to the fact that this kinda cable are more fragile than the old ide ones...

---

