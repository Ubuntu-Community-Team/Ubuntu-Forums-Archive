---
title: "Black screen when starting No Man's Sky after update to Ubuntu 21.04"
date: 2021-07-18
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2021-07-18
I was running Ubuntu 20.04 and NMS loaded fine but was to slow to play.

I am using an Intel® UHD Graphics 750 integrated GPU until I can afford a dedicated GPU so thought upgrading would help.

I upgraded and found that when I start the game it appears to load correctly, no error messages. However, I am left with a blank screen apart from the pointer.

I cannot get out of this other than to shut down and restart the machine.

I have this information:

Processor (CPU): Intel® CoreTM i7 Eight Core Processor i7-11700K (3.6GHz) 16MB Cache

Mobo: ASUS® TUF GAMING Z590-PLUS WIFI (LGA1200, USB 3.2, PCIe 4.0) - ARGB Ready

Graphics Card: INTEGRATED GRAPHICS ACCELERATOR (GPU)

```

makem@makem-pc:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 4c8a (rev 04)
makem@makem-pc:~$ find /dev -group video
/dev/fb0
/dev/dri/card0
makem@makem-pc:~$ glxinfo | grep -i vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
    Vendor: Intel (0x8086)
OpenGL vendor string: Intel
makem@makem-pc:~$ lsmod | grep "kms\|drm"
drm_kms_helper        245760  1 i915
cec                    53248  2 drm_kms_helper,i915
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
drm                   552960  20 drm_kms_helper,i915
makem@makem-pc:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-5.11.0-22-generic root=UUID=97853106-9dde-4bb7-ada7-25e282956f9f ro quiet splash vt.handoff=7
makem@makem-pc:~$ find /etc/modprobe.d/
/etc/modprobe.d/
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/amd64-microcode-blacklist.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/dkms.conf
/etc/modprobe.d/intel-microcode-blacklist.conf
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
makem@makem-pc:~$ cat /etc/modprobe.d/*kms*
# modprobe information used for DKMS modules
#
# This is a stub file, should be edited when needed,
# used by default by DKMS.
makem@makem-pc:~$ ls /etc/X11/xorg.conf
ls: cannot access '/etc/X11/xorg.conf': No such file or directory
makem@makem-pc:~$ glxinfo | grep -i "vendor\|rendering"
direct rendering: Yes
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
    Vendor: Intel (0x8086)
OpenGL vendor string: Intel
makem@makem-pc:~$ grep LoadModule /var/log/Xorg.0.log
[     2.613] (II) LoadModule: "glx"
[     2.618] (II) LoadModule: "modesetting"
[     2.619] (II) LoadModule: "fbdev"
[     2.619] (II) LoadModule: "vesa"
[     2.629] (II) LoadModule: "fbdevhw"
[     2.629] (II) LoadModule: "glamoregl"
[     2.813] (II) LoadModule: "fb"
[     3.014] (II) LoadModule: "libinput"
makem@makem-pc:~$

```

It is a driver/kernel problem?

Can anyone shed any light on this?

---

### Post by ActionParsnip on 2021-07-18
What is the output of
```

sudo lshw -C display

```
Thanks

---

### Post by makem2 on 2021-07-18
> **ActionParsnip said:**
> What is the output of
```

sudo lshw -C display

```
Thanks

```

makem@makem-pc:~$ sudo lshw -C display
[sudo] password for makem: 
  *-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 mode=1920x1080 visual=truecolor xres=1920 yres=1080
       resources: iomemory:600-5ff iomemory:400-3ff irq:159 memory:6000000000-6000ffffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff
makem@makem-pc:~$ 

```

Thanks for taking the time

---

### Post by MAFoElffen on 2021-07-19
So let me clarify something...

You previously were running the Steam Game version of "No Man's Sky" on the 64bit version of Steam, right? You didn't say.

You did system updates. Everything works.in your desktop... Except when you are in the Steam Player and you try to start up "No Man's Sky"?

---

### Post by makem2 on 2021-07-20
> **MAFoElffen said:**
> So let me clarify something...

You previously were running the Steam Game version of "No Man's Sky" on the 64bit version of Steam, right? You didn't say.

You did system updates. Everything works.in your desktop... Except when you are in the Steam Player and you try to start up "No Man's Sky"?

I use 64bit Steam, I installed and played No Man's Sky from Steam when I was using Ubuntu 20.04.  The game started and played without a problem except for being so slow it was impossible to play.

It was suggested that this could be a kernel problem and I took the easy way out and upgraded from Ubuntu 20.04 to Ubuntu 21.04.

