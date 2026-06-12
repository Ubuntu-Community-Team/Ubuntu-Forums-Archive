---
title: "Bizarre video running from CD"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by GRobLewis on 2011-09-26
Just booted the CD of Ubuntu 11. It's "trying" to work, but the display is acting strange. Trying to drop down a menu creates only a black rectangle on the screen. So does clicking anywhere on the screen. Switching workspaces sort of cleans things up, but only temporarily. Bottom line, it's unusable. I wonder if doing a real install to a hard drive would correct any of this. 

Target system is a Dell Dimension 4600 P4, which AFAIK is about as "vanilla" as you can get in a PC.

---

### Post by ajgreeny on 2011-09-26
I suspect your problem is the low spec of that machine, particularly the 512MB of ram.

Are you sure that the live CD is a good one, burned as slow as possible, and from a good .iso file in the first place?  I certainly don't imagine you'll get unity to run on that machine, but you should have managed the classic desktop, I think.

---

### Post by GRobLewis on 2011-09-26
> **ajgreeny said:**
> I suspect your problem is the low spec of that machine, particularly the 512MB of ram.

Are you sure that the live CD is a good one, burned as slow as possible, and from a good .iso file in the first place?  I certainly don't imagine you'll get unity to run on that machine, but you should have managed the classic desktop, I think.

Actually, I upgraded the RAM to 1.5GB. My CD wasn't burned "as slow as possible"--it was 8X in a brand-new burner. The burning software reported success (I'm pretty sure verify was turned on). I have no reason to suspect the downloaded image.

---

### Post by MAFoElffen on 2011-09-26
> **GRobLewis said:**
> Actually, I upgraded the RAM to 1.5GB. My CD wasn't burned "as slow as possible"--it was 8X in a brand-new burner. The burning software reported success (I'm pretty sure verify was turned on). I have no reason to suspect the downloaded image.
The next suspect condition would be that the Video GPU (yours) might need a special kernel boot option to boot the LiveCD.  Do you know what brand and model Video Chipset you have?

Once we know that, there is a way to force the Install disk to boot in a VGA mode... or to Download the Alternate Install ISO image which is default as a text based install... but I wouldn't really recommend an install until you can confirm with the LiveCD that you "Can" run Ubuntu.

---

### Post by GRobLewis on 2011-09-26
I believe the system has Intel motherboard graphics. The control panel says "Intel Extreme Graphics 2" and there's nothing that looks like a graphics card in the expansion slots (which contain a modem and a WiFi card). 

In an attempt to get as much speed as possible, I have it set to 16-bit color, with resolution at 1280 x 1024 (60Hz). The system info lists an Intel 82865G Graphics Controller.

---

### Post by MAFoElffen on 2011-09-26
> **GRobLewis said:**
> I believe the system has Intel motherboard graphics. The control panel says "Intel Extreme Graphics 2" and there's nothing that looks like a graphics card in the expansion slots (which contain a modem and a WiFi card). 

In an attempt to get as much speed as possible, I have it set to 16-bit color, with resolution at 1280 x 1024 (60Hz). The system info lists an Intel 82865G Graphics Controller.
Have you tried different kernel boot options such as 

xforcevesa
i915.modeset=1 or i915.modeset=0
remove splash from the boot line
add vga=xxx, where xxx is a valid decimal VESA mode for your card... also set the GFXMODE to that same resolution...

2 workarounds for your card-->
GRUB_GFXPAYLOAD_LINUX=text # (by adding that line  /etc/default/grub and running update-grub) and remove the "splash" boot switch from the kernel boot line.  That switch has known problems with your card...

Please use posts 1 and 3 of this sticky for instructions and reference:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Once you get the kernel to boot and get to a text console... If you have hwinfo installed (you should if not) then
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor

```Then you can use the results to find a shared graphics mode that matches between your monitor and GPU... and use those results (will give a hex value for each mode to use in vga=).

Edit-- Use post 3 of that sticky for instructions on how to change and edit the kernel boot options on the LiveCD... Use these options in "TRY" mode of the LiveCD to see if you can get the graphics to run succesfully.

---

