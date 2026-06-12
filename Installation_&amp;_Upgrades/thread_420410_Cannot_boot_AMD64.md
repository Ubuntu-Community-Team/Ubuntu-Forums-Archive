---
title: "Cannot boot AMD64"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by hotpurple on 2007-04-23
Hi all,

I'm trying to install the AMD64 version of Feisty but the live cd won't boot. It simply stops when the bootsplash would have appeared. The monitor turns to standby and the scroll and caps lock lights start flashing.

I managed to install using the text based installer but upon rebooting the same happened. 

My system is as follows:

Opteron 144 (Socket 939, not overclocked)
Asus A8N-E (NForce 4 Ultra)
1GB Crucial Ballistix PC 3200
Seagate Barracuda 7200.9 160Gb SATA II drive
LG DVD +-RW
ATI Radeon X850XT PCI-E card
Audigy 4 value sound

That's about it. What could be causing the problem I describe?

Chris

---

### Post by Spyrious on 2007-04-23
I have exactly the same problem with ubuntu 7.04 x64

System is almost the same

Opteron 144
dfi nf4 ut d
2x512 mb ocz pc4000
ati x850xt
nec3540
plextor px116a2
audigy 2
philips 20wp7es 20.1" widescreen

try to install it on wd 153aa 15gb ata100 hdd

---

### Post by psusi on 2007-04-23
I have the same problem.  Disabling the splash screen fixed it.  Edit the boot parameters and change "splash" to "nosplash".

---

### Post by hotpurple on 2007-04-23
> **psusi said:**
> I have the same problem.  Disabling the splash screen fixed it.  Edit the boot parameters and change "splash" to "nosplash".

Ah, great stuff. I thought it might be something like that.

Cheers

Chris

---

### Post by Spyrious on 2007-04-24
I need a little help because im new to linux.How can i do that using the live cd.I already installed ubuntu.
Thanks

---

### Post by RawMustard on 2007-04-24
see here you need to change your grun params
[http://ubuntuforums.org/showthread.php?p=2509903#post2509903]("http://ubuntuforums.org/showthread.php?p=2509903#post2509903")

---

### Post by Spyrious on 2007-04-24
I had to change the splash to nosplash also.
But i have the same problem on shutdown.
Can i do anything about that?
Thanks for the support though.

---

### Post by RawMustard on 2007-04-24
I don't understand same problem on shutdown  Can you provide more information?

---

### Post by Spyrious on 2007-04-24
What info do you need?
Thanks again.

---

### Post by Spyrious on 2007-04-25
I will try to describe it a little.
When i choose to shutdown or restart the screan goes black and the caps lock and scroll lock led flash.I can hear the shutdow sound that is playing like when the system is crashed.

---

