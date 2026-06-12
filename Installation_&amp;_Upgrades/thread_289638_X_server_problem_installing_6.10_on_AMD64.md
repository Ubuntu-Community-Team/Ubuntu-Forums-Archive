---
title: "X server problem installing 6.10 on AMD64"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Guar0x on 2006-10-31
Hello, first of all i'm new to Linux, but i do have some experience.

This is my story: I downloaded the Desktop CD for AMD64 6.10 and am now trying to install it. I boot from the CD and i select Start or Install Ubuntu, There's a Ubuntu screen with a bar below it like it's loading something (in black and white, or shades of gray. not in color anyway). After a while it gives me this error:

Failed to start the X server (your graphical interface) It is likely it is not set up correctly. Would you like to see the log file.

I cliked ok and i see this at the end
(EE) No Devices Detected

I did the memtest just in case and everything was fine.

If i need to install the video drivers for my card first, how can i do it if i havent even installed Ubuntu yet.

This is the hardware i have.
AMD64 X2 4200 Processor
A8N-SLI deluxe Motherboard
ATI X800XL 256mb PCI-E Video Card
1Gb RAM
Maxtor 300Gb HDD

Please reply with any ideas and tips on what I need to do next.

Im sorry if someone else had this problem before and has already been addressed, but i looked everywhere and didnt find anything about this, all the solutions I see are when you're already on Ubuntu and i can't even get there.

Thanks

Daniel

---

### Post by elvisd on 2006-10-31
I have the same problem here.
The ubuntu logo in shades of gray but no errors at all... 

I've tried to re-burn the CD and control md5checksum but all is ok.
I have a fujitsu siemens pc (esprimo edition p2410) amd64-dual (athlon x2)

---

### Post by elvisd on 2006-10-31
in this forum i'll find other posts (search for amd64)
one option seams to be downloading the alternate install cd.
but first try to boot adding the acpi=off switch (F6 on boot selection).

but as said from others i can't understand that ubuntu releases a ne version without testing it... if you find something please post it here... i'm digging too! ;-)

---

### Post by Fabre on 2006-11-01
I have the same problem tried both ubuntu and kubuntu 6.10 Amd64.

I get a loading screen with a corrupt loading bar (greyscale for ubuntu, in color for kubuntu)
Then the monitor switch off (no signal) but I can still hear startup music once it's loaded.

System is:
Athlon 64 X2 3800
Asrock 939Dual-VSTA
ATI X800 XT AGP
SATA II 250GB HDD
1GB DDR PC 3200

That's a big bug, it's very surprising the Amd64 was released that way.

---

### Post by riprjak on 2006-11-07
Ditto! with the last post...  I get all the sounds and signs of loading, but no output.

I have a DVI-D monitor attached to my primary 7800GTX and suspect this to be the issue.  Being VERY new to this debian apt-get thing (normally a gentoo user) I havent yet worked out how to install the nvidia binaries on the live CD(whose configuration I know backwards)...

I have only tried the desktop 6.10 x64 install disk last night; both "safe mode" and standard graphics.  I also validated the disk (ok) and memtested just in case the box was unhealthy.

I have decided to look up the output device configuration for the nv driver and explicitly telling it to use DVI-D output and see if that fixes it (or is possible).  I have already tried forcing xorg to try the alternative card by explicitly entering both addresses...  ctrl-alt-backspace WORKED, but the issue remained.

Addendum : I am going to fiddle with these two xorg.conf settings for the nv driver (Im sure the open source ATI driver has similar settings)
> Option "CrtcNumber" "integer" 
GeForce2 MX, nForce2, Quadro4, GeForce4, Quadro FX and GeForce FX may have two video outputs. The driver attempts to autodetect which one the monitor is connected to. In the case that autodetection picks the wrong one, this option may be used to force usage of a particular output. The options are "0" or "1". Default: autodetected. 
Option "FlatPanel" "boolean" 
The driver usually can autodetect the presence of a digital flat panel. In the case that this fails, this option can be used to force the driver to treat the attached device as a digital flat panel. With this driver, a digital flat panel will only work if it was POSTed by the BIOS, that is, the machine must have booted to the panel. If you have a dual head card you may also need to set the option CrtcNumber described above. Default: off. 

Hopefully this will force the display to use the LCD... Ill try both output options with flatpanel forced on and see if a ctrl-alt-backspace fixes it.  Posted, I will keep you.
err!
jak.

The Boxen in Question:
Gigabyte GA-8N SLI-pro
Amd64 x2 4600+
2 x Geforce 7800GTX (sli)
2 x 1024 GB Corsair XMS
Soundblaster X-Fi
Intel PCI-Express Pro/1000 PT Ethernet
2 x WD 250GB SATA-II TCQ HDD
2 x WD 150GB Raptor HDD (Raid-0)
1 x WD 300GB HDD
1 x Pioneer DVR109 CD/DVD burner
Acer 20.1" LCD

---

### Post by riprjak on 2006-11-08
Issue resolved by explicitly setting the nv driver option

> Option "FlatPanel" "1"

in the Device section.

I also had to manually adjusting the device address of the display (from 4 to 5 in my case) in the same section, as it had selected the card which didn't have a monitor attached..

After this, X functioned and I was able to successfully install and reboot into a working desktop.  After this, I went to the binary drivers and enabled SLI and it worked better.

This solution may not work for ATI users, but I recommend trying a similar approach.

err!
jak.

---

### Post by Fabre on 2006-11-09
riprjak could you please explain step by step how you did it?

Which cd did use?

---

