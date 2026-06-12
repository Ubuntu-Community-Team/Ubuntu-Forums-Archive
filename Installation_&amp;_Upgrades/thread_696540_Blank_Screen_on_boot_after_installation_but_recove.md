---
title: "Blank Screen on boot after installation but recovery mode works..."
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by acrim on 2008-02-14
Installed a fresh copy of 7.10 Desktop using the alternate CD (I had I/O error errno 5 when using the live CD).

The install completed fine, and GRUB appeared on boot (i'm dual booting with Vista). 

When I select Ubuntu from the GRUB menu I get a blank screen, with a few tiny white lines flickering in a sort of diagonal pattern across one of my monitors really, really fast (so fast I didn't notice them the first could of times).

If I boot into "recovery mode" everything appears to work fine, and I get dropped into the command line.

I'm thinking it might be something to do with VGA settings, but I'm not sure where to start when it comes to editing the x config. Could someone offer me some advice?

Thanks for any help in advance,

Some system info:
ATI Radeon HD 2900 XT (in dual head configuration with 2 x 21" Fujitsu Siemens widescreen displays)
ASUS P5B Premium Motherboard
Intel Quadcore Q6600 2.4GHz 64bit CPU
4GB RAM 
Ubuntu is on 3rd HDD: W.D. Raptor 150GB 10krpm

---

### Post by Venor on 2008-02-14
guessing you are trying 1680x1050 res.... doesn't seem to be supported on all machines.

---

### Post by hp59dk on 2008-02-14
I have a similar problem
I checked that the laptop worked fine with the live CD before installation, but now it can only start in recovery mode. I says very fast, so that i can not read it all, someting like "... cannot allocate ...", and there is seven or eight lines with that information. I can't freeze the screen with the "pause" button.

System: Acer Aspire 3050 (Aspire 3054WXMi); 14.1" WXGA Acer CrystalBrite LCD ...

Can I strat X from recovery mode?

Any help is welcome :)

Hans Pedersen

---

### Post by acrim on 2008-02-14
I can start x in recovery mode with "startx" which seems to work.

Still have the same problem when i try and boot into standard mode though.

I get a message about the Kernel tables just at the bottom of the screen, a flash of a message at the top of the screen which is too fast to read, then everything goes blank and nothing happens.

I've tried using the failsafe xconf file, but this doesn't seem to work either.

---

### Post by hp59dk on 2008-02-14
Following this [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox) i have solved part of my problem reported earlier in this thread.

I an not a newbie, but still I don't know what I do. I randomly tried to follow the advise, and now i can start ubuntu. In the process of configuring X i really randomly pushed buttons not knowing what i did.

Still: At fist i get a black screen. Ten I crtl+alt+F1 and the logon process continue. It says that i have Bios Bug #81 and that i cannot allocate somthing, that I am not quick enough to register. Nevertheless, Ubuntu starts and everything seems to be in order. But this is only the case when i am on AC-power. If I am on battery ubuntu can not start, it only shows a colored screen.

When I successful run Ubuntu i can crtl+alt+F1 again, and read the txt produced in the loginprocess. Unfortunately I can't read more txt than my screen displays. Here is some of it:

[I]Starting up
[Some number] PCI: BIOS BUG # 81 [49435000] found
[Some number] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[Some number] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
[Some number] PCI: Cannot allocate resource region ...
[/I]

How can i see the rest of the txt from the start where the Bios Bug is reported?

Computer: Acer Aspier 3050 Series. Aspire 3054WXMi. Mobile AMD Sempron processor3500+. ATI Radeon Xpress. Phoenix Bios.

Yours Hans Pedersen

---

### Post by jaya28inside on 2008-02-22
hey...me too having BLANK Screen probs

but then if i try to RECONFIGURE the XServer via Recovery mode
it's works...

but if it happened i can't get in touch with my Pendrive sighn.... :(

---

### Post by dstew on 2008-02-22
Yes, try to reconfigure the xserver:```
sudo dpkg-reconfigure xserver-xorg
```This is much more reliable than editing xorg.conf by hand.

---

### Post by Victormd on 2008-02-22
Ok, I'm trying to install Ubuntu on my wife's laptop and after install, Ubuntu won't boot. The laptop is an HP dv6000 series (dv6458se) (I know there are issues) with Turion 64 X2 proc. Nvidia graphics, and broadcom wireless card. I tried to install Gutsy 32bits, 64bits and per this thread, feisty 32 bits (from live and alternate CD). In all cases, using the noapic allowed me to boot from the live CD. My current install is from Feisty Alternate CD 7.04. I was able to install, no problems, and I can get into the terminal. However, when I try to boot normally, it starts to boot and freezes up. Furthermore, I'm getting a PCI BUG #81[SOME NUMBERS] Found... Any suggestions???

UPDATE: From the recovery mode, I get in the terminal and can get into X using startx. However, still won't boot under normal conditions. I've tried including noapic (noacpi - not sure which one is right) and added irqfixup, also tried these options together: noacpi nolacpi noirqpoll nosmp from [https://wiki.ubuntu.com/HP_dv6000_Series](https://wiki.ubuntu.com/HP_dv6000_Series)

---

### Post by Victormd on 2008-02-22
> **acrim said:**
> 
When I select Ubuntu from the GRUB menu I get a blank screen, with a few tiny white lines flickering in a sort of diagonal pattern across one of my monitors really, really fast (so fast I didn't notice them the first could of times).

If I boot into "recovery mode" everything appears to work fine, and I get dropped into the command line.

I'm thinking it might be something to do with VGA settings, but I'm not sure where to start when it comes to editing the x config. Could someone offer me some advice?


When you reach the GRUB menu, select the Ubuntu option and hit "e" add    vga=791
then try to boot... If it's a VGA setting, this might help.

---

