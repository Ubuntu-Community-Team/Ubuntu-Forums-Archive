---
title: "Updates to 22.10 are toxic to the Raspberry Pi-400"
date: 2023-02-13
forum: Installation &amp; Upgrades
---

### Post by teledyn on 2023-02-13
I have now confirmed this on both the latest download for the RPI 22.10 using both gdm3 and sddm, as well as my original problem machine which had been upgraded from 22.04. In all cases Ubuntu performed pre-upgrade without incident using my HDMI connected to a Philips monitor at 1920x1080. I suspect precious few folks are using Ubuntu on the pi-400, but I thought I'd leave at least a note of warning. If all this is short on details, that's mostly because I can't find any details. Xorg.0.log, kern.log, syslog and .xsessionerrors are all silent, they simply stop with no significant errors or warnings before.

Normally, on boot, we see the Pi colour-box splash, followed by the Ubuntu logo and hourglass, and then either the login screen (gdm3 or sddm) or the autologin to the selected account. This was the behaviour since the upgrade in November until just last week.

In the case of the upgraded image, it was a simple routine apt upgrade under a KDE Plasma configuration.  With the fresh image, just installing the kde-plasma-desktop *appeared* to precede it, although I could logout and login again, the machine failed after an upgrade-recommended reboot. On a *normal* running image, the Ubuntu logo is concurrent with an fsck check, but I don't know what else happens in there; there seems no evidence gdm3 or sddm are started.

The behaviour post-update, on both the fresh install and the upgraded machine, we see the colour-box followed by a *very brief* flash of the Ubuntu logo screen, and then the monitor goes black and starts showing a floating box saying the video mode is unsupported and should be changed to 1920x1080. I haven't figured out how to add F-key shells, so I then connect using ssh:

The following were obtained in the ssh -X shell:

```

$ xrandr
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768      60.00*+
HDMI-0 disconnected (normal left inverted right x axis y axis)

$ lshw -c video
  *-graphics                
       product: vc4drmfb
       physical id: 6
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=16 resolution=1920,1080

$ lspci -v
00:00.0 PCI bridge: Broadcom Inc. and subsidiaries BCM2711 PCIe Bridge (rev 20) (prog-if 00 [Normal decode])
        Device tree node: /sys/firmware/devicetree/base/scb/pcie@7d500000/pci@0,0
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: 00000000-000fffff [size=1M] [32-bit]
        Prefetchable memory behind bridge: [disabled] [64-bit]
        Capabilities: <access denied>
        Kernel driver in use: pcieport

01:00.0 USB controller: VIA Technologies, Inc. VL805/806 xHCI USB 3.0 Controller (rev 01) (prog-if 30 [XHCI])
        Subsystem: VIA Technologies, Inc. VL805/806 xHCI USB 3.0 Controller
        Device tree node: /sys/firmware/devicetree/base/scb/pcie@7d500000/pci@0,0/usb@0,0
        Flags: bus master, fast devsel, latency 0, IRQ 39
        Memory at 600000000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: xhci_hcd
        Kernel modules: xhci_pci

$ ps ax | grep Xorg
   1087 tty1     Ssl+   0:28 /usr/lib/xorg/Xorg -nolisten tcp -auth /var/run/sddm/{174dc394-edec-43c6-a993-6df54c1f5bd9} -background none -noreset -displayfd 17 -seat seat0 vt1

```

I notice there are no video controllers listed in the lspci and lshw only shows a FrameBuffer, but that's maybe normal on a Pi? Also there is the LVDS-0 listed, but this is a Pi, there is no 'laptop screen', only the micro-HDMI ports. It *appears* Xorg/Xwayland is running, and that flash of the Ubuntu logo perhaps confirms it? (unless that, like the colour box, is all FB?)

From an HP laptop, here is the xrandr for HDMI connected to the same monitor with the resolution correctly identified:
```

HDMI-A-0 connected 1920x1080+1366+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080     60.00*+  50.00    59.94  

```

Are there any other tests I can do that might hint at where this goes wrong?

---

### Post by teledyn on 2023-02-13
I just confirmed a test using a fresh install of the 22.10 desktop, and then _only_ doing apt update and upgrade without kde-plasma-desktop; on reboot, the screen fails.

