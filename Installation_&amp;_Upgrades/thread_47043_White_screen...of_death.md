---
title: "White screen...of death?"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by Yorak on 2005-07-07
Hi, I am new to Linux. A friend told me to try Ubuntu as my first Linux, so I'm trying. I downloaded the Live CD, put it on a CD. The installation starts where you have to hit the return/enter key to begin the installation. It installs a few things then goes to a blue screen that fades quickly into a bright white screen. Then nothing happens.

Here are my specs:

Dell Inspiron 6000
Pentium M Processor (1.6 GHZ)
Radeon x300
Wi-Fi Connection

---

### Post by bunced on 2005-07-07
[QUOTE=Yorak]Hi, I am new to Linux. A friend told me to try Ubuntu as my first Linux, so I'm trying. I downloaded the Live CD, put it on a CD. The installation starts where you have to hit the return/enter key to begin the installation. It installs a few things then goes to a blue screen that fades quickly into a bright white screen. Then nothing happens.

Here are my specs:

Dell Inspiron 6000
Pentium M Processor (1.6 GHZ)
Radeon x300
Wi-Fi Connection[/QUOTE]
 Where exactly does it fade? What goes just before.

---

### Post by Yorak on 2005-07-07
I think it says something like the name of the video card and [OK] or something like that, then goes to a blue screen, then quickly fades to a white screen. Nothing is on either blue or white screen.

---

### Post by notos on 2005-07-07
You downloaded the "live CD" and you are instaling it?


Well if you downloaded the live CD you dont need to install anything

If you downloaded the install CD ... well never had that problem with ubuntu or debian ...:S

you could also change to other TTY to see some debug

CTRL+ALT+ F1 -> F6

or alt + Left/Right Key 

you may find whats goin on :)

---

### Post by audax321 on 2005-07-07
Try hitting CNTRL+ALT+BACKSPACE a few times and see if you can get back to a linux prompt. Log in (I think for the LiveCD you just put ubuntu as your username and leave the password blank, but I might be wrong) if you have to and then type:

sudo nano /etc/X11/xorg.conf


Then when the file opens up, go down to Section "Device" and try changing the driver to "vesa"

Then push CNTRL+X to exit and Y to save it. When you get back to the prompt type startx and see if that fixes it. I had a similar problem a long long time ago and this fixed it. Its a LiveCD though, so as soon as you reboot you will lose all your changes... it doesn't actually install anything on your computer, just loads it in memory temporarily.

good luck  :)

---

### Post by Yorak on 2005-07-07
Nothing worked. Once you get to that screen there is no key combination to allow yourself out of it.

---

### Post by Yorak on 2005-07-07
Okay now this is really bothering me. I decided to try the Install CD to notice it had the same beginning setup as the Live CD. All I can tell you is that it goes through, does a few things, I think one of the last things I see is PCI [OK] or something like that, it goes to a blue-ish screen that I can't really describe...then fades to a white screen. The cd stops spinning, and there I am with a bright white screen in which I can do nothing to return to any previous menus. If anyone could help, it'd be greatly appreciated.

---

### Post by mingus on 2005-07-07
[QUOTE=Yorak]Okay now this is really bothering me. I decided to try the Install CD to notice it had the same beginning setup as the Live CD. All I can tell you is that it goes through, does a few things, I think one of the last things I see is PCI [OK] or something like that, it goes to a blue-ish screen that I can't really describe...then fades to a white screen. The cd stops spinning, and there I am with a bright white screen in which I can do nothing to return to any previous menus. If anyone could help, it'd be greatly appreciated.[/QUOTE]

The problem is probably with the hardware detection.  Laptops are notorious for this because to pack everything in, the manufacturers frequently use proprietary non-standard components, BIOS, or OS tweaks.

Use the Live-CD first; it has drivers compiled into its kernel that the install CD does not.  Sometimes it is necessary to add kernel "arguments" to turn off certain hardware detection or to handle strange BIOS's.  Try these (there is a limit to nbr of arguments on a line, hence the need to spread across several attempts):

:live noapic nodma noapic nolapic vga=771 noapm

:live debian-installer/framebuffer=false debian-installer/probe/usb=false

:live aic7xxx=no_probe noscsi pci=noacpi pnpbios=off

:live nopcmcia noaudio mem=xxxM vga=normal
(where xxx is the amount of RAM - must be followed by a capital "M")

---

### Post by stalflare on 2005-07-08
[QUOTE=mingus]The problem is probably with the hardware detection.  Laptops are notorious for this because to pack everything in, the manufacturers frequently use proprietary non-standard components, BIOS, or OS tweaks.

