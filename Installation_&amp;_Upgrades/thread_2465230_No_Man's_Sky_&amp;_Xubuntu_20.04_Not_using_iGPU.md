---
title: "No Man's Sky &amp; Xubuntu 20.04: Not using iGPU?"
date: 2021-07-26
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2021-07-26
I have been trying to get this game working in 20.04 and 21.04, eventually re-installing 20.04. I reported this to ValveSoftware/Proton and received this reply:

snip>

Hello, looking at your system information, your system is not configured to use your GPU at all. Instead, llvmpipe and lavapipe are being used for software rendering on the CPU, which is not ideal at all. It looks like all the needed drivers are installed, but something is broken or misconfigured system-wide.

From your system information:

            "vulkan: No DRI3 support detected - required for presentation",
            "Note: you can probably enable DRI3 in your Xorg config"
[...]
            "libGL: screen 0 does not appear to be DRI2 capable",

These hint that something major has been disabled. Blind guess, maybe the system was booted with modeset=0 as a kernel option?

snip>

I am unable to deal with that without assistance can I ask for help please?

This is the system information as received from the Steam program and what I posted toValveSoftware/Proton:

[https://paste.ubuntu.com/p/tw75N22CYf/](https://paste.ubuntu.com/p/tw75N22CYf/)

```

Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "SwapBuffersWait" "0"
   Option      "DRI" "3"
EndSection

```

If I added this to the /usr/share/doc/xserver-xorg-video-intel/ file would it enable DRI3?

The existing /usr/share/doc/xserver-xorg-video-intel/xorg.conf is:

```

Section "Device"
        Identifier "Intel"
        Driver "intel"
#       Option "AccelMethod" "uxa"
EndSection

```

---

### Post by CatKiller on 2021-07-26
From a quick search I did find [this](https://www.phoronix.com/scan.php?page=article&item=intel-rkl-linux&num=2):

> With Rocket Lake, the Linux support is all in order once again. But there is one sort of exception: the Gen12 Xe Graphics might not be working out-of-the-box depending upon your kernel. When I first booted up the Rocket Lake test system with Linux 5.12 + Mesa Git previously already installed, I was startled to find accelerated graphics not working... LLVMpipe was at play. This was a big surprise given Intel's track record and Gen12 Linux graphics support being out for a while now. Checking dmesg though quickly revealed that the PCI ID was still hidden behind the early support flag.

Re-booting the system while having "i915.force_probe=4c8a" avoided the issue and accelerated graphics were quickly working. All was well on both the i5-11600K and i9-11900K processors when booting the stable Linux kernel with the force_probe option. While the patch to remove Rocket Lake from requiring the force probe has been on the mailing list for several months, as of writing it hasn't landed in the stable upstream Linux kernel. At the moment that is queued into DRM-Next ahead of Linux 5.13... We'll see if one of the "fixes" pull request soon removes this restriction. Some distribution kernels including the likes of Ubuntu are already carrying the patch for providing the Rocket Lake support out-of-the-box.

So long story short, the Xe Graphics are ready to go for Linux users on sufficiently new kernels/Mesa, but you may end up needing to boot with the "i915.force_probe=4c8a" option in order to enable it for the time being. 

I don't know if that points you in the right direction. The Intel systems I've used haven't needed any fiddling, so I don't have any experience.

---

### Post by makem2 on 2021-07-26
> **CatKiller said:**
> From a quick search I did find [this]("https://www.phoronix.com/scan.php?page=article&item=intel-rkl-linux&num=2"):

 

I don't know if that points you in the right direction. The Intel systems I've used haven't needed any fiddling, so I don't have any experience.

And I don't have any idea about "i915.force_probe=4c8a" so I have no idea where it points I'm afraid.

I have had another reply from ValveSoftware/Proton which says that NMS will never run on the hardware I have and may not run on Windows even. That the game needs a dedicated GPU.

However, it has run on Ubuntu 20.04, slow indeed but without any graphics problem in appearance. On Windows 10 it also runs, much quicker than on 20.04 but still a little slow.

I am sure they are right and to get the games running at its best it does need a dedicated GPU. However, I am trying to get it to run once again on 20.04 with a view to having it working with a new GPU in time. I should have left well alone and not tried 21.04.

Edit: This web page details how to use "i915.force_probe=4c8a"

[https://www.reddit.com/r/linuxhardware/comments/ms28mk/getting_any_linux_distro_to_work_using_latest/](https://www.reddit.com/r/linuxhardware/comments/ms28mk/getting_any_linux_distro_to_work_using_latest/)

---

### Post by CatKiller on 2021-07-26
> **makem2 said:**
> However, it has run on Ubuntu 20.04, slow indeed but without any graphics problem in appearance. 
And from your version string (5.11.0-051100-generic) it looks like you've got your kernel from... somewhere... whereas when you had it working you were just using a standard Ubuntu kernel. Which makes sense, since Phoronix implies that Ubuntu apply the patches that enable it to work out of the box. The kernel version on my 20.04 (since I'm running hwe-edge) is 5.11.0-25(-lowlatency, but that part doesn't matter).

---

### Post by MAFoElffen on 2021-07-26
catkiller:

That was when he installed a Newer Kernel from Mainline and updated his Mesa from the Kisak PPA...He had thata both installed, following leads that those worked for NMS and Intel UHD 730... But he was missing the piece you found (good job!) on the kernel boot line... he knows how to do all that now from the last two of his threads... Except how to test with with temporarily with adding that as a boot param from editing his Grub boot menu to test it...

I'm just on a break at the moment... CatKiller, could you please talk him through that, for him to see? Either that, or I could in about 4 hours...

---

### Post by makem2 on 2021-07-26
My current kernel is:

```

makem@makems-TUF:~$ uname -r
5.11.0-051100-generic
makem@makems-TUF:~$

```

My grub file /etc/default/grub is:

```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.force_probe=4c8a"
GRUB_CMDLINE_LINUX=""

```

Further info:

```

makem@makems-TUF:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 4c8a (rev 04)
makem@makems-TUF:~$ find /dev -group video
/dev/fb0
/dev/dri/card0
makem@makems-TUF:~$ glxinfo | grep -i vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
    Vendor: Intel (0x8086)
OpenGL vendor string: Intel
makem@makems-TUF:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-5.11.0-051100-generic root=UUID=a018cecd-ae3a-4e56-8e59-a457c8dd43ab ro quiet splash i915.force_probe=4c8a vt.handoff=7
makem@makems-TUF:~$ find /etc/modprobe.d/
/etc/modprobe.d/
/etc/modprobe.d/dkms.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/intel-microcode-blacklist.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/amd64-microcode-blacklist.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-framebuffer.conf
makem@makems-TUF:~$ cat /etc/modprobe.d/*kms*
# modprobe information used for DKMS modules
#
# This is a stub file, should be edited when needed,
# used by default by DKMS.
makem@makems-TUF:~$ ls /etc/X11/xorg.conf
ls: cannot access '/etc/X11/xorg.conf': No such file or directory
makem@makems-TUF:~$ glxinfo | grep -i "vendor\|rendering"
direct rendering: Yes
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
    Vendor: Intel (0x8086)
OpenGL vendor string: Intel
makem@makems-TUF:~$ grep LoadModule /var/log/Xorg.0.log
[     4.098] (II) LoadModule: "glx"
[     4.105] (II) LoadModule: "modesetting"
[     4.106] (II) LoadModule: "fbdev"
[     4.106] (II) LoadModule: "vesa"
[     4.131] (II) LoadModule: "fbdevhw"
[     4.131] (II) LoadModule: "glamoregl"
[     4.276] (II) LoadModule: "fb"
[     4.471] (II) LoadModule: "libinput"
makem@makems-TUF:~$ ls /usr/share/doc/xserver-xorg-video-intel/
changelog.Debian.gz  copyright  NEWS.gz  README  README.Debian  xorg.conf
makem@makems-TUF:~$

```

xorg.conf:

```

Section "Device"
    Identifier "Intel"
    Driver "intel"
#    Option "AccelMethod" "uxa"
EndSection

```

```

makem@makems-TUF:~$ lspci -k | grep -EA3 'VGA|3D|Display'
00:02.0 VGA compatible controller: Intel Corporation Device 4c8a (rev 04)
    DeviceName: Onboard - Video
    Subsystem: ASUSTeK Computer Inc. Device 8694
    Kernel driver in use: i915
makem@makems-TUF:~$

```

vulkaninfo | less result:
```

===========
VULKAN INFO
===========

Vulkan Instance Version: 1.2.70

ERROR: [Loader Message] Code 0 : /usr/lib/i386-linux-gnu/libvulkan_intel.so: wrong ELF class: ELFCLASS32
ERROR: [Loader Message] Code 0 : /usr/lib/i386-linux-gnu/libvulkan_lvp.so: wrong ELF class: ELFCLASS32
ERROR: [Loader Message] Code 0 : /usr/lib/i386-linux-gnu/libvulkan_radeon.so: wrong ELF class: ELFCLASS32
ERROR: [Loader Message] Code 0 : /usr/lib/i386-linux-gnu/libvulkan_intel.so: wrong ELF class: ELFCLASS32
ERROR: [Loader Message] Code 0 : /usr/lib/i386-linux-gnu/libvulkan_lvp.so: wrong ELF class: ELFCLASS32
ERROR: [Loader Message] Code 0 : /usr/lib/i386-linux-gnu/libvulkan_radeon.so: wrong ELF class: ELFCLASS32








Instance Extensions:
====================
Instance Extensions     count = 18

```

vt.handoff=7 - what is that for in grub?

---

### Post by CatKiller on 2021-07-26
> **makem2 said:**
> My grub file /etc/default/grub is:

```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.force_probe=4c8a"
GRUB_CMDLINE_LINUX=""

```
Cool. Once you've saved that change to the file, you'll need to run ```
sudo update-grub
``` to apply the change in configuration to the files that your machine uses to boot. Then reboot to test.

Should it all go pear-shaped, you can edit the boot parameters from the Grub menu. Just in case you're unable to boot otherwise.

---

### Post by makem2 on 2021-07-26
> **CatKiller said:**
> And from your version string (5.11.0-051100-generic) it looks like you've got your kernel from... somewhere... whereas when you had it working you were just using a standard Ubuntu kernel. Which makes sense, since Phoronix implies that Ubuntu apply the patches that enable it to work out of the box. The kernel version on my 20.04 (since I'm running hwe-edge) is 5.11.0-25(-lowlatency, but that part doesn't matter).

Are you suggesting that maybe I should go back to kernel 5.8.0.63.71 which is still installed if 5.11 is not working and wait for an update coming through as it may  have done previously?

---

### Post by makem2 on 2021-07-26
> **CatKiller said:**
> Cool. Once you've saved that change to the file, you'll need to run ```
sudo update-grub
``` to apply the change in configuration to the files that your machine uses to boot. Then reboot to test.

Should it all go pear-shaped, you can edit the boot parameters from the Grub menu. Just in case you're unable to boot otherwise.

Yes I was aware that I needed to run update-grub and did so to achieve the result posted.

I did reboot and it did not go pear shaped :D

NMS gave me a black screen though without errors - been there before with 21.04.

---

### Post by CatKiller on 2021-07-26
> **makem2 said:**
> Are you suggesting that maybe I should go back to kernel 5.8.0.63.71 which is still installed if 5.11 is not working and wait for an update coming through as it may  have done previously?

The 5.8 branch was working in ways that the others you've installed haven't been, so that seems desirable. Then maybe trying the hwe and hwe-edge branches, since they'll have all of Ubuntu's patches installed. 

> **makem2 said:**
> Yes I was aware that I needed to run update-grub and did so to achieve the result posted. 
Yay! 
> I did reboot and it did not go pear shaped :D 
Yay! 
> NMS gave me a black screen though without errors - been there before with 21.04.
Boo...

---

### Post by makem2 on 2021-07-26
> **CatKiller said:**
> The 5.8 branch was working in ways that the others you've installed haven't been, so that seems desirable. Then maybe trying the hwe and hwe-edge branches, since they'll have all of Ubuntu's patches installed. 

 
Yay! 
 
Yay! 

Boo...

LOL

I think it may be good to see what @MAFoElffen has to say first. I may wait up for him! I am currently expanding my /home partition as I was not used to the size needed when playing games.

I looked at this page about Vulkan and without changing anything or adding anything the game Dota2 played fine with Vulkan settings.

But still I got the black page with NMS :(

[URL="https://linuxconfig.org/install-and-test-vulkan-on-linux"]https://linuxconfig.org/install-and-test-vulkan-on-linux

[/URL]

---

### Post by makem2 on 2021-07-26
Has this been overlooked?

"These hint that something major has been disabled. Blind guess, maybe the system was booted with modeset=0 as a kernel option?"

From #1

From that post it says I was using  llvmpipe but since then I am now using Intel Mesa:

```

Video Card:
    Driver:  Intel Mesa Intel(R) Graphics (RKL GT1)
    Driver Version:  4.6 (Compatibility Profile) Mesa 21.1.5 - kisak-mesa PPA
    OpenGL Version: 4.6
    Desktop Color Depth: 24 bits per pixel
    Monitor Refresh Rate: 60 Hz
    VendorID:  0x8086
    DeviceID:  0x4c8a
    Revision Not Detected
    Number of Monitors:  1
    Number of Logical Video Cards:  1
    Primary Display Resolution:  1920 x 1080
    Desktop Resolution: 1920 x 1080
    Primary Display Size: 20.75" x 11.65" (23.78" diag)
                                            52.7cm x 29.6cm (60.4cm diag)
    Primary VRAM Not Detected

```

However I cannot determine anything at the moment about:

"vulkan: No DRI3 support detected - required for presentation",
            "Note: you can probably enable DRI3 in your Xorg config"

But DRI3 is now mentioned many times in Steam settings.

---

### Post by MAFoElffen on 2021-07-27
EDITTED: Somehow got a double post(???) And now getting a database error trying to edit it...

---

### Post by MAFoElffen on 2021-07-27
Here now. been dev testing visualized gpu'sLet me catch up to where you are...

You tried that boot but... You are now back to kernel 5.8 and it's associated mesa. You heard me before, and in the last couple posts, CatKiller tell you that for the newer, in-kernel graphics drivers, you would need a kerenl of 5.12 or newr, ans the newer mesa-drivers from Kisak's PAA... AND try that boot parameter...

Yes. DRM should be enabled for Vulkan and any 3D acceleration... But important for you to note that DRM is already enabled by default on the Intel i915 driver for your GPU. I remember you being confused about the term i915... That is actually "the Intel Graphics driver", written by Intel.

If you are curious, your conf file is at /etc/modprobe.d/i915.conf... It should be fine. if it has an xorg.con fi;e (which Intel usually doesn't need one... then that currnently would be at /etc/X11/xorg.conf.d/20-intel.conf...

What is more important to you is the kernel version and mesa... Mesa has the DRM which relates with your graphics driver, which is in the Kernel... So if you monitor that when you are making chnages and after your tests, then that will tell you the why's of your black screen. Such as this right after boot...
```
dmesg | grep -i drm
sudo journalctl -b --grep='i915'
```
And check those again after you test something...

One more
```
sudo journalctl -b ''grep='drm'
```
should show when the drm.service was loaded...

**** Important note about your last post... nomodest or a modeset line should not be in your kernel line... That will turn off that driver.

---

### Post by CatKiller on 2021-07-27
> **makem2 said:**
> Has this been overlooked?

"These hint that something major has been disabled. Blind guess, maybe the system was booted with modeset=0 as a kernel option?" 

Nope. They were asking you if you'd put it there. That's a boot parameter, the same as the one you later added, and you had to look up how to add boot parameters so you couldn't have had it before. You also showed us your boot configuration and that wasn't there. 

>  From that post it says I was using  llvmpipe but since then I am now using Intel Mesa: 

Yes, now that you've told the kernel that it's OK to use your iGPU, it's using your GPU OK. 

>  However I cannot determine anything at the moment about:

"vulkan: No DRI3 support detected - required for presentation",
            "Note: you can probably enable DRI3 in your Xorg config"

But DRI3 is now mentioned many times in Steam settings.
You were using software rendering before. Now you aren't.

I don't recall whether with your 21.04 experiment you did an upgrade or a fresh install. If the latter, you'd have also had to reinstall Steam, which means you'd have gone back to default settings for some things. In particular, it would have likely changed which version of Proton you were using. You'd definitely have done a fresh install to now be on 20.04. Now that you seem to be using your GPU, you can try again to get the game working. You can pick different Proton versions from the dropdown box on the game's Properties page.

---

### Post by makem2 on 2021-07-27
> **MAFoElffen said:**
> Here now. been dev testing visualized gpu'sLet me catch up to where you are...

You tried that boot but... You are now back to kernel 5.8 and it's associated mesa. You heard me before, and in the last couple posts, CatKiller tell you that for the newer, in-kernel graphics drivers, you would need a kerenl of 5.12 or newr, ans the newer mesa-drivers from Kisak's PAA... AND try that boot parameter...

Yes. DRM should be enabled for Vulkan and any 3D acceleration... But important for you to note that DRM is already enabled by default on the Intel i915 driver for your GPU. I remember you being confused about the term i915... That is actually "the Intel Graphics driver", written by Intel.

If you are curious, your conf file is at /etc/modprobe.d/i915.conf... It should be fine. if it has an xorg.con fi;e (which Intel usually doesn't need one... then that currnently would be at /etc/X11/xorg.conf.d/20-intel.conf...

What is more important to you is the kernel version and mesa... Mesa has the DRM which relates with your graphics driver, which is in the Kernel... So if you monitor that when you are making chnages and after your tests, then that will tell you the why's of your black screen. Such as this right after boot...
```
dmesg | grep -i drm
sudo journalctl -b --grep='i915'
```
And check those again after you test something...

One more
```
sudo journalctl -b ''grep='drm'
```
should show when the drm.service was loaded...

My xorg.conf is at
/usr/share/doc/xserver-xorg-video-intel/ (contents in my previous posts above)

the /etc/modprobe.d/i915.conf does not exist

the /etc/X11/xorg.conf.d/20-intel.conf does not exist

Upgrading the kernel to 12 or I think, any above where I am now always creates an error message which I have previously posted:

".........linux headers......depends on lib6 (>= 2.33); however version of lib6:amd64 on system is 2.31-0ubuntu9.2"

```

sudo nano /var/lib/dkms/openrazer-driver/3.0.1/build/make.log

```

Output of make.log:

make -C /lib/modules/5.12.15-051215-generic/build M=/var/lib/dkms/openrazer-dri>
make[1]: Entering directory '/usr/src/linux-headers-5.12.15-051215-generic'
  CC [M]  /var/lib/dkms/openrazer-driver/3.0.1/build/driver/razerkbd_driver.o
scripts/basic/fixdep: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not>
make[2]: *** [scripts/Makefile.build:271: /var/lib/dkms/openrazer-driver/3.0.1/>
make[2]: *** Deleting file '/var/lib/dkms/openrazer-driver/3.0.1/build/driver/r>
make[1]: *** [Makefile:1865: /var/lib/dkms/openrazer-driver/3.0.1/build/driver]>
make[1]: Leaving directory '/usr/src/linux-headers-5.12.15-051215-generic'
make: *** [Makefile:25: driver] Error 2

I do not know how to post the output of the mainline installer but it does say consult that log.

I also don't know if the errors can be ignored as it does say the kernel is installed.

CatKiller mentioned:

"Maybe trying the hwe and hwe-edge branches, since they'll have all of Ubuntu's patches installed".

I removed that kernel install.

---

### Post by makem2 on 2021-07-27
I have not made any change, however, immediately after re-boot:

```

makem@makems-TUF:~$ sudo dmesg | grep -i drm
[sudo] password for makem: 
[    1.361701] systemd[1]: Starting Load Kernel Module drm...
[    1.373430] systemd[1]: modprobe@drm.service: Succeeded.
[    1.373568] systemd[1]: Finished Load Kernel Module drm.
[    1.704491] fb0: switching to inteldrmfb from EFI VGA
[    1.705776] i915 0000:00:02.0: [drm] Couldn't get system memory bandwidth
[    1.707967] i915 0000:00:02.0: [drm] Finished loading DMC firmware i915/rkl_dmc_ver2_02.bin (v2.2)
[    1.733269] [drm] Initialized i915 1.6.0 20201103 for 0000:00:02.0 on minor 0
[    1.761179] fbcon: i915drmfb (fb0) is primary device
[    1.819890] i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer device
makem@makems-TUF:~$

```

sudo journalctl -b --grep='i915'

Was not easily pasted here so:

```

makem@makems-TUF:~$ sudo journalctl -b | grep i915
Jul 27 12:31:58 makems-TUF kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-5.11.0-051100-generic root=UUID=a018cecd-ae3a-4e56-8e59-a457c8dd43ab ro quiet splash i915.force_probe=4c8a vt.handoff=7
Jul 27 12:31:58 makems-TUF kernel: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.11.0-051100-generic root=UUID=a018cecd-ae3a-4e56-8e59-a457c8dd43ab ro quiet splash i915.force_probe=4c8a vt.handoff=7
Jul 27 12:31:58 makems-TUF kernel: i915 0000:00:02.0: vgaarb: deactivate vga console
Jul 27 12:31:58 makems-TUF kernel: i915 0000:00:02.0: [drm] Couldn't get system memory bandwidth
Jul 27 12:31:58 makems-TUF kernel: i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jul 27 12:31:58 makems-TUF kernel: mei_hdcp 0000:00:16.0-b638ab7e-94e2-4ea2-a552-d1c54b627f04: bound 0000:00:02.0 (ops i915_hdcp_component_ops [i915])
Jul 27 12:31:58 makems-TUF kernel: i915 0000:00:02.0: [drm] Finished loading DMC firmware i915/rkl_dmc_ver2_02.bin (v2.2)
Jul 27 12:31:58 makems-TUF kernel: [drm] Initialized i915 1.6.0 20201103 for 0000:00:02.0 on minor 0
Jul 27 12:31:58 makems-TUF kernel: snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
Jul 27 12:31:58 makems-TUF kernel: fbcon: i915drmfb (fb0) is primary device
Jul 27 12:31:58 makems-TUF kernel: i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer device
Jul 27 12:33:07 makems-TUF sudo[2284]:    makem : TTY=pts/0 ; PWD=/home/makem ; USER=root ; COMMAND=/usr/bin/journalctl -b --grep=i915
Jul 27 12:37:21 makems-TUF sudo[2337]:    makem : TTY=pts/0 ; PWD=/home/makem ; USER=root ; COMMAND=/usr/bin/journalctl -b --grep=i915
makem@makems-TUF:~$

```

```

makem@makems-TUF:~$ sudo journalctl -b ''grep='drm'
Failed to add match 'grep=drm': Invalid argument
makem@makems-TUF:~$ sudo journalctl -b | grep drm
Jul 27 12:31:58 makems-TUF systemd[1]: Starting Load Kernel Module drm...
Jul 27 12:31:58 makems-TUF systemd[1]: modprobe@drm.service: Succeeded.
Jul 27 12:31:58 makems-TUF systemd[1]: Finished Load Kernel Module drm.
Jul 27 12:31:58 makems-TUF kernel: fb0: switching to inteldrmfb from EFI VGA
Jul 27 12:31:58 makems-TUF kernel: i915 0000:00:02.0: [drm] Couldn't get system memory bandwidth
Jul 27 12:31:58 makems-TUF kernel: i915 0000:00:02.0: [drm] Finished loading DMC firmware i915/rkl_dmc_ver2_02.bin (v2.2)
Jul 27 12:31:58 makems-TUF kernel: [drm] Initialized i915 1.6.0 20201103 for 0000:00:02.0 on minor 0
Jul 27 12:31:58 makems-TUF kernel: fbcon: i915drmfb (fb0) is primary device
Jul 27 12:31:58 makems-TUF kernel: i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer device
Jul 27 12:32:00 makems-TUF systemd[1]: Condition check resulted in Load Kernel Module drm being skipped.
Jul 27 12:39:13 makems-TUF sudo[2342]:    makem : TTY=pts/0 ; PWD=/home/makem ; USER=root ; COMMAND=/usr/bin/journalctl -b grep=drm
Jul 27 12:45:53 makems-TUF sudo[2363]:    makem : TTY=pts/0 ; PWD=/home/makem ; USER=root ; COMMAND=/usr/bin/journalctl -b grep=drm
Jul 27 12:46:23 makems-TUF sudo[2365]:    makem : TTY=pts/0 ; PWD=/home/makem ; USER=root ; COMMAND=/usr/bin/journalctl -b grep=drm
makem@makems-TUF:~$ 

```

Edit: It may be worth reading the last post from kisak-valve which says:

snip>
The section you've highlighted says that the Intel GPU is now  available along with lavapipe and the GPU side of the Intel chip is the  default, which is an improvement. That does count as having a  Vulkan-capable GPU available. That said, it does sound like the game is not tested (by the game's devs) against Intel-only systems.
snip>

[URL="https://github.com/ValveSoftware/Proton/issues/438"]https://github.com/ValveSoftware/Proton/issues/438

[/URL]

---

### Post by MAFoElffen on 2021-07-27
I see everything looking  a bit okay on dkms... I mean, there are a few things there that is causing me to research further to see it they are problems for you or not, but nothing real obvious that is hitting me over the head yet. You know your own CPU/GPU... What Gen iCore is it? I could go back and look through your posts, but easier to just ask you...

That is, that I didn't see problems about that, but then I just noticed that you said "openrazer" having problems building in it's "make" with libc6 dependency problems...I just caught what you were saying with that...And that "that" was preventing you from doing a lot of things. Because you keep getting that error.

Do you have a "Razor" keyboard and/or mouse? And that jog's my memory that you were having mouse problems... Please tell us more about this...

EDIT: When I tested Mainline Kernels for you and installed the most current Kernel (5.13) to test for you, adding it to a 20.04 VM, I didn't have any OpenRazor module... On Lib6... upgrading it to 2.33... that would be possible, but it is a mess to do manually, because of it's cascading dependencies above and below. It doesn't get to that version until 21.04 Hersute Hippo. (That is not a recommendation for you to upgrade releases just for you to do that. Just saying...)

Does it give you that same OpenRazor error message if you only try to add Kernel 5.12.0? Or do you get that message when you try to go newer than that?

I have "Razor" keyboard, mouses, game pad, and their RGB mouse pad in storage...But I haven't used them since I hand-built my own programmable mechanical gaming keyboard and game pad.

(I need to get back to testing. Will check this later.)

---

### Post by makem2 on 2021-07-27
> **MAFoElffen said:**
> I see everything looking  a bit okay on dkms... I mean, there are a few things there that is causing me to research further to see it they are problems for you or not, but nothing real obvious that is hitting me over the head yet. You know your own CPU/GPU... What Gen iCore is it? I could go back and look through your posts, but easier to just ask you...

That is, that I didn't see problems about that, but then I just noticed that you said "openrazer" having problems building in it's "make" with libc6 dependency problems...I just caught what you were saying with that...And that "that" was preventing you from doing a lot of things. Because you keep getting that error.

Do you have a "Razor" keyboard and/or mouse? And that jog's my memory that you were having mouse problems... Please tell us more about this...

EDIT: When I tested Mainline Kernels for you and installed the most current Kernel (5.13) to test for you, adding it to a 20.04 VM, I didn't have any OpenRazor module... On Lib6... upgrading it to 2.33... that would be possible, but it is a mess to do manually, because of it's cascading dependencies above and below. It doesn't get to that version until 21.04 Hersute Hippo. (That is not a recommendation for you to upgrade releases just for you to do that. Just saying...)

Does it give you that same OpenRazor error message if you only try to add Kernel 5.12.0? Or do you get that message when you try to go newer than that?

I have "Razor" keyboard, mouses, game pad, and their RGB mouse pad in storage...But I haven't used them since I hand-built my own programmable mechanical gaming keyboard and game pad.

Intel® CoreTM i7 Eight Core Processor i7-11700K (3.6GHz) 16MB Cache

I do have a Razer keyboard. I didn't see any errors to that though? I have a G903 Logitech mouse - no problems though.

I need to find the OpenRazor error message in what I have posted. I am only aware of an error with a lib6(?) file which I have mentioned twice I think when installing a higher kernel.

I will try kernel 5.12.0 and look for the OpenRazor error in a few minutes. In the meantime I have installed vulkan-tools and apart from the ELF errors I mentioned I now have this:

PS. Is there a way to copy/paste the output from mainline?

```

makem@makems-TUF:~$ vulkaninfo | grep GPU
MESA-INTEL: warning: Performance support disabled, consider sysctl dev.i915.perf_stream_paranoid=0

        GPU id       : 0 (Intel(R) Graphics (RKL GT1))
        GPU id       : 1 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 2 (Intel(R) Graphics (RKL GT1))
        GPU id       : 3 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 0 (Intel(R) Graphics (RKL GT1))
        GPU id       : 1 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 2 (Intel(R) Graphics (RKL GT1))
        GPU id       : 3 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 0 (Intel(R) Graphics (RKL GT1))
        GPU id       : 1 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 2 (Intel(R) Graphics (RKL GT1))
        GPU id       : 3 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 0 (Intel(R) Graphics (RKL GT1))
        GPU id       : 1 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 2 (Intel(R) Graphics (RKL GT1))
        GPU id       : 3 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 0 (Intel(R) Graphics (RKL GT1))
        GPU id       : 1 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 2 (Intel(R) Graphics (RKL GT1))
        GPU id       : 3 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 0 (Intel(R) Graphics (RKL GT1))
        GPU id       : 1 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 2 (Intel(R) Graphics (RKL GT1))
        GPU id       : 3 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 0 (Intel(R) Graphics (RKL GT1))
        GPU id       : 1 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 2 (Intel(R) Graphics (RKL GT1))
        GPU id       : 3 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 0 (Intel(R) Graphics (RKL GT1))
        GPU id       : 1 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 2 (Intel(R) Graphics (RKL GT1))
        GPU id       : 3 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 0 (Intel(R) Graphics (RKL GT1))
        GPU id       : 1 (llvmpipe (LLVM 12.0.1, 256 bits))
        GPU id       : 2 (Intel(R) Graphics (RKL GT1))
        GPU id       : 3 (llvmpipe (LLVM 12.0.1, 256 bits))
GPU id       : 0 (Intel(R) Graphics (RKL GT1))
GPU id       : 1 (llvmpipe (LLVM 12.0.1, 256 bits))
GPU id       : 2 (Intel(R) Graphics (RKL GT1))
GPU id       : 3 (llvmpipe (LLVM 12.0.1, 256 bits))
GPU0
    deviceType     = INTEGRATED_GPU
GPU1
GPU2
    deviceType     = INTEGRATED_GPU
GPU3
makem@makems-TUF:~$

```

I believe that can be ignored as the the iGPU is being used.

---

### Post by makem2 on 2021-07-27
> **MAFoElffen said:**
> 
That is, that I didn't see problems about that, but then I just noticed that you said "openrazer" having problems building in it's "make" with libc6 dependency problems...I just caught what you were saying with that...And that "that" was preventing you from doing a lot of things. Because you keep getting that error.

Do you have a "Razor" keyboard and/or mouse? And that jog's my memory that you were having mouse problems... Please tell us more about this...

Does it give you that same OpenRazor error message if you only try to add Kernel 5.12.0? Or do you get that message when you try to go newer than that?

I have "Razor" keyboard, mouses, game pad, and their RGB mouse pad in storage...But I haven't used them since I hand-built my own programmable mechanical gaming keyboard and game pad.

(I need to get back to testing. Will check this later.)

Yes, when installing 5.12.0 I did have an OpenRazor error which j I missed previously. I also still had the same libc6 error too. AH, I see you relate the libc6 error to the keyboard!

I have a photo of the install output but forget how to post it to some place - I even forget the name of the place!" (age eh?)

Edit: I have a wireless keyboard (cheapo) which I could use temporarily if that would help get the kernel upgraded?

[https://drive.google.com/file/d/1DM9LRN9BKggBoMCMrxauHooezGPnhmT-/view?usp=sharing](https://drive.google.com/file/d/1DM9LRN9BKggBoMCMrxauHooezGPnhmT-/view?usp=sharing)

---

### Post by makem2 on 2021-07-27
I am now running:

```

makem@makems-TUF:~$ uname -sr
Linux 5.12.0-051200-generic
makem@makems-TUF:~$

```

However it is complaining about a broken package which I have traced down to headers of the current kernel using Synaptic but I cannot fix that. (Related to libc6?) 

From Synaptic:
This is for sites that want the latest kernel headers.  Please read
/usr/share/doc/linux-headers-5.12.0-051200/debian.README.gz for details

But:

```

makem@makems-TUF:~$ sudo apt --fix-missing update
[sudo] password for makem: 
Hit:1 http://gb.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]     
Hit:3 http://ppa.launchpad.net/cappelikan/ppa/ubuntu focal InRelease           
Hit:4 http://ppa.launchpad.net/kisak/kisak-mesa/ubuntu focal InRelease         
Get:5 http://gb.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]   
Hit:6 http://ppa.launchpad.net/kisak/turtle/ubuntu focal InRelease             
Hit:7 http://ppa.launchpad.net/openrazer/stable/ubuntu focal InRelease
Get:8 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Hit:9 http://ppa.launchpad.net/polychromatic/stable/ubuntu focal InRelease
Fetched 328 kB in 1s (266 kB/s)                         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
makem@makems-TUF:~$ apt list --upgradable
Listing... Done
vulkan-utils/focal,focal 1.2.131.1+dfsg1-1 amd64 [upgradable from: 1.1.70+dfsg1-1]
N: There is 1 additional version. Please use the '-a' switch to see it
makem@makems-TUF:~$ apt list -a --upgradable
Listing... Done
vulkan-utils/focal,focal 1.2.131.1+dfsg1-1 amd64 [upgradable from: 1.1.70+dfsg1-1]
vulkan-utils/now 1.1.70+dfsg1-1 amd64 [installed,upgradable to: 1.2.131.1+dfsg1-1]
makem@makems-TUF:~$ 

```

vulkan can be upgraded (because of the kernel update?) Should I update now and will the mesa drivers need updating too?

Cannot upgrade vulkan because of unmet dependencies in the headers which apt wants to remove completely.

---

### Post by MAFoElffen on 2021-07-27
This is what you posted, here in this thread...

> **makem2 said:**
> Upgrading the kernel to 12 or I think, any above where I am now always creates an error message which I have previously posted:

".........linux headers......depends on lib6 (>= 2.33); however version of lib6:amd64 on system is 2.31-0ubuntu9.2"

```

sudo nano /var/lib/[COLOR=#ff0000]dkms/openrazer-driver[/COLOR]/3.0.1/build/make.log

```

Output of make.log:

make -C /lib/modules/5.12.15-051215-generic/build M=/var/lib/dkms/[COLOR=#ff0000]openrazer-dri>[/COLOR]
make[1]: Entering directory '/usr/src/linux-headers-5.12.15-051215-generic'
  CC [M]  /var/lib/dk[COLOR=#ff0000]ms/openrazer-driver[/COLOR]/3.0.1/build/driver/[COLOR=#ff0000]razerkbd_driver.o[/COLOR]
scripts/basic/fixdep: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not>
make[2]: *** [scripts/Makefile.build:271: /var/lib/dkms/[COLOR=#ff0000]openrazer-driver[/COLOR]/3.0.1/>
make[2]: *** Deleting file '/var/lib/dkms/[COLOR=#ff0000]openrazer-driver[/COLOR]/3.0.1/build/driver/r>
make[1]: *** [Makefile:1865: /var/lib/dkms/[COLOR=#ff0000]openrazer-driver[/COLOR]/3.0.1/build/driver]>
make[1]: Leaving directory '/usr/src/linux-headers-5.12.15-051215-generic'
make: *** [Makefile:25: driver] Error 2

I do not know how to post the output of the mainline installer but it does say consult that log.

I also don't know if the errors can be ignored as it does say the kernel is installed.
That was preventing you from upgrading your Kernel to 5.12.12-051215-generic...

Do you get that same message if you try to just Upgrade it to 5.12.0? Or do you still get that dependency error on that?

---

### Post by makem2 on 2021-07-27
> **MAFoElffen said:**
> This is what you posted, here in this thread...


That was preventing you from upgrading your Kernel to 5.12.12-051215-generic...

Do you get that same message if you try to just Upgrade it to 5.12.0? Or do you still get that dependency error on that?

Yes i still get the dependency error and as I said above I need to remove the headers

---

### Post by MAFoElffen on 2021-07-27
if in that Mainline app, you remove the extra kernels and then in a terminal, do
```
sudo apt autoremove
``` 
Then it will be removed. My suggestion would be to also purge the Kisak PPA, and reinstall Mesa to rollback your mesa driver.. That newer mesa driver does no good without the newer graphic's driver from a newer kernel.

You're stuck. Easiest would be to save up for another GPU that is "officially" supported by that Game.

---

### Post by makem2 on 2021-07-27
> **MAFoElffen said:**
> if in that Mainline app, you remove the extra kernels and then in a terminal, do
```
sudo apt autoremove
``` 
Then it will be removed. My suggestion would be to also purge the Kisak PPA, and reinstall Mesa to rollback your mesa driver.. That newer mesa driver does no good without the newer graphic's driver from a newer kernel.

You're stuck. Easiest would be to save up for another GPU that is "officially" supported by that Game.


Ok, I agree, we with all your help have tried everything. Time to stop

And finally, knowing I am Using a Streaming Service and intend to get a dedicated GPU, would it be worthwhile reinstalling 20.04 and not 'interfering' with it until the new GPU comes? It is easy for me and quite quick to do.

---

### Post by MAFoElffen on 2021-07-27
Oh... and remember to remove that parameter we just tried yesterday from your grub fiel and reun update-grub... all that should get you back to a default installation.

---

### Post by makem2 on 2021-07-28
> **MAFoElffen said:**
> Oh... and remember to remove that parameter we just tried yesterday from your grub fiel and reun update-grub... all that should get you back to a default installation.

Yes, I have done that.

Once again, thank you for all the time you have spent on this for me.

If you have a look at this page, which shows results of various Linux versions and various graphics card I think it will show that NMS does work but does have problems. There is also a lack of pure Intel systems.

[https://www.protondb.com/app/275850](https://www.protondb.com/app/275850)

---

