---
title: "Stuck in GRUB 1.99-21ubuntu3.1"
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by andrew118 on 2014-05-25
[COLOR=#000000]Hi![/COLOR]
[COLOR=#000000]i have a problem at startup of ubuntu 12.04 64bit.[/COLOR]
[COLOR=#000000]when i start the computer it says:[/COLOR]

[COLOR=#000000]GNU GRUB VERSION 1.99-21ubuntu3.1[/COLOR]
[COLOR=#000000]Minimal BASH- like line editing supported. for the first word, TAB[/COLOR]
[COLOR=#000000]lists all possible command completions. Anywhere else TAB list possible device or file completions.[/COLOR]

[COLOR=#000000]if i press tab, it shows a list of some words that don't make sense to me.[/COLOR]

---

### Post by mörgæs on 2014-05-26
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by andrew118 on 2014-05-26
how can i use this on the computer that is stuck in gnu grub?

---

### Post by Bashing-om on 2014-05-26
andrew118; Hi !

The thing is to fix the booting issue on that install, to do that one must work outside of the install ( why you will work from a liveDVD/USB).

Follow the 
> 
2nd option : install Boot-Repair in Ubuntu

As directed.

All you are going to do is boot up with the liveDVD, down load boot-repair - read and comprehend the instructions- and hopefully
boot-repair will effect it's magic and correct your situation.

Else: We will do something else.

---

### Post by andrew118 on 2014-05-26
umm i cant even get into windows 8.1 (factory installed) or linux which i installed yesterday

---

### Post by Bashing-om on 2014-05-26
andrew118; UMphh,

Windows 8 = UEFI booting = a sloppyation.There is no standard at this time how UEFI is implemented, each manufacture sets up UEFI differently. You will have to read the manual to see how to 
a) change the boot order
b) turn off secure boot ?

So that you can boot from the liveDVD and/or liveUSB.

Not a good answer
[INDENT][INDENT][INDENT]just the way it is
[/INDENT][/INDENT][/INDENT]

---

### Post by andrew118 on 2014-05-26
like i mean i dont know how to get past grub to anything like to change a boot order

---

### Post by Bashing-om on 2014-05-26
andrew118; Oh My ..You have a non-comprehension of how an operating system works.

The booting is to boot to grub so grub can boot the operating system.

The very 1st thing in that chain of events is - in your case - UEFI. That is at the hardware level and has no direct relation to grub or the operating system.(yet) -> 1st things come 1st

When you turn on your computer, well the hardware and memory must be checked, once verified then UEFI passes control to Grub, grub loads up and passes control to the kernel and the kernel once loaded up passes control to the operating system.

SO, back to your situation.. ya got to tell UEFI what to load/where so it can pass control to where it needs to.
Many time that function within the setup is in some keyboard key access at the initial stage of firing up the system.
say maybe - emphasis on maybe - the F2 key, maybe F12. Maybe the delete key .. maybe maybe maybe... how one access the setup varies, as I have advised, with each manufacturer.

No one who is not setting in front of your exact machine can advise on exactly how to access the UEFI set up. Besides generally, when the system initially is starting, hit some key to stop the boot process and go to the setup screens - to alter how UEFI behaves  .

You must tell UEFI to boot from the liveDVD.

[INDENT][INDENT]when all else fails
[INDENT][INDENT][INDENT]read the instructions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by prmurthy on 2014-05-26
Dear OP, without meaning to be condescending, I dont think you should be trying to dual-boot Ubuntu and Windows on a UEFI machine with your level of understanding. I sincerely hope you dont have any data/documents on this PC. If you do, please find a way to take a backup first.

---

### Post by andrew118 on 2014-05-26
lol to late for that... sent it to a guy i know to fix everything i screwed up lol..

---

