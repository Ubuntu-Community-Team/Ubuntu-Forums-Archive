---
title: "Install causes PC to restart"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by Haegin on 2006-12-21
I am trying to install ubuntu on a PC for my sister who prefers ubuntu to windows but whenever it loads the kernel it restarts the PC and this problem isn't unique to ubuntu but has happened with geexbox and with gentoo as well. I am currently running memtest but 512/768 is new so should be fine. The cpu and mobo are both second hand from a friends pc which was running windows xp perfectly happily. Any ideas?

---

### Post by bulldog on 2006-12-21
If you add some new RAM,you should be sure the specifications are a like.
Best way to obtain this,is to take the 'old' RAM with you so the reseller can see what you need.

---

### Post by Haegin on 2006-12-21
Well memtest has just finished pass 1 with no errors so on the advice of reverseblade on IRC I booted with noapic and nolapic but that still caused a failure.
With edgy it doesn't restart but it brings up alot of messages all saying
"Unknown interrupt or fault at EIP " followed by three numbers.

---

### Post by Haegin on 2006-12-21
When booting fedora core 4 as a test I noticed it restarted immediatly after loading the two init thingies that linux always loads (cant remember their names now) initrd.gz or something.
It loads those, prints "Ready" to the screen and restarts.

---

### Post by wpshooter on 2006-12-21
Does this computer have any O/S on it other than Ubuntu ?

Which version of Ubuntu are you attempting to install from, the DESKTOP CD or the ALTERNATE CD ?

When you burned your CDs, did you burn at 4X or less ?

Did you check the integrity of the CDs by running the verification test found on the initial Ubuntu boot screen menu ?

Have you tried installing with the safe video mode parameter ?

As far as your memory is concerned how many memory modules do you have and are you positive that ALL of these modules are compatible with your motherboard ?  Check with the memory manufacturer or the motherboard manufacturer.

---

### Post by az on 2006-12-21
What version of the cd are you using?

---

### Post by K.Mandla on 2006-12-21
You might be running into problems if the computer is old and you're booting from Edgy. But it sounds like it's not *that* old.

---

### Post by Haegin on 2006-12-22
I am using the edgy ubuntu alternate install cd which I have used successfully several times before so I think the burn is OK though I have not tested it.
The PC isn't that old but the mobo and cpu are second user (from a friend whose pc I upgraded - old stuff worked fine on windows).
I am pretty sure the memory is fine as its all DDR1 PC3200 (one 256MB and one 512MB).
The HDD is brand new and has nothing on it (therefore no other OS).
I'm pretty sure I tried the safe video mode to no avail.

All looks bleak....

---

### Post by bigken on 2006-12-22
constant restarts are usually due to over heating look in the bios for the hardware monitor :-k

---

### Post by Haegin on 2006-12-22
Thats a good point and I will check but it always gets to the exact same point when booting from cd no matter what version of ubuntu or what distro I use. Also windows works fine (when I boot from the install cd).

---

### Post by bigken on 2006-12-22
more pointers unplug everything except the monitor mouse and keyboard
disable firewire usb and seriel ports in the bios

---

### Post by Haegin on 2006-12-23
I only have a keyboard, mouse, monitor and power plugged in and I have already stripped down anything I don't need in the bios - I'm gonna give it one more go but if that won't work I think it will have to be a windows PC as it needs to be ready for Christmas.

---

### Post by bigken on 2006-12-30
> **Human Prototype said:**
> I only have a keyboard, mouse, monitor and power plugged in and I have already stripped down anything I don't need in the bios - I'm gonna give it one more go but if that won't work I think it will have to be a windows PC as it needs to be ready for Christmas.

Just wondering if you solved the problem and if so what was it ? :-k

---

### Post by Haegin on 2006-12-31
I'm afraid I couldn't fix it in time for christmas so the computer now has windows XP running on it - I don't like it but I don't have time to fix it or the money to replace the motherboard (which I am sure is causing the problem).

---

