---
title: "[SOLVED] problems with installing ubuntu on a external hard drive"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by Darth0wned on 2008-01-28
i have installed ubuntu to an external drive, as the main drive is windows xp, the problem is that when i installed it i could no longer boot xp or the linux, and it doesnt even recognise my internal hard drive, i dont know what to do, because every time i try to use the xp recovery console, at the windows setup disk, but the keyboard wont work when it gets there.

i get a GRUB error when trying to load windows

i need help because i cant use that pc .

---

### Post by RudolfMDLT on 2008-01-28
You need to tell the BIOS(start praying here :) ) to boot from a usb drive. Not all Bios's can do this. I have installed Ubuntu on a flash drive before, but you need to be VERY careful when doing this.

Look around in you bios for an option that will have something to do with booting off of a USB drive. 

If you can't boot from a USB drive, I recommend that you use the Ubuntu Live CD and either install Ubuntu on the same drive as WinXP or at least use the live CD to install GRUB to the actual fixed drive. But we can get there later. First see whether you can't boot from the USB drive. Then unplug the USB drive and try booting normally, make sure that your BIOS can see the fixed Hard Drive during the POST or in the BIOS. Report back on what you find! Goodluck!

---

### Post by Darth0wned on 2008-01-28
the instillation didnt work properly on the usb, and the ubuntu i will try a gain

---

### Post by Darth0wned on 2008-01-28
the good news is that when booting from the ubuntu disk, i saw that my hard drvie was stillthere ( aka not dead) so now i will work on removing what i think is the grub files from it, but from ubuntu how can i fix the mbr for windows?

---

### Post by RudolfMDLT on 2008-01-28
You boot into the Windows recovery console and I think there is a command, fixmbr?

> Insert the XP CD and boot from it. When the setup starts type R for the recovery console then it will ask you to logon to your windows partition. When logged in you can type FIXMBR press [ENTER] and confirm with Y. This will re write the MBR. 

Though you do need a keyboard for this! ;) Try borrowing a standard USB or PS2 keyboard from a friend?

The reason that I said you should install Ubuntu or at least install GRUB is that grub is a boot up manager and will allow  you to boot windows and Ubuntu.

If you don't want Ubuntu anymore, you'll have to get the Recovery console in Windows to work with a keyboard or completely reinstall windows.[thats why I run Linux]

Goodluck and post back if you need anyhelp.

---

### Post by Darth0wned on 2008-01-28
well you see i reinstalled ubuntu to a 100gb i made of my main disk, but it still doesnt seem to boot, because the first instillation to the usb hd acc installed grub to windows, so now i cant load either

---

### Post by Mze on 2008-01-28
Check this[ thread]("http://ubuntuforums.org/showthread.php?t=80811") out.

---

### Post by RudolfMDLT on 2008-01-28
> **Mze said:**
> Check this[ thread]("http://ubuntuforums.org/showthread.php?t=80811") out.

I had to find that out on the hard way! ;)

> ( STEP 3 ) When the install gets to loading the GRUB bootloader ... DO NOT LET IT LOAD TO ANY OTHER DRIVE BUT THE EXTERNAL USB drive we are working with here.

I had all my drives unplugged when I did the install.

@Darth0wned

Dude, what exactly is your situation and the moment, and what do you want to end up with?

Please explain in detail what you have done, what your current partition configuration is, and exactly what is wrong. Then tell me in detail what you want to end up with? That way I can help you quicker. I'm not exactly sure what you are sitting with right now Windows and Ubuntu on the same hard drive but they still can't boot?

---

### Post by Darth0wned on 2008-01-28
ok first problem grub is on windows disk, ubuntu is on partition one of hd and on usb hd, the usbhd is configured properly, but the windows grub still interfeares.., i want to have a windows and linux on partitions of my man hard drive now

---

### Post by Darth0wned on 2008-01-28
i am having trouble booting any of the lnux instillations, and i cant seem to fix the prob with ms-sys from ubuntu or a recovery disk that had ms-sys , and when the menu on xp comes up that doest work with me pressing any keys, so i dunno what to do atm.

---

### Post by RudolfMDLT on 2008-01-29
Cool - That is very possible! :)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

That should sort you out and get you into Linux. This may not work for XP, but first let us fix GRUB and then, if XP still doesn't boot, we can add the code for XP later.

---

