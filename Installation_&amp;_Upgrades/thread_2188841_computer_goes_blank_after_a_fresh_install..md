---
title: "computer goes blank after a fresh install."
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by bbmak on 2013-11-19
One of my old computers has freshly installed Lubuntu 13.10, but the computer screen goes blank. The computer display is Trident CyberBlade XP. I think I get this problem since 13.04. However, 12.04.03LTS is working fine. I try to jump into terminal mode by pressing ctrl + F# keys, but none of them works. Anybody know why that Trident Cyberblade XP stops working?

---

### Post by Bashing-om on 2013-11-19
bbmak; Hi !

Certainly sounds like a graphics driver issue.
Can you boot to the GUI desktop from grub's recovery option (13.10) ? If so, from there we can examine what the graphics info is and what might be done to fix.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by bbmak on 2013-11-20
> **Bashing-om said:**
> bbmak; Hi !

Certainly sounds like a graphics driver issue.
Can you boot to the GUI desktop from grub's recovery option (13.10) ? If so, from there we can examine what the graphics info is and what might be done to fix.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

Recovery Mode is read only. I don't know how can I edit /etc/X11/xorg.conf in a read only mode.

---

### Post by Bashing-om on 2013-11-20
bbmak; That is profress !

At least you can get to a terminal. As to editing " /etc/X11/xorg.conf" .. with the advent of "Kernel Mode Setting" that file is rarely needed (Nvidia graphics card ?). At this time setting the system to read/write in the recovery mode is not a consideration. What is of interest presently is what graphics card(s) are installed and the related driver(s). From this info we should be able to set the boot parameters to boot to the GUI and install the appropriate graphics driver.

Be aware there are other ways also to get to a terminal, one can edit the boot parameters to boot the system to a terminal login.
 
To see your graphics card and info:
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga

```

I hope it is a easy as simply installing a driver for the graphics card.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by bbmak on 2013-11-20
> **Bashing-om said:**
> bbmak; That is profress !

At least you can get to a terminal. As to editing " /etc/X11/xorg.conf" .. with the advent of "Kernel Mode Setting" that file is rarely needed (Nvidia graphics card ?). At this time setting the system to read/write in the recovery mode is not a consideration. What is of interest presently is what graphics card(s) are installed and the related driver(s). From this info we should be able to set the boot parameters to boot to the GUI and install the appropriate graphics driver.

Be aware there are other ways also to get to a terminal, one can edit the boot parameters to boot the system to a terminal login.
 
To see your graphics card and info:
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga

```

I hope it is a easy as simply installing a driver for the graphics card.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

Thx for replying. I actually able to get into recovery mode with write permission
```
mount -o rw,remount /
```
And, I am able to replace my /etc/X11/xorg.conf, a working one for earlier version of my laptop. However, the monitor still goes blank after it boots.

---

### Post by Bashing-om on 2013-11-20
bbmak: Hey .

In order to assist you, we need to know what graphics card is installed and what driver is loaded. Any number of things may now be incompatible.

Why do you want to use a possibly depreciated  "/etc/X11/xorg.conf" file ???

Try this: not knowing your card, may not work -
Boot to the grub menu, booting kernel line highlighted - and hit the 'e' key for edit mode -> boot parameters screen;
Arrow down and across to "quiet splash" and insert the term "nomodeset" - with out the quotes-;
ctl+x to continue the boot process.

Do you now boot to the GUI login ? Login -> desktop ? degraded graphics at this point is OK .

Provide the results of the requested terminal commands and will advise further.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by bbmak on 2013-11-24
I try your suggestion by putting nomodeset in boot parameters, but it still has the blank screen.

I try your command:
it gives me
description: VGA Compatible controller
product: CyberBlade XPAi1
Vendor Trident Microsystems
Physical id: 0
bus info pci@0000:01:00.0
version: 82
width: 32 bits
clock: 66Mhz
capabilities: agp agp-2.0 pm vga_contoller bus master cap_list
configuration: latency=8
resources: memory:fc000000-fdffffff memory:fbc00000-fbffffff memory:f8000000-f9fffff memory:f7ff8000-f7ffffff memory:10100000-1010ffff 

