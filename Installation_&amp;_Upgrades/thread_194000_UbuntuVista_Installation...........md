---
title: "Ubuntu/Vista Installation.........."
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by EndGame on 2006-06-10
OK, I know already some of the opinion here concerning Vista but, be that as it may, some of us need to use/learn it and let's leave it at that.

My question concerns installation of Dapper with Vista/XP 64bit already installed and running. I have a complete drive to dedicate to Ubuntu on this system, but, my question and what I've searched for.............will this be as easy as simply allowing Grub to take over the initial booting considering Vista's new boot loader? 

Anyone having already done this, please let me know ASAP. I have the CD in my drive and about to just try it.......but don't want to mess up the Vista/XPX64 installs I already have up and running...........

---

### Post by Herman on 2006-06-10
You can back up your MBR and restore it again later quite easily using any LiveCD and any media. [*Click here*]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd") for how to do that. I haven't tested this on Vista yet, but it should be the same. Let me know if it doesn't work.
Regards, Herman

---

### Post by EndGame on 2006-06-10
I actually gave that a try earlier upon reading a thread. It shows the XP 64bit but shows no trace of Vista..........otherwise, I would have tried knowing I had a good backup of my mbr..........

Hard to believe that there's no more documentation on this than there is! I'm about to become a "guinee pig" and go for it.............but hate the idea of reinstalling XP64bit & Vista on this system just because I couldn't wait for a definative answer.........;)

---

### Post by Herman on 2006-06-10
> I actually gave that a try earlier upon reading a thread. It shows the XP 64bit but shows no trace of Vista..........otherwise, I would have tried knowing I had a good backup of my mbr..........Hmm, well maybe there is something different about the way Vista boots then. I don't know anything about Vista yet but I spend a lot of my own time using my own computers as guinea pigs to discover what can be done with Ubuntu for a hobby. It's no problem when there's no data at risk. I feel your pain, I wish I could help. > Hard to believe that there's no more documentation on this than there is! I guess you will have the honour of finding out and letting us all know. I think the Ubuntu and GRUB developers would know, but maybe they're busy developing and tend to skip the documentation side of things. Or maybe I just don't know how to find such docs and maybe wouldn't understand them anyway if I did read them.
Mind you I doubt if Microsoft would bother explaining to anyone how Vista boots and how to make it compatible with Linux. They would more likely do their best to keep that a secret and maybe even make it incompatible.
Would [GAG Boot Manager]("http://gag.sourceforge.net/") on a floppy or CD-ROM help? I always recommend people with more traditional versions of Windows make a GAG boot floppy disk before installing GRUB just in case. I don't know if that will be effective either, for 64bit and with Vista. [My GAG info Page]("http://users.bigpond.net.au/hermanzone/p12.htm").
It looks like I'll have to go buy modern new computers to keep up with new advances too, even just to maintain my hobby (website). 
EndGame, any feedback you can provide will be helpful to others, Regards, Herman :-k

---

### Post by jrd on 2006-06-11
To boot Vista with grub just choose "XP", then Vista's boot loader will give you the option of booting XP or Vista.

---

### Post by Herman on 2006-06-11
> To boot Vista with grub just choose "XP", then Vista's boot loader will give you the option of booting XP or Vista.   	
jrd, Thanks! 

Can anyone tell me anything about what differences there may be between Vista's bootloader and previous versions of Windows? Does it still use boot.ini and NTDRL? :confused: Herman

---

### Post by EndGame on 2006-06-11
[QUOTE=jrd]To boot Vista with grub just choose "XP", then Vista's boot loader will give you the option of booting XP or Vista.[/QUOTE]

Didn't work on mine..........I have the option to boot XP 64 but Vista is nowhere to be found.........

Herman: Vista uses BCD (boot configuration data) to load Vista. Earlier MS OS's are listed as "earlier Windows OS" and when you click on this option you are taken to the older ntldr boot loader............

You will find BCDedit (explained above) and bootmgr.exe which replaces earlier loaders. It's designed to be easier to mange and edit as well as quicker.........I'll agree with the quicker part but at this point...that's about it.

---

### Post by EndGame on 2006-06-11
Been trying to edit BCD/bootmgr to no avail........guess I'll look at Grub now...........

I can get to Ubuntu through a floppy with Grub but I'm not satisfied.......want to get this working!;)

---

### Post by EndGame on 2006-06-12
Well............I've come to the conclusion.................I can't do it. Grub/Lillo wipes out Vista boot loader and a repair to Vista BCD wipes out Grub/Lilo.......

I've searched endlessly and tried some scripts that others thought might work to no avail. At this point, it seems immpossible to have a dual+ boot with Ubuntu/Vista and whatever else.

---

### Post by SpartNux on 2006-06-22
[QUOTE=EndGame]Well............I've come to the conclusion.................I can't do it. Grub/Lillo wipes out Vista boot loader and a repair to Vista BCD wipes out Grub/Lilo.......

I've searched endlessly and tried some scripts that others thought might work to no avail. At this point, it seems immpossible to have a dual+ boot with Ubuntu/Vista and whatever else.[/QUOTE]

I've tried probably 5 times myself and wound up with the same conclusion - Vista kills Ubuntu and Ubuntu kills vista (boot sectors/ loaders) - Can't we all just get along ! ](*,)

---

