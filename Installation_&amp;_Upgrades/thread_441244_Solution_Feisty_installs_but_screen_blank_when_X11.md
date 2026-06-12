---
title: "Solution: Feisty installs but screen blank when X11 starts"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by RatherCurseTheDarkness on 2007-05-12
In the hopes that this will save others from hair loss...

I installed Feisty on a PIII with an onboard intel i810  video AND an nVidia Corporation NV44 [GeForce 6200 LE]  PCI video card.  (NOT PCI-e  just plain old PCI).  

The BIOS was set to boot with the PCI video card active; the install went fine.  On the first and subsequent boots, the machine came up but the screen would go blank just as  gdm loaded.  


The problem was that /etc/X11/xorg.conf  had the device set to i810 instead of the nvidia. Oddly lspci shows this onboad vido chip as having a PCI busID and that corresponded t the entry in xorg.conf.   (Maybe onboard video chips are supposed to look like PCI devices what do I know)  

But getting to the point.   The solution is to boot into single user and run

lspci to get the bus id of the pci video card

lspci shows this kind of stuff

00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
01:01.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
01:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
01:09.0 SCSI storage controller: LSI Logic / Symbios Logic 53c810 (rev 23)
01:0b.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


in my case the relevant id is 01:0b:0    
in single user mode that showed up as 1:11:0    

Now to get a useful xorg.conf   run

Xorg -configure -isolateDevice 1:11:0
(obviously 1:11:0 might not be right at your house see lspci above)

Xorg will tell you how to test your configuration something like

X  -config /root/xorg.conf.new

should work.

If it works you will see a grey screen with an X pointer that you can move with your mouse
but that's all.  You'll need to know that the secret key combination to shut down X11 is  CTRL + ALT  + BACKSPACE  in order to get back to the command line.

if this all worked, then move you /root/xort.conf.new onto /etc/X11/xorg.conf

and boot into multuser mode.

---

### Post by earobinson on 2007-05-12
Thanks for the tip!

---

### Post by Thomas,Bakker on 2007-05-18
could someone turn this into an easy to use How To for command line noobs like myself?
i understand the explanation only no idea what commands to use.

---

