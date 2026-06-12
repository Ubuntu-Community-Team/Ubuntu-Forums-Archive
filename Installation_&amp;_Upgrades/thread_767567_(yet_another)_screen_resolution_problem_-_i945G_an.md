---
title: "(yet another) screen resolution problem - i945G and 1440x900 on Hardy"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by agivati on 2008-04-25
Intel i945G integrated gfx, Samsung SyncMaster 931bw 1440x900 monitor.
Installed Ubuntu 8.04. Can not set to 1440x900 resolution.
1440x900 do not appear in System->Preference->Screen Resolution.
Tried playing with xorg.conf based on tips from these forums. either the resolution did not show up in the list or when it did, it did not display correctly (e.g. could not see bottom of screen).
Tried installing and using 915resolution hack for Intel chipset (using tip from [here]("http://ubuntuforums.org/showthread.php?p=2113867")) but it didn't get me further.
from Xorg.0.log:
> ...
(--) PCI:*(0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xd3100000/19, 0xc0000000/28, 0xd3180000/18, I/O @ 0xc000/3
...
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset 945G found
...
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xD3100000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1280x768
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000000 to 0x00000b00
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000203 to 0x80000203
(WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): PIPEASTAT after: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd3180000 - 0xd31bffff (0x40000) MS[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[2] 0	0	0xd3100000 - 0xd317ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd2000000 - 0xd20003ff (0x400) MX[B]
	[8] -1	0	0xd3000000 - 0xd300ffff (0x10000) MX[B]
	[9] -1	0	0xd3010000 - 0xd3010fff (0x1000) MX[B]
	[10] -1	0	0xd31c4000 - 0xd31c43ff (0x400) MX[B]
	[11] -1	0	0xd31c0000 - 0xd31c3fff (0x4000) MX[B]
	[12] -1	0	0xd3180000 - 0xd31bffff (0x40000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd3100000 - 0xd317ffff (0x80000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] 0	0	0x0000c000 - 0x0000c007 (0x8) IS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[22] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[23] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): [drm] Registers = 0xd3100000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] mapped front buffer at 0xc1000000, handle = 0xc1000000
(II) intel(0): [drm] mapped back buffer at 0xc4000000, handle = 0xc4000000
(II) intel(0): [drm] mapped depth buffer at 0xc5000000, handle = 0xc5000000
(II) intel(0): [drm] mapped classic textures at 0xc6000000, handle = 0xc6000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 31457280 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x06000000 (pgoffset 24576)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB, 0x000000003f832000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (10240 kB) X tiled
(II) intel(0): 0x02000000-0x03dfffff: exa offscreen (30720 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (10240 kB) X tiled
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (10240 kB) X tiled
(II) intel(0): 0x06000000-0x07ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled


---

### Post by dabd on 2008-10-23
Do intel drivers for 945GM support SDVO?

---

