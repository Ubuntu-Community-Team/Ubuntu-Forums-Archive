---
title: "Video scrambled after install of hardy on Toshiba laptop 2105cds"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by questant on 2008-10-18
Have installed 8.04 LTS on Toshiba Laptop 2105CDS.  On first boot Ubuntu progress screen appears fine but login screen totally scrambled and unusuable.  Ran dpkg-reconfigure xserver-xorg from prompt.  Next boot no video at all.  Please advise at to steps to configure video from prompt.
Thanks in advance for any assistance.

---

### Post by mikewhatever on 2008-10-18
What graphics card do you have? If you don't know, run <sudo lshw -C display> and post the output.

---

### Post by questant on 2008-10-21
Thank you for your reply and please accept my apologies for taking so long but I was inadvertantly hindered.
The lshw -C display command yields the following:
Description:  VGA compatible controller
Product:  VIRGE/MX
Ventor:  S3, Inc.
Physical ID: 0
Bus Info:  pci@0000:00:08.0
Version:  06
Width:  32 bits
Clock 33MHz
Capabilities:  vga_controller bus_master
Configuration: latency 0  maxlatency = 255 mingnt = 4

The printout of the configuration of the laptop from its original spec sheet says
Video
Memory: 16Mbit SGRAM, 3.3V   2 MB
Speed  83MHz
Controller Chip S3 ViRGE MX (86C260)
     Data Bus Width  64-bit
PCI Bus Architecture w/burst mode:  Yes, 32-bit BitBLT support
     2D graphics support:  BitBLT, DirectDraw, H/W Cursor
     2D Graphics support:  Direct3D
Digital Video Accelerator:  Yes
     YUB-to-RGB color space conversion:  Yes
     Zoom:  Yes
     Scaling/Interpolation:  Yes
     Direct MPEG support:  Yes
     DirectVideo support:  Yes
Internal Support:
     Resolution:  640x480 16.7 colors
                  800x600  16.7
                  1024x768  64K
                  1280x1024  256
External support:  same as internal except adds frequencies
                  640 ...85Hz@16M
                  800 ...85Hz@16M
                  1024 ...85Hz@64K
                  1280 ...60Hz@256

I suspicion it will be repaired by the modification of a configuration file but am short on time as I am doing this for a colleague while in transit for a trip and do not have the luxury of time to sleuth it out as I would normally do, so thanks for any assistance.

---

