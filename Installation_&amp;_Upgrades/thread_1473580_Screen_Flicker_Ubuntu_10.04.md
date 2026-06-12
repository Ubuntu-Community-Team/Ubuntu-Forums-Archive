---
title: "Screen Flicker Ubuntu 10.04"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by ve3tru on 2010-05-05
I did a clean install Ubuntu 10.04 64bit Dell Inspiron 1545 laptop.
I get a screen flicker bottom half of the screen every couple of minutes for like one second. I updated things, it's not as bad, but its still there, It only happens like every 20 minutes or so.

---

### Post by Charliemong on 2010-05-05
Sounds like you need to install graphics driver.

---

### Post by ve3tru on 2010-05-05
sorry should of posted this
peter@peter-laptop:~$ sudo lspci
[sudo] password for peter: 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
peter@peter-laptop:~$

---

### Post by umuskie on 2010-05-05
Same thing happened using Fujitsu A1120 with v10.04 x64. 


```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
18:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```


And, still have the flickering even applied:

```

echo "i915.powersave=0" | sudo tee  /etc/modprobe.d/i915-disable-powersave.conf
sudo update-initramfs -u

```

---

### Post by ve3tru on 2010-05-06
Quote
"And, still have the flickering even applied:
echo "i915.powersave=0" | sudo tee  /etc/modprobe.d/i915-disable-powersave.conf
sudo update-initramfs -u" 

   Well Ive tried that too it didn't work for me either, so I changed it back.
As far as I can figure, you and I have the "Intel mobile 4 Series chipset" and thats the problem and I'm not a computer tech. 
 This problem was not there in 9.10 and it started with kernel packages 2.6.32-16 and later on some reports. Since there are no drivers to download we are dead in the water until a kernel fix, or at least someone smarter then us can figure this out. I was a little disappointed when i did a kernel  update and the fix was not there. It's kind of like hoping your going to win the lottery.
 When no one acknowledges you have a problem or at least working on a solution it makes it even more frustrating.

---

### Post by MirzaD on 2010-05-06
I also have this problem, will try to find solution, if I discover something that works will post it here.

---

### Post by MirzaD on 2010-05-06
I found a solution!
I edited wiki and added instructions for Kubuntu.

Here it is:
[http://ubuntuguide.org/wiki/Template:Lucid/Hardware#Screen_Keeps_Flickering]("http://ubuntuguide.org/wiki/Template:Lucid/Hardware#Screen_Keeps_Flickering")

---

### Post by ve3tru on 2010-05-06
"I found a solution!
I edited wiki and added instructions for Kubuntu.

Here it is:
[http://ubuntuguide.org/wiki/Template...eps_Flickering"]("http://ubuntuguide.org/wiki/Template:Lucid/Hardware#Screen_Keeps_Flickering")

Thanks but I don't think thats it somehow, 1st off they talk about Kbuntu not Ubuntu. So I'm lost and not sure what they are talking about 2nd they talk about an Intel Corporation Mobile 915GM/GMS/910GML card i have a intel mobile 4 integrated graphics.

still lost in space here.

Tnx anyway

---

### Post by zeevb on 2010-05-07
I'm experiencing a similar problem running Lucid on my Lenovo G550 laptop.

lspci output:
> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
07:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)


---

### Post by janneman37 on 2010-05-07
same problem with fujitsu siemens pi1536 mobility radeon x1400

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

---

### Post by benishor on 2010-05-07
Same thing happening here. ( kubuntu 10.04, Intel Mobile 4 chipset ). I thought I was the only one experiencing this until I found this thread. It's a very frustrating issue, hopefully someone will be able to help us. 

lspci:

[FONT="Courier New"]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
[/FONT]

---

### Post by Cheater87 on 2010-05-08
Having the brightness on the lowest setting helps.

---

### Post by rodrigth on 2010-05-08
> **ve3tru said:**
> "I found a solution!
I edited wiki and added instructions for Kubuntu.

Here it is:
[http://ubuntuguide.org/wiki/Template...eps_Flickering"]("http://ubuntuguide.org/wiki/Template:Lucid/Hardware#Screen_Keeps_Flickering")

Thanks but I don't think thats it somehow, 1st off they talk about Kbuntu not Ubuntu. So I'm lost and not sure what they are talking about 2nd they talk about an Intel Corporation Mobile 915GM/GMS/910GML card i have a intel mobile 4 integrated graphics.

still lost in space here.

Tnx anyway

Kubuntu = Ubuntu + K Desktop Environment. The standard Ubuntu uses Gnome as the GUI. Any fixes you find for Kubuntu *should* work in your Ubuntu install.  

My room mate has this video card and he tried the above fix, but no luck. Hope this is resolved soon!

--tharon

---

### Post by the.scarecrow on 2010-05-08
I also have this problem on my Dell 1750, 10.04 64bit.

---

### Post by Catharsis on 2010-05-08
You can try reconfiguring the X server:
```
sudo dpkg-reconfigure xserver-xorg
```

Or making a default xorg.conf:
```
Xorg -configure
```

You can also try playing with KMS:
1) Hold down Shift while booting to enter grub.
2) Press 'e', and add "i915.modeset=1" after "quiet splash"
3) Ctrl+x to boot.
You can also try "i915.modeset=0".

It would also be helpful to post your Xorg log:
```
cat /var/log/Xorg.0.log
```

---

### Post by janneman37 on 2010-05-08
Problem is solved when i boot with option "nomodeset"

---

### Post by ve3tru on 2010-05-08
I even had one of those flickers crash my computer
anyway here is my Xorg log


    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
(--) intel(0): Chipset: "GM45"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 5441  Serial#: 0
(II) intel(0): Year: 2008  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 72.3 MHz   Image Size:  344 x 194 mm
(II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) intel(0):  R801J&#65533;156AT
(II) intel(0): Unknown vendor-specific block 0
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004ca3415400000000
(II) intel(0):     00120103902213780a87f594574f8c27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101411c56a0500016303020
(II) intel(0):     250061c61000001a411c56a050001630
(II) intel(0):     3020250058c21000001a000000fe0052
(II) intel(0):     3830314a8031353641540a2000000000
(II) intel(0):     00000000000000000001010a20200036
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1366x768"x60.0   72.33  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (47.4 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output DP1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1366x768
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Kernel mode setting active, disabling FBC.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 361 x 203
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event8)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event9)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event9"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Right Jack (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Right Jack (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/event6)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event6"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event7)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event7"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event5)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event5"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) intel(0): EDID vendor "SEC", prod id 21569
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 21569
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 21569
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 21569
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 21569
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 21569
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 21569
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 21569
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (47.4 kHz)
peter@peter-laptop:~$

