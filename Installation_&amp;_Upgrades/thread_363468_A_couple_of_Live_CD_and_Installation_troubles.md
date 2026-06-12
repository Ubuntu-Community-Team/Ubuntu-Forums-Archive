---
title: "A couple of Live CD and Installation troubles"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by lominare on 2007-02-17
Hello,
I'm attempting to boot the ubuntu amd64 live CD with an eye towards eventually installing Ubuntu permanently.  However, I'm currently encountering a couple of problems that are preventing me from doing this.
First, if I try to boot normally using the first option on the Live CD, I receive the following message (where X is a random digit):
[   XX.XXXXXX] Kernel panic - not syncing: IO-APIC + timer doesn't work! Try using 'noapic' kernel parameter
[   XX.XXXXXX]

Okay, I'm a newbie but I can read, so I try pressing the 'Further Options' key and put 'noapic' at the end of the line of kernel parameters.  When I do this, I no longer receive the kernel panic message, but the loading screen that appears next is in black and white and partially garbled.  When loading finishes, I get a series of screens made up of blue and red windows with borders made of strange ascii characters, and a message saying the X server could not be started.  It asks if I would like to see the log file, and when I look at it, it includes these messages:
(EE) No devices detected
Fatal server error:
No screens found.

When I eventually exit out of those screens, I'm left with a black screen with a line cursor in the top left corner, and I can't go any farther.

If anyone can help me with any of the above issues or point me in the direction to get started looking for answers, I would greatly appreciate it.  Here is some information about my system.  Please let me know if I need to include anything else.

Motherboard: Foxconn C51XEM2AA
Processor: AMD Athlon 64 X2 Dual Core 3800+ (AMD Opteron 8212)
BIOS Version: Nvidia - 42302e31	Phoenix - Award WorkstationBIOS v6.00PG
Video Adapter: ATI RADEON X850 XT 256 MB
RAM: 2GB
Hard Drive: Western Digital WDC WD2500KS-00MJB0	250GB IDE SATA-II
CD-ROM NEC DVD Writer _NEC DVD_RW ND-3550A IDE ATAPI


Thanks,
--lominare

---

### Post by teaker1s on 2007-02-17
okay well from my experience your problems relate to noapic and also ATI driver issue not installed/miss- configured by how xserver is behaving.
If you search the forums regarding your graphics card your sure to find the driver solution as others have complained.

Reason I have no more direct answers is because I have no working experience with ATI, but rest assured your situation is resolvable 

welcome to the forums

---

### Post by eapache on 2007-02-17
They're actually two separate problems. You fixed the first one yourself, and to fix the second one, follow these instructions that I got from aberry555 in regards to my own ati card:

> This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line.

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better ).

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum!

If these don't work, post the new x error, and I'll try to give a more precise method of completely rebuilding the xorg.conf file.

---

### Post by bilbothebaggins on 2007-02-18
Greetings.

Just wanted to say that I have a ATI X800SE and the 6.10 Live CD also initially crashed on me and after using this break=bottom procedure here I got it running :)

cheers.

---

### Post by lominare on 2007-02-18
Just to follow up, I'm posting this from Ubuntu, so I'm happy to report success from your suggestions.  I had foolishly assumed that I had improperly resolved problem A and that was the cause of problem B, so I hadn't looked for independent solutions to problem B.  And this despite knowing full well what assuming does to you.  Oh well, I'll know better next time.  I appreciate all the help!

Thanks,
--lominare

---

### Post by epb on 2007-02-21
I'm also using the live-cd and are having these troubles as well (although not at every statup - sometimes it's working just fine!) but i've got a built-in Intel GMA 950 graphics card.. not an ATI! Do you think these fixes would work for me too?

---

### Post by teaker1s on 2007-02-21
> **epb said:**
> I'm also using the live-cd and are having these troubles as well (although not at every statup - sometimes it's working just fine!) but i've got a built-in Intel GMA 950 graphics card.. not an ATI! Do you think these fixes would work for me too?

[B]If you decide to install with Intel GMA 950 then there is a known resolution bug with it and 915resolution package resolves it.

[/B]

---

### Post by Zelutos on 2007-02-27
Thank you for your knowledge. With my ATI x850 putting in 'radeon' did the trick. I knew I had to change that ATI driver to something (I wanted to avoid Vesa) but I didn't know to do the 'break=bottom' thing. Again thanks for the great answer of a very annoying bug!

---

