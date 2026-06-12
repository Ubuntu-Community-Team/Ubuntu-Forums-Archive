---
title: "My system hangs :-("
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by Drewstain on 2006-04-10
Pardon me.  I just wanted to revive my old system, but it appears that I migh just have to take it back to its dark corner as it hangs when I tried Ubuntu.

The system is an old Dell 
Processor   550
96M SDRAM
CD rom 

Ubuntu appears to load, and everything is "OK", but somewhere the screen just goes blank, and it also appears to have a cursor on the top left corner but I can not type or do anything.

Does any one have any sugestions?  I really do not want to spend over $100 just to upgrade the memory but if that is the issue, then I guess that is the end for that system.

Respectfully,
Drew

---

### Post by ledonnell on 2006-04-10
Sounds to me to be an X issue.  Perhaps putting another vid card in temporarily to check it.

[QUOTE=Drewstain]Pardon me.  I just wanted to revive my old system, but it appears that I migh just have to take it back to its dark corner as it hangs when I tried Ubuntu.

The system is an old Dell 
Processor   550
96M SDRAM
CD rom 

Ubuntu appears to load, and everything is "OK", but somewhere the screen just goes blank, and it also appears to have a cursor on the top left corner but I can not type or do anything.

Does any one have any sugestions?  I really do not want to spend over $100 just to upgrade the memory but if that is the issue, then I guess that is the end for that system.

Respectfully,
Drew[/QUOTE]

[QUOTE=hizaguchi]Yeah, the fan is working fine.  And yeah, it's a Dell Inspiron 4150. ](*,)  I'm probably having that same motherboard problem.

This is just one of a long list of things that broke about a month after the warranty expired.  I don't thin

k I'll be buying any more Dells.

Thanks for the info.  I was hoping there'd be a cheap fix.  Hmm, 512 meg ram sticks are $37 over at newegg...[/QUOTE]

---

### Post by Drewstain on 2006-04-10
Well that is what I thought, but the original system came with:
Intel 810e chip set with Dynamic Video Memory and 4-MB display cache memory

So I installed a 64M TNT.

Now is there a command that will only install the bare minimum, or should I try Ubantu 4.1?

Drew

---

### Post by Kapre on 2006-04-10
[QUOTE=Drewstain]Well that is what I thought, but the original system came with:
Intel 810e chip set with Dynamic Video Memory and 4-MB display cache memory

So I installed a 64M TNT.

Now is there a command that will only install the bare minimum, or should I try Ubantu 4.1?

Drew[/QUOTE]

Drew - from your 1st post, you have the lest than minimum requirements for a gui linux. But it can work. But you need to make sure to give a bigger swap (what is your HD size?) and use Xubuntu (Ubuntu with XFCE). 1st is you need to install "server" then read  [thread]("http://doc.gwos.org/index.php/Minimal_Install") from Ubuntu Docs

K

---

### Post by Drewstain on 2006-04-13
My system has a 10G HD

I found Ubuntu 4.1 and it appeared to have install great, then it asked if I wanted to download all the packages via internet to which I said yes.  After all the downloading it re-started, but the monitor is just black/blank so I do not know what to do.  I have done this procedure three times so now.  

Does this means that the OS does not recognize the video card?  If so what do I need to do to by-pass that and make it think is a generic card?

Note:  I have never seen the logging screen.

Drew

---

### Post by Drewstain on 2006-04-13
I decided to pay more attention when the system starts and this is what I found:

GRUB loading stage 2 

Starting hotplug subsystem
     Modprobe: Fatal: Error inserting pciehp (/lib/module/s.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permited

     Modprobe: Fatal: Error inserting shpchp (/lib/module/s.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permited

So it looks like this module is not being loaded for whatever reason

At the very bottom I can barely see something like #something login: but then the monitor goes blank.

I have no clue what this means as this is my first try at something other than Windows.

Drew

---

