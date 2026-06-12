---
title: "installing ubuntu 9.10 i386 on windows 7 virtual pc problem"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by newyawker on 2009-11-14
I'm trying to install ubuntu 9.10 i386 on Windows 7 virtual pc.  The OS installs, and it prompts me to restart.  When it restarts, ubuntu hangs before loading.  I restarted the virtual machine and ubuntu loads successfully, but it gives two error messages: 

the panel encountered while loading OAFIID:GNOME_IndicatorApplet 

and 

the panel encountered while loading OAFIID:GNOME_FastUserSwitch

Also, programs won't load.

I see the problem is discussed here:
[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/349237](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/349237)

But since programs don't work, I can't use the terminal to fix it. 

Any ideas?  Thanks.

---

### Post by darkod on 2009-11-14
Dumb question. Is the win7 also in the virtual pc or win7 is main OS and you are trying ubuntu in virtual pc environment?

If it's the second, better option is to use the wubi.exe from the ubuntu CD in windows, it installs ubuntu similar to a windows software, somewhat a virtual ubuntu.

It will add Ubuntu choice to the normal windows bootloader (it will not install grub), and the whole ubuntu will just be a folder on the drive you select. It will put Ubuntu in your add/remove programs in windows and you just remove it from there like any other windows app.

The above is if you want just to try ubuntu without installing immediately. Another option, preferred by many, is what's called live CD, booting from ubuntu CD and selecting Try Ubuntu, it runs ubuntu from the cd without making any changes to your computer/hdd/partitions.

It all depends what do you want to do with it, and why you chose to install as virtual pc.

---

### Post by andrewthetechie on 2009-11-14
I suspect that newyawker is trying to do exactly what he described, install ubuntu 9.10 in a virtual machine, not via the Wubi installer or use it as a live cd.  This would mean he could run it VIRTUALLY inside of his current OS (Win7). This means none of your advice is useful at all.

I am currently working on this same issue and will report back with my findings and solutions to the issues that arise.

---

### Post by CALStech on 2009-11-28
I'm having some problems as well. I've installed Karmic_Koala in a Win7 Virtual PC on a Dell D-620 and have two immediate issues that I can't seem to resolve: 

1) there is no wireless card detected

-Ubuntu9:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 VGA compatible controller: S3 Inc. 86c764/765 [Trio32/64/64V+]
00:0a.0 Ethernet controller: Digital Equipment Corporation DECchip 21140 [FasterNet] (rev 20)
00:0c.0 Non-VGA unclassified device: Microsoft Corporation Device 0007

and 2)
I cannot bump display above 800x600

---