---

### Post by Catharsis on 2010-05-08
Did this do anything for you?
> **Catharsis said:**
> You can also try playing with KMS:
1) Hold down Shift while booting to enter grub.
2) Press 'e', and add "i915.modeset=1" after "quiet splash"
3) Ctrl+x to boot.
You can also try "i915.modeset=0".

I also strongly suggest you try MirzaD's suggestion in post 7:
1) System -> Administration -> Advanced -> Service Manager
2) Uncheck "Detect RANDR (monitor) changes"

I've seen this fix the flicker on a variety of intel chips. It's worth a try; if it doesn't do anything, reverting it is as easy as checking the box again.

---

### Post by ve3tru on 2010-05-08
"System -> Administration -> Advanced -> Service Manager"
I don't have a service Manager, this OS is Ubuntu.
Tnx

---

### Post by ve3tru on 2010-05-08
tried adding i915.modeset=1
didn't do anything still flickering
tnx

---

### Post by Catharsis on 2010-05-09
You can try updating your drivers through the X-Updates PPA:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Jimtheplanner on 2010-05-09
Well I've looked for 

```
"System -> Administration -> Advanced -> Service Manager"
```

But like ve3tru 

```
"System -> Administration -> Advanced -> Service Manager"
I don't have a service Manager, this OS is Ubuntu.
Tnx 
```

I can't find "advanced" never mind Service Manager? Or is this in Kubuntu?

Jim

---

### Post by Catharsis on 2010-05-09
> **Jimtheplanner said:**
> Well I've looked for 

```
"System -> Administration -> Advanced -> Service Manager"
```

But like ve3tru 

```
"System -> Administration -> Advanced -> Service Manager"
I don't have a service Manager, this OS is Ubuntu.
Tnx 
```

I can't find "advanced" never mind Service Manager? Or is this in Kubuntu?

Jim

Yeah, I got this workaround mixed up with another one that's worked before in a different situation. My apologies. This is only appropriate for Kubuntu; I haven't figured out how to do it in Ubuntu yet.

---

### Post by benishor on 2010-05-10
In kubuntu the service manager can be found here : System Settings -> Advanced (Tab) -> Service Manager.

I have tried disabling the randr monitor change detection but the flicker is still there. Just like before, it appears at random times so it's kind of painful to test whether a fix really works or not.

I'll go for the nomodeset option and see what happens.

---

### Post by ve3tru on 2010-05-10
In Ubuntu 8.04 my webcam,  printer never worked got my wireless working after a lot of work. 9.04 webcam, no, but printer got working much later. 10.04 everything works except this dam bug. 10.04 seems a little bloated with stuff most of us would never use. The Apps they chose well they just suck. Brasero dosn't work half the time I used it to back me up before this upgrade. I checked and double checked but it wasn't there in the end. Empathy is confusing hard to use, simple scan is too simple and lost all the usefull features. Worst of all this bug has started to crash my computer. The truth is they have never fixed any bug they wait for Debian or someone else to fix it for them. (just Google how much they contribute to the Linux kernel)
I'm downloading Debian right now il let you know if they have this problem who knows maybe ill never come back.

---

### Post by rcktsingh on 2010-05-10
> **janneman37 said:**
> Problem is solved when i boot with option "nomodeset"

Could you please elaborate on this ? Like where to set this option ? 

Did it permanently solve the problem ? I have Gnome as my Desktop!

Thanks!

---

### Post by ve3tru on 2010-05-10
Debian seems stable no flickering but I got way too much on here to just jump ship.
hope someone can find a solution.

---

### Post by ismailmarmoush on 2010-05-11
i'm having same problem as you ve3tru  ,, also my laptop is same as yours ...

did you find solution yet ? 

and about the kernel editing thing how do you guys do it ? cause when i press shift it shows me a list of around 7 options 

ubuntu (recovery mode ) 
memtest86 

etc so i donno how to even edit that kernel

---

### Post by ve3tru on 2010-05-11
"i'm having same problem as you ve3tru  ,, also my laptop is same as  yours ...
did you find solution yet ? "

Tried them all they don't work.
Has anyone actually reported this bug, maybe if we all get on their backs, a fix may come faster; I'm just out of ideas.

---

### Post by yipeng on 2010-05-11
Also facing the same problem. 
Running Ubuntu 10.04 64bit, Intel Chipset 4 on my Levono T400.

---

### Post by Catharsis on 2010-05-11
> **ve3tru said:**
> Has anyone actually reported this bug, maybe if we all get on their backs, a fix may come faster; I'm just out of ideas.

You're welcome to try filing a bug report. Just check Launchpad to make sure it's not already there. To submit a bug report for this:
```
ubuntu-bug xserver-xorg-video-intel
```

---

### Post by ve3tru on 2010-05-11
I did a report very confusing for your 1st time.
hope i did it right. anyway I'm sure i did.

---

### Post by ismailmarmoush on 2010-05-11
i guess i found the solution 

my laptop is dell inspiron 1545 ,, ubuntu x64 

anyway here is it 

just open ubuntu normally and open terminal 

write:
```
sudo edit /etc/default/grub

```
then find this line in the text file:  
GRUB_CMDLINE_LINUX ""

then make it like this:
GRUB_CMDLINE_LINUX " i915.powersave=0  " 

then save , then back to terminal and write:
```
sudo update-grub;

```
hope it works for you like it did for me
---------------------------------

---

### Post by ve3tru on 2010-05-12
Thanks but..
I get this
peter@peter-laptop:~$ sudo edit /etc/default/grub
Warning: unknown mime-type for "/etc/default/grub" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
peter@peter-laptop:~$ 

whatever that means
and just a little side note by " i915.powersave=0  " 
You turned off your power save, so your laptop battery wont last as long. Your CPU hotter, your fan will work harder and thus more noise, but I can live with all that, if I can figure this out.

tnx

---

### Post by Catharsis on 2010-05-12
```
gksudo gedit /etc/default/grub
```

---

### Post by ve3tru on 2010-05-12
I used 
sudo nano /etc/default/grub

to edit the line seems to of worked
so far so good only time will tell, but i think this is it
nice work
tnx

---

