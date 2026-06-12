---
title: "ubuntu hangs on startup and strange behaviour"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by metafor on 2005-04-13
hi 

i installed (k)ubuntu on a ibm a21e. i realized strange things the last couple of days.
i think they have nothing todo with kubuntu, think it would be the same with ubuntu.

sometimes the laptop is not booting up, saying something like:

Uncompressing Linux ..... OK, booting the kernel.
audit(1113400815.108:0):initialized 

and nothing is going on anymore, it hangs. 
if i start with recovery mode it hangs as well and shows:

ACPI:PCI interrupt 0000:00:03.1[A] -> GSI 11 (level, low) -> IRQ 11

and again it hangs. after several retries it comes up and i turned off acpi in 
grub with acpi=off after the ro entry, but the first reboot gave me the same result.

what could this be????
tested it on the stocked -386 kernel and on the -686 which should be optimized 
for this celeron machine.

then i realised some problem with the sound. if i play a cd it works for some seconds and then i get the noise from the machine, strange distortion sounds, 
if i move a window in kde, for example the cd-player, the sound is cristal clear. only
alsa-player plays them without any problems, why this?? how can i configure alsaplayer as default for playing cd's? mp3 is no problem.

any help would be apreciated, thanks.
metafor

---

### Post by metafor on 2005-04-15
just installed ubuntu and the same thing is happening. could be a bios thing. 
i saw that the bios has not been updated sine 2001, it's still verision 1.01 which is when the computer was assembled. so i have to install windows to update the bios as this IBM has no floppy  :? 

just post this if someone has similar problems, will tell if it helped....

if someone could tell me what's going on at the hangtime, this could help.
does it mean that it hangs starting ACPI, or ist because of some strange IRQ sharing??

cu
metafor

---

### Post by xebitx on 2005-04-17
I have the same problem...

If my computer wont boot I get this:
*Uncompressing Linux ..... OK, booting the kernel.*

Then I reboot until it starts booting and when it boots I get this:
[I]Uncompressing Linux ..... OK, booting the kernel.
audit(1113400815.108:0):initialized [/I] followed by the rest of the boot process...

---

### Post by metafor on 2005-04-18
just some additional info, still it is not working.

i updated bios to the latest version. now it should be possible to install 
win xp, before this was not possible. 

but ubuntu, not kubuntu this time, is installing properly. 
when i reboot it is working. if i shutdown it is working. but if i shutdown and unplug
and replug and boot up, it hangs at the same place. i do not know if it has something to do with the battery of the computer, which is more or less dead. it could also be, that it has something to do with the little bios battery which has not been changed for four years since assembling. 

i tried to load without acpi, apic, lapic and pcmcia. but it hangs at the same place, something with IRQ sharing. i tested all IRQ combination in the bios from autodetect to all avaible numbers. but it hangs whatever irq i take. 

win2000 which i installed then as i have to write some stuff is working properly so far... but thats not really a solution i just dont feels good  ](*,) 

any idea is still welcome and i can feel with everyone who has the same problem. 
m.

---

### Post by superoxy on 2008-02-18
Hi,

Im trying to install Ubuntu 7.10 on my thinkpad a21e laptop but it keeps hanging up after a couple of minutes into the start process.  

It still has the 1999 bios (also having problems flashing with a new bios).

here's a screenshot of some code before it hangs: 

[[IMG]http://img.photobucket.com/albums/v689/superoxy/thinkpad%20update%20errors/th_DSC02846.jpg[/IMG]](http://img.photobucket.com/albums/v689/superoxy/thinkpad%20update%20errors/DSC02846.jpg)

Any idea on hoiw I can make ubuntu work on this laptop?

---