[https://github.com/intel-gpu/documentation/issues/14#issuecomment-881415861](https://github.com/intel-gpu/documentation/issues/14#issuecomment-881415861)

Everything works fine using Ubuntu 21.04  (I don't play any other games) in my desktop and every other program I have used works fine.

When I use NMS (No Man's Sky) from the Steam player that is when I get the black screen and must reboot although no errors are shown.

---

### Post by MAFoElffen on 2021-07-20
I don't have Intel UHD graphics... So maybe someone using that and Linux Steam can help you with that, but...

In Steam > Help > System Info, under Video Card, you might want to post what the Steam App see's for: Driver, Driver Version, & OpenGL Version...

---

### Post by makem2 on 2021-07-20
> **MAFoElffen said:**
> I don't have Intel UHD graphics... So maybe someone using that and Linux Steam can help you with that, but...

In Steam > Help > System Info, under Video Card, you might want to post what the Steam App see's for: Driver, Driver Version, & OpenGL Version...

Video car result from Steam:

Video Card: 
    Driver:  Intel Mesa Intel(R) Graphics (RKL GT1) 
    Driver Version:  4.6 (Compatibility Profile) Mesa 21.3.0-devel (git-ed57666 2021-07-17 focal-oibaf-ppa) 
    OpenGL Version: 4.6 
    Desktop Color Depth: 24 bits per pixel 
    Monitor Refresh Rate: 60 Hz 
    VendorID:  0x8086 
    DeviceID:  0x4c8a 
    Revision Not Detected 

Before I bought the integrated GPU I saw that it was in a compatible list but I forget where I saw that. I did realise there may be problems while I wait for prices to drop and knew I would have to use GeForce NOW in the meantime, so it was just a fingers crossed thing.

Edit: I need $5 spend or in my wallet before Steam will assist plus a 2-3 day wait until it is verified!

---

### Post by MAFoElffen on 2021-07-20
Please post the results of this:
```
lsb_release -a
uname -r
vulkaninfo | less
```
I found out some things while looking into it for you...

NMS used to use OpenGL, now uses vulcan-mesa...

On reddit, for Intel UHD Graphics 750, they say if on Ubuntu 21.XX, then be on kernel version 5.12 or newer, and install the appropriate mesa drivers (such as vulcan-mesa) from [https://launchpad.net/~kisak/+archive/ubuntu/turtle](https://launchpad.net/~kisak/+archive/ubuntu/turtle)... 

That is how they said they got it working. That is hear-say. I can't confirm that myself...

---

### Post by makem2 on 2021-07-21
> **MAFoElffen said:**
> Please post the results of this:
```
lsb_release -a
uname -r
vulkaninfo | less
```
I found out some things while looking into it for you...

NMS used to use OpenGL, now uses vulcan-mesa...

On reddit, for Intel UHD Graphics 750, they say if on Ubuntu 21.XX, then be on kernel version 5.12 or newer, and install the appropriate mesa drivers (such as vulcan-mesa) from [https://launchpad.net/~kisak/+archive/ubuntu/turtle](https://launchpad.net/~kisak/+archive/ubuntu/turtle)... 

That is how they said they got it working. That is hear-say. I can't confirm that myself...

```

makem@makem-pc:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 21.04
Release:    21.04
Codename:    hirsute
makem@makem-pc:~$ uname -r
5.11.0-22-generic
makem@makem-pc:~$ 

```

The command vulkaninfo | less[/code] produces a never ending stream of data therefore I have shown only a portion. If it is missing any relevant information please let me know:

```

==========
VULKANINFO
==========

Vulkan Instance Version: 1.2.162


Instance Extensions: count = 18
===============================
        VK_EXT_acquire_xlib_display            : extension revision 1
        VK_EXT_debug_report                    : extension revision 10
        VK_EXT_debug_utils                     : extension revision 2
        VK_EXT_direct_mode_display             : extension revision 1
        VK_EXT_display_surface_counter         : extension revision 1
        VK_KHR_device_group_creation           : extension revision 1
        VK_KHR_display                         : extension revision 23
        VK_KHR_external_fence_capabilities     : extension revision 1
        VK_KHR_external_memory_capabilities    : extension revision 1
        VK_KHR_external_semaphore_capabilities : extension revision 1
        VK_KHR_get_display_properties2         : extension revision 1
        VK_KHR_get_physical_device_properties2 : extension revision 2
        VK_KHR_get_surface_capabilities2       : extension revision 1
        VK_KHR_surface                         : extension revision 25
        VK_KHR_surface_protected_capabilities  : extension revision 1
        VK_KHR_wayland_surface                 : extension revision 6
        VK_KHR_xcb_surface                     : extension revision 6
        VK_KHR_xlib_surface                    : extension revision 6

Layers: count = 8
=================
VK_LAYER_INTEL_nullhw (INTEL NULL HW) Vulkan version 1.1.73, layer version 1:
        Layer Extensions: count = 0
        Devices: count = 2
                GPU id = 0 (Intel(R) Graphics (RKL GT1))
                Layer-Device Extensions: count = 0

                GPU id = 1 (llvmpipe (LLVM 12.0.1, 256 bits))
                Layer-Device Extensions: count = 0

VK_LAYER_KHRONOS_validation (Khronos Validation Layer) Vulkan version 1.2.162, l
ayer version 1:
        Layer Extensions: count = 3
                VK_EXT_debug_report        : extension revision 9
                VK_EXT_debug_utils         : extension revision 1
                VK_EXT_validation_features : extension revision 2
        Devices: count = 2
                GPU id = 0 (Intel(R) Graphics (RKL GT1))
                Layer-Device Extensions: count = 3
                        VK_EXT_debug_marker     : extension revision 4
                        VK_EXT_tooling_info     : extension revision 1
                        VK_EXT_validation_cache : extension revision 1

                GPU id = 1 (llvmpipe (LLVM 12.0.1, 256 bits))
                Layer-Device Extensions: count = 3
                        VK_EXT_debug_marker     : extension revision 4
                        VK_EXT_tooling_info     : extension revision 1
                        VK_EXT_validation_cache : extension revision 1

VK_LAYER_MESA_device_select (Linux device selection layer) Vulkan version 1.2.73
, layer version 1:
        Layer Extensions: count = 0
        Devices: count = 2
                GPU id = 0 (Intel(R) Graphics (RKL GT1))
                Layer-Device Extensions: count = 0

                GPU id = 1 (llvmpipe (LLVM 12.0.1, 256 bits))
                Layer-Device Extensions: count = 0

VK_LAYER_MESA_overlay (Mesa Overlay layer) Vulkan version 1.1.73, layer version 
1:
        Layer Extensions: count = 0
        Devices: count = 2
                GPU id = 0 (Intel(R) Graphics (RKL GT1))
                Layer-Device Extensions: count = 0

                GPU id = 1 (llvmpipe (LLVM 12.0.1, 256 bits))
                Layer-Device Extensions: count = 0

VK_LAYER_VALVE_steam_fossilize_32 (Steam Pipeline Caching Layer) Vulkan version 
1.2.136, layer version 1:
        Layer Extensions: count = 0
        Devices: count = 2
                GPU id = 0 (Intel(R) Graphics (RKL GT1))
                Layer-Device Extensions: count = 0

                GPU id = 1 (llvmpipe (LLVM 12.0.1, 256 bits))
                Layer-Device Extensions: count = 0

VK_LAYER_VALVE_steam_fossilize_64 (Steam Pipeline Caching Layer) Vulkan version 
1.2.136, layer version 1:
        Layer Extensions: count = 0
        Devices: count = 2
                GPU id = 0 (Intel(R) Graphics (RKL GT1))
                Layer-Device Extensions: count = 0

                GPU id = 1 (llvmpipe (LLVM 12.0.1, 256 bits))
                Layer-Device Extensions: count = 0

VK_LAYER_VALVE_steam_overlay_32 (Steam Overlay Layer) Vulkan version 1.2.136, la
yer version 1:
        Layer Extensions: count = 0
        Devices: count = 2
                GPU id = 0 (Intel(R) Graphics (RKL GT1))
                Layer-Device Extensions: count = 0

                GPU id = 1 (llvmpipe (LLVM 12.0.1, 256 bits))
                Layer-Device Extensions: count = 0

VK_LAYER_VALVE_steam_overlay_64 (Steam Overlay Layer) Vulkan version 1.2.136, la
yer version 1:
        Layer Extensions: count = 0
        Devices: count = 2
                GPU id = 0 (Intel(R) Graphics (RKL GT1))
                Layer-Device Extensions: count = 0

                GPU id = 1 (llvmpipe (LLVM 12.0.1, 256 bits))
                Layer-Device Extensions: count = 0

Presentable Surfaces:
=====================
GPU id : 0 (Intel(R) Graphics (RKL GT1)):
        Surface types: count = 2
                VK_KHR_xcb_surface
                VK_KHR_xlib_surface
        Formats: count = 2
                SurfaceFormat[0]:
                        format = FORMAT_B8G8R8A8_SRGB
                        colorSpace = COLOR_SPACE_SRGB_NONLINEAR_KHR
                SurfaceFormat[1]:
                        format = FORMAT_B8G8R8A8_UNORM
                        colorSpace = COLOR_SPACE_SRGB_NONLINEAR_KHR
        Present Modes: count = 4
                PRESENT_MODE_IMMEDIATE_KHR
                PRESENT_MODE_MAILBOX_KHR
                PRESENT_MODE_FIFO_KHR
                PRESENT_MODE_FIFO_RELAXED_KHR
        VkSurfaceCapabilitiesKHR:
        -------------------------
                minImageCount       = 3
                maxImageCount       = 0
                currentExtent:
                        width  = 256
                        height = 256
                minImageExtent:
                        width  = 256
                        height = 256
                maxImageExtent:
                        width  = 256
                        height = 256
                maxImageArrayLayers = 1
                supportedTransforms: count = 1
                        SURFACE_TRANSFORM_IDENTITY_BIT_KHR
                currentTransform    = SURFACE_TRANSFORM_IDENTITY_BIT_KHR
                supportedCompositeAlpha: count = 2
                        COMPOSITE_ALPHA_OPAQUE_BIT_KHR
                        COMPOSITE_ALPHA_INHERIT_BIT_KHR
                supportedUsageFlags: count = 5
                        IMAGE_USAGE_TRANSFER_SRC_BIT
                        IMAGE_USAGE_TRANSFER_DST_BIT
                        IMAGE_USAGE_SAMPLED_BIT
                        IMAGE_USAGE_STORAGE_BIT
                        IMAGE_USAGE_COLOR_ATTACHMENT_BIT
        VkSurfaceCapabilities2EXT:
        --------------------------
                supportedSurfaceCounters: count = 0
                        None
        VkSurfaceProtectedCapabilitiesKHR:
        ----------------------------------
               supportsProtected = false


GPU id : 1 (llvmpipe (LLVM 12.0.1, 256 bits)):
        Surface types: count = 2
                VK_KHR_xcb_surface
                VK_KHR_xlib_surface
        Formats: count = 2
                SurfaceFormat[0]:
                        format = FORMAT_B8G8R8A8_SRGB
                        colorSpace = COLOR_SPACE_SRGB_NONLINEAR_KHR
                SurfaceFormat[1]:
                        format = FORMAT_B8G8R8A8_UNORM
                        colorSpace = COLOR_SPACE_SRGB_NONLINEAR_KHR
        Present Modes: count = 4
                PRESENT_MODE_IMMEDIATE_KHR
                PRESENT_MODE_MAILBOX_KHR
                PRESENT_MODE_FIFO_KHR
                PRESENT_MODE_FIFO_RELAXED_KHR
        VkSurfaceCapabilitiesKHR:
        -------------------------
                minImageCount       = 3
                maxImageCount       = 0
                currentExtent:
                        width  = 256
                        height = 256
                minImageExtent:
                        width  = 256
                        height = 256
                maxImageExtent:
                        width  = 256
                        height = 256
                maxImageArrayLayers = 1
                supportedTransforms: count = 1
                        SURFACE_TRANSFORM_IDENTITY_BIT_KHR
                currentTransform    = SURFACE_TRANSFORM_IDENTITY_BIT_KHR
                supportedCompositeAlpha: count = 2
                        COMPOSITE_ALPHA_OPAQUE_BIT_KHR
                        COMPOSITE_ALPHA_INHERIT_BIT_KHR
                supportedUsageFlags: count = 5
                        IMAGE_USAGE_TRANSFER_SRC_BIT
                        IMAGE_USAGE_TRANSFER_DST_BIT
                        IMAGE_USAGE_SAMPLED_BIT
                        IMAGE_USAGE_STORAGE_BIT
                        IMAGE_USAGE_COLOR_ATTACHMENT_BIT
        VkSurfaceCapabilities2EXT:
        --------------------------
                supportedSurfaceCounters: count = 0
                        None
        VkSurfaceProtectedCapabilitiesKHR:
        ----------------------------------
                supportsProtected = false


```

Would please post a link to the Reddit page to which you refer as I could not find it but did find many reference to the gpu.

---

### Post by MAFoElffen on 2021-07-21
From my history, where I found that yesterday:
[https://www.reddit.com/r/linux_gaming/comments/nqrf5j/no_mans_sky_on_ubuntu_with_integrated_gpu_intel/h0c9to2/](https://www.reddit.com/r/linux_gaming/comments/nqrf5j/no_mans_sky_on_ubuntu_with_integrated_gpu_intel/h0c9to2/) (Select the View Parent Comments)
[https://www.reddit.com/r/linux_gaming/comments/nqrf5j/no_mans_sky_on_ubuntu_with_integrated_gpu_intel/h0c9to2/](https://www.reddit.com/r/linux_gaming/comments/nqrf5j/no_mans_sky_on_ubuntu_with_integrated_gpu_intel/h0c9to2/) (Continued)

As per...Your Vulnan driver is 1.2+ so that is okay, but
```
makem@makem-pc:~$ uname -r
5.11.0-22-generic
```
Is not newer than Kernel 5.12... So the kernel module is not?

What they went on to discuss was to install a newer kernel from Ubuntu Mainline Kernels...

Beyond their instructions, the easiest way to do that is:
```

sudo add-apt-repository ppa:cappelikan/ppa
sudo apt update
sudo apt install mainline

```
Then start up that GUI application by going to Activities > Typing Mainline > Selecting "Ubuntu Mainline Kernel Installer"... Select the Kernel you want to try... I was an Ubuntu Dev Cycle tester... Not all those kernel versions work well. Stay away from one that are mark with "rc" unless you are brave and read the kernel.org release notes first.. Those were "release candidates"... So still in test. 

```

mafoelffen@ovirt-vm-01:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal

mafoelffen@ovirt-vm-01:~$ uname -r
5.13.4-051304-generic

```
That is the above code, tested on a VM, to show you 20.04.2 running on a Kernel Version 5.13.4.

After that... There are newer mesa drivers in these two PPA's:
[https://launchpad.net/~kisak/+archive/ubuntu/turtle](https://launchpad.net/~kisak/+archive/ubuntu/turtle) (Stable)
[https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa) (Test)

---

### Post by makem2 on 2021-07-22
Brilliant, thank you, I will try the suggested kernel update, see what happens and if necessary continue with the mesa drivers too if necessary.

---

### Post by makem2 on 2021-07-22
> **MAFoElffen said:**
> From my history, where I found that yesterday:
[https://www.reddit.com/r/linux_gaming/comments/nqrf5j/no_mans_sky_on_ubuntu_with_integrated_gpu_intel/h0c9to2/](https://www.reddit.com/r/linux_gaming/comments/nqrf5j/no_mans_sky_on_ubuntu_with_integrated_gpu_intel/h0c9to2/) (Select the View Parent Comments)
[https://www.reddit.com/r/linux_gaming/comments/nqrf5j/no_mans_sky_on_ubuntu_with_integrated_gpu_intel/h0c9to2/](https://www.reddit.com/r/linux_gaming/comments/nqrf5j/no_mans_sky_on_ubuntu_with_integrated_gpu_intel/h0c9to2/) (Continued)

As per...Your Vulnan driver is 1.2+ so that is okay, but
```
makem@makem-pc:~$ uname -r
5.11.0-22-generic
```
Is not newer than Kernel 5.12... So the kernel module is not?

What they went on to discuss was to install a newer kernel from Ubuntu Mainline Kernels...

Beyond their instructions, the easiest way to do that is:
```

sudo add-apt-repository ppa:cappelikan/ppa
sudo apt update
sudo apt install mainline

```
Then start up that GUI application by going to Activities > Typing Mainline > Selecting "Ubuntu Mainline Kernel Installer"... Select the Kernel you want to try... I was an Ubuntu Dev Cycle tester... Not all those kernel versions work well. Stay away from one that are mark with "rc" unless you are brave and read the kernel.org release notes first.. Those were "release candidates"... So still in test. 

```

mafoelffen@ovirt-vm-01:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal

mafoelffen@ovirt-vm-01:~$ uname -r
5.13.4-051304-generic

```
That is the above code, tested on a VM, to show you 20.04.2 running on a Kernel Version 5.13.4.

After that... There are newer mesa drivers in these two PPA's:
[https://launchpad.net/~kisak/+archive/ubuntu/turtle](https://launchpad.net/~kisak/+archive/ubuntu/turtle) (Stable)
[https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa) (Test)

Started with you suggestion of installing mainline only to find I already have the most up-to-date version! I remembered before upgrading to 21.04  that I did attempt to change kernels but I was a bit out of my depth at the time. I have added the output here for completeness.

```

makem@makem-pc:~$ sudo apt install mainline
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
mainline is already the newest version (1.0.14-0~202107051645~ubuntu21.04.1).
0 to upgrade, 0 to newly install, 0 to remove and 23 not to upgrade.
makem@makem-pc:~$

```

Edit: After installing kernel 5.13.4 and rebooting I received an error on the lines of. "kernel not signed or wrong signature, press any key to continue", pressing any key took me to the  ubuntu/windows choices and choosing ubuntu gave the error again. A roundabout. So I took the option to choose a different kernel via Advanced Options, the previous one.

I am not sure if I should purge or remove 5.13.4 and try 5.13.3 and so on or if I can just install any kernel leaving the others in place (as is 5.11.0.22.23) and just choose the one to try.

I have just tried to choose 5.13.4 to determine the exact error message but am told the kernel needs to be loaded  first.  Getting out of my depth again :(

Edit 2: The exact error message is, "Invalid signature" for the kernel 5.13.4

---

### Post by CatKiller on 2021-07-22
> **makem2 said:**
> Edit: After installing kernel 5.13.4 and rebooting I received an error on the lines of. "kernel not signed or wrong signature, press any key to continue", pressing any key took me to the  ubuntu/windows choices and choosing ubuntu gave the error again.

Have you got Secure Boot enabled? That means that you'll only be able to use software that's signed.

---

### Post by MAFoElffen on 2021-07-22
Yes, as CatKiller mentioned, turn off SecureBoot in BIOS.

Yes, use the Mainline App to Remove the Kernels that won't work before trying another. Using Remove from that app, will purge it.

Note that the Grub Menu, will default to the newest Kernel as it's default. And you are trying the newest, working towards older kernels (that's how the list shows up in that app...) So if you leave a newer kernel, it will default to that most recent kernel, unless you select, "other" in the grub menu, and select it manually... But if you have SecureBoot, you probably have UEFI and don't see a Grub Boot Menu, do you. (Unless you press the <Escape> key repeatedly while it is booting...) So it would just keep going to that newer kernel(?) without giving you the chance to use the older,  If you don't purge the newer that didn't work... 

I would try on of the 12.x Kernels, then try one of the newer mesa drivers from stable. If those don't work, then go to the NMS website, Or Steam and turn in support ticket.

I don't have a problem on Linux or Windows Steam... But I have NVidia Graphics. I think the problem you are going to run into, is the that both Steam and NMS'es publisher say the minimum requirements do not list Intel Graphics as being supported for NMS. (Only AMD and NVidia).

---

### Post by makem2 on 2021-07-22
> **CatKiller said:**
> Have you got Secure Boot enabled? That means that you'll only be able to use software that's signed.

Yes Secure Boot was on and I found how to turn it off in the new unfamiliar BIOS. As a result:

```

makem@makem-pc:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 21.04
Release:    21.04
Codename:    hirsute
makem@makem-pc:~$ uname -r
5.13.4-051304-generic
makem@makem-pc:~$

```

So I am now running the latest kernel and will try starting up the game before looking into the mesa drivers.

Edit: The black screen still persists so I will look into the mesa drivers.
Btw, should I remove the older kernel or leave it there to fall back on?

---

### Post by makem2 on 2021-07-22
> **MAFoElffen said:**
> Yes, as CatKiller mentioned, turn off SecureBoot in BIOS.

Yes, use the Mainline App to Remove the Kernels that won't work before trying another. Using Remove from that app, will purge it.

I would try on of the 12.x Kernels, then try one of the newer mesa drivers from stable. If those don't work, then go to the NMS website, Or Steam and turn in support ticket.

I don't have a problem on Linux or Windows Steam... But I have NVidia Graphics. I think the problem you are going to run into, is the that both Steam and NMS'es publisher say the minimum requirements do not list Intel Graphics as being supported for NMS. (Only AMD and NVidia).

I am now able to use the latest kernel having turned off Secure Boot and will try mesa drivers now.

Yes, I intend to use a dedicated AMD or Nvidea when possible, not sure which at the moment.

Edit: Btw I do see a grub menu when using Secure Boot (You mentioned I may not see grub earlier)

---

### Post by MAFoElffen on 2021-07-22
Leave the original kernel you started from before this, with those updates! Yes, you should keep that failsafe/fallback. Eventually you update to something newer again... But in the meanwhile, you are wading in the currents. LOL

---

### Post by makem2 on 2021-07-22
> **MAFoElffen said:**
> Leave the original kernel you started from before this, with those updates! Yes, you should keep that failsafe/fallback. Eventually you update to something newer again... But in the meanwhile, you are wading in the currents. LOL

Thank you.

I have installed the mesa ppa but now wonder (forgive the ignorance), if it actually installs the newer mesa drivers or whether I have to do something. From what I read there I think it does instal the drivers/driver. I don't suppose it will do any harm if I start NMS again whether or not they are installed lol.

Edit: Black screen again I'm afraid. I am now beginning to wonder if I should give up on this as the chances of this integrated gpu being capable of dealing with this game at full speed is asking to much. Also, if I persist and try lower kernels, what damage am I risking by the hard boots I am having to do to recover from the black screen?

---

### Post by makem2 on 2021-07-22
From Steam after updating mesa driver:

Video Card: 
    Driver:  Intel Mesa Intel(R) Graphics (RKL GT1) 
    Driver Version:  4.6 (Compatibility Profile) Mesa 21.3.0-devel (git-ed57666 2021-07-17 focal-oibaf-ppa) 
    OpenGL Version: 4.6 
    Desktop Color Depth: 24 bits per pixel 
    Monitor Refresh Rate: 60 Hz 
    VendorID:  0x8086 
    DeviceID:  0x4c8a 
    Revision Not Detected 
    Number of Monitors:  1 
    Number of Logical Video Cards:  1

No change in the mesa driver :(

This page suggests how to get the latest mesa driver:

[URL="https://itsfoss.com/install-mesa-ubuntu/"]https://itsfoss.com/install-mesa-ubuntu/
[/URL]
I ask help before using another ppa.

---

### Post by MAFoElffen on 2021-07-22
Isn't the PPA in that tutorial the same PPA I linked for you for Mesa? lol

you are on 21.3.0... 21.1.5~kisak1~g is the newest there.

---

### Post by makem2 on 2021-07-22
> **MAFoElffen said:**
> Isn't the PPA in that tutorial the same PPA I linked for you for Mesa? lol

you are on 21.3.0... 21.1.5~kisak1~g is the newest there.

Yes it may be from the same web page but further down it talks about later than the one you suggested:

ppa  is 

oibaf/graphics-drivers

Which is a different source?

---

### Post by makem2 on 2021-07-23
As nothing has worked for mesa so far I thought I would try the oibaf/drivers but I cannot understand:

snip>
Note: Using ppa-purge with Ubuntu derivatives needs to include -d  <based_on_name> to work safely. For example, Linux Mint 20 is  based on Ubuntu Focal, so that would make it:
sudo ppa-purge -d focal ppa:kisak/turtle
snip>

Does that mean the -d is based on focal and that for me I need another letter -x for 21.04? 21.04 is based on Hirsute Hippo so is my command: sudo ppa-purge -x hirsute ppa:kisak/turtle and if so where would I find the letter to substitute for x?

My ppas look a mess now :( and it is hard to find help I can trust.

```

makem@makem-pc:~$ apt policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://ppa.launchpad.net/kisak/turtle/ubuntu hirsute/main i386 Packages
     release v=21.04,o=LP-PPA-kisak-turtle,a=hirsute,n=hirsute,l=kisak-mesa stable,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/kisak/turtle/ubuntu hirsute/main amd64 Packages
     release v=21.04,o=LP-PPA-kisak-turtle,a=hirsute,n=hirsute,l=kisak-mesa stable,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/kisak/kisak-mesa/ubuntu hirsute/main i386 Packages
     release v=21.04,o=LP-PPA-kisak-kisak-mesa,a=hirsute,n=hirsute,l=kisak-mesa fresh,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/kisak/kisak-mesa/ubuntu hirsute/main amd64 Packages
     release v=21.04,o=LP-PPA-kisak-kisak-mesa,a=hirsute,n=hirsute,l=kisak-mesa fresh,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/cappelikan/ppa/ubuntu hirsute/main amd64 Packages
     release v=21.04,o=LP-PPA-cappelikan,a=hirsute,n=hirsute,l=PPA for cappelikan,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://security.ubuntu.com/ubuntu hirsute-security/multiverse i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute-security,n=hirsute,l=Ubuntu,c=multiverse,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu hirsute-security/multiverse amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute-security,n=hirsute,l=Ubuntu,c=multiverse,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu hirsute-security/universe i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute-security,n=hirsute,l=Ubuntu,c=universe,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu hirsute-security/universe amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute-security,n=hirsute,l=Ubuntu,c=universe,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu hirsute-security/restricted i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute-security,n=hirsute,l=Ubuntu,c=restricted,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu hirsute-security/restricted amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute-security,n=hirsute,l=Ubuntu,c=restricted,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu hirsute-security/main i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute-security,n=hirsute,l=Ubuntu,c=main,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu hirsute-security/main amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute-security,n=hirsute,l=Ubuntu,c=main,b=amd64
     origin security.ubuntu.com
 100 http://gb.archive.ubuntu.com/ubuntu hirsute-backports/universe i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute-backports,n=hirsute,l=Ubuntu,c=universe,b=i386
     origin gb.archive.ubuntu.com
 100 http://gb.archive.ubuntu.com/ubuntu hirsute-backports/universe amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute-backports,n=hirsute,l=Ubuntu,c=universe,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute-updates/multiverse i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute-updates,n=hirsute,l=Ubuntu,c=multiverse,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute-updates/multiverse amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute-updates,n=hirsute,l=Ubuntu,c=multiverse,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute-updates/universe i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute-updates,n=hirsute,l=Ubuntu,c=universe,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute-updates/universe amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute-updates,n=hirsute,l=Ubuntu,c=universe,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute-updates/restricted i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute-updates,n=hirsute,l=Ubuntu,c=restricted,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute-updates/restricted amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute-updates,n=hirsute,l=Ubuntu,c=restricted,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute-updates/main i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute-updates,n=hirsute,l=Ubuntu,c=main,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute-updates/main amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute-updates,n=hirsute,l=Ubuntu,c=main,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute/multiverse i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute,n=hirsute,l=Ubuntu,c=multiverse,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute/multiverse amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute,n=hirsute,l=Ubuntu,c=multiverse,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute/universe i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute,n=hirsute,l=Ubuntu,c=universe,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute/universe amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute,n=hirsute,l=Ubuntu,c=universe,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute/restricted i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute,n=hirsute,l=Ubuntu,c=restricted,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute/restricted amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute,n=hirsute,l=Ubuntu,c=restricted,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute/main i386 Packages
     release v=21.04,o=Ubuntu,a=hirsute,n=hirsute,l=Ubuntu,c=main,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu hirsute/main amd64 Packages
     release v=21.04,o=Ubuntu,a=hirsute,n=hirsute,l=Ubuntu,c=main,b=amd64
     origin gb.archive.ubuntu.com
Pinned packages:
     networkd-dispatcher -> 2.1-2~ubuntu21.04.1 with priority 1
     zfs-zed -> 2.0.2-1ubuntu5.1 with priority 1
     zfs-test -> 2.0.2-1ubuntu5.1 with priority 1
     zfs-initramfs -> 2.0.2-1ubuntu5.1 with priority 1
     spl -> 2.0.2-1ubuntu5.1 with priority 1
     libnvpair3linux -> 2.0.2-1ubuntu5.1 with priority 1
     base-passwd -> 3.5.49ubuntu1 with priority 1
     base-passwd:i386 -> 3.5.49ubuntu1 with priority 1
     pyzfs-doc -> 2.0.2-1ubuntu5.1 with priority 1
     libzpool4linux -> 2.0.2-1ubuntu5.1 with priority 1
     libuutil3linux -> 2.0.2-1ubuntu5.1 with priority 1
     zfs-dkms -> 2.0.2-1ubuntu5.1 with priority 1
     libzfslinux-dev -> 2.0.2-1ubuntu5.1 with priority 1
     spl-dkms -> 2.0.2-1ubuntu5.1 with priority 1
     python3-pyzfs -> 2.0.2-1ubuntu5.1 with priority 1
     zfs-dracut -> 2.0.2-1ubuntu5.1 with priority 1
     shim -> 15.4-0ubuntu5 with priority 1
     libzfs4linux -> 2.0.2-1ubuntu5.1 with priority 1
     shim-dbg -> 15.4-0ubuntu5 with priority 1
     libzfsbootenv1linux -> 2.0.2-1ubuntu5.1 with priority 1
     libpam-zfs -> 2.0.2-1ubuntu5.1 with priority 1
     zfsutils-linux -> 2.0.2-1ubuntu5.1 with priority 1

```

---

### Post by MAFoElffen on 2021-07-23
since you referred to an It's FOSS article previously, here's there tutorial on that: [https://itsfoss.com/ppa-purge/](https://itsfoss.com/ppa-purge/)

And yes, there is a mess there: 
 - In Lines 3 thru 5- you have Kisak's Mesa Stable repo added. 
 - In Lines 6 thru 8 you have his Fresh PPA added. 

There are packages in both PPA's with the same names, so there IS a conflict there. Only one of those PPA's should be there at a time... One of them needs to be purged to resolve that conflict... (I don't believe I'm saying this, but...) Since you are looking for the newest version, you are probably wanting to purge the Stable PPA. 
```
sudo apt install ppa-purge
sudo ppa-purge ppa:kisak/turtle

```
Then do an upgrade on mesa
```
sudo apt update
sudo apt install --reinstall mesa

```

---

### Post by deadflowr on 2021-07-23
> Does that mean the -d is based on focal 
No, it means distro or distribution.
Releases like mint may need it as they have their own repositories and so when ppa-purge tries to revert the packages to the originally installed versions it needs to do so for the correct repo.

---

### Post by MAFoElffen on 2021-07-23
To make that easier to read in more of a human format, please post the results of:
```
inxi -Sr
```

---

### Post by makem2 on 2021-07-24
> **MAFoElffen said:**
> since you referred to an It's FOSS article previously, here's there tutorial on that: [https://itsfoss.com/ppa-purge/](https://itsfoss.com/ppa-purge/)

And yes, there is a mess there: 
 - In Lines 3 thru 5- you have Kisak's Mesa Stable repo added. 
 - In Lines 6 thru 8 you have his Fresh PPA added. 

There are packages in both PPA's with the same names, so there IS a conflict there. Only one of those PPA's should be there at a time... One of them needs to be purged to resolve that conflict... (I don't believe I'm saying this, but...) Since you are looking for the newest version, you are probably wanting to purge the Stable PPA. 
```
sudo apt install ppa-purge
sudo ppa-purge ppa:kisak/turtle

```
Then do an upgrade on mesa
```
sudo apt update
sudo apt install --reinstall mesa

```

The first purge was done and completed successfully. I then had a  problem trying to post the reply and had to restart the machine, hence  the error 'unable to find kisak turtle' seen below.

The last error 'unable to locate package mesa' also occurred during the first attempt.

```

makem@makem-pc:~$ sudo apt install ppa-purge
[sudo] password for makem: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
ppa-purge is already the newest version (0.2.8+bzr63).
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.
makem@makem-pc:~$ sudo ppa-purge ppa:kisak/turtle
Updating packages lists
PPA to be removed: kisak turtle
Warning:  Could not find package list for PPA: kisak turtle
makem@makem-pc:~$ sudo apt update
Hit:1 http://gb.archive.ubuntu.com/ubuntu hirsute InRelease
Hit:2 http://ppa.launchpad.net/cappelikan/ppa/ubuntu hirsute InRelease     
Hit:3 http://gb.archive.ubuntu.com/ubuntu hirsute-updates InRelease        
Hit:4 http://gb.archive.ubuntu.com/ubuntu hirsute-backports InRelease          
Hit:5 http://ppa.launchpad.net/kisak/kisak-mesa/ubuntu hirsute InRelease       
Get:6 http://security.ubuntu.com/ubuntu hirsute-security InRelease [101 kB]
Fetched 101 kB in 1s (94.2 kB/s)   
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
makem@makem-pc:~$ sudo apt install --reinstall mesa
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package mesa
makem@makem-pc:~$ 

```

---

### Post by makem2 on 2021-07-24
> **MAFoElffen said:**
> To make that easier to read in more of a human format, please post the results of:
```
inxi -Sr
```

```

makem@makem-pc:~$ inxi -Sr
System:
  Host: makem-pc Kernel: 5.13.4-051304-generic x86_64 bits: 64 
  Desktop: Xfce 4.16.0 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Repos:
  Active apt repos in: /etc/apt/sources.list 
  1: deb http://gb.archive.ubuntu.com/ubuntu/ hirsute main restricted
  2: deb http://gb.archive.ubuntu.com/ubuntu/ hirsute-updates main restricted
  3: deb http://gb.archive.ubuntu.com/ubuntu/ hirsute universe
  4: deb http://gb.archive.ubuntu.com/ubuntu/ hirsute-updates universe
  5: deb http://gb.archive.ubuntu.com/ubuntu/ hirsute multiverse
  6: deb http://gb.archive.ubuntu.com/ubuntu/ hirsute-updates multiverse
  7: deb http://gb.archive.ubuntu.com/ubuntu/ hirsute-backports main restricted universe multiverse
  8: deb http://security.ubuntu.com/ubuntu hirsute-security main restricted
  9: deb http://security.ubuntu.com/ubuntu hirsute-security universe
  10: deb http://security.ubuntu.com/ubuntu hirsute-security multiverse
  No active apt repos in: /etc/apt/sources.list.d/cappelikan-ubuntu-ppa-focal.list 
  Active apt repos in: /etc/apt/sources.list.d/cappelikan-ubuntu-ppa-hirsute.list 
  1: deb http://ppa.launchpad.net/cappelikan/ppa/ubuntu/ hirsute main
  No active apt repos in: /etc/apt/sources.list.d/google-earth-pro.list 
  Active apt repos in: /etc/apt/sources.list.d/kisak-ubuntu-kisak-mesa-hirsute.list 
  1: deb http://ppa.launchpad.net/kisak/kisak-mesa/ubuntu/ hirsute main
  No active apt repos in: /etc/apt/sources.list.d/kisak-ubuntu-turtle-hirsute.list 
  No active apt repos in: /etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-focal.list 
  No active apt repos in: /etc/apt/sources.list.d/openrazer-ubuntu-stable-focal.list 
  No active apt repos in: /etc/apt/sources.list.d/teamviewer.list 
makem@makem-pc:~$ 

```

---

### Post by makem2 on 2021-07-24
I am not sure if this error message is off topic so if so please advise and I can deal with it elsewhere.

It is seen after choosing Ubuntu in the grub menu.

[URL="https://imgur.com/SWmSYNl.png"]https://imgur.com/SWmSYNl.png
[/URL]
I comprehend the first line.

```

makem@makem-pc:~$ inxi -Fxz
System:
  Kernel: 5.13.4-051304-generic x86_64 bits: 64 compiler: gcc v: 10.2.1 
  Desktop: Xfce 4.16.0 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:
  Type: Desktop System: ASUS product: N/A v: N/A serial: <filter> 
  Mobo: ASUSTeK model: TUF GAMING Z590-PLUS WIFI v: Rev 1.xx 
  serial: <filter> UEFI: American Megatrends v: 0820 date: 04/26/2021 
Battery:
  ID-1: hidpp_battery_0 charge: N/A condition: N/A 
  model: Logitech G903 LIGHTSPEED Wireless Gaming Mouse w/ HERO 
  status: Discharging 
CPU:
  Info: 8-Core model: 11th Gen Intel Core i7-11700K bits: 64 type: MT MCP 
  arch: N/A rev: 1 L2 cache: 16 MiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 
  bogomips: 115200 
  Speed: 801 MHz min/max: 800/4900 MHz Core speeds (MHz): 1: 801 2: 800 
  3: 800 4: 800 5: 801 6: 800 7: 800 8: 800 9: 800 10: 800 11: 800 12: 800 
  13: 800 14: 800 15: 800 16: 800 
Graphics:
  Device-1: Intel vendor: ASUSTeK driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.11 driver: loaded: modesetting 
  unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel Graphics (RKL GT1) 
  v: 4.6 Mesa 21.1.5 - kisak-mesa PPA direct render: Yes 
Audio:
  Device-1: Intel vendor: ASUSTeK driver: snd_hda_intel v: kernel 
  bus ID: 00:1f.3 
  Device-2: JMTek LLC. USB PnP Audio Device type: USB 
  driver: hid-generic,snd-usb-audio,usbhid bus ID: 1-7:5 
  Device-3: SteelSeries ApS SteelSeries Arctis 1 Wireless type: USB 
  driver: hid-generic,snd-usb-audio,usbhid bus ID: 1-4:3 
  Sound Server: ALSA v: k5.13.4-051304-generic 
Network:
  Device-1: Intel driver: iwlwifi v: kernel port: 4000 bus ID: 00:14.3 
  IF: wlo1 state: up mac: <filter> 
  Device-2: Intel Ethernet I225-V vendor: ASUSTeK driver: igc v: kernel 
  port: efa0 bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
Bluetooth:
  Device-1: Intel type: USB driver: btusb v: 0.8 bus ID: 1-14:8 
  Report: ID: hci0 state: up running pscan bt-v: 3.0 lmp-v: 5.2 
  address: <filter> 
Drives:
  Local Storage: total: 476.94 GiB used: 52.95 GiB (11.1%) 
  ID-1: /dev/nvme0n1 vendor: Intel model: SSDPEKNW512G8 size: 476.94 GiB 
Partition:
  ID-1: / size: 34.58 GiB used: 11.86 GiB (34.3%) fs: ext4 
  dev: /dev/nvme0n1p6 
  ID-2: /boot/efi size: 256 MiB used: 30.5 MiB (11.9%) fs: vfat 
  dev: /dev/nvme0n1p1 
  ID-3: /home size: 76.88 GiB used: 41.06 GiB (53.4%) fs: ext4 
  dev: /dev/nvme0n1p7 
Swap:
  ID-1: swap-1 type: partition size: 3.73 GiB used: 0 KiB (0.0%) 
  dev: /dev/nvme0n1p5 
Sensors:
  System Temperatures: cpu: 27.8 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 346 Uptime: 25m Memory: 15.4 GiB used: 3.36 GiB (21.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 10.3.0 Packages: 2248 
  Shell: Bash v: 5.1.4 inxi: 3.3.01 
makem@makem-pc:~$

```

---

### Post by MAFoElffen on 2021-07-24
And "No Man's Land" still doesn't  want to work? My goodness, you are on the latest Kernel 5.14 and Mesa 4.6. Your  UHD graphics works with everything else. That Kernel and that Mesa Driver has the latest updates to Vulcan Graphics... for Vulcan Ray Tracing...

It's well time to turn it in as a bug report to Steam and the publisher, CDV Software.

The errors you are getting are a byproduct of using a kernel that is well ahead of the other software in the OS. It seems to boot and work, but something. that were built with earlier kernels are confused, right? If you bring up the Grub menu and boot from another Kernel, you don't have those error messages do you. Right?

Right now, it documented here what you did, so you have a checkpoint where you can roll back to. By purging the Mesa PPA, and uninstalling the very new Ker, then you will be back to normal. 

LOL. You have done more than other's to try to make your's work. Correctly and methodically. About the only other thing I can think of, would be to install the Phoronix Test Suite... There is a test in that Benchmark Suite for Vulcan Ray Tracing that would verify that "that" works on your machine, which would point all that back, specifically on something wrong with the game itself... But I don't know. See... I have high end NVidia, and that test works with mine on Kernel 5.8... But I'm using the NVidia proprietary drivers.

---

### Post by makem2 on 2021-07-24
> **MAFoElffen said:**
> And "No Man's Land" still doesn't  want to work? My goodness, you are on the latest Kernel 5.14 and Mesa 4.6. Your  UHD graphics works with everything else. That Kernel and that Mesa Driver has the latest updates to Vulcan Graphics... for Vulcan Ray Tracing...

It's well time to turn it in as a bug report to Steam and the publisher, CDV Software.

The errors you are getting are a byproduct of using a kernel that is well ahead of the other software in the OS. It seems to boot and work, but something. that were built with earlier kernels are confused, right? If you bring up the Grub menu and boot from another Kernel, you don't have those error messages do you. Right?

Right now, it documented here what you did, so you have a checkpoint where you can roll back to. By purging the Mesa PPA, and uninstalling the very new Ker, then you will be back to normal. 

LOL. You have done more than other's to try to make your's work. Correctly and methodically. About the only other thing I can think of, would be to install the Phoronix Test Suite... There is a test in that Benchmark Suite for Vulcan Ray Tracing that would verify that "that" works on your machine, which would point all that back, specifically on something wrong with the game itself... But I don't know. See... I have high end NVidia, and that test works with mine on Kernel 5.8... But I'm using the NVidia proprietary drivers.

Are you willing to assist with Phoronix Test Suite? I hate leaving stones unturned, is it worth it?.Btw. Its No Man's Sky.

I do have the same error if I use an earlier kernel. The only time I didn't have an error was when I last used Ubuntu 20.04 which was to slow to play but no errors.

snip>
Right now, it documented here what you did, so you have a checkpoint  where you can roll back to. By purging the Mesa PPA, and uninstalling  the very new Ker, then you will be back to normal.
snip>

Roll back to what point? 20.04? Because I think I may have to reinstall 20.04 if/when I get a dedicated GPU and I still can't a) afford and b) not sure which would be best AMD or Nvidia.

You mentioned a bug report to Steam but I tried but gave up:

snip>
New accounts are limited from using all of Steam's community features.  You'll have access to all of Steam's features once you've spent $5.00  USD in the Steam store or added $5.00 USD to your Steam Wallet. Some of  the features that you won't be able to access are: ....................

When you first spend $5 on your account you will have to wait at least 1-2 day.
And do the Steam Quests(Badge) to get the "Steam Community" badge therefore, you also get two levels! 
snip>

I will understand if you think we should just say we had a bliddy good try and it's time to stop and just continue paying for streaming for the time being.

Edit: Did you look at the link to the errors I get when starting xubuntu? Do they have any bearing?

I have installed Phoronix Test Suite, it looks interesting but I am struggling lol.

---

### Post by CatKiller on 2021-07-24
I mean, your initial probem was just your mouse speed, but
> **makem2 said:**
> You mentioned a bug report to Steam but I tried but gave up:

the place to make a bug report about it would be [here](https://github.com/ValveSoftware/Proton/issues/438).

---

### Post by MAFoElffen on 2021-07-24
Sure... Go to [https://www.phoronix-test-suite.com/?k=downloads](https://www.phoronix-test-suite.com/?k=downloads) and downlod the Ubuntu/Debain Package. After it downloads, open the file manager, navigate to the download directory... Right click on the file and open wth the software manager, which will then install it.

Then you have to run the tests from a terminal session in the form ot: 
```
phoronix-test-suite run <test_name>
```
The 3 included tests that would test for Vulkan Ray Tracing are:
```
mafoelffen@ovirt-mgnt-01:~$ phoronix-test-suite list-available-tests | grep -i "vulkan"
pts/geexlab-rt              GeeXLab Vulkan Ray-Tracing Demo        Graphics  
pts/rtiv                         Ray Tracing In Vulkan                               Graphics  
pts/waifu2x-ncnn        Waifu2x-NCNN Vulkan                               Graphics  

```
So an example command to run the first would be:
```
phoronix-test-suite run geexlab-rt
```

No. I mean to get back to basic config of 21.04... LOL "No Man's Land" from "No Man's Sky" = Freudian slip with this adventure...

---

### Post by MAFoElffen on 2021-07-24
> **CatKiller said:**
> I mean, your initial probem was just your mouse speed, but...
When I cam e into this he had a blank screen when he went to start up his game "No Man's Sky"...

---

### Post by CatKiller on 2021-07-24
> **MAFoElffen said:**
> When I cam e into this he had a blank screen when he went to start up his game "No Man's Sky"...
[https://ubuntuforums.org/showthread.php?p=14048766#post14048766](https://ubuntuforums.org/showthread.php?p=14048766#post14048766)
> **makem2 said:**
> I am unable to run No Man's Sky game. The symptoms are very very slow mouse movement making the game unplayable.
OP had this issue and decided to upgrade their kernel. They were shown how to do so on 20.04, but decided to upgrade to 21.04 instead. AFAIK they've never had the game working on 21.04.

---

### Post by MAFoElffen on 2021-07-25
Oh... Okay...

---

### Post by makem2 on 2021-07-25
> **CatKiller said:**
> I mean, your initial probem was just your mouse speed, but

the place to make a bug report about it would be [here]("https://github.com/ValveSoftware/Proton/issues/438").

Thank you, in fact I did report to [email]sfmbugs@valvesoftware.com[/email] but having read about smf, I think this is wrong.

I will use the page to which you point.

---

### Post by makem2 on 2021-07-25
> **MAFoElffen said:**
> Sure... Go to [https://www.phoronix-test-suite.com/?k=downloads](https://www.phoronix-test-suite.com/?k=downloads) and downlod the Ubuntu/Debain Package. After it downloads, open the file manager, navigate to the download directory... Right click on the file and open wth the software manager, which will then install it.

Then you have to run the tests from a terminal session in the form ot: 
```
phoronix-test-suite run <test_name>
```
The 3 included tests that would test for Vulkan Ray Tracing are:
```
mafoelffen@ovirt-mgnt-01:~$ phoronix-test-suite list-available-tests | grep -i "vulkan"
pts/geexlab-rt              GeeXLab Vulkan Ray-Tracing Demo        Graphics  
pts/rtiv                         Ray Tracing In Vulkan                               Graphics  
pts/waifu2x-ncnn        Waifu2x-NCNN Vulkan                               Graphics  

```
So an example command to run the first would be:
```
phoronix-test-suite run geexlab-rt
```

No. I mean to get back to basic config of 21.04... LOL "No Man's Land" from "No Man's Sky" = Freudian slip with this adventure...


```

GeeXLab Vulkan Ray-Tracing Demo 2021.2.18.0:
    pts/geexlab-rt-1.0.1 [Resolution: 1920 x 1080]
    Test 1 of 1
    Estimated Trial Run Count:    3                     
    Estimated Time To Completion: 2 Minutes [11:50 BST] 
        Started Run 1 @ 11:49:40
        The test run did not produce a result.
        Started Run 2 @ 11:49:45
        The test run did not produce a result.
        Started Run 3 @ 11:49:49
        The test run did not produce a result.

     CPU Temperature: 36.00 C   CPU Usage (Summary): 0.25  %  
        Memory Usage: 1828  MB   System Temperature: 27.8  C  
        System Uptime 17    M 

```

Test pts/rtiv (part output below) just goes round in circles: "[PROBLEM] pts/rtiv-1.0.1 is not installed".

```

        Installing Test @ 11:56:59
            The installer exited with a non-zero exit status.
            ERROR: Missing Command: cmake
            LOG: ~/.phoronix-test-suite/installed-tests/pts/rtiv-1.0.1/install-failed.log


    [PROBLEM] pts/rtiv-1.0.1 is not installed. 
    Would you like to stop and install these tests now (Y/n): y
    Evaluating External Test Dependencies ..................................
    Evaluating System Dependencies .........................................

The following dependencies are needed and will be installed: 

- build-essential
- autoconf
- meson
- cmake
- cmake-data
- git-core
- xorg-dev
- mesa-utils
- vulkan-tools
- unzip
- apt-file

This process may take several minutes.
E: Unable to correct problems, you have held broken packages.
Reading package lists...
Building dependency tree...
Reading state information...
build-essential is already the newest version (12.8ubuntu3).
build-essential set to manually installed.
unzip is already the newest version (6.0-26ubuntu1).
unzip set to manually installed.
mesa-utils is already the newest version (8.4.0-1build1).
mesa-utils set to manually installed.
vulkan-tools is already the newest version (1.2.162.0+dfsg1-1).
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libdrm-dev : Depends: libdrm2 (= 2.4.105-3~21.04.1) but 2.4.107+git2107170500.87a68f~oibaf~f is to be installed
              Depends: libdrm-intel1 (= 2.4.105-3~21.04.1) but 2.4.107+git2107170500.87a68f~oibaf~f is to be installed
              Depends: libdrm-radeon1 (= 2.4.105-3~21.04.1) but 2.4.107+git2107170500.87a68f~oibaf~f is to be installed
              Depends: libdrm-nouveau2 (= 2.4.105-3~21.04.1) but 2.4.107+git2107170500.87a68f~oibaf~f is to be installed
              Depends: libdrm-amdgpu1 (= 2.4.105-3~21.04.1) but 2.4.107+git2107170500.87a68f~oibaf~f is to be installed

There are dependencies still missing from the system:
- C/C++ Compiler Toolchain
- CMake
- Git
- Meson Build System
- X.Org Development

1: Ignore missing dependencies and proceed with installation.
2: Skip installing the tests with missing dependencies.
3: Re-attempt to install the missing dependencies.
4: Quit the current Phoronix Test Suite process.
Missing dependencies action: 3

The following dependencies are needed and will be installed: 

- build-essential
- autoconf
- meson
- cmake
- cmake-data
- git-core
- xorg-dev

This process may take several minutes.
E: Unable to correct problems, you have held broken packages.
Reading package lists...
Building dependency tree...
Reading state information...
build-essential is already the newest version (12.8ubuntu3).
build-essential set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libdrm-dev : Depends: libdrm2 (= 2.4.105-3~21.04.1) but 2.4.107+git2107170500.87a68f~oibaf~f is to be installed
              Depends: libdrm-intel1 (= 2.4.105-3~21.04.1) but 2.4.107+git2107170500.87a68f~oibaf~f is to be installed
              Depends: libdrm-radeon1 (= 2.4.105-3~21.04.1) but 2.4.107+git2107170500.87a68f~oibaf~f is to be installed
              Depends: libdrm-nouveau2 (= 2.4.105-3~21.04.1) but 2.4.107+git2107170500.87a68f~oibaf~f is to be installed
              Depends: libdrm-amdgpu1 (= 2.4.105-3~21.04.1) but 2.4.107+git2107170500.87a68f~oibaf~f is to be installed
    To Install:    pts/rtiv-1.0.1

    Determining File Requirements ..........................................
    Searching Download Caches ..............................................

    1 Test To Install
        3500MB Of Disk Space Is Needed
        4 Seconds Estimated Install Time

    pts/rtiv-1.0.1:
        Test Installation 1 of 1
        2 Files Needed [218 MB / 1 Minute]
        File Found: RayTracingInVulkan-r6.tar.gz                   [19.26MB]
        File Found: vulkansdk-linux-x86_64-1.2.162.1.tar.gz          [199MB]
        Approximate Install Size: 3500 MB
        Estimated Install Time: 4 Seconds
        Installing Test @ 11:57:17
            The installer exited with a non-zero exit status.
            ERROR: Missing Command: cmake
            LOG: ~/.phoronix-test-suite/installed-tests/pts/rtiv-1.0.1/install-failed.log


    [PROBLEM] pts/rtiv-1.0.1 is not installed. 
    Would you like to stop and install these tests now (Y/n):

```

```

phoronix-test-suite run pts/waifu2x-ncnn

    [PROBLEM] pts/waifu2x-ncnn-1.0.0 is not installed. 
    Would you like to stop and install these tests now (Y/n):

```

I think it is time to stop.

I will keep 21.04, see what happens when I do get some dedicated GPU and take it from there. However I am sorely tempted to go back to 20.04 and start afresh, knowing how to upgrade the kernel.

Thank you for all your help, it has been very enlightening but it seems I am flogging a dead horse at the moment.

Thank you too @CatKiller, yes, I did make a wrong decision through lack of knowledge, but I have learned.

---

### Post by makem2 on 2021-07-25
Well the horse is dead. I decided to revert to a fresh install of 20.04 as I had a separate /home and backups of everything anyway.

However (there is always a 'however' I find), the install was using kernel 5.8.0.63.71 so I decided to install 5.13.4 being one below the latest. It installed with errors and left me with 5.8.0.63.71. Fine, maybe it was too big a jump?

So I tried 5.11.0 and this worked fine and is where I currently am.

I then went for 5.13.4 again and this also failed leaving me at 5.11.0

5.8.0 to 5.11.0 is 3 jumps and it worked. 5.11.0 to 5.13.4 is two jumps and it did not.

I tried a smaller jump, 5.11.0 to 5.12.10 but again this failed with the same error: 

```

dpkg: dependency problems prevent configuration of linux-headers-5.12.10-051210-generic: linux-headers-5.12.10-051210-generic depends on libc6 (>= 2.33); however Version of lib6:amd64 on system is 2.31-0ubuntu9.2

```

So, it is time to ask for help once again and risk admonishment. But I  am a trier and hate being  beaten especially when it could have been  avoided maybe if I had updated the kernel before 21.04. I take the risk :smile:

I am unable to find how to correct this by updating libc6.

---

### Post by CatKiller on 2021-07-25
> **makem2 said:**
> Thank you too @CatKiller, yes, I did make a wrong decision through lack of knowledge, but I have learned.
That's how we all learn; no biggie.

---

### Post by CatKiller on 2021-07-25
> **makem2 said:**
> I am unable to find how to correct this by updating libc6.
Oh, I did hear something about this. libc is so fundamental to a system that you don't want to be messing with it. Having newer kernels that can't be built on the latest LTS is at least against the spirit of policy. I don't know for sure that they'll fix it, but I hope they do. Until they do you can use the latest before that change, and it will definitely be sorted out when the 21.10 kernel is working its way through the HWE channel.

---

### Post by makem2 on 2021-07-25
> **CatKiller said:**
> Oh, I did hear something about this. libc is so fundamental to a system that you don't want to be messing with it. Having newer kernels that can't be built on the latest LTS is at least against the spirit of policy. I don't know for sure that they'll fix it, but I hope they do. Until they do you can use the latest before that change, and it will definitely be sorted out when the 21.10 kernel is working its way through the HWE channel.

Thanks for bearing with me.

There is a suitable version available I find:

[https://packages.ubuntu.com/search?keywords=libc6](https://packages.ubuntu.com/search?keywords=libc6)

However as I know it is an important package I have left it alone.

As a point of interest, why are there so many kernels available? Is it because they increment one by one?

---

### Post by MAFoElffen on 2021-07-25
I built that vrtx Test Suite in a VM... Yes, is very resource intensive, if you don't have at least 8GB of memory, give it a very big swap file to use. If you read the build log, it would have said that it ran out of memory in the RAM and the Swap file, before it crashes... I gave it 16GB and 8 cores, and it had all 8 cores pegged for 18 minutes straight compiling it.

Why, if it worked in 20.04 and Kernel 5.8 , are you using newer Kernels again? Yes to 5.13.x is a big jump. 

I have Kernel 5.13 running on 20.04 in a VM, but that's not saying that other things didn't have to be changed also. 

Did you read the details posted on Kisak's PPA? Yes, he talked about installing newer Mesa on older Versions of Ubuntu, but he also talked about newer versions. There are changes to Mesa (and Libc) because of changes and inclusions of newer features within newer Kernels. Things like libclc are then obsolete and replaced by other things, like llvm, which then have to be added in it's place. Then there are updates to libdrm... That is why his PPA has all those in that PPA, because they are dependent on each other...  Yes, there are going to be dependency changes that affect each other and cascade...

Now again, why do you think you need a bleeding edge Kernel if everything worked for you with Kernel 5.8? Is there something there, that you can't do, or your want to do better? Because, again, your rpoblem with No Man's Sky and Graphic's started when you upgraded the release to 21.04 and were running it's newer Kernel's in that release right?

But that is only how a newer Kernel relates to Mesa. I'm sure there are other things. What he also said there (and implies), is that a future LTS version, (I'm thinking he is implying at 22.04), that these changes will be included, and that PPA will be frozen and go away.

---

### Post by makem2 on 2021-07-25
> **MAFoElffen said:**
> I built that vrtx Test Suite in a VM... Yes, is very resource intensive, if you don't have at least 8GB of memory, give it a very big swap file to use. If you read the build log, it would have said that it ran out of memory in the RAM and the Swap file, before it crashes... I gave it 16GB and 8 cores, and it had all 8 cores pegged for 18 minutes straight compiling it.

Why, if it worked in 20.04 and Kernel 5.8 , are you using newer Kernels again? Yes to 5.13.x is a big jump. 

I have Kernel 5.13 running on 20.04 in a VM, but that's not saying that other things didn't have to be changed also. 

Did you read the details posted on Kisak's PPA? Yes, he talked about installing newer Mesa on older Versions of Ubuntu, but he also talked about newer versions. There are changes to Mesa (and Libc) because of changes and inclusions of newer features within newer Kernels. Things like libclc are then obsolete and replaced by other things, like llvm, which then have to be added in it's place. Then there are updates to libdrm... That is why his PPA has all those in that PPA, because they are dependent on each other...  Yes, there are going to be dependency changes that affect each other and cascade...

Now again, why do you think you need a bleeding edge Kernel if everything worked for you with Kernel 5.8? Is there something there, that you can't do, or your want to do better? Because, again, your rpoblem with No Man's Sky and Graphic's started when you upgraded the release to 21.04 and were running it's newer Kernel's in that release right?

But that is only how a newer Kernel relates to Mesa. I'm sure there are other things. What he also said there (and implies), is that a future LTS version, (I'm thinking he is implying at 22.04), that these changes will be included, and that PPA will be frozen and go away.

I attempted the kernel update because of your post #12, thinking it was the way to go to improve what I had already had. I was unaware that other changes would/may be needed but I am learning even if I do so in a 3 forward 2 back manner :)


In fact when I did run NMS before the kernel upgrade attempt I had Vulkan errors which I had had some while before I 'suddenly' found it did work albeit slowly. I assume changes were made during updates to the system which made it work.

I know it is not going to ever work successfully now and I must wait for a new GPU. I/we have done all possible.

Edit: Intel's i915 driver is built into the kernel

---

