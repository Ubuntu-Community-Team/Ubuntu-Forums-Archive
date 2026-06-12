---
title: "Dell Optiplex 320 : unable to install"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by CyrilleMortreux on 2007-01-03
Hi. 

I try to install Ubuntu on a Dell Optiplex 320.
- PIV 3Ghz
- SATA
- Pci bridge ATI RS480
- IDE interface : ATI SB600 Non Raid 5 SATA
- IDE Interface : ATI SB600 IDE
- USB Controler :  ATI SB600 USB

**_1- Ubuntu 6.10_**

I have tried first an Ubuntu 6.10 Alternate i386 but the boot from the CD hangs up and shows many BIOS bugs (USB, SATA, ACPI, IRQ...)
I have passed some extra options at boot like : 
```
pci=nomsi noapic nolapic
``` but no way to get that working. 

So I have took the SDA at home to perform an Ubuntu setup on, and that worked... At home... But does not boot here. 

**_2- Linux Rescue CD_**

This one works fine with a 2.6.18 kernel. I can access my SDA drive and mount my slices, or modidy then with gparted. But this is a rescue CD; not a working Linux box. 
[B]
_3- Ubuntu 7.04_[/B]

I have download a fresh ISO of Feisty, and passed these extra options at boot : 
```
irqpoll pci=nomsi pci=noacpi nolapic noapic
```

That boots, I have my ncurses dialog opening, but no way to get the CDrom recognized even if I change my Cdrom :/

**_4- Debian Etch daily snapshot_**

I have tried with : 
```
expert irqpoll pci=nomsi pci=noacpi nolapic noapic
```

But no way too to get the CDrom working

What could I say more ? ... What a mess !!!
 I have tried to switch off as many things as possible in the BIOS but this is a very poorly BIOS, and there is not a lot og things to do with (No USB legacy support, no Ide compatibility support...), and I just can't switch off USB support because mouse and keyboard are USB (no PS/2 din. )

Any idea ???

Cyrille

---

### Post by CyrilleMortreux on 2007-01-04
Hi. 
So, I have succed in a Debian install. 

- Debian Etch daily snapshot
- options "install pci=nomsi"
- no GRUB but LILO installed instead

But no way to get installed Ubuntu Feity not Edgy / Dapper...

It seems to be a common problem as you may see by searching in Google with "dell Optiplex 320 Linux". Many others just can't install Ubuntu on this computer.

---

### Post by daehenoc on 2007-02-25
Hi,

Can you please post your complete lilo.conf and what kernel/lilo versions you are using please?

Thanks,
Greg

---

### Post by zgoda on 2007-02-28
So, there's no hope but wait for a release with 2.6.20 kernel? Oh, my... Dell, why are you doing it to me? Should we buy HP or anything...

---

### Post by marshcast on 2007-04-16
Have spent a few days on this, and although my experience is not the finest I have come up with a fantastic cure (at least I think so... it's not quite finished install yet - but all problems seem to be fixed & fine so far)

install feisty.

;)

[http://releases.ubuntu.com/7.04/ubuntu-7.04-beta-desktop-amd64.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-beta-desktop-amd64.iso)

don't know why i didn't think of it 3 days ago - given that i just bought 7 optiplex320's this is a bit of a relief!!!

I believe automatix has been released for fiesty now... willl update as i find out :D

---

### Post by marshcast on 2007-04-16
gonna have to put a hold on that (sorry) feisty has some sort of install issue. it wont start up (was that the start of the thread - sorry - obviously too excitable... :(

have to try lilo later.

---

### Post by Staceman on 2007-04-16
I finally got the Feisty Fawn beta working on an Optiplex 320, check out the thread here:
[URL="http://ubuntuforums.org/showthread.php?t=409345"]
http://ubuntuforums.org/showthread.php?t=409345[/URL]

And by the way, the Optiplex 320, at least mine, anyway, is a Pentium 4 system, and not an AMD64. That may be why you're having install issues, since the ISO you linked to is for the AMD64.

---

### Post by marshcast on 2007-04-16
And by the way, the Optiplex 320, at least mine, anyway, is a Pentium 4 system, and not an AMD64. That may be why you're having install issues, since the ISO you linked to is for the AMD64.[/QUOTE]

nice one, staceman - will try it.

My optiplex is 64bit thiough - bios says it's Intel EM64T... think thats the right link (for me anyways), doesn't work tho :(...

am ondering whether the x86 will work on 64 bit technology... Hmmm...

have to give it  a go, eh?

---

### Post by marshcast on 2007-04-17
Thanks Staceman - got feisty working.

the [http://ubuntuforums.org/showthread.php?t=409345](http://ubuntuforums.org/showthread.php?t=409345) thread was really helpful. lilo works ok (need to work on that splash screen though - 's pretty ugly! 

dmesg still has BIOS handoff failed (among other bootup problems) but that's another story.

Also: my optiplex is a EM64T pentium D (dual core 64bit) - so I did use the AMD64 install.

Still - thanks again for the help, and best of luck to all yous others trying out there,

Marsh ;)

---

