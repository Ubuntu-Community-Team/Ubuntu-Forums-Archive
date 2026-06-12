---
title: "Installing on Toshiba Satellite(OLD) Laptop problems"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by logreeval on 2008-06-10
Hi

I just bought an old toshiba satellite 330cds laptop and I wanted to install Xubuntu on it. 

Well i am going to have to download xubuntu so that will take a while, but in the mean time I tried both my LiveCD and Alternate CD of Ubuntu 8.04

While trying to install it says it can't detect my CD rom drive but that is what i booted the installer from ???

And in the beginning i get a problem that says something like it needs "acpi=forice" or something like that...

This last problem isn't a ubuntu problem but someone might know...the laptop no matter what i do it looks like their is trails behind the moving stuff. Kind of like on windows the pointer trails option...except it happens on everything, even in the BIOS . Does anyone have any suggestions on that?

Thanks

---

### Post by GhostPilot on 2008-06-11
Older laptops do not support ACPI in their BIOS.  ACPI has something to do with power management of the Laptop.  Also older laptops may suppoet APM.  So after installation, make sure that you install APM (Go to synaptic package manager and search for APM) You may like to remove acpi. By desfualt Ubuntu kernel has support for APM but its disabled.  Edit /grub/menu.lst.  
Look for following:-
title           Ubuntu 8.04, kernel 2.6.24-18-generic
root            (hd0,6)
kernel          /vmlinuz-2.6.24-18-generic root=UUID=dc64b4ad-34a2-4c4b-9426-5cb076041c5e ro quiet splash
initrd          /initrd.img-2.6.24-18-generic

and add apm=on infront of ro quiet splash infront of kernel

I hope this solves your problem

---

### Post by logreeval on 2008-06-11
Thanks for the reply, i really appreciate

I tried to do that on the startup of the livecd but had to add acpi=off in there as well. So that worked for the most part. Didnt hear any more problems on that.

But then it still doesn't install.

On my alternate install here is what happens:
Boots up, select install ubuntu with the acpi=off etc..

Starts going, kinda sits with that little line _ for a while.

Says something about irq and "nobody cared"

I wait about 10 seconds and then the installer comes up. 

Do the usual stuff until detects hardware, it kind of hangs and then says "no cd-rom"

it says i need to manually show it where the CD rom is...i havent the slightest where it is.

Thats where it ends.

I am unsure of the next step.

oh, and the laptop screen trails so everything is blurry, but then i hooked it up to my regular monitor and it looked fine :-\

Thanks for the reply! :)

---

### Post by logreeval on 2008-06-12
does anyone know? :-\

---

### Post by Pumalite on 2008-06-12
Try adding 'irqpoll' to the boot line.

---

### Post by logreeval on 2008-06-12
it says BUG: soft lockup - CPU#0 stuck for 11s! [modprobe:913]

then it does its usual stuff, detect keyboard, blah blah.

When it hits detect hardware, still says CD-rom not detected... 

this really is an old laptop ... i was  thinking of maybe trying DSL or Puppy on it?

i don't know...i just want to get some sort of linux that is semi-user friendly and that can install...

---

### Post by logreeval on 2008-06-12
oh, and thanks for the replies, i appreciate it.

---

### Post by logreeval on 2008-06-13
i have been messing around with other linux distros, small ones

It seems that out of all of them, the one that detects hardware the best is Damn Small Linux.

Maybe I should consider if this laptop can actually fit *ubuntu on it?

It has 96ram, 4gb harddrive, pentium 266mmx processor....

Does anyone happened to know any distros that have the same hardware detection database or whatever its caled, of Damn Small Linux?

Thanks :)

---

### Post by avtolle on 2008-06-13
With only 96 mb ram, you might want to look at Puppy Linux (I've not used this).

---

### Post by buntunub on 2008-06-13
Ubuntu requires 384M Ram minimum. Xubuntu slightly less. You could maybe try Fluxbuntu without too many issues.

---

### Post by snowpine on 2008-06-13
> **buntunub said:**
> Ubuntu requires 384M Ram minimum. Xubuntu slightly less. You could maybe try Fluxbuntu without too many issues.

+1 I would not try Xubuntu with less than 256 mb of ram, sorry. :(
Damn Small Linux (DSL) is a great way to learn about linux on an older machine.

---

### Post by logreeval on 2008-06-13
Thanks for the replies guys! :)

I am bouncing back and forth between DSL and Puppy, both are great distros as well for older machines.

If anyone knows anything about puppy....

My PCMCIA card and USB port are not getting recognized correctly...

I would love to get this laptop running before the 23rd because i am leaving on a trip and my younger brother would like something to do besides nothing ;)

THanks again for all the replies guys!!

---

