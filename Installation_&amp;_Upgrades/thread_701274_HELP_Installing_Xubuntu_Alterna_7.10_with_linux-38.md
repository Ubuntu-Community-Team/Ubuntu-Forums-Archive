---
title: "HELP Installing Xubuntu Alterna 7.10 with linux-386 kernel module, not linux-generic."
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by ExcaliburDX4 on 2008-02-19
Hi guys,

Im knew to ubuntu, but ive been building computers & working with windows since Win95. 

Ive been restoring a late Amtron 486 machine, call me old school for my reasons, but i want to see how it copes with Xubuntu, so that i can write it up, as it would seem no one else has so far.

**Specs:**
i486DX4 100 MHz / 33 MHz FSB -- Heatsink & Fan installed ;)
Cache Async 256KB Memory Module -- In the post.
Amptron 9700 Ver 3.2  AT Socket 3 -- 3 PCI / 4 ISA / 1 VESA / 4 30-Pin SIMM's + 2 72-Pin SIMM's
128MB 72-Pin SIMM's 60ns EDO
120GB Western Digital 7200 RPM IDE
Sony DW-D22A DVD/CD
Maxor Ultra ATA/133 PCI Adapter  
S3 Dirge DX PCI Graphics Card -- Memory unknown expected to be 4MB+
NE2000 ISA Ethernet Card
SoundBlaster ISA Sound Card

Already installed Xubuntu up the point that it gives me the error message "No installable kernel found", so i need some help... i want to install the linux-386 kernel module when i install xubuntu, and not linux-generic. Ive been working on this system most of the last 3 days, and ive tons of reading to deal with other problems to get this far, and i can not seem to find any help in booting Xubuntu Alternative 7.10 with the linux-386 kernel installed.

I tryed at no kernel found error.
[B]ALT-F2
"Chroot /target"
"apt-get install linux-386"[/B]

Comes back with not found, though it works with linux-generic.

I know that i486DX4 100  is pushing it, and that i will be getting a lower performance than a pentium 2, but its an adventure.

Any help welcome, thx.
**Excalibur-DX4**

---

### Post by kakaroth on 2008-06-02
> **ExcaliburDX4 said:**
> Hi guys,

Im knew to ubuntu, but ive been building computers & working with windows since Win95. 

Ive been restoring a late Amtron 486 machine, call me old school for my reasons, but i want to see how it copes with Xubuntu, so that i can write it up, as it would seem no one else has so far.

**Specs:**
i486DX4 100 MHz / 33 MHz FSB -- Heatsink & Fan installed ;)
Cache Async 256KB Memory Module -- In the post.
Amptron 9700 Ver 3.2  AT Socket 3 -- 3 PCI / 4 ISA / 1 VESA / 4 30-Pin SIMM's + 2 72-Pin SIMM's
128MB 72-Pin SIMM's 60ns EDO
120GB Western Digital 7200 RPM IDE
Sony DW-D22A DVD/CD
Maxor Ultra ATA/133 PCI Adapter  
S3 Dirge DX PCI Graphics Card -- Memory unknown expected to be 4MB+
NE2000 ISA Ethernet Card
SoundBlaster ISA Sound Card

Already installed Xubuntu up the point that it gives me the error message "No installable kernel found", so i need some help... i want to install the linux-386 kernel module when i install xubuntu, and not linux-generic. Ive been working on this system most of the last 3 days, and ive tons of reading to deal with other problems to get this far, and i can not seem to find any help in booting Xubuntu Alternative 7.10 with the linux-386 kernel installed.

I tryed at no kernel found error.
[B]ALT-F2
"Chroot /target"
"apt-get install linux-386"[/B]

Comes back with not found, though it works with linux-generic.

I know that i486DX4 100  is pushing it, and that i will be getting a lower performance than a pentium 2, but its an adventure.

Any help welcome, thx.
**Excalibur-DX4**

Hi, I know it is an old post, but I'm interested to know if you installed succefully the ne2000 ISA network card. if yes HOW?
I have the same card, but I cant make it works in xubuntu 7.10.
please help me.
sorry 4 my bad english...

---

### Post by ExcaliburDX4 on 2008-06-03
Hi,

I managed to get around my orginal problem, which turned out to be the problem relating to the installation not installing correctly, i think i used "aptitude" command on one of the command prompt screens.

"Aptitude" > Not installed > Base > Main > linux-image-2.6.20.15

Then returned to the installation and asked it to continue regardless, and it thankfully continued.

The NE2000 network card:
When the installation fails to find the network card, switch to one of to the command screens, press enter. When its ready, type "modprobe ne io=0x300 irq=9", exit the screen, then return to the installation screen, re start the network installation stage, and it should find it. I found i had to wait until the network hardware installation stage failed before i could, enter the command above.

Im a Ubuntu noob, but i hope i helped.

As for my adventure, its still on going, though ive had some good results, though probably still slow to most, once i made some changes, though im finishing of my college course at this moment, so ill write update in a few weeks.

---

