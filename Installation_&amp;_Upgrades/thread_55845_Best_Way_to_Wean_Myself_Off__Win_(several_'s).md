---
title: "Best Way to Wean Myself Off  Win (several ?'s)"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by cjoshuav on 2005-08-10
Thanks to all of you who have been so helpful as I did my first trial install of Ubuntu.

I'm now committed to, at the very least, running a dual-boot system; but I'm sorely tempted to try running a Linux-only system and running my key windows app's in a shell.

I've got a pretty high-end laptop (Dell XPS2 with a 256MB nVidia GeForce Go 6800 Ultra and 2GB of RAM).

Here are my make-or-break Windows app's:

- EndNote (I'm a Ph.D. student, and none of the Linux-native app's I've tried are as robust)
- PocketPC applications (I review them)
- New Windows Games (I review them)

Can I manage to run all of the above with WINE or some such?  
Am I better off going ahead and investing in VMWare?  
If I do use VMWare, does VMWare run *in* Linux (as a Window?)?  I found the VMWare website a bit confusing, and I wasn't even sure which app I would want to buy?
Should I just go ahead and do a dual-boot system (I'd rather not).
If I go the VMWare or emulator route, will I need a Fat32 partition or can I keep everything Ext3?

Thanks very much for your help.

One other thing.  I tried playing around with Kubuntu and decided I'm more of a GNOME guy.  I've tried to apt-get remove kubuntu-desktop; but I've still got lots of kde hanging around.  How do I make gdm my default desktop, etc in all ways?

Joshua

---

### Post by pmjdebruijn on 2005-08-10
Hi,

I think, for your purposes you would be best off with a dual boot system...

WINE does not properly do DirectX... well it does... but very limited... And it's bitch to setup...

WineX/Transgaming might suit your better for game reviews, but these might introduce screen artifact and/or errors not present when running in Windows. So using WINE might influence your reviews...

For EndNote/PocketPC apps maybe Crossover Office? Anyway, here again, with a dual boot, you'll be sure to have everything properly working...

Please keep in mind that VMWare has a significant performance impact, and doesn't do OpenGL/DirectX acceleration, as far as I know... 


Generally please post seperate questions, when asking about totally different topics... but gdm isn't a desktop, it's login manager... I'm assuming your using kdm now... Remove kdm from your runlevel 5 and add gdm...

Regards,
Pascal de Bruijn

---

### Post by xaque on 2005-08-10
To find out what applications run under Wine, check out the Wine Application Database (appdb.winehq.org). It's still somewhat incomplete, but it's getting better.
According to the AppDB, Endnote runs under Wine, but pmjdebruijn is right: Wine sucks at DirectX right now. As for PocketPC, I have no idea... you're probably better off sticking with Windows for those.

---

### Post by cjoshuav on 2005-08-10
On a dual-boot system, any partition that I want both OS's to be able to read will have to be FAT32, correct?

Joshua

---

### Post by varunus on 2005-08-10
> On a dual-boot system, any partition that I want both OS's to be able to read will have to be FAT32, correct?

Joshua

Correction, any partition that you want both OS's to be able to read and write will have to be FAT32.

Linux can read NTFS out of the box, and you can use the Captive driver to write it as well, though its a pain to set up.  And with this software, Windows can read/write ext2/ext3.
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
Never used it, though, so I don't know how trustworthy it is...Some other forum posters said they used it, though.

---

