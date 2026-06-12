---
title: "Ubuntu will not install ( ver 6.10 or 7.04 )"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by samuraix51 on 2007-04-25
I am having issues installing any version Ubuntu.

I've tried 4 different install CDs:
Ubuntu 6.10, Kubuntu 6.10
Ubuntu 7.04, Kubuntu 7.04
I know all the CDs are good, I've installed off of them on other machines, and also have tested them in VMWare too.

I've tried the start / install choice and the VGA safe mode choice too from all 4 discs, none will work.
This happens on all 4 discs, with either of the above choices, so it seems not to be version specific.

It boots the kernel, then stops showing the graphical loading screen, and drops to text mode.
Then it dumps a lot of text to the screen that scrolls and scrolls, so can't get a capture of it to look at.
It looks like a kernel dump or something, not sure though, I have to manually reboot the machine to stop it.

I've tried booting off a gentoo install CD, and it boots just fine, and it recognized all the hardware.
So I'm not sure where to start on trying to fix this and get it installed.

My hardware is:
Celeron 2.9GHz
Gigabyte Motherboard with intel chipset (not sure of model, can look if need for more help)
1Gb PC2700 RAM
Nvidia GeForce MX440
40GB Hard drive

Any help / advice / ideas are very very much welcome.

---

### Post by jda1701 on 2007-04-25
A) Is your Celeron overlcocked?
B) Can you post the model number of your motherboard and/or what Intel chipset it uses.

Also try doing a quick search on how to turn ACPI off when you boot the liveCD and see if that gets you any farther. 

Good luck!

---

### Post by SunnyRabbiera on 2007-04-25
maybe you should use dapper, latest doesn't mean greatest...

I think feisty sucks myself....

---

### Post by samuraix51 on 2007-04-25
> **jda1701 said:**
> A) Is your Celeron overlcocked?
B) Can you post the model number of your motherboard and/or what Intel chipset it uses.

Also try doing a quick search on how to turn ACPI off when you boot the liveCD and see if that gets you any farther. 

Good luck!


A. No its not overclocked
B. I will do that when I get back home to the box.

I'll try turning ACPI off and see if that helps

I'll look into Dapper as well.

 Thanks

---

### Post by samuraix51 on 2007-04-25
Here is my motherboard and chipset specs

Gigabyte 8I845GVMRZ motherboard
Intel i845G chipset

---

### Post by samuraix51 on 2007-04-27
So I tried Dapper, and the same thing kept happening, I also tried turning off acpi and that didn't solve it either.  Anyone got any other ideas for this?  An alternate install way or something?

 Any help is much apprciated.

---

### Post by danielm on 2007-05-10
Hmm, probably not relevant, but you can try adding irqpoll to the boot flags (F6 at the first install menu will let you edit them; add it after the quiet spash). In my case, the install wouldn't even load because for some reason Feisty can't see my ATA drives without that poll (funny, edgy did).

I too am of the opinion Feisty is a disappointment with respect to hardware support. I'm also having problems with my system locking up which is related to my video card/driver.

---

