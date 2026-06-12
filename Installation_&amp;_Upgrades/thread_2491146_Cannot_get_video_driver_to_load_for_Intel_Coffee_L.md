---
title: "Cannot get video driver to load for Intel Coffee Lake UHD 630 Graphics"
date: 2023-09-27
forum: Installation &amp; Upgrades
---

### Post by lazaruslong67 on 2023-09-27
Mostly first time Linux user here - trying to install Ubuntu on a Lenovo m720Q "mini" PC.  Has 16GB of RAM and an Intel i5-8500T CPU w/Intel UHD 630 GPU

It appears to not be picking up the included video driver for some reason.  I think it's the i915 driver?

I have tried various Linux distributions (Mint, Ubuntu, (k)ubuntu) - all exhibit the same problem.  Because it's not using the driver, I get weird video artifacts, slowness, freezing, etc.

Just not sure where to start.  I can boot into recovery mode and most of the time as least navigate some of the UI.

---

### Post by #&amp;thj^% on 2023-09-27
There has been a few report this, as a try and see method, would you try to add this to:
"/etc/default/grub" and add this:
```
GRUB_CMDLINE_LINUX_DEFAULT="i915.alpha_support=1 quiet"
```
Then inform grub about the change with:
```
sudo update-grub
```
A member here is working very hard with Intel now over all this.

---

### Post by MAFoElffen on 2023-09-27
You didn't post the version of Ubuntu and which Linux kernel version you are running on. Could you please post that information? It matters for using that kernel parameter. 

In my notes from Intel, the kernel range for alpha support was from 3.12 to 5.10 (that was confirmed by them), but from kernel 4.10 and "newer" that you need to use i915.alpha_support=1 instead of i915.preliminary_hw_support=1. For newer, I don't see where their code changed for that up through 6.5.
RE: [https://github.com/Intel-Media-SDK/MediaSDK/wiki/Intel-Graphics-Support-in-Linux-Kernels](https://github.com/Intel-Media-SDK/MediaSDK/wiki/Intel-Graphics-Support-in-Linux-Kernels)

There is no harm if it isn't matched correctly for the kernel version range... In that case it will just ignore that parameter.

For that to work, that implies that /usr/lib/firmware/i915 is populated and up-to-date by package 'linux-firmware' and is affected by which version of intel-media-va-driver* you are using...

---

### Post by lazaruslong67 on 2023-09-27
> **MAFoElffen said:**
> You didn't post the version of Ubuntu and which Linux kernel version you are running on. Could you please post that information? It matters for using that kernel parameter. 

In my notes from Intel, the kernel range for alpha support was from 3.12 to 5.10 (that was confirmed by them), but from kernel 4.10 and "newer" that you need to use i915.alpha_support=1 instead of i915.preliminary_hw_support=1. For newer, I don't see where their code changed for that up through 6.5.
RE: [https://github.com/Intel-Media-SDK/MediaSDK/wiki/Intel-Graphics-Support-in-Linux-Kernels](https://github.com/Intel-Media-SDK/MediaSDK/wiki/Intel-Graphics-Support-in-Linux-Kernels)

There is no harm if it isn't matched correctly for the kernel version range... In that case it will just ignore that parameter.

For that to work, that implies that /usr/lib/firmware/i915 is populated and up-to-date by package 'linux-firmware' and is affected by which version of intel-media-va-driver* you are using...

I've tried various versions - started with 22.04.3 LTS but then have gone back to 20, 18 and 17 (basically trying with various "fixes" I've seen suggested).  What version would give me the best luck of success?

---

### Post by #&amp;thj^% on 2023-09-27
Tell us where you are now.
```
cat /etc/os-release && uname -r

```

---

### Post by lazaruslong67 on 2023-09-27
I decided to start over and currently have booted from a USB ISO of 22.04.3.  I haven't installed yet - currently just booted into "Safe Graphics" from the flash drive.

Should I try to install first (while in Safe Graphics mode)?  Or just "try Ubuntu" ?

---

### Post by lazaruslong67 on 2023-09-27
> **1fallen said:**
> Tell us where you are now.
```
cat /etc/os-release && uname -r

```

PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
6.2.0-33-generic

---

### Post by lazaruslong67 on 2023-09-27
> **1fallen said:**
> There has been a few report this, as a try and see method, would you try to add this to:
"/etc/default/grub" and add this:
```
GRUB_CMDLINE_LINUX_DEFAULT="i915.alpha_support=1 quiet"
```
Then inform grub about the change with:
```
sudo update-grub
```
A member here is working very hard with Intel now over all this.

Added that line and rebooted and still no luck - graphics issues immediately after login.  Only way I can use the environment is booting into Recovery.

---

### Post by lazaruslong67 on 2023-09-27
> **MAFoElffen said:**
> You didn't post the version of Ubuntu and which Linux kernel version you are running on. Could you please post that information? It matters for using that kernel parameter. 

In my notes from Intel, the kernel range for alpha support was from 3.12 to 5.10 (that was confirmed by them), but from kernel 4.10 and "newer" that you need to use i915.alpha_support=1 instead of i915.preliminary_hw_support=1. For newer, I don't see where their code changed for that up through 6.5.
RE: [https://github.com/Intel-Media-SDK/MediaSDK/wiki/Intel-Graphics-Support-in-Linux-Kernels](https://github.com/Intel-Media-SDK/MediaSDK/wiki/Intel-Graphics-Support-in-Linux-Kernels)

There is no harm if it isn't matched correctly for the kernel version range... In that case it will just ignore that parameter.

For that to work, that implies that /usr/lib/firmware/i915 is populated and up-to-date by package 'linux-firmware' and is affected by which version of intel-media-va-driver* you are using...

I did check and I do have a populated i915 folder.  How would I make sure it's up-to-date by package 'linux-firmware' ?

---

### Post by #&amp;thj^% on 2023-09-27
> **lazaruslong67 said:**
> I did check and I do have a populated i915 folder.  How would I make sure it's up-to-date by package 'linux-firmware' ?
all of this through:
```
apt update
apt upgrade
```
Give him some time to respond, like I said he is working with them now.
I'm all older Intel chips, and newer AMD nVidia chips here.
MAFoElffen has the newish i9 chip so he will be better suited to assist here.

---

### Post by MAFoElffen on 2023-09-27
Sorry for the delay. Was out Salmon Fishing. Had to unwind sometimes. LOL.

Checking the versions of?
```

sudo lspci -nnv | grep -i -e 'Intel' | grep -A 11 -e 'VGA' | grep -i -e 'VGA\|Kernel driver\|Kernel modules'
sudo lshw -C video | grep -e 'product\|driver'
apt list intel-va-media-driver* --installed
apt list linux-firmware* --installed

```

---

### Post by lazaruslong67 on 2023-09-27
> **MAFoElffen said:**
> Sorry for the delay. Was out Salmon Fishing. Had to unwind sometimes. LOL.

Checking the versions of?
```

sudo lspci -nnv | grep -i -e 'Intel' | grep -A 11 -e 'VGA' | grep -i -e 'VGA\|Kernel driver\|Kernel modules'
sudo lshw -C video | grep -e 'product\|driver'
apt list intel-va-media-driver* --installed
apt list linux-firmware* --installed

```

00:02.0 VGA compatible controller [0300]: Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630] [8086:3e92] (prog-if 00 [VGA controller])
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_cnl

product: CoffeeLake-S GT2 [UHD Graphics 630]
       product: EFI VGA

Nothing returned for "apt list intel-va-media-driver* --installed"

linux-firmware/jammy-updates,jammy-updates,now 20220329.git681281e4-0ubuntu3.18 all [installed,automatic]
linux-firmware/jammy-security,jammy-security 20220329.git681281e4-0ubuntu3.14 all
linux-firmware/jammy,jammy 20220329.git681281e4-0ubuntu1 all


NOTE - not sure if this matters, but I ran this stuff while within Recovery mode (otherwise the GUI is basically unresponsive/pixelated/etc.)

And now I could use some salmon!

---

### Post by MAFoElffen on 2023-09-28
Something is wrong there. Rerun this to expand the filter on this. You say the desktop boots but is unresponsive or unusable. What I want you to do is boot that, but after you log, when the pixelated desktop loads, then press the keys <Cntrl><Alt><F4>. Log into VTTY4. Then do
```

sudo lspci -nnv | grep -i -e 'Intel' | grep -A 11 -e 'VGA' > ~/Documents/lspci.txt

```
That way you can capture the exact output to a file, and you don't have to retype anything...

---

### Post by lazaruslong67 on 2023-09-28
> **MAFoElffen said:**
> Something is wrong there. Rerun this to expand the filter on this. You say the desktop boots but is unresponsive or unusable. What I want you to do is boot that, but after you log, when the pixelated desktop loads, then press the keys <Cntrl><Alt><F4>. Log into VTTY4. Then do
```

sudo lspci -nnv | grep -i -e 'Intel' | grep -A 11 -e 'VGA' > ~/Documents/lspci.txt

```
That way you can capture the exact output to a file, and you don't have to retype anything...

Currently I can't even get past the login screen...that screen itself has graphics artifacts on it and appears to be frozen.  I reboot and sometimes get different results - I login and get the desktop but then it freezes up.

Would there by any other better way to get this info?

---

### Post by lazaruslong67 on 2023-09-28
> **MAFoElffen said:**
> Something is wrong there. Rerun this to expand the filter on this. You say the desktop boots but is unresponsive or unusable. What I want you to do is boot that, but after you log, when the pixelated desktop loads, then press the keys <Cntrl><Alt><F4>. Log into VTTY4. Then do
```

sudo lspci -nnv | grep -i -e 'Intel' | grep -A 11 -e 'VGA' > ~/Documents/lspci.txt

```
That way you can capture the exact output to a file, and you don't have to retype anything...

OK - finally was able to get into VTTY4 from the login screen.  Results are below:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630] [8086:3e92] (prog-if 00 [VGA controller])
00:08.0 System peripheral [0880]: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model [8086:1911]
00:14.0 USB controller [0c03]: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller [8086:a36d] (rev 10) (prog-if 30 [XHCI])
00:14.2 RAM memory [0500]: Intel Corporation Cannon Lake PCH Shared SRAM [8086:a36f] (rev 10)
00:16.0 Communication controller [0780]: Intel Corporation Cannon Lake PCH HECI Controller [8086:a360] (rev 10)
00:17.0 SATA controller [0106]: Intel Corporation Cannon Lake PCH SATA AHCI Controller [8086:a352] (rev 10) (prog-if 01 [AHCI 1.0])
00:1b.0 PCI bridge [0604]: Intel Corporation Cannon Lake PCH PCI Express Root Port #21 [8086:a32c] (rev f0) (prog-if 00 [Normal decode])
00:1c.0 PCI bridge [0604]: Intel Corporation Cannon Lake PCH PCI Express Root Port #6 [8086:a33d] (rev f0) (prog-if 00 [Normal decode])
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:a308] (rev 10)
00:1f.3 Audio device [0403]: Intel Corporation Cannon Lake PCH cAVS [8086:a348] (rev 10) (prog-if 80)
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_cnl
```

---

### Post by #&amp;thj^% on 2023-09-28
Intel is to blame here:
```
 inxi -G &&  sudo dmesg | grep -i i915
