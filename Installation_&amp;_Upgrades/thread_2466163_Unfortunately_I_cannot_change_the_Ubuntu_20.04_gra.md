---
title: "Unfortunately I cannot change the Ubuntu 20.04 graphic resolution to 1920 x 1024"
date: 2021-08-21
forum: Installation &amp; Upgrades
---

### Post by marceloatmartins on 2021-08-21
Unfortunately I cannot change the Ubuntu 20.04 graphic resolution to 1920 x 1024.
Asa defaulte, I have just 1024 x 780 resolution, but this is not enough to work fine with Ubuntu currently.

This is the message after I have tried to make resolution change on Ubunto 20.04 running on notebook ASUS FX504, as below:

[FONT=Arial]xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync[/FONT]
[FONT=Arial]xrandr: Failed to get size of gamma for output default[/FONT]
[FONT=Arial]X Error of failed request:  BadName (named color or font does not exist)[/FONT]
[FONT=Arial]  Major opcode of failed request:  140 (RANDR)[/FONT]
[FONT=Arial]  Minor opcode of failed request:  16 (RRCreateMode)[/FONT]
[FONT=Arial]  Serial number of failed request:  19[/FONT]
[FONT=Arial]  Current serial number in output stream:  19

I have tried a lot of recommendations found in several foruns aroud the globe, but nothing worked fine.
Thanks in advance for any help.[/FONT]

---

### Post by Dennis N on 2021-08-21
Did you try Settings > Displays > Resolution?
It shows all available resolutions in the drop menu and sets them for you.

---

### Post by MAFoElffen on 2021-08-21
Can you get to the Grub2 Menu in the startup? (Pressing the left shift key repeatedly as it ends the BIOS POST end...)

What I am hinting at, is that the Graphics Layer takes hints from the Kernel KMS settings... Which if set in the Grub Kernel boot line... Then will be recognized as a valid mode when the Graphics Layer comes up. More technically, $linux_gfx_mode is default at "keep", $gfxmode is default at "auto"... and if you manually set $vbe_mode in grub, then it carries through to the graphics layer, where the DE resides...

If at the Grub Menu, you drop down to a Grub Command Line CLI and type "vbeinfo" it will show you the modes of the display that Grub see's as valid in the connected display... Copy down what mode you want to set it at... which will probably be shown as 1920x1080x32 (or similar).

Press <Esc> then continue to boot... Edit your Grub default file (with Sudo elevation)... Uncomment and change this line to" this", with the specific mode you found...
```
GRUB_GFXPAYLOAD_LINUX=1920x1080x32
```
Then save it and exit the editor. Open a Terminal and update your Grub Menu settings
[code]sudo update-grub
sudo reboot{/code]
That should be in the mode you selected... If it isn't, tell me... and there are other ways to do that.

---

### Post by tea for one on 2021-08-21
> **marceloatmartins said:**
> Unfortunately I cannot change the Ubuntu 20.04 graphic resolution to 1920 x 1024.
Asa defaulte, I have just 1024 x 780 resolution, but this is not enough to work fine with Ubuntu currently.

I just had a quick search for the specification of your device.
The default resolution is 1920 x 1080
Also, it comes supplied with a Nvidia GTX 1050 

If you have Nvidia GPU, have you installed the relevant drivers?

---

### Post by MAFoElffen on 2021-08-21
As "Tea for One" suggested... make sure ubuntu-drivers-common is installed first, then go to Additional Drivers to install the driver you want to try...

Note... I still do what I suggested earlier on mine with NVidia, as it helps with the Plymouth Boot Splash and the Graphical Login Manager (DM), before the NVidia driver is loaded for the DE.

---

### Post by not-published on 2021-08-25
[FONT=Arial]xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync[/FONT]
[FONT=Arial]xrandr: Failed to get size of gamma for output default

xrandr isn't setting a mode that isn't supported.  also Xorg has have a video driver that has "mode sensing" (i forget the term) that allows X to communicate with the driver to get all available (HDMI or other) modes.  you have to check /var/log/Xorg.foo.log to check what kind of video mode sensing stanards were made available.

[FONT=Arial]xrandr: Failed to get size of gamma for output default, means exactly as it said.  it asked for size of gamma, but Xorg didn't detect any video driver which complied OR the specs you listed were not in the set[/FONT]
[/FONT]
last ditch attempt is:  if you don't have "mode sensing" for any reason:  you have to list or "bless" good modes in the xorg.conf - which xrandr will later have access to *attempt.  but no matter - if the settings you gave are not completely real they will never work*

---

