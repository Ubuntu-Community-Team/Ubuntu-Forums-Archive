---
title: "Only 640X480 resolution displays desktop via HDMI output"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by safrisrael on 2013-05-11
Hello community,

I have been searching quite a lot about this issue before I decided to post in the forum, but haven't managed to get the slightest clue to explain it or resolve it. 

I would really appreciate some light on how to troubleshoot this. I'm really hoping that this is some silly configuration I am missing.

The problem is that the only resolution where I can see the desktop on my TV via the HDMI port is 640x480. The TV feels when I change the resolution on the server, as it reports it in the on-screen-display, but the display remains black :(

Thanks a lot in advance!

**My environment:**
_*Hardware*_:
Motherboard - ASUS P8H77-M PRO
CPU Intel Core i3-3225 with integrated graphics HD4000.

_*Software:*_
Ubuntu server 12.04 (64-bit)

_*Some other details:*_
- This is a brand new installation and my ultimate goal is to get xbmc running together with other services.
- My Sharp TV supports 720p and 1080i HD resolutions and both vendor and resolutions are correctly detected by the operating system.
- Using VGA every resolution my tv supports is displayed perfectly.
- My TV displays perfectly other video output devices via HDMI (Unfortunately I do not have any other HDMI displays to check the behavior.)
- Via VNC I can see the HDMI output correctly in the secondary screen. 

_*What I have done and hasn't made any difference whatsoever:*_
- I have installed the latest version of the Intel Linux drivers here - [https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)
- Changed the cable plugging order, disconnected VGA and connected HDMI only.
- Connected the TV via the DVI poprt using a DVI-HDMI converter.

Below are some outputs of commands that I saw were requested for display issues in forums and thought may help. Thanks a ton!!!

[FONT=courier new]# sudo lshw -C display[/FONT]
[FONT=courier new]  *-display[/FONT]
[FONT=courier new]       description: VGA compatible controller[/FONT]
[FONT=courier new]       product: Ivy Bridge Graphics Controller[/FONT]
[FONT=courier new]       vendor: Intel Corporation[/FONT]
[FONT=courier new]       physical id: 2[/FONT]
[FONT=courier new]       bus info: pci@0000:00:02.0[/FONT]
[FONT=courier new]       version: 09[/FONT]
[FONT=courier new]       width: 64 bits[/FONT]
[FONT=courier new]       clock: 33MHz[/FONT]
[FONT=courier new]       capabilities: msi pm vga_controller bus_master cap_list rom[/FONT]
[FONT=courier new]       configuration: driver=i915 latency=0[/FONT]
[FONT=courier new]       resources: irq:44 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)[/FONT]

[FONT=courier new]# lspci -nnk | grep -iA2 vga[/FONT]
[FONT=courier new]00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0162] (rev 09)[/FONT]
[FONT=courier new]        Subsystem: ASUSTeK Computer Inc. Device [1043:84ca][/FONT]
[FONT=courier new]        Kernel driver in use: i915[/FONT]

[FONT=courier new]# grep WW /var/log/Xorg.0.log[/FONT]
[FONT=courier new][    11.774] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.[/FONT]
[FONT=courier new][    11.774] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.[/FONT]
[FONT=courier new][    11.774] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.[/FONT]
[FONT=courier new][    11.774] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.[/FONT]
[FONT=courier new][    11.774] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.[/FONT]
[FONT=courier new][    11.774] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.[/FONT]
[FONT=courier new][    11.779] (WW) Falling back to old probe method for vesa[/FONT]
[FONT=courier new][    11.779] (WW) Falling back to old probe method for fbdev[/FONT]
[FONT=courier new][    13.184] (WW) evdev: MOSART Semi. Rapoo 2.4G Wireless Touch Desktop : ignoring absolute axes.[/FONT]
[FONT=courier new]