### Post by ve3tru on 2010-05-12
YAH!!!!!!
Day two I have a 100 percent stable OS success
Weird thing is by envoking a (i915.powersave=0) command I sould of lost my power save.
From my point of view, I lost nothing, only gained a stable OS. So now I'm a little curious what a this actually did; anyway.
I got to thank every one here you guys are wonderful, and now I can stop bitching about Ubuntu and fall in love with it again. 


Yours truly,
Peter

---

### Post by rcktsingh on 2010-05-12
> **ve3tru said:**
> 
whatever that means
and just a little side note by " i915.powersave=0  " 
You turned off your power save, so your laptop battery wont last as long. Your CPU hotter, your fan will work harder and thus more noise, but I can live with all that, if I can figure this out.

tnx

If that's the case, I so don't think this is a good solution! Why mess up with your CPU for all this ?!

---

### Post by john1066 on 2010-05-12
Same problem with Acer Aspire 6930G

---

### Post by ismailmarmoush on 2010-05-12
glad i've helped i found the fix in the bug report website , 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648)


About the Power saving issue. i donno i will try my battery now and see , but laptop isn't heating up it's normal . 

so i'll see now if the battery will be exhausted or not

---

### Post by rcktsingh on 2010-05-12
> **ismailmarmoush said:**
> i guess i found the solution 

my laptop is dell inspiron 1545 ,, ubuntu x64 

anyway here is it 

just open ubuntu normally and open terminal 

write:
```
sudo edit /etc/default/grub

```
then find this line in the text file:  
GRUB_CMDLINE_LINUX ""

then make it like this:
GRUB_CMDLINE_LINUX " i915.powersave=0  " 

then save , then back to terminal and write:
```
sudo update-grub;

```
hope it works for you like it did for me
---------------------------------


Has anybody else tried this solution ? I wanna make sure that this is it, before I try on mine :D

---

### Post by opogon1 on 2010-05-13
I had this same issue, tried the solution with grub, didn't work.  Fixed my flickering display on my Thinkpad r61 in the bios under the display settings.  Changed from "Normal" to "High", and the flicker disappeared.  Linux kernel must not like this, cause it didn't happen on Win7.

---

### Post by mdonahoe on 2010-05-13
I believe this issue is tied to memory and how the video drivers use that.  I have no expertise in that area but on my IBM/Lenova z61m it starts jumping all over the place when I start using some heavy applications simultaneously such as GIMP and Virtualbox at the same time.  Neither apps on their own seem to cause it, but when I start really tasking the memory or possibly even the cpu I suppose is when the screen flicker starts.  If I close everything down, dim the screen it will stop and then I can carry on.  This may not be much help, but just the observation from what I see.  I have both KDE and Gnome desktops installed and both experience the issue. 

I hope somebody can figure this out, this is about to drive me nuts.

---

### Post by mdonahoe on 2010-05-15
Ok, I have resorted to wiping the machine with a fresh install of 10.04 and I couldn't be happier.  No screen flicker, everything works, and I am loving Ubuntu again!  Still would like to know the cause though.

---

