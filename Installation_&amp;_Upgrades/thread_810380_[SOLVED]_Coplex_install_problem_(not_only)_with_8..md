---
title: "[SOLVED] Coplex install problem (not only) with 8.04"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by _sleeper on 2008-05-28
hey guys. i have a problem i can't figure it out!

here's the deal. i can't install on my machine any linux distro! neither i can run live cds! i tried to install openSuse, fedora, ubuntu, kubuntu, mandrake and nothing! the live cd's don't boot, too! the only thing that actually did boot and worked was knoppix 3.4. so i'm just wondering if it has to do with with kernel-hardware incompatibilities. 

no here's the sequence of things: when the pc boots (depending the distro) it asks if i want to install or just boot from the cd. whatever the choice is, it starts loading the kernel and then it freezes. in the ubuntu/kubuntu distros the brown/blue loading bar just fills a little and then sits there forever.

my machine is:
cpu: amd 64X2 5800+
memory: 2 gb
m/b: asus m2n-e sli
vga: msi 8500gt
dvd: nec optiarc dvd-rw
hdd: 2x320 wd

i tried a bios update, but there was no change at all. i've tried every single distro in my older pc and everything went smoothly.

my older machine is:
cpu: amd 64 athlon 2600+
memory: 512 mb
m/b: asus k8v-x se (now, before i had an asus k8n- something)
vga: nvidia tnt2
dvd: nec optiarc dvd-rw
hdd: 1x120 wd 

has anyone faced similar obscurities and found out what was the problem?

anyway, thanx in advance guys!

P.S. when i try to install the openSuse distro it boots the dvd and when i press the install button, it shows that the dvd cannot be mounted!

---

### Post by Kevbert on 2008-05-28
Have you tried a memory check on the PC which won't install linux ?  If you run the openSuse distro there's probably a memory test you can run in the introductory menu.  It's worth running this for a while (as I've come across someone who could run Windows but couldn't use Linux).  If you get any errors then you've got a memory problem.

---

### Post by dstew on 2008-05-28
The Live Cd kernel is having some trouble with your hardware. Try removing quiet splash from the kernel line (use F6 at the opening menu) and see what the errors are. Sometimes you can get the Live CD to boot using kernel parameters to alter the behavior of the troublesome hardware. Often-tried parameters are irqpoll noapic nolapic acpi=off all_generic_ide.

Have you tried the Alternate Install CD? It uses a text-based interface, maybe it will work better than the Live CD.

---

### Post by _sleeper on 2008-05-28
i'm trying the suggestions you recommended guys and i'll be right back for some feedback.
thanx alot!

---

### Post by _sleeper on 2008-05-28
reporting time:
i did run the memory tests and it doesn't seem to be a problem there.

i tried to install in text mode and the following message appeared:
"The CDROM does not seem to contain a valid 'Release' file, or that file could not be read correctly." and then:
"bla, bla ,bla. failing step: Detecting and Mounting CDROM"

is it possible for a jumper to be blamed? i have only one CDROM device, but if the jumper is on the slave mode, could it be it? but i highly doubt that that's the case. (of being the jumper in the wrong place - i put it there)

P.S. i tried to do the no quiet splash and it started to write lines with lots of stuff and it stopped when:

[123.3882992] VFS: Cannot open root device "<NAME>" or unknown block (104,1)
[123.3442422] Please append a correct "root=" boot option; here are the available partitions: 
[123.2342325] Kernel panic - not syncing:VFS: Unable to mount root fs or unknown block (104,1)

*the numbers in the brackets are irrelevant

thanx.

---

### Post by dstew on 2008-05-28
It seems the kernel is not able to access the DVD drive for some reason. It could be a problem with something in your BIOS setup, or even how you have your DVD drive connected. I assume your DVD drive is an IDE drive. Is it the only drive on the IDE interface? If so, is it jumpered correctly (that is, is it Master, or if Cable Select, in the right position)? The hard drives I guess are on the SATA interfaces.

It is possible that the IDE interface is set up some way in BIOS such that the kernel can't access it properly. Check your BIOS settings of your IDE interface. Also, you can try the kernel parameter **all_generic_ide** to see if that helps.

EDIT: Another one to try is **ide=nodma**

---

### Post by _sleeper on 2008-05-28
guys i think i found it! i just changed the ide cable of the dvd-rom and the 8.04 cd did boot like a live cd. so i guess that it will work as an installation cd too.

if anything else occurs, i'll let you know!

thanx alot for the replies!

---