Graphics:
  Device-1: Intel CometLake-U GT2 [UHD Graphics] driver: i915 v: kernel
  Device-2: IMC Networks Integrated Camera driver: uvcvideo type: USB
  Display: x11 server: X.org v: 1.21.1.8 driver: X: loaded: intel
    unloaded: modesetting dri: i965 gpu: i915
    resolution: <missing: xdpyinfo/xrandr> resolution: 1920x1080
  API: OpenGL v: 4.6 Mesa 23.1.5 renderer: Mesa Intel UHD Graphics (CML GT2)
[    1.233736] i915 0000:00:02.0: enabling device (0006 -> 0007)
[    1.234436] i915 0000:00:02.0: vgaarb: deactivate vga console
[    1.235612] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=mem
[    1.237235] i915 0000:00:02.0: [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[    1.276548] i915 0000:00:02.0: [drm] [ENCODER:102:DDI B/PHY B] is disabled/in DSI mode with an ungated DDI clock, gate it
[    1.276553] i915 0000:00:02.0: [drm] [ENCODER:118:DDI C/PHY C] is disabled/in DSI mode with an ungated DDI clock, gate it
[    2.483964] [drm] Initialized i915 1.6.0 20201103 for 0000:00:02.0 on minor 0
[    2.502863] fbcon: i915drmfb (fb0) is primary device
[    2.502866] i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer device
[    4.541566] mei_hdcp 0000:00:16.0-b638ab7e-94e2-4ea2-a552-d1c54b627f04: bound 0000:00:02.0 (ops i915_hdcp_component_ops [i915])
[    4.984273] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])

```
And:
```
cat /etc/default/grub
# GRUB boot loader configuration

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="Arch"
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 snd-intel-dspcfg.dsp_driver=1 lsm=landlock,lockdown,yama,integrity,apparmor,bpf quiet"
GRUB_CMDLINE_LINUX=""

# Preload both GPT and MBR modules so that they are not missed
GRUB_PRELOAD_MODULES="part_gpt part_msdos"

# Uncomment to enable booting from LUKS encrypted devices
#GRUB_ENABLE_CRYPTODISK=y

# Set to 'countdown' or 'hidden' to change timeout behavior,
# press ESC key to display menu.
GRUB_TIMEOUT_STYLE=menu

# Uncomment to use basic console
GRUB_TERMINAL_INPUT=console

# Uncomment to disable graphical terminal
#GRUB_TERMINAL_OUTPUT=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `videoinfo'
GRUB_GFXMODE=auto

# Uncomment to allow the kernel use the same resolution used by grub
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you want GRUB to pass to the Linux kernel the old parameter
# format "root=/dev/xxx" instead of "root=/dev/disk/by-uuid/xxx"
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY=true

# Uncomment and set to the desired menu colors.  Used by normal and wallpaper
# modes only.  Entries specified as foreground/background.
#GRUB_COLOR_NORMAL="light-blue/black"
#GRUB_COLOR_HIGHLIGHT="light-cyan/blue"

# Uncomment one of them for the gfx desired, a image background or a gfxtheme
#GRUB_BACKGROUND="/path/to/wallpaper"
#GRUB_THEME="/path/to/gfxtheme"

# Uncomment to get a beep at GRUB start
#GRUB_INIT_TUNE="480 440 1"

# Uncomment to make GRUB remember the last selection. This requires
# setting 'GRUB_DEFAULT=saved' above.
#GRUB_SAVEDEFAULT=true

# Uncomment to disable submenus in boot menu
#GRUB_DISABLE_SUBMENU=y

# Probing for other operating systems is disabled for security reasons. Read
# documentation on GRUB_DISABLE_OS_PROBER, if still want to enable this
# functionality install os-prober and uncomment to detect and include other
# operating systems.
#GRUB_DISABLE_OS_PROBER=false

```
Please don't use anything from grub line yet, as they are for Arch
```
sudo lspci -nnv | grep -i -e 'Intel' | grep -A 11 -e 'VGA' | grep -i -e 'VGA\|Kernel driver\|Kernel modules'
[sudo] password for me: 
00:02.0 VGA compatible controller [0300]: Intel Corporation CometLake-U GT2 [UHD Graphics] [8086:9b41] (rev 02) (prog-if 00 [VGA controller])
	Kernel driver in use: intel_pch_thermal
	Kernel modules: intel_pch_thermal
	Kernel driver in use: intel-lpss

```

---

### Post by MAFoElffen on 2023-09-28
That was my fault. Sorry.

Lets try that again, hopefully only one more time:
```

GPU_List=$(sudo lspci | awk '/VGA|Display|3D/ {print $1}');for GPU_ID in ${GPU_List[@]};do sudo lspci -s $GPU_ID -vnn; done