# xrandr --verbose -d :0.0[/FONT]
[FONT=courier new]Screen 0: minimum 320 x 200, current 1280 x 720, maximum 8192 x 8192[/FONT]
[FONT=courier new]VGA1 disconnected (normal left inverted right x axis y axis)[/FONT]
[FONT=courier new]        Identifier: 0x42[/FONT]
[FONT=courier new]        Timestamp:  1330033[/FONT]
[FONT=courier new]        Subpixel:   unknown[/FONT]
[FONT=courier new]        Clones:[/FONT]
[FONT=courier new]        CRTCs:      0 1[/FONT]
[FONT=courier new]        Transform:  1.000000 0.000000 0.000000[/FONT]
[FONT=courier new]                    0.000000 1.000000 0.000000[/FONT]
[FONT=courier new]                    0.000000 0.000000 1.000000[/FONT]
[FONT=courier new]                   filter:[/FONT]
[FONT=courier new]HDMI1 disconnected (normal left inverted right x axis y axis)[/FONT]
[FONT=courier new]        Identifier: 0x43[/FONT]
[FONT=courier new]        Timestamp:  1330033[/FONT]
[FONT=courier new]        Subpixel:   unknown[/FONT]
[FONT=courier new]        Clones:[/FONT]
[FONT=courier new]        CRTCs:      0 1 2[/FONT]
[FONT=courier new]        Transform:  1.000000 0.000000 0.000000[/FONT]
[FONT=courier new]                    0.000000 1.000000 0.000000[/FONT]
[FONT=courier new]                    0.000000 0.000000 1.000000[/FONT]
[FONT=courier new]                   filter:[/FONT]
[FONT=courier new]        Broadcast RGB:  Full[/FONT]
[FONT=courier new]                supported: Full         Limited 16:2[/FONT]
[FONT=courier new]        audio:  auto[/FONT]
[FONT=courier new]                supported: force-dvi    off          auto         on[/FONT]
[FONT=courier new]HDMI2 connected 1280x720+0+0 (0x4a) normal (normal left inverted right x axis y axis) 820mm x 460mm[/FONT]
[FONT=courier new]        Identifier: 0x44[/FONT]
[FONT=courier new]        Timestamp:  1330033[/FONT]
[FONT=courier new]        Subpixel:   unknown[/FONT]
[FONT=courier new]        Gamma:      1.0:1.0:1.0[/FONT]
[FONT=courier new]        Brightness: 1.0[/FONT]
[FONT=courier new]        Clones:[/FONT]
[FONT=courier new]        CRTC:       0[/FONT]
[FONT=courier new]        CRTCs:      0 1 2[/FONT]
[FONT=courier new]        Transform:  1.000000 0.000000 0.000000[/FONT]
[FONT=courier new]                    0.000000 1.000000 0.000000[/FONT]
[FONT=courier new]                    0.000000 0.000000 1.000000[/FONT]
[FONT=courier new]                   filter:[/FONT]
[FONT=courier new]        EDID:[/FONT]
[FONT=courier new]                00ffffffffffff004d10081000000000[/FONT]
[FONT=courier new]                ff11010380522e782a1bbea25534b326[/FONT]
[FONT=courier new]                144a5200000001010101010101010101[/FONT]
[FONT=courier new]                010101010101011d00bc52d01e20b828[/FONT]
[FONT=courier new]                554034cc3100001e011d007251d01e20[/FONT]
[FONT=courier new]                6e28550034cc3100001e000000fc0053[/FONT]
[FONT=courier new]                484152502048444d490a2020000000fd[/FONT]
[FONT=courier new]                00313d0f2e08000a2020202020200196[/FONT]
[FONT=courier new]                020325724d9384140512031102160715[/FONT]
[FONT=courier new]                060123090707830100006a030c002000[/FONT]
[FONT=courier new]                800f801501011d80d0721c1620102c25[/FONT]
[FONT=courier new]                8034cc3100009e011d8018711c162058[/FONT]
[FONT=courier new]                2c250034cc3100009e00000000000000[/FONT]
[FONT=courier new]                00000000000000000000000000000000[/FONT]
[FONT=courier new]                00000000000000000000000000000000[/FONT]
[FONT=courier new]                00000000000000000000000000000037[/FONT]
[FONT=courier new]        Broadcast RGB:  Full[/FONT]
[FONT=courier new]                supported: Full         Limited 16:2[/FONT]
[FONT=courier new]        audio:  auto[/FONT]
[FONT=courier new]                supported: force-dvi    off          auto         on[/FONT]
[FONT=courier new]  1280x720 (0x47)   74.2MHz +HSync +VSync +preferred[/FONT]
[FONT=courier new]        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock   37.5KHz[/FONT]
[FONT=courier new]        v: height  720 start  725 end  730 total  750           clock   50.0Hz[/FONT]
[FONT=courier new]  1920x1080 (0x48)   74.2MHz +HSync +VSync Interlace[/FONT]
[FONT=courier new]        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.8KHz[/FONT]
[FONT=courier new]        v: height 1080 start 1084 end 1094 total 1125           clock   30.0Hz[/FONT]
[FONT=courier new]  1920x1080 (0x49)   74.2MHz +HSync +VSync Interlace[/FONT]
[FONT=courier new]        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   28.1KHz[/FONT]
[FONT=courier new]        v: height 1080 start 1084 end 1094 total 1125           clock   25.0Hz[/FONT]
[FONT=courier new]  1280x720 (0x4a)   74.2MHz +HSync +VSync *current[/FONT]
[FONT=courier new]        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz[/FONT]
[FONT=courier new]        v: height  720 start  725 end  730 total  750           clock   60.0Hz[/FONT]
[FONT=courier new]  1440x576 (0x4b)   27.0MHz -HSync -VSync Interlace[/FONT]
[FONT=courier new]        h: width  1440 start 1464 end 1590 total 1728 skew    0 clock   15.6KHz[/FONT]
[FONT=courier new]        v: height  576 start  580 end  586 total  625           clock   25.0Hz[/FONT]
[FONT=courier new]  1440x480 (0x4c)   27.0MHz -HSync -VSync Interlace[/FONT]
[FONT=courier new]        h: width  1440 start 1478 end 1602 total 1716 skew    0 clock   15.7KHz[/FONT]
[FONT=courier new]        v: height  480 start  488 end  494 total  525           clock   30.0Hz[/FONT]
[FONT=courier new]  720x576 (0x4d)   27.0MHz -HSync -VSync[/FONT]
[FONT=courier new]        h: width   720 start  732 end  796 total  864 skew    0 clock   31.2KHz[/FONT]
[FONT=courier new]        v: height  576 start  581 end  586 total  625           clock   50.0Hz[/FONT]
[FONT=courier new]  720x480 (0x4e)   27.0MHz -HSync -VSync[/FONT]
[FONT=courier new]        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz[/FONT]
[FONT=courier new]        v: height  480 start  489 end  495 total  525           clock   59.9Hz[/FONT]
[FONT=courier new]  640x480 (0x4f)   25.2MHz -HSync -VSync[/FONT]
[FONT=courier new]        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz[/FONT]
[FONT=courier new]        v: height  480 start  490 end  492 total  525           clock   59.9Hz[/FONT]
[FONT=courier new]DP1 disconnected (normal left inverted right x axis y axis)[/FONT]
[FONT=courier new]        Identifier: 0x45[/FONT]
[FONT=courier new]        Timestamp:  1330033[/FONT]
[FONT=courier new]        Subpixel:   unknown[/FONT]
[FONT=courier new]        Clones:[/FONT]
[FONT=courier new]        CRTCs:      0 1 2[/FONT]
[FONT=courier new]        Transform:  1.000000 0.000000 0.000000[/FONT]
[FONT=courier new]                    0.000000 1.000000 0.000000[/FONT]
[FONT=courier new]                    0.000000 0.000000 1.000000[/FONT]
[FONT=courier new]                   filter:[/FONT]
[FONT=courier new]        Broadcast RGB:  Full[/FONT]
[FONT=courier new]                supported: Full         Limited 16:2[/FONT]
[FONT=courier new]        audio:  auto[/FONT]
[FONT=courier new]                supported: force-dvi    off          auto         on[/FONT]
[FONT=courier new]DP2 disconnected (normal left inverted right x axis y axis)[/FONT]
[FONT=courier new]        Identifier: 0x46[/FONT]
[FONT=courier new]        Timestamp:  1330033[/FONT]
[FONT=courier new]        Subpixel:   unknown[/FONT]
[FONT=courier new]        Clones:[/FONT]
[FONT=courier new]        CRTCs:      0 1 2[/FONT]
[FONT=courier new]        Transform:  1.000000 0.000000 0.000000[/FONT]
[FONT=courier new]                    0.000000 1.000000 0.000000[/FONT]
[FONT=courier new]                    0.000000 0.000000 1.000000[/FONT]
[FONT=courier new]                   filter:[/FONT]
[FONT=courier new]        Broadcast RGB:  Full[/FONT]
[FONT=courier new]                supported: Full         Limited 16:2[/FONT]
[FONT=courier new]        audio:  auto[/FONT]
[FONT=courier new]                supported: force-dvi    off          auto         on[/FONT]

---

### Post by safrisrael on 2013-05-15
If anybody is interested, I finally solved after tedious iterations by installing Ubuntu server 13.04.

---

### Post by hvralpha on 2013-05-17
You can install ARandR from the Ubuntu store and run it or fix the monitors.xml file.

You can find it at : /home/username/.config/monitors.xml.
Open it with Gedit and just change the configuration you want in there under your HDMI2 section

---