Also confirmed that the 22.04 desktop freshly installed and then an update and upgrade, followed by installing kde-plasma-desktop is also fine, updated to the latest jammy.  So whatever causes this is lurking in the 22.10 branch...

---

### Post by MAFoElffen on 2023-02-13
Here is how I do it for RaspberryPi: [https://ubuntuforums.org/showthread.php?t=2466200&p=14055389#post14055389](https://ubuntuforums.org/showthread.php?t=2466200&p=14055389#post14055389)

---

### Post by teledyn on 2023-02-13
Thanks, but setting those config.txt changes do not change the behaviour, and I think this is likely to be expected since the boot splash and the Ubuntu logo both appear, the change that kills the video happens long after config.txt.  I also wonder about that HDMI line that says it is not active when the monitor is connected. Perhaps something about a driver crashes, but the screen itself doesn't say no-signal, it says it is in the wrong resolution to display.

One thing about config.txt and cmdline.txt, I added the rw and init='/bin/sh' to cmdline, but when it boots, I apparently have no systemd and so cannot start network access or install packages. Is this correct, or am I missing something? Anyway, that's another issue and no longer important since the error is in Linux-space, not Grub.

---

### Post by MAFoElffen on 2023-02-14
Okay. A little explanation seems to be needed.

Raspberry Pi has a  frame buffer for graphics. The graphics mode is set through Linux  Kernel via the config files (more of an explanation below). It doesn't use Grub, it uses it's own  Boot files + the config files...

My config files are config.txt, command.txt, syscfg.txt and usercfg.txt. I put all my graphics related configs in usercfg.txt.

Being  framebuffer graphics, whatever mode it is in doesn't matter until the  framebuffer gets initialized after the splash screen... That is where  yours fails.

Yours is getting set to 1366x768+0+0...

Here is mine through ssh -X:
```

mafoelffen@ubuntu:~$ xrandr -q
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
LVDS-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)
LVDS-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080     60.00*+  60.00    50.00  
   1680x1050     60.00  
   1400x1050     60.00  
   1600x900      60.00  
   1280x1024     60.00  
   1400x900      60.00  
   1280x960      60.00  
   1440x810      60.00  
   1368x768      60.00  
   1280x800      60.00  
   1280x720      60.00  
   1024x768      60.00  
   960x720       60.00  
   928x696       60.00  
   896x672       60.00  
   1024x576      60.00  
   960x600       60.00  
   960x540       60.00  
   800x600       60.00  
   840x525       60.00  
   864x486       60.00  
   700x525       60.00  
   800x450       60.00  
   640x512       60.00  
   700x450       60.00  
   640x480       60.00  
   720x405       60.00  
   684x384       60.00  
   640x360       60.00  
   512x384       60.00  
   512x288       60.00  
   480x270       60.00  
   400x300       60.00  
   432x243       60.00  
   320x240       60.00  
   360x202       60.00  
   320x180       60.00  
VGA-1-1 disconnected (normal left inverted right x axis y axis)

```
Ubuntu  22.10 made a lot of changes to the graphics layer for Raspberry Pi...  It went from using fkms (fake KMS) to kms. So shifted from using a separate, closed  source driver to doing graphics through the Linux Kernel. So yes,  changes in the config.txt type files are directly linked to the graphics  layer. And in 22.10, there where a lot of config.txt options added for  that.

In particular, graphics setting of 1366x768, there is an  open bug filed ([https://github.com/raspberrypi/linux/issues/4472](https://github.com/raspberrypi/linux/issues/4472)) on that mode. But you need  to set yours to 1920x1080. That is what your error from your display is  telling you... Which, for RaspPi, you change in the config.txt type files.

So in saying that, please post your config.txt type files, so we can see what you have set, and can use to determine what is going on.

---

### Post by teledyn on 2023-02-17
Thanks for that very thorough reply -- unfortunately I only have two sdcards to play with so I kept re-installing the 22.10 img as I experimented with solutions.

I do know that the only files I changed were the cmdline.txt, and that only to add "rw init=/bin/sh", and, because I thought the problem might be HDMI related, I tried adding these lines to the config.txt, but they had no effect:
```

hdmi_group=2    # 0:Autodetect EDID, 1:AEC, 2:DMT
hdmi_mode=82    # 1920x1080 60Hz

```

Post-upgrade still killed the video. What I *didn't* try was the hdmi_cvt modeline, so I will add that.

Although I reverted to 22.04 to get my machine back in service, I obviously still need to solve the upgrade thing going forward. Unfortunately I may not get a chance to try the cvt settings until next week, but will update here when I do.

---

### Post by MAFoElffen on 2023-02-18
I think since it was an update, and the usual suspects don't seem to apply, an update may have well went south. I feel you are a good candidate to report it to launchpad. I'm thinking against 'gdm3'. If different, they can figure that out and change it.

I mean it is bfore the Login screen comes up. The rest of the graphics layer doesn't even come into play until after that...

When you do, please post the link to the post, and please keep us updated. I for one am interested in finding out what it might be, and what resolves it for you.

---

### Post by aphototool on 2023-02-20
I seem to have same issue with Raspberry Pi 400.

I used Raspberry Pi Imager to flash Ubuntu Desktop 22.10 (64-bit).
Booted fine and then I used Software Updater.
Reboot started fine but no login screen. Monitor detects no signal and goes to sleep.

Thought I have corrupted card but other card was the same.

Ubuntu Desktop 22.04 LTS works fine.

My monitor is old Lenovo C24-10 (1920x1080 hdmi connection).

---

### Post by ActionParsnip on 2023-02-20
I suggest you report a bug too. If a fresh install with updates causes issues then it doesn't sound right. Note that 22.10 is not LTS and I always recommend the LTS releases to users.

---

### Post by MAFoElffen on 2023-02-20
+1... Especially since they are making underhood changes to how graphics works on Raspberry Pi in 22.10. Hopefully they can get that worked out, ironed out and stable before the next LTS.

---

### Post by aphototool on 2023-02-21
Kernel 5.19.0-1014.21 worked for me.

[https://bugs.launchpad.net/ubuntu/+source/linux-raspi/+bug/2007259](https://bugs.launchpad.net/ubuntu/+source/linux-raspi/+bug/2007259)

---

### Post by MAFoElffen on 2023-02-21
Thank you.

As I read that, there was a bad upstream commit on Kernel 5.19.0-1013-raspi. The work-around was to use 'hdmi_safe=1' or another low resolution until it is booted, then it changed to 1920x1080 just fine after the boot. The fix was Linux Kernel 5.19.0-1014.21-raspi which is currently in the Proposed Repo.

---

### Post by teledyn on 2023-02-28
Sadly, the modeline had no effect.

I had the following in the config.txt
```

  hdmi_group=2    # 0:Autodetect EDID, 1:AEC, 2:DMT
  hdmi_mode=82    # 1920x1080 60Hz
  hdmi_cvt=1920 1020 60 3 0 0 0

```

When that didn't work, I read the fine documentation at [https://www.raspberrypi.com/documentation/computers/config_txt.html](https://www.raspberrypi.com/documentation/computers/config_txt.html) where I learned about
```

  hdmi_safe=1

```

and that does boot into a lo-res text mode, then switch to the Ubuntu logo, and then I get the same error, the floating box telling me to switch to 1920x1080.

*Update:* if I remove all the hdmi options and set ```
dtoverlay=vc4-fkms-v3d
``` the system is painfully slow, but it comes up so I can now probe things, albeit under the deprecated fake driver, and possibly replace the kernel.

---

### Post by MAFoElffen on 2023-02-28
Is your kernel version now the newer 5.19.0-1014.21-raspi?
```

uname -r 

```

---

### Post by teledyn on 2023-02-28
I can confirm: using sudo apt-add-repository -p proposed to get Linux pi-400 5.19.0-1014-raspi solves the problem!

---

### Post by MAFoElffen on 2023-03-01
Happy to be of help in directing you to a solution.

---

### Post by teledyn on 2023-03-06
... and I can confirm that today's update to 1015 kills it again.

but this time, adding the explicit hdma_* settings in config.txt does work!

---

### Post by MAFoElffen on 2023-03-07
LOL. Gosh dang.

I'm just happy that since this thread started, that you have to tools to figure these kinds of graphics issues out now.

I'm glad that I stayed with an LTS release for stability. (22.04)

Please keep us posted.

---

