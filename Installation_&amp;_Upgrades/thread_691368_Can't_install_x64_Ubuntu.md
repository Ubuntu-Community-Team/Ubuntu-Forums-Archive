---
title: "Can't install x64 Ubuntu?"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by tehpwnerofn00bs on 2008-02-08
I'm having some major issues installing the 64-bit version of Ubuntu 7.1. I don't have any issues with the 32-bit (I'm using it right now). But when I run the x64 install disk, it comes to the menu, I select install, and it say something about loading the kernel, then the screen goes blank. Nothing happens. I've waited until my monitor goes into standby because it isn't getting any input from my computer. I've used many different disks, so I know I don't have a faulty install disk, but I need to use the x64 so I can run Folding @ Home. 

Does anyone know what might be wrong?

Thanks. :)

---

### Post by chrisdeckard on 2008-02-08
What kind of CPU do you have?  It may not be 64-bit compatible.

-Chris

---

### Post by tehpwnerofn00bs on 2008-02-08
I have a Q6600 (definitely 64-bit), an EVGA 680i mobo, SLI'd 8800GTXs and 2gb of ram. Oh, and I have tried both the regular and alternative installation CDs.

---

### Post by ErusGuleilmus on 2008-02-08
It could be a bad burn, couldnt it? Try reburning the disc at the lowest speed possible.

EDIT: Found this post. maybe it will help. [http://ubuntuforums.org/showthread.php?t=667080](http://ubuntuforums.org/showthread.php?t=667080)

---

### Post by tehpwnerofn00bs on 2008-02-08
Nope. I've burned about 6 disks. some as low as 4x, and I even paid $10 to get a disk sent to me. (I figured i was just doing it wrong :()

---

### Post by ErusGuleilmus on 2008-02-08
Could you maybe put up what message you get when you try to boot the disc?

---

### Post by chrisdeckard on 2008-02-08
Hmmm, you've got me.  Should definitely work.  Sorry I'm not much more help.  Did you try the low graphics mode?  It may be a video card framebuffer driver issue on x64.  I know on my laptop, I had to install using the low graphics mode.

-Chris

---

### Post by tehpwnerofn00bs on 2008-02-08
Erus, Thanks for the link, that was pretty helpful. Its good to know others are stuggling with this too. I'll try using the F6 key to disable the splash and quiet commands, and try reburning the alternate CD. I'll let you guys know is a few minutes what happens.

---

### Post by ErusGuleilmus on 2008-02-08
I wish I could say I had the same problems as you. I wish I had a Quad Core setup. :) Just thought I would give it a shot.

---

### Post by tehpwnerofn00bs on 2008-02-08
Alright... so I reburned the alternative disk and it installed. however, I have the same issue once I try to actually run it. It just goes to a blank screen. I even left it for 15min and it still wouldn't go. However i did run it in recovery mode and it works fine.

So as it stands right now, the 32-bit works fine and the 64-bit recovery mode works. But the regular 64 doesn't and neither does the regular install disk. Could it be something to do with display drivers?

---

### Post by chrisdeckard on 2008-02-08
When you get the grub loaded, hit escape.

You want to edit the boot line options.  Hit e, a couple times to finally get to the boot string that it's going to use.  You want to edit the line with the kernel options, and add vga=791 (this is 1024x768, 24-bit color for your framebuffer).

See if that works.  If it does, you'll want to edit /boot/grub/menu.lst and find the place in there and edit the "defoptions" line.

-Chris

---

### Post by tehpwnerofn00bs on 2008-02-08
thanks, but is there a way to get it to be 1680x1050 to fit my monitor?

---

### Post by tehpwnerofn00bs on 2008-02-08
I tried what you suggested, but no dice. :(

---

### Post by chrisdeckard on 2008-02-08
vga=865 is for 1680x1050.  That's what I use with an NVidia Quadro NVS 140.

-Chris

---

### Post by Aethor on 2008-02-08
I had the same problem. Usually, the splash screen is the problem.

When you see the initial list of boot options, hit 'e' to edit the one you want to use, and in there, remove 'splash'. Then boot from there. This works for both the install CD and already installed Ubuntu on a hard disk.

To make this permanent, edit /boot/grub/menu.lst and remove splash option from all versions of boot.

Use this when booting from the install CD if you want to install while in graphic mode. Or install in text mode, and use this on first boot of installed system, then edit menu.lst.

---

