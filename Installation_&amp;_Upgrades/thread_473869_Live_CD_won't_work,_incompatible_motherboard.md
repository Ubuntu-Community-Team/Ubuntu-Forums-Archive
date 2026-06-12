---
title: "Live CD won't work, incompatible motherboard?"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Sirron on 2007-06-14
I am aware that I could use the alternative install method, but I have a Windows Vista installation on here too, and I suspect that if I installed ubuntu to the hard drive I would get this same error and be unable to access anything.

[b]Specifications:

CPU: Intel Core 2 Duo 2.13GHz
Motherboard: Abit AB9 Pro
RAM: 1GB DDR2-800
HDD1: 200GB Seagate Barracuda, SATA300
HDD2: 300GB Maxtor DiamondMax, SATA150
DVD-RW1: HP, IDE
DVD-RW2: Asus, SATA[/b]

I have never been able to use ubuntu on this computer, because it won't boot from the Live CD.

With Feisty (for example - I've tried every other version back to Breezy):

If I use the 64 bit disc, and select the ordinary "start or install", it starts reading from the (empty) floppy drive and just keeps going for about 30 seconds - perhaps looking for a driver - then gives up. The screen goes blank and the drives slow down. Nothing else happens.

If I use the Safe Graphics Mode, the same thing happens.

If I use a 32 bit disc, and select "start or install" I see the ubuntu boot screen with the slider moving from side to side then it starts reading the floppy drive, then it gives up and the screen goes blank.

If I use the Safe Graphics Mode, I get error messages when it gives up - and it seems like it hasn't given up, it's just stuck. I have photographed the output:

[IMG]http://img392.imageshack.us/img392/3861/dsc00287dr6.png[/IMG]

Originally I thought maybe it was the JMicron chipset on my motherboard causing the problem. This chipset is separate to the intel one, and really just provides a way of connecting old IDE optical drives. But today I purchased a SATA drive and connected it directly to the Intel chipset, and it still gives the same error when I use that, so either it's NOT the JMicron chipset, or I need to completely disable it. Which I can't do - there's supposed to be a way in the BIOS but Abit seems to have forgotten that bit.

It says "initramfs", if that means "initialise RAM file system" then it's even weirder, my RAM is just Corsair XMS2, not some obscure or cheap stuff.

I have updated the motherboard's BIOS to the latest revision. To no avail.

I've seen the odd post around regarding this problem, it seems to crop up now and then. I'm sure you'll agree that the chances of me being the only person in the world to buy this motherboard are pretty slim, so it's not just confined to me.

---

### Post by caratuco on 2007-06-19
Did you read my post? Just search AB9. I too have a ab9 board, one IDE with Vista and one SATA with Kubuntu. In my Bios I set my IDE as primary (the second line down in advanced setup) and the SATA as secondary. I also set my drives under peripherals (I think that is where it is) to IDE not raid. Your case may be a little different since you have 2 SATAs . For me the disk would boot sometimes to install and sometimes not. But if you press f6 and add "all_generic_ide naopic nolapic" (without the quotes) it should run the install. Read my post and I hope it helps you. I spent probably 20 or so installs trying to figure it out but I am online now with Kubuntu.

---

### Post by Sirron on 2007-06-25
Thanks for the reply, but I'm afraid it doesn't work. It might be as you say, because I'm using SATA drives. My motherboard doesn't even support IDE hard drives.

Does anyone know when a new version of the kernel that supports my motherboard is likely to become available?

---

### Post by Sirron on 2007-06-29
Sounds like this is very serious bug, and it mostly only affects my motherboard (sod's law).

I won't be changing this motherboard for a long time, so what can I do to make sure this is fixed? Is it something I should put on the bug system?

Just to clarify, this is an **AB9 Pro** motherboard. The "Pro" is important. I have updated to the latest Bios, which is ab917 - I am about to update to ab918 which is the latest.

---

### Post by kyphi on 2007-06-29
I run an intel 965 board that has two SATA II hard drives and originally had two IDE optical drives.  Ubuntu would not load just as described.  I then inserted an IDE to SATA adapter to one optical drive which allowed me to install Ubuntu.  Installing a second IDE to SATA adapter did not work.  These adapters have to have a power supply and it is possible that the line I soldered together lacked continuity somewhere.
Therefore the second optical drive remained dysfunctional in Ubuntu, although it worked fine in XP.  Recently I replaced the remaining optical drive on IDE with a SATA drive and now everything works fine.
Remember that when using SATA drives you do not need to set master/slave jumpers as you would with IDE.
So, what to do.
I would disconnect the IDE optical drive temporarily and try to install Ubuntu from the SATA optical drive.  I assume that you have your BIOS adjusted to boot from CD first and hard drive last.
I hope that reading my experiences with the 965 chipset mobo gives you some hope that any difficulties can be resolved.
Cheers

---