Use the Live-CD first; it has drivers compiled into its kernel that the install CD does not.  Sometimes it is necessary to add kernel "arguments" to turn off certain hardware detection or to handle strange BIOS's.  Try these (there is a limit to nbr of arguments on a line, hence the need to spread across several attempts):

:live noapic nodma noapic nolapic vga=771 noapm

:live debian-installer/framebuffer=false debian-installer/probe/usb=false

:live aic7xxx=no_probe noscsi pci=noacpi pnpbios=off

:live nopcmcia noaudio mem=xxxM vga=normal
(where xxx is the amount of RAM - must be followed by a capital "M")[/QUOTE]
 Hi guys, sorry to bring this up again, I have had the same problems with the installation CD. 

but typing "linux vga=771 noapic nolapic" it worked its way into the installation screens...

Thought it might help, there is no need to dnload the other cd maybe..

---

### Post by allforcarrie on 2005-07-08
try another distro live disk, see if that works.

---

### Post by brim4brim on 2005-07-20
[QUOTE=stalflare]Hi guys, sorry to bring this up again, I have had the same problems with the installation CD. 

but typing "linux vga=771 noapic nolapic" it worked its way into the installation screens...

Thought it might help, there is no need to dnload the other cd maybe..[/QUOTE]
 This works for anyone having this issue or at least it did with my D810 Latitude.

---

### Post by noodle on 2005-07-20
You're not alone. 

I tried running the live CD on my laptop (Dell Inspirion 9300) and the screen just fades to white (with a brownish tinge) as well. I assumed the hardware was just incompatible. 

If you write to Dell, and ask them if this hardware is compatible with Ubuntu/linux they might be able to give you an exact reason why this happens.

---

### Post by Bari40 on 2005-07-21
[QUOTE=mingus]The problem is probably with the hardware detection.  Laptops are notorious for this because to pack everything in, the manufacturers frequently use proprietary non-standard components, BIOS, or OS tweaks.

Use the Live-CD first; it has drivers compiled into its kernel that the install CD does not.  Sometimes it is necessary to add kernel "arguments" to turn off certain hardware detection or to handle strange BIOS's.  Try these (there is a limit to nbr of arguments on a line, hence the need to spread across several attempts):

:live noapic nodma noapic nolapic vga=771 noapm

:live debian-installer/framebuffer=false debian-installer/probe/usb=false

:live aic7xxx=no_probe noscsi pci=noacpi pnpbios=off

:live nopcmcia noaudio mem=xxxM vga=normal
(where xxx is the amount of RAM - must be followed by a capital "M")[/QUOTE]


Thank you Mingus. I had a similar problem with my install CD, but instead of a white screen I get a black one with a blu box with a "OUT OF SCAN RANGE" written in it (see my post in the Live CD Support forum) I wrote the first line of Mingus suggestion and everything after that went smooth. It's a matter of fact that I'm writing this reply using Firefox from Ubuntu. Thanks again Mingus, you solved my problem .

---

### Post by RJARRRPCGP on 2005-07-21
[QUOTE=Bari40]Thank you Mingus. I had a similar problem with my install CD, but instead of a white screen I get a black one with a blu box with a "OUT OF SCAN RANGE" written in it (see my post in the Live CD Support forum) I wrote the first line of Mingus suggestion and everything after that went smooth. It's a matter of fact that I'm writing this reply using Firefox from Ubuntu. Thanks again Mingus, you solved my problem .[/QUOTE]

That message is from your monitor, because your monitor lost a video signal.

Many monitors give an out-of-range message if and when the video signal is lost.

---

### Post by mingus on 2005-07-22
[QUOTE=RJARRRPCGP]That message is from your monitor, because your monitor lost a video signal.

Many monitors give an out-of-range message if and when the video signal is lost.[/QUOTE]

To Bari40 -