### Post by rcktsingh on 2010-05-15
:(. I tried doing that too, but the flickering is still there.

---

### Post by cprofitt on 2010-05-16
I am working on a fresh install and have the issue as well.

---

### Post by witeshark17 on 2010-05-16
It does seem like something that needs a look. There's a [ thread](https://bugs.launchpad.net/ubuntu/+bug/576555) in Launchpad.

---

### Post by cake nom nom on 2010-05-18
> **mdonahoe said:**
> Ok, I have resorted to wiping the machine with a fresh install of 10.04 and I couldn't be happier.  No screen flicker, everything works, and I am loving Ubuntu again!  Still would like to know the cause though.

1. what kind of laptop did you have?

2. what did you reinstall / have before 64bit or 32bit?

---

### Post by mdonahoe on 2010-05-18
Laptop is an IBM/Lenovo z61m, Dual core 2Ghz version.  I'm running 32bit, i did complete wipe of the hard drive and installed 10.04 from the live CD.  I restored my Mozilla and Virtualbox from backup and then just moved my doc, music, video, files, etc over.  All the other settings have been wiped clean.  

I've been upgrading this one rather than a fresh install since 8.10 when this computer had a hard drive fail.  

It's been over a week now and I've been tasking this computer pretty hard.  Running Virtualbox with WinXP with Outlook and so forth running in it, while using Rhythmbox and GIMP all at the same time, no hint of any video issues.  (of course file manager running with all of this copying files from the backup USB drive.  I have not reloaded the Kubuntu KDE desktop on here yet though, but doubt that was the issue.

***** update ****
After 3 weeks the laptop did the screen flickering again.  I rebooted and it hasn't occurred since.  The conditions again surrounding it were that I had a lot of applications running, the laptop was quite hot from being on all day as well.

---

### Post by cake nom nom on 2010-05-19
> **cprofitt said:**
> I am working on a fresh install and have the issue as well.
did this work?

---

### Post by romankuzmik on 2010-05-20
I've installed patched kernel with FBC turned off from here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648/comments/88](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648/comments/88)

works just fine for me, w/o any tricks with power save and related crap.

---

### Post by cake nom nom on 2010-05-20
> **romankuzmik said:**
> I've installed patched kernel with FBC turned off from here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648/comments/88](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648/comments/88)

works just fine for me, w/o any tricks with power save and related crap.

what do you mean by FBC?

---

### Post by broschb on 2010-05-23
Yes, more details on this would be appreciated, are things still working properly?

---

### Post by ve3tru on 2010-05-24
I deleted the i915.powersave=0
from line
GRUB_CMDLINE_LINUX "i915.powersave=0   "
and loaded the new 64bit patched kernal located in the link and
no flicker. It has only been a day but i think this is a winner it works.
I don't know what a FBC is, buts thats fine by me lol.

---

### Post by ve3tru on 2010-05-25
Update
Getting a flicker again not  bad, one or two a day, so it was hard to know if this kernal
works or not, well I guess it doesn't for me.
tnx

---

### Post by rcktsingh on 2010-05-26
Hi, 

I did the GRUB_CMDLINE_LINUX "i915.powersave=0 " thing and haven't got the flickers since then, irrespective of any heavy application being loaded. But I know this is not a great solution.

I would like to try the patch thing. Can anybody tell me a step by step procedure to implement this patched solution ?

Thanks in advance.

---

### Post by Catharsis on 2010-05-26
> **rcktsingh said:**
> Hi, 

I did the GRUB_CMDLINE_LINUX "i915.powersave=0 " thing and haven't got the flickers since then, irrespective of any heavy application being loaded. But I know this is not a great solution.

I would like to try the patch thing. Can anybody tell me a step by step procedure to implement this patched solution ?

Thanks in advance.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648)
You should click the "Does this bug affect you too?" link at the top below the title, and also subscribe to the bug in the toolbar on the right. That'll keep you up-to-date on the development of the bug/patch.

[http://people.canonical.com/~apw/lp538648-lucid/](http://people.canonical.com/~apw/lp538648-lucid/)
To try the new kernels, download the *_all.deb header file, and the header and image file for your architecture (amd64 for 64-bit, i386 for 32-bit). Then doubleclick them (should open gdebi) and install them, starting with the *_all.deb, then your architecture-specific headers, then the architecture-specific image.

Reboot and hold down shift during the BIOS. This'll get you to GRUB; make sure you're booting into the kernel you just installed (if it's the first one on the top, then it'll automatically boot into that kernel).

Make sure you report your results with this patched kernel in the bug comments. Just make sure you play with the patched kernel for a few days before commenting so you that your results can be definitive.

---

### Post by Loan_Refi on 2010-05-26
I fixed the flickering problem by accident on a Dell D505 Laptop.  I had a 46" inch flat screen attached to the laptop and I had the flickering but when I adjusted the display resolution to my 46" inch TV from 1024X768 the flickering went away and has not returned for many days now.

This was the only problem from a fresh install Ubuntu 10.04 on Dell D505 with Intel Video Driver. I installed but got a black screen at 1st boot so I followed these instructions and the black screen went away but left me the flickering which I resolve by accident like I said.

I got the instructions from here;

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Booting from CD

This section outlines how to workaround the video issue while booting from the CD. Your mileage may vary, depending on your video card, but hopefully this steers you in the right direction:

   1. At the install screen press ‘F6‘ and insert one of the options below, depending on your hardware.
   2. On first boot after install, press e to edit the GRUB menu.
   3. Using the arrow keys to navigate, delete quiet and splash and again insert one of the options below.
   4. Press Ctrl and X to boot.

The suggested options that I have found are hardware specific. Here is a list:

    * Order Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa

Hopefully one of these options will get you up and running. Keep reading now to make these changes persistent!

GRUB

You’ll want to change these settings in GRUB so they’ll automatically be applied on each reboot. To do so, follow the steps below:

   1. Edit the /etc/default/grub file. You will need Admin privileges to do so (sudo)
   2. Find this line: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
   3. Replace with: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash <option>”

For example, if I had an older Intel model, my GRUB configuration would read:

    GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash i915.modeset=1&#8243;

Save your changes and you should get proper graphics on each reboot.

UPDATE: Based on a lot of user feedback I am reminded that you need to run ‘update-grub’ after you make changes.

The instructions on this thread help me solve the flickering problem on "Lenovo SL410".

Hope this helps!

---

### Post by Whisp3r on 2010-05-27
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

I have the same problem. My flickering gets bad if I full screen a video. If I move the mouse around a lot while it's a full screen video, it gets even worse. I have tried the grub change and it hasn't helped. I went to my hardware drivers to see what was going on, but there are none listed except for my wireless card?

---

### Post by Catharsis on 2010-05-28
> **Whisp3r said:**
> ```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

I have the same problem. My flickering gets bad if I full screen a video. If I move the mouse around a lot while it's a full screen video, it gets even worse. I have tried the grub change and it hasn't helped. I went to my hardware drivers to see what was going on, but there are none listed except for my wireless card?

Which grub changes have you tried? "nomodeset", "i915.powersave=0", "noacpi", "noapic"?

You could try the mainline kernel.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)

---

### Post by Frantic_Earthling on 2010-05-29
I have found a solution to the screen flicker problem on my Asus UL20A.

Although the solution affecting power saving described above probably works (I have not tried it), I was a bit reluctant to tamper with this.

The overclocking function provided in my BIOS was originally set at 3% on a scale of 1 to 5%. 

I set it at 1%. 

The screen flicker has disappeared and frankly, I do not see any loss of performance resulting from the 2% overclocking drop.

---

### Post by rcktsingh on 2010-05-30
> **Catharsis said:**
> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648)
You should click the "Does this bug affect you too?" link at the top below the title, and also subscribe to the bug in the toolbar on the right. That'll keep you up-to-date on the development of the bug/patch.

[http://people.canonical.com/~apw/lp538648-lucid/](http://people.canonical.com/~apw/lp538648-lucid/)
To try the new kernels, download the *_all.deb header file, and the header and image file for your architecture (amd64 for 64-bit, i386 for 32-bit). Then doubleclick them (should open gdebi) and install them, starting with the *_all.deb, then your architecture-specific headers, then the architecture-specific image.

Reboot and hold down shift during the BIOS. This'll get you to GRUB; make sure you're booting into the kernel you just installed (if it's the first one on the top, then it'll automatically boot into that kernel).

Make sure you report your results with this patched kernel in the bug comments. Just make sure you play with the patched kernel for a few days before commenting so you that your results can be definitive.

Implemented. I will report the results in a few days time after observing them. Thanks a lot for the help.

---

### Post by rcktsingh on 2010-06-01
Today's the third day and the results are not very good. While I get about 2-3 flickers/day normally, the rate gets higher when I try to run a heavy application. If at the same time, I do the powersave thing, the flickers seem to go away.

Can anybody tell me if I am going to run into some loss in terms of hardware (like battery and CPU life time) if I do the powersave thing ? I don't mind using this workaround for the time being, if it doesnt cost me anything !!

I love my computer more than I hate the flickers though!!

Also, whats this 'nomodeset/i915.modeset=1' option ?  what does it actually do ?

Thanks a lot.

---

### Post by ragingmon on 2010-06-05
> **Frantic_Earthling said:**
> I have found a solution to the screen flicker problem on my Asus UL20A.

Although the solution affecting power saving described above probably works (I have not tried it), I was a bit reluctant to tamper with this.

The overclocking function provided in my BIOS was originally set at 3% on a scale of 1 to 5%. 

I set it at 1%. 

The screen flicker has disappeared and frankly, I do not see any loss of performance resulting from the 2% overclocking drop.

I got AsusUL80 with fresh install ubuntu 10.04. Then installed kernel version 2.6.34 (for touchpad and FN+F9). 

I got the flickering issue, not really noticeable on day to day use but it flickers randomly. I just tried this solution, I'll update when this one works out. Thanks ;)

---

### Post by witeshark17 on 2010-07-05
This issue has not improved with all the current updates...

---

### Post by ve3tru on 2010-07-05
"This issue has not improved with all the current updates.."
How true,, I finally got the kernal thing to work, but in the last update I lost it, I updated my kernal. I even read how people are now going back to 9.04, because of the lack of progress. On a side note I'm even finding Wine going backwards, most everything won't work with it, stuff that used to.

---

### Post by Whisp3r on 2010-07-06
I swapped out my HD's and tried 10.04 with the mainline kernel, power save changes, etc. Still have the flickering. 

I'm camped out at 9.10 until this is fixed. I agree with the last poster. Between Wine, this issue, and other things, it sure seems like Ubuntu has plowed itself into a mud field. I recognize that this is a minor issue, but geez. It wasn't a problem for the last umpteen releases. 

Many thanks to the developers who are working on this issue. I hope it's resolved soon.

---

### Post by gmc on 2010-07-08
I managed to bork my Mac Mini system at home by screwing around with too many PPA's so I'm a bit leary to try this, but HowToForge ( [http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx) ) has information on installing the Intel v2.12 video drivers on Lucid.

Has anyone tried this to see if it corrects the random flickering problem?

Gord

---

### Post by Catharsis on 2010-07-08
Those instructions aren't the recommended way to install those packages. A much better way is:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update && sudo apt-get install ppa-purge
sudo apt-get upgrade
sudo apt-get install linux-lts-backport-maverick
```

This will keep the Maverick kernel up-to-date automatically. You can also remove the PPAs by using ppa-purge just like you'd use add-apt-repository.

---

### Post by Bagustrix on 2010-07-08
Does those instruction above to solve screen flicker on ubuntu 10.04?
I will apply those instruction and let see the result
I applied the previous intstruction but I still get flicker on my laptop (emachines D725,  Intel mobile 4 vga)..
Please, post to this forum ig anyone has solved it.
I'll keep get update from this forum.

---

### Post by whispers1944 on 2010-07-08
clean install on 2yo desktop , flicker will drive me back to UBUNTU 9 as there is no cure for 10.4 .... thats sad :-{

---

### Post by Mattevt on 2010-07-09
> **Catharsis said:**
> Those instructions aren't the recommended way to install those packages. A much better way is:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update && sudo apt-get install ppa-purge
sudo apt-get upgrade
sudo apt-get install linux-lts-backport-maverick
```

This will keep the Maverick kernel up-to-date automatically. You can also remove the PPAs by using ppa-purge just like you'd use add-apt-repository.

Thank you very much! Everything seems to be working just fine. I didn't notice this thread before I started my own. Fantastically, nothing was wrong with my hardware.

---

### Post by witeshark17 on 2010-07-09
Does this issue affect desktop LCD and CRT displays?

---

### Post by Mattevt on 2010-07-09
> **Mattevt said:**
> Thank you very much! Everything seems to be working just fine. I didn't notice this thread before I started my own. Fantastically, nothing was wrong with my hardware.

I take that back...I turned my computer on today and none of the kernels worked. Sound is there but there is no display.

Edit: I guess I should report my experience. The maverick kernel update worked for me initially, but today after a reboot, it was like my (laptop) monitor had turned off I had sound but no video on any of the kernels. I had to reinstall Ubuntu. Luckily I had just reinstalled it so there wasn't much to change (+all my files are on a separate partition).

I just tried the "i915.powersave=0" and everything seems fine so far. 

I really encourage everyone to visit this page:

[here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648") and vote if this problem affects you. Hopefully this issue will be addressed at least by next release.

---

### Post by ve3tru on 2010-07-18
Why is it when I read blogs on lets say linux mint, they don't have this problem.
I thought this was a kernal issue, they should have this problem too, as they are based on Ubuntu, and why is there no progress anywhere.
just asking?

---

### Post by meiklehmann on 2010-07-19
I'm having similar problems with my HP Compaq nc6400 notebook: flickering in darker areas of the screen. This happens with Ubuntu 10.04 with 32-bit installation as well as with 64-bit installation. Never had this problem with Ubuntu 9.04 or 9.10.

Here is the output of lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
02:06.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express (rev 21)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

That is the content of /var/logs/Xorg.0.log:
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntu104 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=2d8b7583-9180-4864-a67d-5a425c24fd99 ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 19 11:11:19 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:714a:103c:30ac ATI Technologies Inc M52 [Mobility Radeon X1300] rev 0, Mem @ 0xd8000000/67108864, 0xe0600000/65536, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched ati as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(II) [KMS] Kernel modesetting enabled.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Mobility Radeon X1300" (ChipID = 0x714a)
(II) RADEON(0): PCIE card detected
(II) RADEON(0): KMS Color Tiling: disabled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: AUO  Model: 1147  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 87.6 MHz   Image Size:  304 x 190 mm
(II) RADEON(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 912 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  AUO
(II) RADEON(0):  B141PW01 V1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af471100000000
(II) RADEON(0): 	010f0103801e13780a87c594574f8c27
(II) RADEON(0): 	25505400000001010101010101010101
(II) RADEON(0): 	0101010101013822a0a050840c303020
(II) RADEON(0): 	360030be100000180000000f00000000
(II) RADEON(0): 	00000000000000000020000000fe0041
(II) RADEON(0): 	554f0a202020202020202020000000fe
(II) RADEON(0): 	004231343150573031205631200a006f
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1440x900"x60.0   87.60  1440 1488 1520 1600  900 903 909 912 -hsync -vsync (54.8 kHz)
(II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
(II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
(II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1440x900
(II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:4000000 visible:3ab2000
(II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.5.0
	ABI class: X.Org Video Driver, version 6.0
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) RADEON(0): [DRI2] Setup complete
(II) RADEON(0): Front buffer size: 5244K
(II) RADEON(0): VRAM usage limit set to 49374K
(==) RADEON(0): Backing store disabled
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) EXA(0): Driver allocated offscreen pixmaps
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Set up textured video
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 381 x 238
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(II) XKB: reuse xkmfile /var/lib/xkb/server-76D2B5A359D34EEB9BFAEB1701EF70014DF39715.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device Lid Switch (/dev/input/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event0)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event0"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) RADEON(0): EDID vendor "AUO", prod id 4423
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0   87.60  1440 1488 1520 1600  900 903 909 912 -hsync -vsync (54.8 kHz)
(II) RADEON(0): EDID vendor "AUO", prod id 4423
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0   87.60  1440 1488 1520 1600  900 903 909 912 -hsync -vsync (54.8 kHz)
(II) RADEON(0): EDID vendor "AUO", prod id 4423
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0   87.60  1440 1488 1520 1600  900 903 909 912 -hsync -vsync (54.8 kHz)
(II) RADEON(0): EDID vendor "AUO", prod id 4423
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0   87.60  1440 1488 1520 1600  900 903 909 912 -hsync -vsync (54.8 kHz)
(II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event9)
(**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Generic Mouse: always reports core events
(**) PS/2 Generic Mouse: Device: "/dev/input/event9"
(II) PS/2 Generic Mouse: Found 3 mouse buttons
(II) PS/2 Generic Mouse: Found relative axes
(II) PS/2 Generic Mouse: Found x and y relative axes
(II) PS/2 Generic Mouse: Configuring as mouse
(**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
(II) PS/2 Generic Mouse: initialized for relative axes.
(II) RADEON(0): EDID vendor "AUO", prod id 4423
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0   87.60  1440 1488 1520 1600  900 903 909 912 -hsync -vsync (54.8 kHz)
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) RADEON(0): EDID vendor "AUO", prod id 4423
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0   87.60  1440 1488 1520 1600  900 903 909 912 -hsync -vsync (54.8 kHz)
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) Power Button: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
(II) Sleep Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) PS/2 Generic Mouse: Device reopened after 1 attempts.
(II) RADEON(0): EDID vendor "AUO", prod id 4423
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0   87.60  1440 1488 1520 1600  900 903 909 912 -hsync -vsync (54.8 kHz)
```

---

### Post by zjagannatha on 2010-07-25
I've got the same issue. I'm going to look into configuring the xorg-server via /etc/X11/xorg.conf If I find anything I'll let you know.

sudo lspci
Results:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
```
sudo lshw -C display
Results:
```
  *-display:0
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:f4000000-f43fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f4400000-f44fffff
```

---

### Post by ve3tru on 2010-07-26
10.04 was a disaster for me, the screen flicker got so bad my computer locked up a lot.
It had other issues like most every thing wouldnt work with wine (programs I needed for school would no longer work under 10.04 and wine) and it had other problems too.
So I upgraded to Ubuntu 10.10 Maverick Meerkat "Alpha-2" and it looks like these problems are fixed, although its still early and its full of bugs, hard to tell. I'm not a fan of how Ubuntu just fixes problems in new releases, this really goes against the whole concept of LTS support, or maybe the whole LTS thing is unworkable and needs to die, I don't know. In my case I'm always looking to the latest release to fix my problems and that goes all the way back to 8.04

---

### Post by zjagannatha on 2010-07-28
I'm actually thinking it's a hardware issue. I've noticed than whenever it flickers if I move the screen a bit. (Like wiggle it forward or backward) it goes away for a while.

---

### Post by witeshark17 on 2010-07-28
There may be such in your case. But the central issue here is not hardware; it never occured in my case at all in 9.04 or 9.10. It seems clearly to be a common issue with very many after upgrading to 10.04

---

### Post by HoangDaddy on 2010-07-28
I'm having a screen flickering issue on my projector connected to my IBM R51 laptop. The laptop monitor is working fine.

When there is any type of animation or movement displayed the entire screen would flicker. The project is a Toshiba TLP261. I currently have a mirror monitor setup at 1024x768. Can someone help?!

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

---

### Post by itsols on 2010-08-01
Is this your first OS on Ubuntu or did you upgrade from another?

Like I said in my thread ( [http://ubuntuforums.org/showthread.php?p=9667110#post9667110](http://ubuntuforums.org/showthread.php?p=9667110#post9667110) ), I think it's a bug with the graphics algorithm on Ubuntu.

I originally used Ubuntu for these reasons:

1. Speed on slower hardware
2. More secure
3. Open source

But now I'm rethinking if point 1 is valid.

I honestly don't think this is anything to do with the hardware.

I wish I can go back into version 8.10... but it's too late for that.

---

### Post by witeshark17 on 2010-08-01
Some more on this in [ another thread](http://ubuntuforums.org/showthread.php?t=1521481)

---

### Post by HoangDaddy on 2010-08-02
Hey thanks for the reply... This is a fresh install of Ubuntu 10.04 coming from Windows XP. I never had a problem using the projector with Windows and it started happening using Ubuntu.

---

### Post by witeshark17 on 2010-08-02
Yup... It's clearly an issue with 10.04. Have a look at the Launchpad links in the other thread and add your input if you see that it adds some not already there.

---

### Post by witeshark17 on 2010-08-06
With the current updates, it seems to occur in pairs, twice in quick succession now.

---

### Post by itsols on 2010-08-06
I have many graphics related issues but this flicker with the projector screen seems to be one key issue. The other (not related here but IS connected) is the low-graphics mode crash... I'm not going to repeat my issues but I'd like a quick question answered if possible.

Question: Is there a way to START Ubuntu in low graphics mode? or once I've started, is there a way to get into low-graphics mode? I somehow feel that this MAY fix it.

Thanks

---

### Post by witeshark17 on 2010-08-15
Here's a [ LaunchPad thread](https://bugs.launchpad.net/ubuntu/+bug/587935) to have a look at

---

### Post by alexcherry on 2010-09-28
I have Lenovo G550 with Ubuntu Lucid, and I got problems with random flickering. Yesterday I put i915.powersave=0 into grub.conf and it looks that it fixed this problem

---

### Post by witeshark17 on 2010-09-28
Thanks for letting us know; it seems to work for some but not for others...

---

### Post by ve3tru on 2010-09-28
*Ubuntu* 10.10 "Maverick Meerkat"
Has none of these problems it might be time to upgrade your OS, its fairly stable now and will be released soon.

---

### Post by witeshark17 on 2010-09-28
^ Yeah I've noticed that; so whichever comes first then... :guitar:

---

### Post by itsols on 2010-09-28
Hi alexcherry, Thanks for sharing but I'd like to clarify/elaborate a few things...

1. Anyone having a flickering problem is NOT just a projector screen but with ANY secondary screen.

2. is the grub.conf change specific to your config? I ask because I'm not sure what that parameter means... The more I use Ubuntu, the more I realise I don't know - lol!

Note: As for version 10.10, I wouldn't want to gamble on it right now. I have my hands full with this already - smiles...

---

### Post by Whisp3r on 2010-10-11
Has anyone upgrade to 10.10 and still have the same problem? I've been testing the live version and so far haven't had any problems, but that doesn't mean much...

---

### Post by belgianfries on 2010-10-23
I perfectly have this problem with 10.10. From all I read it seems to be some randr monitor change detection responsible for this and in previous Ubuntu releases it seems it was possible to turn this off - but not in 10.10?

Edit: I just found out this "monitor change detection" is a KDE service which I don't have running. So now I am wondering, if there is something at all that can be done about this repeated monitor detection going on? The screen is not correctly detected anyway...

---

### Post by rothgar on 2010-11-15
I have tested on a HP 2540p with Ubuntu 10.10 and Linux Mint 10 and have the flickering screen issue with both. I only have the problem on the internal monitor and it does not appear to affect an external monitor through display port.

I'm still searching for a solution.

---

### Post by witeshark17 on 2010-11-16
So almost certainly a kernel issue then...

---

### Post by itsols on 2010-11-16
Ok, so it's (probably) a Kernel issue... Can we all do a Kernel comparison? For those who don't know, simply go on the terminal and type the following line:
uname -r

This gives info about the Kernel.

Here's mine:
2.6.33-02063303-generic

Maybe we can narrow down the problem with this.

---

### Post by benishor on 2010-11-16
The problems I had with my ASUS K50IJ laptop screen flickering have disappeared after upgrading to 10.10. My current kernel version is 2.6.35-22-generic. I would really suggest upgrading to Maverick and not looking back.

---

### Post by itsols on 2010-11-16
Yes, it clearly seems like moving on to 10.10 is an option for many. But here's the thing:

1. rothgar seems to have the problem with 10.10 and NOT the older version.
2. If you look carefully, my 10.04 is NOT the default kernel either. With the default one, I had no GUI - it never worked!

But again, we don't have much choice but to move on. As for me, it's still not the right time to upgrade.

---

### Post by the.scarecrow on 2010-11-16
> **benishor said:**
> The problems I had with my ASUS K50IJ laptop screen flickering have disappeared after upgrading to 10.10. My current kernel version is 2.6.35-22-generic. I would really suggest upgrading to Maverick and not looking back.

+1 for me to. Bravo 10.10

I have a Dell Inspiron 1750 and thankfully no more screen flicker.

---

### Post by itsols on 2010-11-16
> **the.scarecrow said:**
> 

I have a Dell Inspiron 1750 and thankfully no more screen flicker.

Are you referring to the primary/default screen or the second screen, or both?

---

### Post by the.scarecrow on 2010-11-18
> **itsols said:**
> Are you referring to the primary/default screen or the second screen, or both?

The primary screen. The flash was most noticeable using Firefox but then again thats what I use most of the time on this laptop.

---

### Post by itsols on 2010-11-19
Yes!
At first, it was disaster. My laptop HDD crashed. Nothings recoverable. I had to do a fresh install!

So I installed a new HDD and when ahead with 10.10.

And, yes, there's NO MORE FLICKER!!!

I had no primary screen issues anyway. But now even the secondary screens look just great!

And now I need to configure and install 8 years of software!!!

Happy computing!

---

### Post by learst on 2010-11-29
Hi,

I'm new to Ubuntu and currently using a dualboot Ubuntu 10.04 and Windows Vista on a Dell Inspiron 1420/nVidia 8400 M GS . 

I switched to Ubuntu earlier this year, and after a while noticed some flickering. I thought it was a hardware problem since it also happened in Windows (thought it started appearing in Ubuntu first). Then the flickering became more frequent until it started flickering every 2-3 seconds which was really bad. I contacted Dell technical support and they thought it was a motherboard problem and changed a new one. I was a bit surprised as I've just had the motherboard changed less than 6 months ago (due to another hardware problem)

I did a fresh install and everything seemed ok, but then the flickering started appearing again. I started googling and now i'm quite sure this is not a hardware problem. And right not the flickering seems to have increased in frequency and intensity again.

I saw some solutions suggested by other posters but I'm not quite sure  how to carry them out since I'm not that great with all the technical  bits.I have some projects to rush now, but will try to figure out the some of those solutions later when I have more time.

---

### Post by scohar70 on 2010-11-29
I had the same problems, and I eventually had to downgrade to Ubuntu 9.xx to solve the problem.  It is definitely not a hardware problem.  A software downgrade solved the problem.

---

### Post by witeshark17 on 2010-11-29
Was that with 10.10 and 10.04 or just .04?

---

### Post by learst on 2010-11-29
> **witeshark17 said:**
> Was that with 10.10 and 10.04 or just .04?

Not sure if you're asking me, but I'm using 10.04 with the current kernel .26. I have not tried 10.10 yet, and a bit loathed to try it since I just reinstalled everything few weeks ago.

---

### Post by scohar70 on 2010-11-29
> **witeshark17 said:**
> Was that with 10.10 and 10.04 or just .04?

10.04 for me.

---

### Post by itsols on 2010-11-29
I was SUFFERING with the same problem when I had 10.04 but now the issue is fixed. Apparently NOTHING solved the issue on 10.04. The only thing I did was do a clean install on 10.10.

And now the problem is gone. So my advice to you is just install 10.10 afresh and you should be fine.

Cheers!

---

### Post by witeshark17 on 2010-11-29
> **itsols said:**
> I was SUFFERING with the same problem when I had 10.04 but now the issue is fixed. Apparently NOTHING solved the issue on 10.04. The only thing I did was do a clean install on 10.10.

And now the problem is gone. So my advice to you is just install 10.10 afresh and you should be fine.

Cheers! Okay good to know. 10.10 is next on the list then. 2.6.32-26.48 is on now in 10.04 and the issue is still there.

---

### Post by learst on 2010-12-01
Ok, firstly apologies ahead if I sound a little bit pissed.

As mentioned previously, I was using a dual-boot Windows Vista/Ubuntu 10.04 on a Dell inspiron 1420/nVidia G8400 M. After some posters suggested doing a clean isntall with 10.10, I finally decided to go ahead since the flicking became very annoying.

I reformatted the drive and installed Windows first, and then realised that the screen flickering is happening even when installing Windows. The flickering persisted throughout the entire Windows install, and Ubuntu 10.10 install. 

I think I read somewhere that the screen flickering bug could be due to messing up of the BIOS (some syncing stuff or something). I'm starting to suspect this is true and I really don't know what to do now! I know going into Ubuntu from Windows would  be a bit rocky, but I never thought it would mess up my laptop this badly. Even after trying a  fresh install of both Windows and Ubuntu and the screen keeps flickering! 

I had the motherboard changed 2 weeks ago as the Dell technical support thought it was a motherboard problem, and I'd really really would not want to contact them again!

---

### Post by aperomsik on 2010-12-01
@learst, it sounds like you suspect that installing Ubuntu messed up your BIOS somehow, in a way that would affect this problem. I don't understand how that could be, especially since you say Dell swapped the motherboard. Isn't the BIOS on the motherboard?

---

### Post by witeshark17 on 2010-12-01
I'm not sure everyone is discussing the same issue. Can the 10.10 users post up whether or not they see this issue anymore please?

---

### Post by learst on 2010-12-01
@aperosmik

Welll, after I got a new motherboard and did a clean install of Windows and Ubuntu 10.04, things seemed ok for a few days before the flickering started again. Then the flickering gets more frequent. 

Since some posters suggested updating to 10.10, I did reformatted my drive and did a clean install of Windows and Ubuntu 10.10 and the flickering still continued. I'm not really sure if the cause was some changes to BIOS (I think i read that while googling somewhere), but other than that what could be the possible cause?

@witeshark
I've updated to 10.10 and the flickering still continued when reformatting my drive/starting up/running Windows/installing Ubuntu/running Ubuntu.

---

### Post by itsols on 2010-12-02
Ok, in short, here's the story...

1. I had no primary screen flicker with my Dell laptop when I used 10.04.
2. But with 10.04, any external display (projectors, CRTs, LCDs) would flicker badly.
3. Nothing could solve the flicker in 10.04 - where the second screen was concerned..
4. I did a fresh install of 10.10 and both primary and secondary screens work GREAT. No more flicker.
5. My laptop is a Dell Inspiron 1150 with 2.8 PIV, 512 RAM.
6. With 10.10, all seem to be ok but I can't enable any animation on the OS. I believe this is due to my RAM restriction.

But I'm happy I can work trouble-free now, unlike before.

Now, can it affect the BIOS? I doubt it. I really don't know. But since you mentioned a motherboard change, I have reason to believe that it's the board.

Happy computing!

---

### Post by learst on 2010-12-02
@itsols:

Maybe I wasn't very clear with the my problem. I have been using Windows Vista primarily on my Dell Inspiron 1420/nVidia GS8400 M. Then once there was a problem where there was no display even though the monitor was lighted. This was April, and I was given a motherboard changed. 

After that I did a clean format to use a dual-boot Windows/ Ubuntu 10.04. And I noticed the flickering started in Ubuntu. It was very brief and rare, but then it got more frequent. The flickering also occured when I use Windows. I contacted Dell technical support, and they thought it was a motherboard problem so I was given a new motherboard again (3 weeks ago). 

With this new motherboard, I did a clean reinstall of Windows and Ubuntu 10.04. After a few days, the flickering started again and I can't get it to stop. Since some posters suggested updating to Ubuntu 10.10, I formatted my drive to reinstall Win/Ubuntu. I noticed the flickering persisted throughout the installation of Windows and Ubuntu, and even while starting up. I really doubt this is a hardware problem with the motherboard as I've just got a new one. 

I really don't know what else to do, and I've spent a lot of time wiping and reinstalling Windows/Ubuntu and now nothing seems to be able to get rid of the flickering!

---

### Post by learst on 2010-12-03
Hi,

Just an update on something I found recently which said that my flickering screen could be due to hardware problem (Dell 1420 with nVidia) rather than anything to do with Ubuntu at all.

[http://en.community.dell.com/dell-blogs/Direct2Dell/b/direct2dell/archive/2008/08/08/latest-on-the-nvidia-gpu-issue-for-dell-laptop-customers.aspx](http://en.community.dell.com/dell-blogs/Direct2Dell/b/direct2dell/archive/2008/08/08/latest-on-the-nvidia-gpu-issue-for-dell-laptop-customers.aspx)

---

### Post by clockworktri on 2011-01-10
I don't know if this is helpful to you, but when looking for a solution for my inspiron 1545, I found that a couple of things can cause flickering. One of which is using nVidia. I don't run it but if you do, maybe that's where the issue lies?

---

### Post by the.scarecrow on 2011-01-17
I used to have this problem using 10.04. I have used 10.10 regularly for many weeks now and have not seen the screen flash again since doing this fresh install.

Regretably, like me, you may get this bug instead.... ho hum.

[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

---

### Post by witeshark17 on 2011-01-17
I had the flicker end with the installation of 10.10 as well. As to GNOME, there was a GUI crash after trying some new themes, launchpad post [ here](https://answers.launchpad.net/ubuntu/+question/141828) Other than that, it's all joy with 10.10 :popcorn:

---

### Post by witeshark17 on 2011-01-25
The flicker seems solved, saw a Launchpad e-mail that says a fix was released.

---

### Post by Kognit on 2011-02-15
Hi

My ASUS k50ij (Ubuntu 10.04) started to randomly flickering 1 week ago. 
Some guys suggested that killing gnome-power-manager solved the issue. But the problem is that in this case you can't manage the power. So, for some guys suffice this to run in terminal:
```
gnome-power-manager --no-daemon
```

[Link]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/415023")

I am trying the workaround for two hours now. No flickering for now.

---

### Post by witeshark17 on 2011-02-15
Are you sure it's the same issue?

---

### Post by Kognit on 2011-02-16
> **witeshark17 said:**
> Are you sure it's the same issue?

Well my laptop's monitor flickers randomly, especially when i change  the monitor's brightness via buttons. For now, this "method" works for me. In the link i have posted above some guy managed to "overcome" the problem with downgrading the "udev".

---

### Post by witeshark17 on 2011-02-17
I'm pretty sure the issue here was not about the use of display brightness buttons... best of luck!

---

### Post by mbdong on 2011-08-29
Absolutely, I have the same problem with Ubuntu 10.04.

My VGA card is Intel 82852/855GM
Must include i915.modeset=1 in boot menu.
But this can only enable the graphic login. The screen still flickers from time to time. Thought this is a problem of Ubuntu.

---

### Post by Kognit on 2011-08-29
> **mbdong said:**
> Absolutely, I have the same problem with Ubuntu 10.04.

My VGA card is Intel 82852/855GM
Must include i915.modeset=1 in boot menu.
But this can only enable the graphic login. The screen still flickers from time to time. Thought this is a problem of Ubuntu.

After kernel upgrade to 2.6.37 or 2.6.39 no more flickering.

---

