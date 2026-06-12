---
title: "Ubuntu Live CD"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by Deasuratae on 2007-02-28
>.<

Ok, I saw Ubuntu on a computer at work and want to try it out.

I have downloaded the ubuntu 6.10 desktop i386 iso... burned it to a cd... made sure it is working right... but its not

I boot up my comp with the cd in, it loads the boot menu. I choose start or install Ubuntu... and it runs the loading splash screen.

It runs that for about three minutes and then goes to an all black dos screen with the lil blinking white line at the top. You cannot type anything or do anything save for ctrl alt delete restarting the computer. I tried starting Ubuntu in Safe Graphics Mode.... I got the same thing.

What might be causing this?

---

### Post by mikewhatever on 2007-02-28
Hi,
there are several things you could try. Fist tell us your hardware: cpu, ram, video & sound cards, etc. Anything you know can be helpfull in case of hardware incompatibility.

md5sum check the iso file you've downloaded
[https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29](https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29)

run the cd integrity check from the fist load screen

reburn the iso at low speed, even if the two checks above are ok.

---

### Post by Deasuratae on 2007-02-28
Right, did the MD5sum check, came back with no errors or differences.

Rebooted with the disk, chose the check CD for Faults option... it switched to the same load bar thing that it does with the other two options, went for a few minutes... then did the same thing, so I dont know results for that.

My System is as follows

Processor Intel Pentium 4 3.0 Ghz processor
512 MB DDR2 Ram
Radeon 9200 series Graphics card (no onboard video card available)
as for sound, not sure... its onboard

HDD are Maxtor 160 gig for main, Western Digital 80 gig secondary and a Samsung 20 gig as the third...

DVD/CD combi writer but dont know the make.

1 unused dial up modem.

on the outside I have my keyboard on USB, and also a Graphire Tablet on USB... oh, and my Wireless Broadband Hub too

---

### Post by Kateikyoushi on 2007-02-28
I would try the following.
Boot from the cd at the menu press F6 then start with these options.

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by trippingbillee on 2007-02-28
I have a similar problem, except that it moves from the blinking white line to some strange patterns and lines on the screen. It stays there until I shut down. Should I try similar settings, or are there any other ideas?

---

### Post by Kateikyoushi on 2007-02-28
That sounds like video related so try safe video mode first.

---

### Post by trippingbillee on 2007-02-28
Did that, same problems.

athlon 3500
corsair value select 2x512 pc3200
nvidia geforce 7900gs
audigy 2

---

### Post by SaddisticTwist on 2007-02-28
> **Kateikyoushi said:**
> I would try the following.
Boot from the cd at the menu press F6 then start with these options.

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

Say, I did that. My Ubuntu loaded. So I decided to install to HD. After which,  when I restart and load Ubuntu. It will hang at the splash screen once again. So I do I put those lines in after Ive installed.

---

### Post by Deasuratae on 2007-02-28
Ty Am going to try with those settings now... by the way...

What do they do? what do they disable or change?

just so I know

---

### Post by Deasuratae on 2007-02-28
Well, Without having to put that stuff in, I got it working... I reburned my disc at 2x speed and it all works now

:lolflag:

---

### Post by gusc on 2007-03-01
It seems i have same problem:

I boot from LiveCD (6.10), press Start or Install Ubuntu, it does some loading and at point of (about) 97% (on progress bar) ir shows up some blue/green artifacts on the screen (seems like video glitch). I tried to boot in Safe Mode - same effect. Then I changed VGA mode to 
"1024x768 16" (and others also) I got that blue underscore blinking in the corner (after loading kinda completed) and after few seconds X11 error screen appeared. Error was something like "No Display found. View report." - i read through this big log and it showed up search for video drivers, it found my card and further on there were lots of errors :)

My PC: AMD Athlon64 3200+, 1Gb RAM, ATi Radeon X800 (in log it showed up that X800SE was mine), motherboard with nForce 4 chipset.

I'm kinda sure it might be a video related problem, but maybe you have some solution or advice.

PS. I also tried to burn LiveCD with slower speed (16x was the slowes I could get for CD-R)

---

### Post by ChuckC on 2007-03-27
I'm having a similar problem with the 6.10 LiveCD.  I boot from the LiveCD, all the splash screens show up fine, but when it comes time to boot into the OS, my monitor just reports "Invalid Mode" and I see nothing.  I HEAR the Ubuntu startup sound though, so it seems like I'm not hanging, just not getting desired video output mode.  I also tried Safe Video mode with the same results.

My monitor is a Vizio P50HDTV plasma screen with a VGA input and my video card is an ATI Radeon 9200.  In Windows, I am running at 1024x768 (the preferred resolution of this plasma screen according to its manual) and 32-bit color.  Choosing those settings from the Ubuntu boot screen using the F4 key still results in "Invalid Mode".  Unfortunately, as far as I can tell, my plasma doesn't have any on-screen menus that let me see what video mode it thinks it is getting fed.

Any ideas?  Obviously I can't edit xorg.conf because this is not a hard drive install (I just want to take the LiveCD for a spin to see how Ubuntu does with my system), plus I wouldn't be able to see it anyway.  I also can't see any error logs to get you any info from them.  Is there some key I can press during bootup to see what's going on during bootup rather than just seeing the splash screen?

---