The suggestion you followed from my earlier post was in response to another user's different problem, which was not known at the time to be video specific.  The above reply to you may be true, although it's not very helpful in terms of why or what to do about it (unless all that's being inferred is that the cable was loose).  However, this post does point to something important for you to consider:

In my post I supplied arguments to instruct the kernel to bypass or substitute a number of hardware detection tasks it performs, of which there are quite a few.  Once one has got the boot process working, one should isolate which specific task was the source of the problem.  Otherwise, one could be turning something off that you don't want to.

So, if you used a line like:  *noacpi nodma noapic nolapic vga=771 noapm*

You are turning off power management, changing how IRQ's are derived by the kernel from the BIOS, changing how the video framebuffer is called, and turning off the dma to all devices on the IDE controller. 

If your problem was only with the video, you definitely do not want to be using the other arguments.  In paticular, turning off dma (which is not supported on old hardware and hence needs to be disabled on those machines) may slow down the performance of your hard and optical drives (actually, the HDD will drop into PIO mode).

It's easy to test where you want to get to.  First, boot without the arguments, and see if your video problem repeats.  If it does not, as may be inferred in the post above, then don't use any, you solved the problem otherwise.  If it does repeat, reboot removing one argument at a time until you find the one that resolved the problem.  And note:  video problems are not always directly related to the video device itself, like the monitor or the adapter.  If one is using an AGP card, the problem can also be with the agp driver or an IRQ on the bus.  Just go about it methodically and you will isolate the actual cause and solution.

---

### Post by wulf on 2005-07-22
[QUOTE=mingus]To Bari40 -

The suggestion you followed from my earlier post was in response to another user's different problem, which was not known at the time to be video specific.  The above reply to you may be true, although it's not very helpful in terms of why or what to do about it (unless all that's being inferred is that the cable was loose).  However, this post does point to something important for you to consider:

In my post I supplied arguments to instruct the kernel to bypass or substitute a number of hardware detection tasks it performs, of which there are quite a few.  Once one has got the boot process working, one should isolate which specific task was the source of the problem.  Otherwise, one could be turning something off that you don't want to.

So, if you used a line like:  *noacpi nodma noapic nolapic vga=771 noapm*

You are turning off power management, changing how IRQ's are derived by the kernel from the BIOS, changing how the video framebuffer is called, and turning off the dma to all devices on the IDE controller. 

If your problem was only with the video, you definitely do not want to be using the other arguments.  In paticular, turning off dma (which is not supported on old hardware and hence needs to be disabled on those machines) may slow down the performance of your hard and optical drives (actually, the HDD will drop into PIO mode).

It's easy to test where you want to get to.  First, boot without the arguments, and see if your video problem repeats.  If it does not, as may be inferred in the post above, then don't use any, you solved the problem otherwise.  If it does repeat, reboot removing one argument at a time until you find the one that resolved the problem.  And note:  video problems are not always directly related to the video device itself, like the monitor or the adapter.  If one is using an AGP card, the problem can also be with the agp driver or an IRQ on the bus.  Just go about it methodically and you will isolate the actual cause and solution.[/QUOTE]
 Here's a variant on a WSOD. I've got a Packard Bell EasyNote laptop and have been using Ubuntu on it most of the time since last December. Sometimes, just as it reaches the end of the boot process, the screen whites out - if you're watching carefully you can often see the edges of the screen fading from grey to white.

Ctrl-Alt-BckSpace will often set things back, although sometimes I have to repeat that several times and sometimes it ends up switching greeter. It happens a little less often with the standard greeter than the graphical one and a little less with Hoary than Warty. It's not a showstopper but, although I've mentioned it here before, I haven't come across any ideas that help.

Do you think it's related to the problem above?

Wulf

---

### Post by wrtrdood on 2005-07-22
There may be more to this description than you know.  I got this once.  It happened on my Fujitsu P1120 after coming out of suspend.  I noticed as I opened the clamshell that the keyboard, indeed the entire PC, was extremely hot.  I don't think it had actually gone into standby.  Shortly after opening the lid, it did what you describe, though the color went from black to white.  It spooked me (brand new laptop) thinking the thing was burning up.  I shut it off and let it cool and when I turned it on again I was happy to find it booting normally.  I think this happened after loading the longrun module.  Seems it didn't work so well and I've not tried it since.

  You may be experiencing something similar that could be related to ACPI not working properly.  Just a thought.

---

### Post by wulf on 2005-07-22
Do you mean my experience? It's only been after the machine has been off for sometime. In fact, if I'm rebooting (mainly because I've popped into WinXP to use one of the programs I haven't got an equivalent for in Linux) I don't think it ever has a problem. I haven't been able to find anything in any of the /var/log files but next time I might try searching for 'apci' and see what I find.

Wulf

---

### Post by mingus on 2005-07-22
guys, just a general remark . . . the whole power management thing can get tricky with laptops . . . manufacturers do custom BIOS and extensions and other tricks with the hardware . . . a whole lotta stuff is playing together to make this work, and it's extremely complex.  And unfortunately, while acpi is a "standard", the implementations are very proprietary.  Many times a device shows a problem symptom that actually is due to power mgmt, not the device itself.

Also, btw, acpi and apic are very different animals.  One is power mgmt, the other IRQ assignment control.

---

