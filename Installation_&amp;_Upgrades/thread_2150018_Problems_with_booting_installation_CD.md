---
title: "Problems with booting installation CD"
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by kaffekanne on 2013-05-30
I've been making a certain number of attempts on installing Xubuntu on my computer. I've burned several DVD's and even tried USB-installer but I get nowhere. The problem remains the same. Whenever I boot from a DVD I get to choose whether I want to try Xubuntu or install it. Same thing happens regardless of what I click, and what happens is that the DVD spins up again and you see a little cursor flashing in top left, and there is stops. I've waited for it, took a walk, made some food, watched some TV, but nothing happens. 
Is there anything I could do in the BIOS? I read in [this thread (Asus ROG forums)]("http://rog.asus.com/forum/showthread.php?28449-How-do-I-install-Linux-on-my-Rampage-IV") that I could set "acpi=off", but have no clue what that is.

I believe I tried this with Ubuntu aswell, so regardless of which version I'm installing the problem remains the same.

Thanks
-Kaffe

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]kaffekanne; Hi !

Try this and see how far you get :
[/COLOR]Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; - try "nomodeset" first - for other additions ,not on the presets, the boot options kernel boot line is now available, append any desired boot parameter to the end of the line, if not using the presets.
Enter key to continue the boot process to the GUI desk top;
At the desk top, key combo clt+alt+t activates a terminal..
...and we will continue when you reach this stage.

Please to advise what version and method you use to install, and what machine.

[INDENT=2]
where there is a will there is a way

[/INDENT]

---

### Post by kaffekanne on 2013-05-31
Thank you for giving me some advice!
I tried what you said about the boot options. I first tried it with only nomodeset and that didn't work. After reseting the computer and booted up the CD again, i now set it to both acpi=off and nomodeset and that didn't work either.

Also I have a self-built computer and the main component specs is as follows:
Motherboard: Asus Rampage IV Gene
CPU: Intel Core I7 3820
RAM: Corsair Vengenance 8GB 1866MHz CL9 (Prod.a[FONT=arial]rt[/FONT].nr.: [COLOR=#404040][FONT=Arial]CMZ8GX3M2A1866C9)
[/FONT][/COLOR]I have read in the "NewDocs", that your signature is referring to, that there could be problems with my optical drive I'm using due to its age. Although my DVD drive isn't really.[COLOR=#404040][FONT=Arial]
[/FONT][/COLOR]

---

### Post by Bashing-om on 2013-05-31
[COLOR=#000000]kaffekanne; Hey --

Right now I am scratching my head over this.
Let us back up once again to basics;
1. Verify the md5sum of the install disk,(NewDocs -"howto md5sum")
2. Does the mother board support UEFI ? If so, work-abouts may be needed,
3. In bios please insure that the boot priority is set to boot the drive that 'buntu is to be installed onto - I have been going round-and-around with my system on a new install, thinking my bios was set correctly, WRONG !
4. What version/distro are you trying to install ? I am aware that sometimes it "was" needed to disable the graphical "introduction to ubuntu"
to get it to install..
5. Verify that you are not installing a 64 bit version on a 32 bit architecture.
[/COLOR][INDENT=2][COLOR=#000000]
what can I say else ?
[/COLOR][/INDENT]
[INDENT=4][COLOR=#000000]where there is a will there is a way
 [/COLOR][/INDENT]

---

