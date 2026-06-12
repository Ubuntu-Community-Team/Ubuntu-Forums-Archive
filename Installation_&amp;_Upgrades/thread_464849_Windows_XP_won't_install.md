---
title: "Windows XP won't install"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by ProfessorMembrane on 2007-06-05
I orginally had a dual-boot setup between Ubuntu and Vista on a single hard drive. I then decided that vista was rubbish and thought i'd format that partition and install windows xp. I put the (working) installation cd in at boot, which loaded for a bit, then gave the message below.

I thought it might be because windows detected the ext3 partition that ubuntu was on and freaked out, so I formatted both partitions, to start over. But even now i still get the error message. Grub is still on the MBR, could this be causing the problem?

I use a Lenovo 3000 notebook.

[B]"A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps:

Check to be sure you have adequate disk space. If a driver is identified in the Stop message, disable the driver or check with the manufacturer for driver upates. Try changing video adapters.

Check with your hardware vendor for any BIOS updates. Disable BIOS memory options such as caching or shadowing. If you need to use Safe Mode to remove or disable components, restart your computer, press F8 to select advanced startup options, and then select Safe mode.

Technical information:

*** STOP: 0x0000007E (0xC0000005,0XF76120BF,0XF7A5E208,0XF7A5DF08)

***      pci.sys - Address F76120BF base at F760B000, datestamp 3b7d855c"[/B]

---

### Post by Bart Ellebaut on 2007-06-05
> A problem has been detected and windows has been shut down to prevent damage to your computer
Well at least Windows knows they damage your pc :D

Normally when you format , You shouldn't hava eny problems. 
I had the same problem with me previous laptop. Never was able to solve it, suddenly my motherboard crashed.

---

### Post by Kevanx on 2008-06-17
I'm running into this same obstacle right now. It looks as though it could be a bunch of things, which doesn't make it easy.

It sucks having to go back to windows, but my curiosity about bioshock overtook me.

1. it could be a pci based graphics card. SP1 doesn't recognize this. In which case, disabling your onboard graphics card in the BIOS should allow it to load properly.

2. It could be broken memory or a MoBo problem. I think that this might be my issue. Run memtest86.

3. It could be a SATA hard drive, which XP build SP1 doesn't recognize.

Most people seem to have found a solution using a slipstreamed XP SP2 install disc. I tried making this, but it didn't seem to work for me, and using WINE to make it wasn't straightforward either, so you probably need to burn it on an XP system to do it.
[http://www.theeldergeek.com/slipstreamed_xpsp2_cd.htm](http://www.theeldergeek.com/slipstreamed_xpsp2_cd.htm)

If I find a different solution, I'll post it.

---

### Post by Kevanx on 2008-06-18
Fortunately for me, it wasn't broken memory, or motherboard. The tutorial I linked to previously at eldergeeks.com worked brilliantly. XP SP1 doesn't support PCI graphics cards and the like (or for that matter, SATA drives). An SP2 slipstreamed disk will probably fix it.

I didnt' have nero or roxio, and the first try with Sonic didn't work for me. I found that [Nlite]("http://www.nliteos.com/") worked flawlessly, and easier than other iso burning software I had used. It also allowed me to uninstall a heap of the unnecessary windows software, which can be a pain to get rid of later on.

I highly recommended that free software for those of you who for whatever reason are required to pollute your pristine hardware with a dual-boot install.

The best part - the SP2 slipstreamed disc recognized the partitions, so I didn't need to wipe the disk, and reinstall everything on the linux side. I heard that sometimes windows install discs try and overwrite anything.

---