```
I need to see that detail... I'm spinning up a VM to test if it shows me what I need to see from toggling over at the DM panel (Graphical Login).

[s]*** Wait for "this" line to update, after I confirmed that... ***[/s]
Yes, it shows what I need to see, from toggling over at that point... Please run that now.

---

### Post by #&amp;thj^% on 2023-09-28
+1 that's much better:
```
GPU_List=$(sudo lspci | awk '/VGA|Display|3D/ {print $1}');for GPU_ID in ${GPU_List};do sudo lspci -s $GPU_ID -vnn; done
[sudo] password for me: 
00:02.0 VGA compatible controller [0300]: Intel Corporation CometLake-U GT2 [UHD Graphics] [8086:9b41] (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Lenovo CometLake-U GT2 [UHD Graphics] [17aa:2292]
	Flags: bus master, fast devsel, latency 0, IRQ 139
	Memory at e9000000 (64-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=64]
	Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
	Capabilities: [40] Vendor Specific Information: Len=0c <?>
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [100] Process Address Space ID (PASID)
	Capabilities: [200] Address Translation Service (ATS)
	Capabilities: [300] Page Request Interface (PRI)
	Kernel driver in use: i915
lspci: Unable to load libkmod resources: error -2

```

---

### Post by MAFoElffen on 2023-09-28
@1fallen --- Yes, if you look at his previous post with his output, Post #9, it said:
```

00:02.0 VGA compatible controller [0300]: Intel Corporation CoffeeLake-S  GT2 [UHD Graphics 630] [8086:3e92] (prog-if 00 [VGA controller])
    Kernel driver in use: [COLOR=#ff0000]snd_hda_intel[/COLOR]
    Kernel modules: [COLOR=#ff0000]snd_hda_intel, snd_sof_pci_intel_cnl[/COLOR]

```
That does not make sense. Those are sound drivers/modules. 

I am just confirming that either the query was at fault, or his system is doing very strange things.

### Sidenote -- That reminds me that I have to fix / update the filter for that in the 'system-info' script.

---

### Post by MAFoElffen on 2023-09-28
Then after that, we can look at the loaded Intel modules that are running... and which firmware files they are using for those modules, with what options.

Do this
```

MODULES=$(sudo lsmod | awk '/intel|i915/ {print $1}' | awk '/intel|i915/ {print}');for MODULE in ${MODULES[@]};do sudo modinfo $MODULE >> ~//Documents/IntelModuleInfo.txt; done

```
Which will create a text file located in your Documents folder called IntelModuleInfo.txt. Use the Advance Reply post editor and upload and attach that file to a post.

---

### Post by lazaruslong67 on 2023-09-28
> **MAFoElffen said:**
> @1fallen --- Yes, if you look at his previous post with his output, Post #9, it said:
```

00:02.0 VGA compatible controller [0300]: Intel Corporation CoffeeLake-S  GT2 [UHD Graphics 630] [8086:3e92] (prog-if 00 [VGA controller])
    Kernel driver in use: [COLOR=#ff0000]snd_hda_intel[/COLOR]
    Kernel modules: [COLOR=#ff0000]snd_hda_intel, snd_sof_pci_intel_cnl[/COLOR]

```
That does not make sense. Those are sound drivers/modules. 

I am just confirming that either the query was at fault, or his system is doing very strange things.

### Sidenote -- That reminds me that I have to fix / update the filter for that in the 'system-info' script.

My monitor (connected with DP) does have built-in speakers - not sure if that's why there are sound drivers?

---

### Post by lazaruslong67 on 2023-09-28
I had to zip the ModuleInfo.txt file to get it down small enough for the forum.  Wasn't sure if there was something else I was also supposed to run?

NOTE - I did run this while in Recovery mode, not sure if that makes a difference?

---

### Post by lazaruslong67 on 2023-09-28
> **MAFoElffen said:**
> That was my fault. Sorry.

Lets try that again, hopefully only one more time:
```

GPU_List=$(sudo lspci | awk '/VGA|Display|3D/ {print $1}');for GPU_ID in ${GPU_List[@]};do sudo lspci -s $GPU_ID -vnn; done

```
I need to see that detail... I'm spinning up a VM to test if it shows me what I need to see from toggling over at the DM panel (Graphical Login).

[s]*** Wait for "this" line to update, after I confirmed that... ***[/s]
Yes, it shows what I need to see, from toggling over at that point... Please run that now.

This is my output from that command:

00:02.0 VGA compatible controller [0300]: Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630] [8086:3e92] (prog-if 00 [VGA controller])
    DeviceName: Onboard - Video
    Subsystem: Lenovo CometLake-S GT2 [UHD Graphics 630] [17aa:312d]
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at b0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: [40] Vendor Specific Information: Len=0c <?>
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [ac] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [100] Process Address Space ID (PASID)
    Capabilities: [200] Address Translation Service (ATS)
    Capabilities: [300] Page Request Interface (PRI)
    Kernel modules: i915

---

### Post by #&amp;thj^% on 2023-09-28
Are you positive you have a good connector and connection?
At least in recovery you have this:
```
lename:       /lib/modules/6.2.0-33-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Intel Corporation
author:         Tungsten Graphics, Inc.
import_ns:      DMA_BUF
```
And
> **lazaruslong67 said:**
> 
    
    Kernel modules: i915

---

### Post by lazaruslong67 on 2023-09-28
> **1fallen said:**
> Are you positive you have a good connector and connection?
At least in recovery you have this:
```
lename:       /lib/modules/6.2.0-33-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Intel Corporation
author:         Tungsten Graphics, Inc.
import_ns:      DMA_BUF
```
And

Tried a different DP cable with same results.  Also tried using HDMI but then I don't even get a display once it gets to loading the GUI.

Same DP cables working without issues on a new Win 11 install (and it installed the driver, etc. without issues).

Sort of at a loss - fortunately I didn't pay much for this PC lol.

---

### Post by #&amp;thj^% on 2023-09-28
Thank You, I wouldn't chalk it off just yet.
If your game, I might have a couple more kernel settings to try.
But lets wait for the fisherman (MAFoElffen) to view your results.

---

### Post by MAFoElffen on 2023-09-28
I looked at the results. It says that the i915 module is loaded in the kernel... And also says "these" are the parameters that version of the module will take:
```

parm:           modeset:Use kernel modesetting [KMS] (0=disable, 1=on, -1=force vga console preference [default]) (int)
parm:           enable_dc:Enable power-saving display C-states. (-1=auto [default]; 0=disable; 1=up to DC5; 2=up to DC6; 3=up to DC5 with DC3CO; 4=up to DC6 with DC3CO) (int)
parm:           enable_fbc:Enable frame buffer compression for power savings (default: -1 (use per-chip default)) (int)
parm:           lvds_channel_mode:Specify LVDS channel mode (0=probe BIOS [default], 1=single-channel, 2=dual-channel) (int)
parm:           panel_use_ssc:Use Spread Spectrum Clock with panels [LVDS/eDP] (default: auto from VBT) (int)
parm:           vbt_sdvo_panel_type:Override/Ignore selection of SDVO panel mode in the VBT (-2=ignore, -1=auto [default], index in VBT BIOS table) (int)
parm:           reset:Attempt GPU resets (0=disabled, 1=full gpu reset, 2=engine reset [default]) (uint)
parm:           vbt_firmware:Load VBT from specified file under /lib/firmware (charp)
parm:           error_capture:Record the GPU state following a hang. This information in /sys/class/drm/card<N>/error is vital for triaging and debugging hangs. (bool)
parm:           enable_hangcheck:Periodically check GPU activity for detecting hangs. WARNING: Disabling this can cause system wide hangs. (default: true) (bool)
parm:           enable_psr:Enable PSR (0=disabled, 1=enable up to PSR1, 2=enable up to PSR2) Default: -1 (use per-chip default) (int)
parm:           psr_safest_params:Replace PSR VBT parameters by the safest and not optimal ones. This is helpful to detect if PSR issues are related to bad values set in  VBT. (0=use VBT parameters, 1=use safest parameters) (bool)
parm:           enable_psr2_sel_fetch:Enable PSR2 selective fetch (0=disabled, 1=enabled) Default: 0 (bool)
parm:           force_probe:Force probe options for specified supported devices. See CONFIG_DRM_I915_FORCE_PROBE for details. (charp)
parm:           disable_power_well:Disable display power wells when possible (-1=auto [default], 0=power wells always on, 1=power wells disabled when possible) (int)
parm:           enable_ips:Enable IPS (default: true) (int)
parm:           fastboot:Try to skip unnecessary mode sets at boot time (0=disabled, 1=enabled) Default: -1 (use per-chip default) (int)
parm:           load_detect_test:Force-enable the VGA load detect code for testing (default:false). For developers only. (bool)
parm:           force_reset_modeset_test:Force a modeset during gpu reset for testing (default:false). For developers only. (bool)
parm:           invert_brightness:Invert backlight brightness (-1 force normal, 0 machine defaults, 1 force inversion), please report PCI device ID, subsystem vendor and subsystem device ID to dri-devel@lists.freedesktop.org, if your machine needs it. It will then be included in an upcoming module version. (int)
parm:           disable_display:Disable display (default: false) (bool)
parm:           memtest:Perform a read/write test of all device memory on module load (default: off) (bool)
parm:           mmio_debug:Enable the MMIO debug code for the first N failures (default: off). This may negatively affect performance. (int)
parm:           verbose_state_checks:Enable verbose logs (ie. WARN_ON()) in case of unexpected hw state conditions. (bool)
parm:           nuclear_pageflip:Force enable atomic functionality on platforms that don't have full support yet. (bool)
parm:           edp_vswing:Ignore/Override vswing pre-emph table selection from VBT (0=use value from vbt [default], 1=low power swing(200mV),2=default swing(400mV)) (int)
parm:           enable_guc:Enable GuC load for GuC submission and/or HuC load. Required functionality can be selected using bitmask values. (-1=auto [default], 0=disable, 1=GuC submission, 2=HuC load) (int)
parm:           guc_log_level:GuC firmware logging level. Requires GuC to be loaded. (-1=auto [default], 0=disable, 1..4=enable with verbosity min..max) (int)
parm:           guc_firmware_path:GuC firmware path to use instead of the default one (charp)
parm:           huc_firmware_path:HuC firmware path to use instead of the default one (charp)
parm:           dmc_firmware_path:DMC firmware path to use instead of the default one (charp)
parm:           enable_dp_mst:Enable multi-stream transport (MST) for new DisplayPort sinks. (default: true) (bool)
parm:           enable_dpcd_backlight:Enable support for DPCD backlight control(-1=use per-VBT LFP backlight type setting [default], 0=disabled, 1=enable, 2=force VESA interface, 3=force Intel interface) (int)
parm:           enable_gvt:Enable support for Intel GVT-g graphics virtualization host support(default:false) (bool)
parm:           request_timeout_ms:Default request/fence/batch buffer expiration timeout. (uint)
parm:           lmem_size:Set the lmem size(in MiB) for each region. (default: 0, all memory) (uint)
parm:           lmem_bar_size:Set the lmem bar size(in MiB). (uint)
parm:           mitigations:Selectively enable security mitigations for all Intel® GPUs in the system.

  auto -- enables all mitigations required for the platform [default]
  off  -- disables all mitigations

Individual mitigations can be enabled by passing a comma-separated string,
e.g. mitigations=residuals to enable only clearing residuals or
mitigations=auto,noresiduals to disable only the clear residual mitigation.
Either '!' or 'no' may be used to switch from enabling the mitigation to
disabling it.

```
That is our instruction book for trying different parameters for this module. We don't have to guess. It includes what is will take as an option parameter, what each parameter does, what th deafults are, the possible values for each parameter, and what those options do... You now have a manual. (LOL)

1fallen and I have been talking on this. He suggests trying these. You can try kernel parameters from the Grub2 menu by, while displayed, press the key <e> to get into an edit mode, arrow down to the line that starts with "linux, then <arrow-right> to the words "quiet splash". I ensure that it has 3 dashes before them (if not add "---"), then I delete the word "quiet" to see the boot messages, then <arrow-right> until after "splash" to enter in the parameter(s).

Try these suggestion first from 1fallen...
```

i915.enable_fbc=0
i915.enable_psr=0

``` 
Yours is Gen 9.5. My server is Gen 10. Here is what my boot commandline is so you can see my options on that:
```

mafoelffen@Mikes-B460M:~$ grep . /proc/cmdline
BOOT_IMAGE=/BOOT/ubuntu_2cwpns@/vmlinuz-6.2.0-33-generic root=ZFS=rpool/ROOT/ubuntu_2cwpns ro -- splash kvm-intel.nested=1 intel_idle.max_cstate=4 [COLOR=#ff0000]video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid[/COLOR] intel_iommu=on iommu=pt [COLOR=#ff0000]i915.enable_gvt=1 i915.enable_guc=2 i915.enable_fbc=0[/COLOR] systemd.unified_cgroup_hierarchy=0 libata.force=noncq vt.handoff=1

mafoelffen@Mikes-B460M:~$ lspci -nnk | grep -A 2 -Ei 'VGA|Display|3D'
00:02.0 VGA compatible controller [0300]: Intel Corporation CometLake-S GT2 [UHD Graphics 630] [8086:9bc5] (rev 05)
    DeviceName: Onboard - Video
    Subsystem: Gigabyte Technology Co., Ltd CometLake-S GT2 [UHD Graphics 630] [1458:d000]

```
In red is the parameters I have set for the iGPU. I set KVM early, by setting the framebuffer during boot... i915.enable_gvt is for enabling support for Intel's GVT-g graphics virtualization host drivers. (not needed by you). i915.enable_guc is also for Intel GVT-g... Not needed by you. I have i915.enable_fbc turned off, just like 1fallen suggested.

I found this in my Intel Compute GPU notes:
> 
Some systems may have compatibility issues between the system BIOS and the Linux kernel MMIO BAR re-allocation which prevents the Intel Data Center GPUs from being accessible once the system has booted. If you are experiencing problems with multi-card solutions and the Intel GPU devices not initializing (entries for the device are not enumerating in /dev/dri), you can work around the issue by adding pci=realloc=off&#8203; to your kernel&#8217;s boot parameter.

That has to do with their compute GPU's but might work for their clinet GPU's. It also might be worth a try.

### 
Also found in those notes, some BIOS settings to check and set to get their drivers working... Will type those up tomorrow. Getting late here.

---

### Post by MAFoElffen on 2023-09-28
Intel Graphics.

Verify these BIOS settings:

Advanced -> Processor configuration
Enable Intel® Hyper-Threading Tech (Hyper-threading technology). This feature is used for improving the IPC (instructions per cycle).

Advanced -> Power & Performance settings
Choose &#8220;Balanced Performance&#8221; option. This setting weights optimization toward performance while conserving energy. ("Mine are set to Performance"... They are servers and Workstations.)

Advanced -> PCI configuration settings
Set MMIO High Base to 56T for MMIO optimization 
Set Memory Mapped I/O size to 1024G

---

### Post by lazaruslong67 on 2023-09-29
> **MAFoElffen said:**
> I looked at the results. It says that the i915 module is loaded in the kernel... And also says "these" are the parameters that version of the module will take:
```

parm:           modeset:Use kernel modesetting [KMS] (0=disable, 1=on, -1=force vga console preference [default]) (int)
parm:           enable_dc:Enable power-saving display C-states. (-1=auto [default]; 0=disable; 1=up to DC5; 2=up to DC6; 3=up to DC5 with DC3CO; 4=up to DC6 with DC3CO) (int)
parm:           enable_fbc:Enable frame buffer compression for power savings (default: -1 (use per-chip default)) (int)
parm:           lvds_channel_mode:Specify LVDS channel mode (0=probe BIOS [default], 1=single-channel, 2=dual-channel) (int)
parm:           panel_use_ssc:Use Spread Spectrum Clock with panels [LVDS/eDP] (default: auto from VBT) (int)
parm:           vbt_sdvo_panel_type:Override/Ignore selection of SDVO panel mode in the VBT (-2=ignore, -1=auto [default], index in VBT BIOS table) (int)
parm:           reset:Attempt GPU resets (0=disabled, 1=full gpu reset, 2=engine reset [default]) (uint)
parm:           vbt_firmware:Load VBT from specified file under /lib/firmware (charp)
parm:           error_capture:Record the GPU state following a hang. This information in /sys/class/drm/card<N>/error is vital for triaging and debugging hangs. (bool)
parm:           enable_hangcheck:Periodically check GPU activity for detecting hangs. WARNING: Disabling this can cause system wide hangs. (default: true) (bool)
parm:           enable_psr:Enable PSR (0=disabled, 1=enable up to PSR1, 2=enable up to PSR2) Default: -1 (use per-chip default) (int)
parm:           psr_safest_params:Replace PSR VBT parameters by the safest and not optimal ones. This is helpful to detect if PSR issues are related to bad values set in  VBT. (0=use VBT parameters, 1=use safest parameters) (bool)
parm:           enable_psr2_sel_fetch:Enable PSR2 selective fetch (0=disabled, 1=enabled) Default: 0 (bool)
parm:           force_probe:Force probe options for specified supported devices. See CONFIG_DRM_I915_FORCE_PROBE for details. (charp)
parm:           disable_power_well:Disable display power wells when possible (-1=auto [default], 0=power wells always on, 1=power wells disabled when possible) (int)
parm:           enable_ips:Enable IPS (default: true) (int)
parm:           fastboot:Try to skip unnecessary mode sets at boot time (0=disabled, 1=enabled) Default: -1 (use per-chip default) (int)
parm:           load_detect_test:Force-enable the VGA load detect code for testing (default:false). For developers only. (bool)
parm:           force_reset_modeset_test:Force a modeset during gpu reset for testing (default:false). For developers only. (bool)
parm:           invert_brightness:Invert backlight brightness (-1 force normal, 0 machine defaults, 1 force inversion), please report PCI device ID, subsystem vendor and subsystem device ID to dri-devel@lists.freedesktop.org, if your machine needs it. It will then be included in an upcoming module version. (int)
parm:           disable_display:Disable display (default: false) (bool)
parm:           memtest:Perform a read/write test of all device memory on module load (default: off) (bool)
parm:           mmio_debug:Enable the MMIO debug code for the first N failures (default: off). This may negatively affect performance. (int)
parm:           verbose_state_checks:Enable verbose logs (ie. WARN_ON()) in case of unexpected hw state conditions. (bool)
parm:           nuclear_pageflip:Force enable atomic functionality on platforms that don't have full support yet. (bool)
parm:           edp_vswing:Ignore/Override vswing pre-emph table selection from VBT (0=use value from vbt [default], 1=low power swing(200mV),2=default swing(400mV)) (int)
parm:           enable_guc:Enable GuC load for GuC submission and/or HuC load. Required functionality can be selected using bitmask values. (-1=auto [default], 0=disable, 1=GuC submission, 2=HuC load) (int)
parm:           guc_log_level:GuC firmware logging level. Requires GuC to be loaded. (-1=auto [default], 0=disable, 1..4=enable with verbosity min..max) (int)
parm:           guc_firmware_path:GuC firmware path to use instead of the default one (charp)
parm:           huc_firmware_path:HuC firmware path to use instead of the default one (charp)
parm:           dmc_firmware_path:DMC firmware path to use instead of the default one (charp)
parm:           enable_dp_mst:Enable multi-stream transport (MST) for new DisplayPort sinks. (default: true) (bool)
parm:           enable_dpcd_backlight:Enable support for DPCD backlight control(-1=use per-VBT LFP backlight type setting [default], 0=disabled, 1=enable, 2=force VESA interface, 3=force Intel interface) (int)
parm:           enable_gvt:Enable support for Intel GVT-g graphics virtualization host support(default:false) (bool)
parm:           request_timeout_ms:Default request/fence/batch buffer expiration timeout. (uint)
parm:           lmem_size:Set the lmem size(in MiB) for each region. (default: 0, all memory) (uint)
parm:           lmem_bar_size:Set the lmem bar size(in MiB). (uint)
parm:           mitigations:Selectively enable security mitigations for all Intel® GPUs in the system.

  auto -- enables all mitigations required for the platform [default]
  off  -- disables all mitigations

Individual mitigations can be enabled by passing a comma-separated string,
e.g. mitigations=residuals to enable only clearing residuals or
mitigations=auto,noresiduals to disable only the clear residual mitigation.
Either '!' or 'no' may be used to switch from enabling the mitigation to
disabling it.

```
That is our instruction book for trying different parameters for this module. We don't have to guess. It includes what is will take as an option parameter, what each parameter does, what th deafults are, the possible values for each parameter, and what those options do... You now have a manual. (LOL)

1fallen and I have been talking on this. He suggests trying these. You can try kernel parameters from the Grub2 menu by, while displayed, press the key <e> to get into an edit mode, arrow down to the line that starts with "linux, then <arrow-right> to the words "quiet splash". I ensure that it has 3 dashes before them (if not add "---"), then I delete the word "quiet" to see the boot messages, then <arrow-right> until after "splash" to enter in the parameter(s).

Try these suggestion first from 1fallen...
```

i915.enable_fbc=0
i915.enable_psr=0

``` 
Yours is Gen 9.5. My server is Gen 10. Here is what my boot commandline is so you can see my options on that:
```

mafoelffen@Mikes-B460M:~$ grep . /proc/cmdline
BOOT_IMAGE=/BOOT/ubuntu_2cwpns@/vmlinuz-6.2.0-33-generic root=ZFS=rpool/ROOT/ubuntu_2cwpns ro -- splash kvm-intel.nested=1 intel_idle.max_cstate=4 [COLOR=#ff0000]video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid[/COLOR] intel_iommu=on iommu=pt [COLOR=#ff0000]i915.enable_gvt=1 i915.enable_guc=2 i915.enable_fbc=0[/COLOR] systemd.unified_cgroup_hierarchy=0 libata.force=noncq vt.handoff=1

mafoelffen@Mikes-B460M:~$ lspci -nnk | grep -A 2 -Ei 'VGA|Display|3D'
00:02.0 VGA compatible controller [0300]: Intel Corporation CometLake-S GT2 [UHD Graphics 630] [8086:9bc5] (rev 05)
    DeviceName: Onboard - Video
    Subsystem: Gigabyte Technology Co., Ltd CometLake-S GT2 [UHD Graphics 630] [1458:d000]

```
In red is the parameters I have set for the iGPU. I set KVM early, by setting the framebuffer during boot... i915.enable_gvt is for enabling support for Intel's GVT-g graphics virtualization host drivers. (not needed by you). i915.enable_guc is also for Intel GVT-g... Not needed by you. I have i915.enable_fbc turned off, just like 1fallen suggested.

I found this in my Intel Compute GPU notes:

That has to do with their compute GPU's but might work for their clinet GPU's. It also might be worth a try.

### 
Also found in those notes, some BIOS settings to check and set to get their drivers working... Will type those up tomorrow. Getting late here.

So quick question - I was able to edit those settings, but are those just for the current boot-up, or do I need to do something to save while in the editor?

I did see Ctrl+X to boot - does that boot with the setting changes I just made?

---

### Post by #&amp;thj^% on 2023-09-29
Try it first to test it, and just one more time I'd like to see:
```
lscpu

```
Please wrap that return in Code Tags, see my signature for Code Tags
Also please try those suggestions one at time, it helps knowing what has been done and works or not works.

---

### Post by lazaruslong67 on 2023-09-29
> **1fallen said:**
> Try it first to test it, and just one more time I'd like to see:
```
lscpu

```
Please wrap that return in Code Tags, see my signature for Code Tags
Also please try those suggestions one at time, it helps knowing what has been done and works or not works.

Got it.  OK, just confirming that this is what it should look like for trying one at a time:

This is at the end of the BOOT_IMAGE line.  Just wondering if I should remove the alpha_support I tried earlier, or move it to after the splash command

```

ro i915.alpha_support=1 --- splash i915.enable_fbc=0

```

---

### Post by lazaruslong67 on 2023-09-29
> **1fallen said:**
> Try it first to test it, and just one more time I'd like to see:
```
lscpu

```
Please wrap that return in Code Tags, see my signature for Code Tags
Also please try those suggestions one at time, it helps knowing what has been done and works or not works.

Here is the lscpu info:

```

Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         39 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  6
  On-line CPU(s) list:   0-5
Vendor ID:               GenuineIntel
  Model name:            Intel(R) Core(TM) i5-8500T CPU @ 2.10GHz
    CPU family:          6
    Model:               158
    Thread(s) per core:  1
    Core(s) per socket:  6
    Socket(s):           1
    Stepping:            10
    CPU max MHz:         3500.0000
    CPU min MHz:         800.0000
    BogoMIPS:            4199.88
    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mc
                         a cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss 
                         ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art
                          arch_perfmon pebs bts rep_good nopl xtopology nonstop_
                         tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cp
                         l vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid ss
                         e4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes 
                         xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_f
                         ault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_sh
                         adow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adj
                         ust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx sma
                         p clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dt
                         herm ida arat pln pts hwp hwp_notify hwp_act_window hwp
                         _epp md_clear flush_l1d arch_capabilities
Virtualization features: 
  Virtualization:        VT-x
Caches (sum of all):     
  L1d:                   192 KiB (6 instances)
  L1i:                   192 KiB (6 instances)
  L2:                    1.5 MiB (6 instances)
  L3:                    9 MiB (1 instance)
NUMA:                    
  NUMA node(s):          1
  NUMA node0 CPU(s):     0-5
Vulnerabilities:         
  Gather data sampling:  Vulnerable: No microcode
  Itlb multihit:         KVM: Mitigation: VMX disabled
  L1tf:                  Mitigation; PTE Inversion; VMX conditional cache flushe
                         s, SMT disabled
  Mds:                   Mitigation; Clear CPU buffers; SMT disabled
  Meltdown:              Mitigation; PTI
  Mmio stale data:       Mitigation; Clear CPU buffers; SMT disabled
  Retbleed:              Mitigation; IBRS
  Spec store bypass:     Mitigation; Speculative Store Bypass disabled via prctl
  Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer
                          sanitization
  Spectre v2:            Mitigation; IBRS, IBPB conditional, STIBP disabled, RSB
                          filling, PBRSB-eIBRS Not affected
  Srbds:                 Mitigation; Microcode
  Tsx async abort:       Mitigation; TSX disabled

```

---

### Post by MAFoElffen on 2023-09-29
Yes, editing at the Grub2 menu will be temporary, as a test. Will not be persistent. To make the changes persistent, then you add the parameters to /etc/default/grub, to the GRUB_CMDLINE_LINUX_DEFAULT= line, like I say in the instructions for that in my "Graphics Resolution" Sticky...

Actually... Please try adding all of these parameters at once for a first try:
```

video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid i915.modeset=1 i915.enable_fbc=0 i915.enable_psr=0

```

---

### Post by #&amp;thj^% on 2023-09-29
Thank you sir:
So this:
[```
 Code Name Products formerly Coffee Lake 
```
Scales on the mid lower range.
with:
```
 Processor Graphics &#8225; Intel® UHD Graphics 630
```
Also I see no microcode installed? puzzling that should have set with the initial install.
to install run:
```
sudo apt install intel-microcode
```
Now reboot with the new change. Any better?

---

### Post by lazaruslong67 on 2023-09-29
> **1fallen said:**
> Thank you sir:
So this:
[```
 Code Name Products formerly Coffee Lake 
```
Scales on the mid lower range.
with:
```
 Processor Graphics ‡ Intel® UHD Graphics 630
```
Also I see no microcode installed? puzzling that should have set with the initial install.
to install run:
```
sudo apt install intel-microcode
```
Now reboot with the new change. Any better?

```

sudo apt install intel-microcode
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
intel-microcode is already the newest version (3.20230808.0ubuntu0.22.04.1).
intel-microcode set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

---

### Post by #&amp;thj^% on 2023-09-29
> **MAFoElffen said:**
> Yes, editing at the Grub2 menu will be temporary, as a test. Will not be persistent. To make the changes persistent, then you add the parameters to /etc/default/grub, to the GRUB_CMDLINE_LINUX_DEFAULT= line, like I say in the instructions for that in my "Graphics Resolution" Sticky...

Actually... Please try adding all of these parameters at once for a first try:
```

video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid i915.modeset=1 i915.enable_fbc=0 i915.enable_psr=0

```

+1
@ lazaruslong67 I like his set up please give that go first.

---

### Post by lazaruslong67 on 2023-09-29
> **MAFoElffen said:**
> Yes, editing at the Grub2 menu will be temporary, as a test. Will not be persistent. To make the changes persistent, then you add the parameters to /etc/default/grub, to the GRUB_CMDLINE_LINUX_DEFAULT= line, like I say in the instructions for that in my "Graphics Resolution" Sticky...

Actually... Please try adding all of these parameters at once for a first try:
```

video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid i915.modeset=1 i915.enable_fbc=0 i915.enable_psr=0

```

Just confirming this looks correct (editing the grub file)

```

GRUB_CMDLINE_LINUX_DEFAULT=" --- splash video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid i915.modeset=1 i915.enable_fbc=0 i915.enable_psr=0"

```

---

### Post by #&amp;thj^% on 2023-09-29
yes let it rip.

---

### Post by lazaruslong67 on 2023-09-29
Unfortunately that took me to a login screen (but no login prompt and the system seemed frozen).

Not sure if this means anything, but I thought with those settings it would drop to 1920x1080 but it has been at full-screen all the time (I am using an ultrawide monitor - 3840x1600).

I am still able to boot into Recovery and get back to a working session fortunately.

---

### Post by #&amp;thj^% on 2023-09-29
Something is wrong, I tested it:
```
cat /etc/default/grub | grep GRUB_CMDLINE_LINUX_DEFAULT
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 snd-intel-dspcfg.dsp_driver=1 lsm=landlock,lockdown,yama,integrity,apparmor,bpf video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid i915.modeset=1 i915.enable_fbc=0 i915.enable_psr=0 quiet"

```
I show no oddities or flaws.
And you've said you also have tried other Linux systems with the same result this is sounding but not yet proven hardware.
Still thinking
BTW Mine for this testing seen here:
```
lscpu
Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         39 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  8
  On-line CPU(s) list:   0-7
Vendor ID:               GenuineIntel
  Model name:            Intel(R) Core(TM) i5-10210U CPU @ 1.60GHz
    CPU family:          6
    Model:               142
    Thread(s) per core:  2
    Core(s) per socket:  4
    Socket(s):           1
    Stepping:            12
    CPU(s) scaling MHz:  18%
    CPU max MHz:         4200.0000
    CPU min MHz:         400.0000
    BogoMIPS:            4201.88

```
Graphics:
```
Processor Graphics

    Processor Graphics &#8225; Intel® UHD Graphics for 10th Gen Intel® Processors
    Graphics Base Frequency 300 MHz
    Graphics Max Dynamic Frequency 1.10 GHz
    Graphics Video Max Memory 32 GB
    Graphics Output eDP/DP/HDMI/DVI
    Execution Units 24
    4K Support Yes, at 60Hz
    Max Resolution (HDMI)&#8225; 4096 x 2304@24Hz
    Max Resolution (DP)&#8225; 4096 x 2304@60Hz
    Max Resolution (eDP - Integrated Flat Panel)&#8225; 4096 x 2304@60Hz
    DirectX* Support 12
    OpenGL* Support 4.5
    Intel® Quick Sync Video Yes
    Intel® Clear Video HD Technology Yes
    Intel® Clear Video Technology Yes
    # of Displays Supported &#8225; 3
    Device ID 0x9B21/0x9B41/0x9BAC/0x9BCA/0x9BCC 
```

---

### Post by MAFoElffen on 2023-09-29
So you updated /etc/default/grub instead of just adding temporarily in the Grub2 menu? Please confirm that you did 'sudo update-grub to pick up the changes...

Since you are doing it that way now... Please change it to this
```

GRUB_CMDLINE_LINUX_DEFAULT=" --- splash video=uvesafb:mode_option=3840x1600-32,mtrr=3,scroll=ywrap,noblank i915.modeset=1 i915.alpha_support=1 i915.enable_fbc pci=realloc=off"&#8203;

```
I'm thinking i915.enable_psr may have been the option that locked it up. --> That is why I asked you "to test" without persistence, so that just rebooting would get it ab to where it was. But no matters.

You said you tested the cable and display on something else, right?

Also... Did you verify the BIOS settings from Post #28?

---

### Post by lazaruslong67 on 2023-09-29
Yes, I found it was just easier for me to copy/paste using the full gui (since I could get to the forum via a browser) vs manually typing into the Grub2 menu. Also was running update-grub after each change. 

Will try your latest suggestion when I get home from camping this weekend. Need to take a break lol. 

And yes, the monitor is my daily and same cable was being used by a slightly older Lenovo (running Windows).

---

### Post by lazaruslong67 on 2023-09-29
> **MAFoElffen said:**
> So you updated /etc/default/grub instead of just adding temporarily in the Grub2 menu? Please confirm that you did 'sudo update-grub to pick up the changes...

Since you are doing it that way now... Please change it to this
```

GRUB_CMDLINE_LINUX_DEFAULT=" --- splash video=uvesafb:mode_option=3840x1600-32,mtrr=3,scroll=ywrap,noblank i915.modeset=1 i915.alpha_support=1 i915.enable_fbc pci=realloc=off"&#8203;

```
I'm thinking i915.enable_psr may have been the option that locked it up. --> That is why I asked you "to test" without persistence, so that just rebooting would get it ab to where it was. But no matters.

You said you tested the cable and display on something else, right?

Also... Did you verify the BIOS settings from Post #28?

Forgot to add: my BIOS doesn’t actually have any of those settings. 

I did update BIOS to latest firmware earlier in the week, just in case.

---

### Post by MAFoElffen on 2023-09-29
Okay. Thanks. 

Have a great weekend! I plan on going Salmon fishing early in the morning. Been pouring rain all week.

---

### Post by lazaruslong67 on 2023-10-02
> **MAFoElffen said:**
> Okay. Thanks. 

Have a great weekend! I plan on going Salmon fishing early in the morning. Been pouring rain all week.

So with that latest change, things seem somewhat better-ish.  I'm no longer getting completely freezing of the GUI and/or any artifacts either.

Not sure if it's actually using the driver yet though as I still get "Unknown Display" in display settings.

This is what it appears to still be using:

```

00:02.0 VGA compatible controller [0300]: Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630] [8086:3e92] (prog-if 00 [VGA controller])
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_cnl

```

On a side note, I decided to try booting to Unraid off a flash drive (since I was planning to really use this machine as a Plex Media server).  It definitely sees the GPU and tries to use it, but I didn't get far enough with Plex settings to get it working.

---

### Post by lazaruslong67 on 2023-10-02
> **MAFoElffen said:**
> So you updated /etc/default/grub instead of just adding temporarily in the Grub2 menu? Please confirm that you did 'sudo update-grub to pick up the changes...

Since you are doing it that way now... Please change it to this
```

GRUB_CMDLINE_LINUX_DEFAULT=" --- splash video=uvesafb:mode_option=3840x1600-32,mtrr=3,scroll=ywrap,noblank i915.modeset=1 i915.alpha_support=1 i915.enable_fbc pci=realloc=off"&#8203;

```
I'm thinking i915.enable_psr may have been the option that locked it up. --> That is why I asked you "to test" without persistence, so that just rebooting would get it ab to where it was. But no matters.

You said you tested the cable and display on something else, right?

Also... Did you verify the BIOS settings from Post #28?

I also noticed while booting up that it said the following:

```

i915: `' invalid for parameter `enable_fbc'

```

---

### Post by #&amp;thj^% on 2023-10-02
> **lazaruslong67 said:**
> I also noticed while booting up that it said the following:

```

i915: `' invalid for parameter `enable_fbc'

```
Will you try this last effort from me anyway, create a file:
```
sudo nano  /usr/share/X11/xorg.conf.d/20-intel.conf
```
With this as content:
```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "uxa"
EndSection
``` 
leave grub as is, and for good messure run:
```
update-initramfs -u -k all
```
Now reboot

---

### Post by lazaruslong67 on 2023-10-02
> **1fallen said:**
> Will you try this last effort from me anyway, create a file:
```
sudo nano  /usr/share/X11/xorg.conf.d/20-intel.conf
```
With this as content:
```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "uxa"
EndSection
``` 
leave grub as is, and for good messure run:
```
update-initramfs -u -k all
```
Now reboot

Thanks for the suggestion, but no luck with that either... :(

---

### Post by #&amp;thj^% on 2023-10-02
Ok I have some possible bad news, some of these  Lenovo m720Q "mini" PC's were written solely and I mean solely for Windows 10, and if refurbished or bought from Walmart with 16Gigs of RAM then your out of luck for Linux. No one to blame here both Intel and Lenovo won't release the code needed.

So I assume you have Windows 10 installed and it works like a champ right?

---

### Post by lazaruslong67 on 2023-10-02
> **1fallen said:**
> Ok I have some possible bad news, some of these  Lenovo m720Q "mini" PC's were written solely and I mean solely for Windows 10, and if refurbished or bought from Walmart with 16Gigs of RAM then your out of luck for Linux. No one to blame here both Intel and Lenovo won't release the code needed.

So I assume you have Windows 10 installed and it works like a champ right?

I actually went straight to a clean install of Win 11 and it worked without issues.  Yes, it was a refurb from eBay but I didn't think it would be a big issue as I assumed most of Lenovo's stuff would be fairly well supported.

Grrrrrrrr

---

### Post by #&amp;thj^% on 2023-10-02
> **lazaruslong67 said:**
> I actually went straight to a clean install of Win 11 and it worked without issues.  Yes, it was a refurb from eBay but I didn't think it would be a big issue as I assumed most of Lenovo's stuff would be fairly well supported.

Grrrrrrrr

That's why I rode with you and  MAFoElffen on this thread, I would have bet my bottom dollar this would work with linux.
They Started out @ $999.00 and dropped quickly to around $500.00 US and now can be found used or refurbished @ $150.00 to $220.00 give or take.

They were aimed at Office applications for large and small Office use.
It's still a Good Windows machine though, But it would be a very nice Linux Box "if" well you know. ;)

---

### Post by lazaruslong67 on 2023-10-02
> **1fallen said:**
> That's why I rode with you and  MAFoElffen on this thread, I would have bet my bottom dollar this would work with linux.
They Started out @ $999.00 and dropped quickly to around $500.00 US and now can be found used or refurbished @ $150.00 to $220.00 give or take.

They were aimed at Office applications for large and small Office use.
It's still a Good Windows machine though, But it would be a very nice Linux Box "if" well you know. ;)

I got mine for $100 lol.  It is a nice little PC but for what I'm needing (Plex server using the IGPU/Quick Sync feature for hardware transcoding), they currently only support Linux, not Windows.

I do have a slightly older model of the same type of Lenovo tiny PC, but it's only a 6th gen which doesn't work as well.

I'm assuming if I tried to run headless/server, I'd still have the same issues?  I expect that if Plex is wanting to use the GPU it needs the drivers to kick in (might be why it also isn't kicking in under UNRAID).

---

### Post by #&amp;thj^% on 2023-10-02
Would Jellyfin work for you?  [https://jellyfin.org/downloads/windows](https://jellyfin.org/downloads/windows)
More info: [https://jellyfin.org/docs/](https://jellyfin.org/docs/)

---

### Post by lazaruslong67 on 2023-10-02
> **1fallen said:**
> Would Jellyfin work for you?  [https://jellyfin.org/downloads/windows](https://jellyfin.org/downloads/windows)
More info: [https://jellyfin.org/docs/](https://jellyfin.org/docs/)

It would probably handle the transcoding fine, but their client apps are pretty bad for the most part (especially on Apple TV).  Plus I've got a pretty large Plex library already (have been a user for 10+ years).

---

### Post by #&amp;thj^% on 2023-10-02
> **lazaruslong67 said:**
> It would probably handle the transcoding fine, but their client apps are pretty bad for the most part (especially on Apple TV).  Plus I've got a pretty large Plex library already (have been a user for 10+ years).

That makes good sense.

---

### Post by MAFoElffen on 2023-10-03
So do this:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=5
GRUB_RECORDFAIL_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- 3 "
GRUB_CMDLINE_LINUX=""
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1920x1080x32
#GRUB_GFXMODE=auto
# Set to true if you want to disable OS_Prober, false to turn on 
#GRUB_DISABLE_OS_PROBER=false
# UncommentE if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
Then it should work headless, as Console, text only display, init mode 3.

I just found this from Intel Graphics support on that same Intel(R) Core(TM) i5-10210U CPU as yours, but with Graphics in Windows 10:
re: [https://community.intel.com/t5/Graphics/Intel-Core-i5-10210U-graphical-artifacts-in-apps-with-hardware/m-p/1415579](https://community.intel.com/t5/Graphics/Intel-Core-i5-10210U-graphical-artifacts-in-apps-with-hardware/m-p/1415579)
> 
After confirming those details, yes, we used, Windows 10*, Google Chrome, Microsoft Edge, and MS Teams. So, unfortunately, everything indicates that this is, as you mentioned, a hardware issue with the Intel® processor itself and a replacement of the unit with your local store will be needed.

So they told the owner to replace the CPU...

EDIT: Which you paid $100 for the whole machine, and a replacement CPU (i5-10500) runs $100-$130 for used or refurbished... $165 for a brand new i5-10500K.

---

### Post by lazaruslong67 on 2023-10-10
> **MAFoElffen said:**
> So do this:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=5
GRUB_RECORDFAIL_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- 3 "
GRUB_CMDLINE_LINUX=""
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1920x1080x32
#GRUB_GFXMODE=auto
# Set to true if you want to disable OS_Prober, false to turn on 
#GRUB_DISABLE_OS_PROBER=false
# UncommentE if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
Then it should work headless, as Console, text only display, init mode 3.

I just found this from Intel Graphics support on that same Intel(R) Core(TM) i5-10210U CPU as yours, but with Graphics in Windows 10:
re: [https://community.intel.com/t5/Graphics/Intel-Core-i5-10210U-graphical-artifacts-in-apps-with-hardware/m-p/1415579](https://community.intel.com/t5/Graphics/Intel-Core-i5-10210U-graphical-artifacts-in-apps-with-hardware/m-p/1415579)

So they told the owner to replace the CPU...

EDIT: Which you paid $100 for the whole machine, and a replacement CPU (i5-10500) runs $100-$130 for used or refurbished... $165 for a brand new i5-10500K.

I actually believe I may have found a fix for this.  Decided to try Linux Mint as someone over on the forums over there seemed to have the exact same Lenovo model.  Well anyways, I ended up with the same issues - digging into the logs and xorg was crashing due to a GPU hang.

But then I found this post:  [https://gitlab.freedesktop.org/drm/intel/-/issues/4858#note_1425529](https://gitlab.freedesktop.org/drm/intel/-/issues/4858#note_1425529)

So I made the change suggested there (set GPU to maximum), and my issues went away in Linux Mint.  So hoping to be able to try the same thing with Ubuntu.

---

### Post by MAFoElffen on 2023-10-10
That is a "different" approach and perspective. 

Curious to see how that goes for you. Mint is built on top of Ubuntu 'Base'. If it works for Mint, I don't see why it wouldn't also work for Ubuntu itself.

---

### Post by lazaruslong67 on 2023-10-10
> **MAFoElffen said:**
> That is a "different" approach and perspective. 

Curious to see how that goes for you. Mint is built on top of Ubuntu 'Base'. If it works for Mint, I don't see why it wouldn't also work for Ubuntu itself.

And low and behold....that also resolved the issue in Ubuntu!  Everything working as expected.

So quick question - what would be the easiest way to run a command at boot to get the GPU set properly?

I can get into a terminal session and run "sudo intel_gpu_frequency" command, but would prefer it to be automatic.

Thanks.

---

### Post by MAFoElffen on 2023-10-10
Does it have to run before login, or at user login? (timing of) That makes a difference what to use and where to call it from.

Also, curious about what specifically the command is, so that we can share it as a work-around. These things do tend to come up again.

---

### Post by #&amp;thj^% on 2023-10-10
> **MAFoElffen said:**
> Does it have to run before login, or at user login? (timing of) That makes a difference what to use and where to call it from.

Also, curious about what specifically the command is, so that we can share it as a work-around. These things do tend to come up again.

I gleamed this much:
```
sudo intel_gpu_frequency -g
```
To me this looks safer, but what do i know LOL
```
# echo 350 > /sys/class/drm/card1/gt_min_freq_mhz 
# echo 350 > /sys/class/drm/card1/gt_boost_freq_mhz

```
I would think a lower frequency would also work....maybe?

---

### Post by MAFoElffen on 2023-10-10
Okay... This is what I think...

Create this script and name it "SetMaxGpuFreq":
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,2023.10.10
# Set GPU to max frequency
# to be Run by system as root user

GPU_REGISTERS=$(ls /sys/class/drm/card*/gt_[b,m][a,i,o][n,o,x]*_freq_mhz)
## Should return the following files for Intel GPU:
# /sys/class/drm/card0/gt_boost_freq_mhz:1300
# /sys/class/drm/card0/gt_max_freq_mhz:1300
# /sys/class/drm/card0/gt_min_freq_mhz:650
for REGISTER in ${GPU_REGISTERS[@]}
do 
    if [[ "$REGISTER" == *"gt_max_freq"* ]]
    then 
       # Get the value of the max frequency setting.
       GT_MAX_FREQ=$(grep . $REGISTER)
    elif [[ "$REGISTER" == *"gt_min_freq"* ]]
    then 
       logger "gt_min_freq was $(grep . REGISTER)"
       echo $GT_MAX_FREQ > $REGISTER
       GT_MIN_FREQ=$(grep . $REGISTER)
       logger "gt_min_freq was reset to $(grep . REGISTER)"
    fi
done

```
That should only be run as root... Move it to /usr/bin and make it executable
```

sudo mv ./SetMaxGpuFreq /usr/bin
sudo chown root:root /usr/bin/SetMaxGpuFreq
sudo chmod 774 /usr/bin/SetMaxGpuFreq

```
It should be run before the Linux Graphical Layer comes up, so in SystemD, right before 'graphical.target'. We can do that by creating a unit file called "pre-graphical.service" with this contents
```

[Unit]
Description=Pre-Reboot Process to call SetMaxGpuFreq script
DefaultDependencies=no
Before=graphical.target
## MAFoElffen,<mafoelffen@ubuntu.com>,20231010
# This works because it is installed in the target and will be
#   executed before the target state is entered
# Name: pre-graphical.service
# Location: /lib/systemd/system/pre-graphical.service 
# Runs script SetMaxGpuFreq to set Intel GPU to max frequency
# Workaround for Intel UHD 630 iGPU

[Service]
Type=oneshot
ExecStart=/usr/bin/SetMaxGpuFreq

[Install]
WantedBy=graphical.target

```
Move it to /usr/lib/systemd/system/... Then, we enable, start the service, check it's status, then we will test it. 
```

sudo mv ./pre-graphical.service /usr/lib/systemd/system/
sudo chown root:root /usr/lib/systemd/system/pre-graphical.service
sudo systemctl daemon-reload 
sudo systemctl enable pre-graphical.service 
sudo systemctl start pre-graphical.service 
sudo systemctl status pre-graphical.service 

```
Look at the last to see if it started was enabled, and started the service without errors. Reboot and test. The service should kick up right before the graphics layer comes up...

The script when it changes the register, logs entries into the syslog. You should be able to see those by doing
```

sudo grep 'logger:' /var/log/syslog

```

---

### Post by #&amp;thj^% on 2023-10-10
Golf Clap and +1  MAFoElffen your worth your weight in gold.

---

### Post by MAFoElffen on 2023-10-10
I figured using the gt_max_value from the range is still safe without overclocking the GPU out of it's rated range. No guessing,. That is found by the kernel when it boots.

---

### Post by lazaruslong67 on 2023-10-11
> **MAFoElffen said:**
> Does it have to run before login, or at user login? (timing of) That makes a difference what to use and where to call it from.

Also, curious about what specifically the command is, so that we can share it as a work-around. These things do tend to come up again.

This is the command that works for me:

```
intel_gpu_frequency -m
```

Apparently that sets GPU frequency to max the GPU will support.  Only real issue is someone else suggested that might run a bit too hot in a "tiny" PC (due to airflow).  There is another option to set a minimum so I might just need to mess with that a bit to figure out a good sweet spot.

I'm thinking 350 (which is what mine drops down to) is too slow to maybe support my monitor?

And yes, I figured it needs to be set before the login screen even appears (I get glitches there before even logging in).

---

### Post by #&amp;thj^% on 2023-10-11
> **lazaruslong67 said:**
> 
I'm thinking 350 (which is what mine drops down to) is too slow to maybe support my monitor?

It's the father in me LOL I  always start low. ;)
I think  MAFoElffen's script might hit the sweet spot @"gt_min_freq_mhz:650"
have you tried that yet post #62

---

### Post by #&amp;thj^% on 2023-10-11
> **1fallen said:**
> It's the father in me LOL I  always start low. ;)
I think  MAFoElffen's script might hit the sweet spot @"gt_min_freq_mhz:650"
have you tried that yet post #62
EDIT: But I would figure someway to get more Air going through that box.


sorry this is suppose to be just an edit and not another post.

---

### Post by lazaruslong67 on 2023-10-11
> **1fallen said:**
> It's the father in me LOL I  always start low. ;)
I think  MAFoElffen's script might hit the sweet spot @"gt_min_freq_mhz:650"
have you tried that yet post #62

Yeah, just tried that and I'm getting this error:

```
Oct 11 16:19:47 ThinkCentre-M720q SetMaxGpuFreq[694]: ls: cannot access '/sys/class/drm/card*/gt_[b,m][a,i,o][n,o,x]*_freq_mhz': No such file or directory
```

Now I am currently booted into recovery mode, wonder if that's why there isn't anything in that directory?  That being said, even after a reboot I'm still having the issues so not sure if the script is running.

---

### Post by #&amp;thj^% on 2023-10-11
> **lazaruslong67 said:**
> Yeah, just tried that and I'm getting this error:

```
Oct 11 16:19:47 ThinkCentre-M720q SetMaxGpuFreq[694]: ls: cannot access '/sys/class/drm/card*/gt_[b,m][a,i,o][n,o,x]*_freq_mhz': No such file or directory
```

Now I am currently booted into recovery mode, wonder if that's why there isn't anything in that directory?  That being said, even after a reboot I'm still having the issues so not sure if the script is running.

Lets have a quick look then:
```
systemctl status pre-graphical.service
```

---

### Post by lazaruslong67 on 2023-10-11
> **1fallen said:**
> Lets have a quick look then:
```
systemctl status pre-graphical.service
```

Trying to do that...so earlier I had to boot into recovery mode and when in recovery mode, that folder is definitely not populated.

However, I was able to see correct data in that folder after a recent restart in normal mode (but it hadn't changed the GPU, even though the service indicated it had ran successfully).

Now I'm trying to boot back into it again - with "normal" mode.  Only way I've been able to get that to work is at the login screen get to a TTY screen and change the GPU, but sometimes I can't even get to a TTY screen - everything just seems frozen...GRRRRRR

---

### Post by lazaruslong67 on 2023-10-11
Am I missing something (or not understanding the script), but I can't seem to see a line that actually changes the GPU speed?  I do see the logging, etc. but not an actual speed change?

---

### Post by #&amp;thj^% on 2023-10-11
> **lazaruslong67 said:**
> 
Now I'm trying to boot back into it again - with "normal" mode.  Only way I've been able to get that to work is at the login screen get to a TTY screen and change the GPU, but sometimes I can't even get to a TTY screen - everything just seems frozen...GRRRRRR

We are trying to force it to do something it's not quite made for, and yes challenging on the nerves as well.

---

### Post by #&amp;thj^% on 2023-10-11
> **lazaruslong67 said:**
> Am I missing something (or not understanding the script), but I can't seem to see a line that actually changes the GPU speed?  I do see the logging, etc. but not an actual speed change?
Kind of easy to miss but the kernel sets it.
> **MAFoElffen said:**
> I figured using the gt_max_value from the range is still safe without overclocking the GPU out of it's rated range. No guessing,. That is found by the kernel when it boots.
EDIT: He used both scripts for this, just to be sure that was not a question.

---

### Post by MAFoElffen on 2023-10-11
Do this:
```

mafoelffen@Mikes-B460M:~$ sudo find /sys -name gt_m*
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/gt_max_freq_mhz
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/gt_min_freq_mhz

```
The script was on a 13thGen iCore. I just did the above on a 10th Gen iCore.

I just confirmed that "that" register is writable by root.

---

### Post by lazaruslong67 on 2023-10-11
OK, so I can see what his script is doing - basically setting the min_freq to be the same as the max_freq.  However, that doesn't seem to be kicking in - only thing I can think of is that it's not actually forcing the "actual" to change when it runs?

As a quick test, I created a new script that just does this:

```
intel_gpu_frequency -m
```

and that works without issues.  There's also an option to set new min/max values.

```
[COLOR=#2E8B57][FONT=monospace]sudo intel_gpu_frequency -c "min=X | max=Y"[/FONT][/COLOR]
```

I tried with a new minimum of 600 (which it did change to), but even that gave GPU glitches and eventually froze again.  So apparently I need to go with something a bit higher for a minimum.

Really sort of surprised as these GPU's are supposed to push even higher resolutions than what I'm using - or the GPU just isn't coming up to speed quickly enough?

---

### Post by lazaruslong67 on 2023-10-11
> **MAFoElffen said:**
> Do this:
```

mafoelffen@Mikes-B460M:~$ sudo find /sys -name gt_m*
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/gt_max_freq_mhz
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/gt_min_freq_mhz

```
The script was on a 13thGen iCore. I just did the above on a 10th Gen iCore.

I just confirmed that "that" register is writable by root.

Yep, I'm getting the same values you are - should I change the script to write to that location instead of the one you provided earlier (/sys/class/drm/card0) ?

---

### Post by MAFoElffen on 2023-10-11
I did this on my server, with is the same gen as yours:
```

mafoelffen@Mikes-B460M:~$ grep . /sys/devices/pci0000:00/0000:00:02.0/drm/card0/gt_max_freq_mhz
1200

mafoelffen@Mikes-B460M:~$ sudo lshw -C video | grep 'product'
       product: CometLake-S GT2 [UHD Graphics 630]

```
I would think setting your safely would either be
```

sudo intel_gpu_frequency -c min=1200
## OR
sudo echo "1200" > /sys/devices/pci0000:00/0000:00:02.0/drm/card0/gt_min_freq_mhz

```
Change the "frequency setting" line in the script file "SetMaxGpuFreq" to either of those...

Wait one, let me look at that script for a second to edit it...

---

### Post by lazaruslong67 on 2023-10-11
> **MAFoElffen said:**
> I did this on my server, with is the same gen as yours:
```

mafoelffen@Mikes-B460M:~$ grep . /sys/devices/pci0000:00/0000:00:02.0/drm/card0/gt_max_freq_mhz
1200

mafoelffen@Mikes-B460M:~$ sudo lshw -C video | grep 'product'
       product: CometLake-S GT2 [UHD Graphics 630]

```
I would think setting your safely would either be
```

sudo intel_gpu_frequency -c min=1200
## OR
sudo echo "1200" > /sys/devices/pci0000:00/0000:00:02.0/drm/card0/gt_min_freq_mhz

```
Change the "frequency setting" line in the script file "SetMaxGpuFreq" to either of those...

Wait one, let me look at that script for a second to edit it...

My max is actually 1100 (but I'm on an 8th Gen)

---

### Post by MAFoElffen on 2023-10-11
Okay, this should now work for all the recent iCores... LOL (Will not work for early iCore Gen's)
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,2023.10.10
# Modified on: 2023.10.11
# Set GPU to max frequency
# to be Run by system as root user

GPU_REGISTERS=$(sudo find /sys -name gt_m*)

for REGISTER in ${GPU_REGISTERS[@]}
do 
    if [[ "$REGISTER" == *"gt_max_freq"* ]]
    then 
       # Get the value of the max frequency setting.
       GT_MAX_FREQ=$(grep . $REGISTER)
    elif [[ "$REGISTER" == *"gt_min_freq"* ]]
    then 
       logger "gt_min_freq was $(grep . REGISTER)"
       echo $GT_MAX_FREQ > $REGISTER
       GT_MIN_FREQ=$(grep . $REGISTER)
       logger "gt_min_freq was reset to $(grep . REGISTER)"
    fi
done

```

---

### Post by lazaruslong67 on 2023-10-11
> **MAFoElffen said:**
> Okay, this should now work for all the recent iCores... LOL (Will not work for early iCore Gen's)
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,2023.10.10
# Modified on: 2023.10.11
# Set GPU to max frequency
# to be Run by system as root user

GPU_REGISTERS=$(sudo find /sys -name gt_m*)

for REGISTER in ${GPU_REGISTERS[@]}
do 
    if [[ "$REGISTER" == *"gt_max_freq"* ]]
    then 
       # Get the value of the max frequency setting.
       GT_MAX_FREQ=$(grep . $REGISTER)
    elif [[ "$REGISTER" == *"gt_min_freq"* ]]
    then 
       logger "gt_min_freq was $(grep . REGISTER)"
       echo $GT_MAX_FREQ > $REGISTER
       GT_MIN_FREQ=$(grep . $REGISTER)
       logger "gt_min_freq was reset to $(grep . REGISTER)"
    fi
done

```

OK!  Will give it a try after dinner (and maybe some bourbon lol!).  Just glad I've been able to get this thing working.  I was about to drop another $250 last weekend on a different HP model (or just switch to Windows), but decided to keep trying...

---

### Post by lazaruslong67 on 2023-10-11
> **MAFoElffen said:**
> Okay, this should now work for all the recent iCores... LOL (Will not work for early iCore Gen's)
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,2023.10.10
# Modified on: 2023.10.11
# Set GPU to max frequency
# to be Run by system as root user

GPU_REGISTERS=$(sudo find /sys -name gt_m*)

for REGISTER in ${GPU_REGISTERS[@]}
do 
    if [[ "$REGISTER" == *"gt_max_freq"* ]]
    then 
       # Get the value of the max frequency setting.
       GT_MAX_FREQ=$(grep . $REGISTER)
    elif [[ "$REGISTER" == *"gt_min_freq"* ]]
    then 
       logger "gt_min_freq was $(grep . REGISTER)"
       echo $GT_MAX_FREQ > $REGISTER
       GT_MIN_FREQ=$(grep . $REGISTER)
       logger "gt_min_freq was reset to $(grep . REGISTER)"
    fi
done

```

So tried that script and still getting errors.  I decided to just try and run from terminal prompt (vs. the service) and this is what I'm getting (script name is just "test"):

```

grep: REGISTER: No such file or directory
grep: REGISTER: No such file or directory

```

---

### Post by MAFoElffen on 2023-10-11
Post the results of this please
```

(sudo find /sys -name gt_m*

```

---

### Post by MAFoElffen on 2023-10-11
Alternate script of the same name (so that the service calls it.)
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,2023.10.10
# Modified on: 2023.10.11
# Set GPU to max frequency
# to be Run by system as root user

intel_gpu_frequency -c min=1200
logger "Set Intel GPU frequency to 1200mhz"

```

---

### Post by lazaruslong67 on 2023-10-12
> **MAFoElffen said:**
> Post the results of this please
```

(sudo find /sys -name gt_m*

```

Yeah that returns exactly what you'd expect it to:

```
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/gt_max_freq_mhz
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/gt_min_freq_mhz
```

However, when the script runs, this is what get returned (this was before a reboot though):

```
&#9675; pre-graphical.service - Pre-Reboot Process to call SetMaxGpuFreq script
     Loaded: loaded (/lib/systemd/system/pre-graphical.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Thu 2023-10-12 07:43:20 CDT; 5s ago
    Process: 4215 ExecStart=/usr/bin/SetMaxGpuFreq (code=exited, status=0/SUCCESS)
   Main PID: 4215 (code=exited, status=0/SUCCESS)
        CPU: 217ms


Oct 12 07:43:20 ThinkCentre-M720q sudo[4216]:     root : problem with defaults entries ; PWD=/ ; USER=root ;
Oct 12 07:43:20 ThinkCentre-M720q sudo[4216]:     root : PWD=/ ; USER=root ; COMMAND=/usr/bin/find /sys -name gt_m*
Oct 12 07:43:20 ThinkCentre-M720q sudo[4216]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=0)
Oct 12 07:43:20 ThinkCentre-M720q sudo[4216]: pam_unix(sudo:session): session closed for user root
Oct 12 07:43:20 ThinkCentre-M720q SetMaxGpuFreq[4219]: grep: REGISTER: No such file or directory
Oct 12 07:43:20 ThinkCentre-M720q root[4220]: gt_min_freq was
Oct 12 07:43:20 ThinkCentre-M720q SetMaxGpuFreq[4222]: grep: REGISTER: No such file or directory
Oct 12 07:43:20 ThinkCentre-M720q root[4223]: gt_min_freq was reset to
Oct 12 07:43:20 ThinkCentre-M720q systemd[1]: pre-graphical.service: Deactivated successfully.
Oct 12 07:43:20 ThinkCentre-M720q systemd[1]: Finished Pre-Reboot Process to call SetMaxGpuFreq script.

```

---

### Post by lazaruslong67 on 2023-10-12
> **MAFoElffen said:**
> Alternate script of the same name (so that the service calls it.)
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,2023.10.10
# Modified on: 2023.10.11
# Set GPU to max frequency
# to be Run by system as root user

intel_gpu_frequency -c min=1200
logger "Set Intel GPU frequency to 1200mhz"

```

And this script works exactly as expected (although I set mine to 1100).  I did find out that if you run this:

```
intel_gpu_frequency -m
```

It sets to GPU to the max supported for your GPU (mine is 1100) - shown by running this:

```
intel_gpu_frequency -g

cur: 1067 MHz
min: 1100 MHz
RP1: 350 MHz
max: 1100 MHz

```

---

### Post by MAFoElffen on 2023-10-12
So now it works with the alternate script... Go with that.

The variable is empty, but if empty, it shouldn't even go into the loop, because there would be no members REGISTER to execute the loop(???)

I'm going to debug the other script to see what is going on, just for my own sanity. Just to see what "is" going on with that, so we can have an alternate backup work-around for that....

But you have something that works for you now.

---