I depreciate the to xorg.conf because the laptop used to have this problem with some of the Ubuntu earlier versions, and can be fixed by replacing a working one. However, it is not working this time.

---

### Post by bbmak on 2013-11-24
I am able get into the GUI now.
First, I replace this line "quiet splash $vt_handoff" with "text" without quote
and then I am able to boot into command line.
Second, I remove the xserver-xorg-video-trident and put my old xorg.conf in /etc/X11/
Finally, I can boot into the GUI now. 

Thx for the helps
I hope that Ubuntu can really fix this problem in the future.

---

### Post by Bashing-om on 2013-11-24
bbmak; Good !

Looking about and that seems to be the way to go (/etc/X11/xorg.conf).
Just to make sure all is now good, what driver is now installed ( I note in your prior post there was no driver installed ) ?
show us the output of terminal code:
```

sudo lshw -C display

```
[INDENT][INDENT]my best regards
[/INDENT][/INDENT]

---

### Post by bbmak on 2013-11-24
> **Bashing-om said:**
> bbmak; Good !

Looking about and that seems to be the way to go (/etc/X11/xorg.conf).
Just to make sure all is now good, what driver is now installed ( I note in your prior post there was no driver installed ) ?
show us the output of terminal code:
```

sudo lshw -C display

```
[INDENT][INDENT]my best regards
[/INDENT][/INDENT]

it gives me this
> 

*-display UNCLAIMED
description: VGA Compatible controller
product: CyberBlade XPAi1
Vendor Trident Microsystems
Physical id: 0
bus info pci@0000:01:00.0
version: 82
width: 32 bits
clock: 66Mhz
capabilities: agp agp-2.0 pm vga_contoller bus master cap_list
configuration: latency=8
resources: memory:fc000000-fdffffff memory:fbc00000-fbffffff memory:f8000000-f9fffff memory:f7ff8000-f7ffffff memory:10100000-1010ffff 



---

### Post by Bashing-om on 2013-11-24
bbmak; Hey;

Not the best I hope we can do, as there is still no driver loaded.
For reference; I run an ATI card with open source driver:
```

*-display:0             
       description: VGA compatible controller
<snip>
width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: [color=red]driver=radeon[/color] latency=0

``` As shown I have the radeon driver loaded.

I am aware that the support for  "CyberBlade XPAi1" is not all that great, However, if you want to investigate this,  I can look about and see what might be done.

It is about my witching hour here, will continue this in my AM .
Could be wrong but I am always open to learning the error of my ways.

[INDENT][INDENT]worth a looksee ?
[/INDENT][/INDENT]

---

### Post by bbmak on 2013-11-25
> **Bashing-om said:**
> bbmak; Hey;

Not the best I hope we can do, as there is still no driver loaded.
For reference; I run an ATI card with open source driver:
```

*-display:0             
       description: VGA compatible controller
<snip>
width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: [color=red]driver=radeon[/color] latency=0

``` As shown I have the radeon driver loaded.

I am aware that the support for  "CyberBlade XPAi1" is not all that great, However, if you want to investigate this,  I can look about and see what might be done.

It is about my witching hour here, will continue this in my AM .
Could be wrong but I am always open to learning the error of my ways.

[INDENT][INDENT]worth a looksee ?
[/INDENT][/INDENT]

The laptop that I installed is Toshiba Portege 2000.

---

### Post by Bashing-om on 2013-11-25
bbmak; Hey !

An old thread, but still I bet is valid. Compare your current xorg.conf file to that that is recommended in this thread:

[http://ubuntuforums.org/showthread.php?t=806835&highlight=portege](http://ubuntuforums.org/showthread.php?t=806835&highlight=portege)
A good prospect, if no joy, will keep try'n !

[INDENT][INDENT]where there is life there is hope
[/INDENT][/INDENT]

---

