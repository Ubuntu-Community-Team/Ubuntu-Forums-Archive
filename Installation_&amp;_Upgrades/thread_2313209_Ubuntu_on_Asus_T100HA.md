---
title: "Ubuntu on Asus T100HA"
date: 2016-02-10
forum: Installation &amp; Upgrades
---

### Post by magyarmester on 2016-02-10
Hello everybody!

First of all, this is my first post, and I don't really know these forums well, so forgive me if I do something wrong.
So my problem is, that I'm planning to buy an Asus T100HA tablet(4gb ram etc.) and I'm interested in that will it work with Ubuntu? Does Asus have any problems with Linux used on their devices(OS lock or something maybe?)? Does Ubuntu actually support Asus T100HA features(screen rotation, wifi, etc)

Have a nice day:
magyarmester

---

### Post by sputnikuk on 2016-02-11
Hi.

I have the 2GB version of the T100HA.  I have tried the howtos for the t100 with no joy.

The following things don't work on my installation:
Sound
Blurtooth
Cameras
Built in wi-fi
 
I'm using a wifi dongle.

To get ubuntu working you need to pass the nomodeset flag to the boot option in grub. I installed ubuntu in portrait mode even though the screen was landscape.

You also need (post install) to use the lxdm display manager, lightdm and gdm give a blank screen.

/usr/share/X11/xorg.conf.d/10-monitor.conf:
Section "Device"
Identifier "Configured Video Device"
Driver "fbdev"
Option "UseFBDev" "true"
Option "Rotate" "CCW"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
DefaultDepth 24
SubSection "Display" 
Depth 24
Modes "800x1280"
EndSubSection  
EndSection

To rotate the screen to landscape the following commands need to be added to /etc/xdg/lxsession/LXDE/autostart
@xinput set-prop 11 "Evdev Axis Inversion" 1, 0 
@xinput set-prop 11 "Evdev Axes Swap" 1


I'm sure device support will be here soon, maybe in Ubuntu 16.04 or with kernel 4.5. If you need device support go with the t100 or maybe the T100Chi? Note webcam support is still being developed for both these models.

Also:
There are open source drivers for the intel graphics card at 01.org. i couldn't run X with a configuration built using X -configure though.

Rob.

---

### Post by andrei31 on 2016-03-18
Hi,

I have installed Ubuntu 15.10 on my T100HA. Although it's not an easy task, it's manageable. The biggest problem I have is the brightness which is always at maximum.

I can live without bluetooth (never used it in 6 years on my previous laptop) or built in wifi (I also have a dongle). Sound and camera would be nice to have but for the moment I don't really need them. I'm sure that, eventually, my t100 will be fully functional under Ubuntu and I knew there are some problems before buying it but the brightness is driving me crazy. 

The touch screen is amazing. Works really well and all it needs is the mentioned rotation.
The keyboard is a bit cheap and, off-course, 10' small.
I bought a 64GB sdxc card that worked immediately after I've installed the exfat package.
I didn't try the micro hdmi port and neither to undock the keyboard mainly due to the wifi dongle that is plugged in the "normal" USB which is on the keyboard.
I played Battle for Wesnoth without any problems. 
Editing latex documents works perfectly and playing only for a few minutes with Libre Office Impress I didn't found any problem. Using the touchscreen for presentations speeds things up quite a bit.

Another problem I have is that the laptop freezes completely just a few seconds after I try to compile something on >1 core. Not sure what the problem is.
The battery life is reasonable considering the full brightness (). 

I would recommend this laptop to Ubuntu users only after I solve the brightness problem. Any idea how to fix this issue?

Best,
Andrei

---

### Post by Florian_Hanisch on 2016-04-03
Hi, 

I used the steps described above in #2 (setting up 10-monitor.conf and editing autostart). The rotation of the screen works fine but for some reason, the touchscreen is not being rotated. Any idea what may have gone wrong ? Which part of the code is responsible for rotating the touchscreen ? Thanks a lot !

Btw: I tried out kernel 4.5 on Lubuntu 15.10 obtained here ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)) but that did not fix the problems with the screen / graphics driver.

**Edit** (5.4.16): I now managed to rotate the touchscreen as well. I added the file /usr/share/X11/xorg.conf.d/99-calibration.conf  containing

Section "InputClass"
   Identifier "calibration"
   MatchProduct   "SIS0457:00 0457:113D"
   Option "SwapAxes" "1"
   Option "InvertX" "1"
EndSection

As far as I understand, this file may have to be saved at a different place (e.g. /etc/X11/xorg.conf.d/99-calibration.conf) depending on your system/distribution. The identfier behind "MatchProduct" can be obtained from the result of xinput --list. 

I spent some time trying to use the commands 

@xinput set-prop 12 "Evdev Axis Inversion" 1, 0 
@xinput set-prop 12 "Evdev Axes Swap" 1

in autostart. These commands work fine if executed in a terminal (without the @) but for some reason, they are ignored or overwritten by something else if I just include them in autostart. I don't understand why this is happing (I made sure that I chose that particular autostart file that is used at the start of xserver) but I am happy now with the solution describes above.

---

### Post by Oflor on 2016-04-24
Any luck getting wifi to work? T100TA [seems]("http://www.jfwhome.com/2016/01/04/latest-steps-to-install-ubuntu-on-the-asus-t100ta/") to have a working wifi, but doing these steps on T100HA leads to no results. Dmesg shows that brcmfmac doesn't try to init any wifi modules, the reason most likely being T100HA's wifi is not 43241. One thing I know for sure is that wifi is one of Broadcom's SDIO modules, but it doesn't show up in lspci, lsusb or lshw, therefore I can't see which module it is.

Additionally, I can't not notice numerous mce messages in dmesg output, "mce: [Hardware Error]: Machine check events logged".

---

### Post by movienut50 on 2016-06-16
I have tried everything i've read with 16.04 and no joy so I have started over and installed lastest build of Ubuntu 16.10. I'm stuck at trying new display managers I only have lightdm installed. Does anyone know how to install multiple display managers to try (install from command line). I would like to try lxdm and maybe others, but even gdm doesn't seem to be installed. I'm learning so be kind

---

### Post by sir2 on 2016-06-18
Hi,

I just installed Ubuntu Mate 16.04. Using the mentioned configurations for correctly rotated monitor and touchpad it looks quite nice. 

So Wifi is the other thing I need to get working. I read in another thread to run a script wireless-info. I attached the info from that script. Is that of any help for someone?

One thing I tried was to copy the nvram file from /sys/firmware/efi/efivars to /lib/firmware/brcm. First try was to brcmfmac43340-sdio.txt. Then I tried brcmfmac4386-sdio.txt (because I found 4386 as device id in the nvram file). But nothing changed. Any idea how to find out, what the correct file name is? Or do I have to anything more?

Thanks for any suggestions

Claus

---

### Post by movienut50 on 2016-06-29
I also have Ubuntu Mate 16.04 installed and running really nice. Upgraded to kernel 4.6.3 still no wireless, bluetooth or sound. Any help would really be appreciated.
Attached is the results of the wireless script (wireless-info.txt)

---

### Post by movienut50 on 2016-07-28
Sooo, No one having any luck with linux drivers for the wireless on the T100HA?

---

### Post by aaaabbb111 on 2016-08-15
We have not the Wifi Bluetooth and Two Camera Driver.
Welcome to the Jungle..

---

### Post by Holmen on 2016-09-04
Hi all, I also found myself in this "jungle", though I'm in it for my girlfriends new computer. Are there any kind of news?

---

### Post by rapiertg on 2016-09-15
Some people managed to make WiFi working:
[http://www.transformerforums.com/forum/asus-transformer-book-t100-alternate-os-s-development/48417-any-success-alternative-os-t100ha-4.html](http://www.transformerforums.com/forum/asus-transformer-book-t100-alternate-os-s-development/48417-any-success-alternative-os-t100ha-4.html)

---

### Post by romis on 2016-12-18
Wanted to chime in, as I just purchased this machine. Wifi and the touch screen works out of the box for me in 16.04 using gnome-shell. GDM does not work (black screen) but lightdm both the Unity greeter and the GTK+ greeter work fine. Ubuntu also needs nomodeset to boot properly from GRUB, and sound, the camera, and rotating the screen do not work, and the resolution only has the one option of the highest one, not that I that I ever need to change that sort of thing. I tried 16.10 live and I don't notice anything better, but isn't this thing just filled with stock standard Intel components that will probably just be supported in a newer kernel?

---

### Post by mörgæs on 2016-12-20
> **romis said:**
> isn't this thing just filled with stock standard Intel components

Maybe, you tell me. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by romis on 2016-12-20
```
computer
    description: Notebook
    product: T102HA (ASUS-TabletSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 vsyscall32
    configuration: boot=normal chassis=notebook family=T sku=ASUS-TabletSKU uuid=[REMOVED]
  *-core
       description: Motherboard
       product: T102HA
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: [REMOVED]
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: T102HA.204
          date: 07/18/2016
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 1600 MHz (0.6 ns)
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: A1_DIMM0
             size: 4GiB
             width: 8 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: Array1_PartNumber1
             vendor: A1_Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: A1_DIMM1
     *-cache:0
          description: L1 cache
          physical id: 12
          slot: CPU Internal L1
          size: 224KiB
          capacity: 224KiB
          capabilities: internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 13
          slot: CPU Internal L2
          size: 2MiB
          capacity: 2MiB
          capabilities: internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) x5-Z8350  CPU @ 1.44GHz
          vendor: Intel Corp.
          physical id: 14
          bus info: cpu@0
          version: Intel(R) Atom(TM) x5-Z8350 CPU @ 1.44GHz
          slot: SOCKET 0
          size: 781MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 80MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 36
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:299 memory:90000000-90ffffff memory:80000000-8fffffff ioport:f000(size=64)
        *-multimedia UNCLAIMED
             description: Multimedia controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: memory:91000000-913fffff
        *-generic:0 UNCLAIMED
             description: Non-VGA unclassified device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:91a3a000-91a3afff
        *-generic:1
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 36
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:300 memory:91a39000-91a39fff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 36
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:116 memory:91a00000-91a0ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-53-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-53-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=7 speed=480Mbit/s
              *-usb:0
                   description: Keyboard
                   product: ASUS HID Device
                   vendor: ASUS HID Device
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.07
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: IMC Networks
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.01
                   capabilities: bluetooth usb-1.10
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 4
                   bus info: usb@1:4
                   version: 32.98
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb UNCLAIMED
                      description: Generic USB device
                      product: ELAN:Fingerprint
                      vendor: ELAN
                      physical id: 2
                      bus info: usb@1:4.2
                      version: 1.28
                      capabilities: usb-2.00
                      configuration: maxpower=100mA speed=12Mbit/s
        *-generic:2
             description: Encryption controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:301 memory:91900000-919fffff memory:91800000-918fffff
        *-pci
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:115 memory:91600000-917fffff
           *-network
                description: Wireless interface
                product: Qualcomm Atheros
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 31
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-53-generic firmware=WLAN.TF.1.0-00267-1 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:302 memory:91600000-917fffff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
```

---

### Post by mörgæs on 2016-12-22
This is brand-new hardware. You could try a live boot of 17.04 (still in development) to see if any of the problems are fixed here. 

It's only meant as a test, not recommended for install yet.

---

### Post by romis on 2016-12-22
> **mörgæs said:**
> This is brand-new hardware. You could try a live boot of 17.04 (still in development) to see if any of the problems are fixed here. 

It's only meant as a test, not recommended for install yet.

I'll try that and report back.

EDIT: After trying the latest zesty daily (hey that's fun to say) there is no apparent change in hardware support, namely speakers/headphones, brightness control, and the same resolution/orientation workaround below is necessary.

As an aside, I did get screen rotation to work. Initially I had been booting with nomodeset, but that locked the screen in vertical-only mode, but editing /etc/default/grub and removing the '#' before GRUB_GFXMODE, the result is GRUB is a crappy resolution, but I can rotate the screen display using the standard GNOME/XRandr, and I only really see GRUB for about ten seconds, not a big deal.

---

### Post by larer on 2017-02-11
I'm reposting the first half of what I've posted on [Transformerforum]("http://www.transformerforums.com/forum/asus-transformer-book-t100-alternate-os-s-development/48417-any-success-alternative-os-t100ha-6.html").

[COLOR=#333333]First a confirming report saying the same thing as others have reported since end of January, aiming at making others confident in starting a new Ubuntu install on the T100HA is fairly easy so we can build momentum and get progress. I successfully booted into "try without install" with the pre-release 17.04 Alpha 2 zesty-ubuntu-desktop-alpha-270117[/COLOR][COLOR=#333333]-linuxium.iso[/COLOR][COLOR=#333333] from [/COLOR][linuxium]("http://www.linuxium.com.au/how-tos/runningubuntuontheintelcomputestick")[COLOR=#333333] and it worked without having to give any options to GRUB (my thanks to Ian Morrison for having builds available). So I installed it, leaving only the EFI partition intact and letting Ubuntu have the rest... It looks lovely and works OK so it is promising.[/COLOR]

[COLOR=#333333]Here comes my list of "confirmed" functionality:[/COLOR]
[COLOR=#333333]- WiFi works out of the box.[/COLOR]
[COLOR=#333333]- Micro SD card reader, works out of the box.[/COLOR]
[COLOR=#333333]- Bluetooth does not work.[/COLOR]
[COLOR=#333333]- Sound works out of the box, but there is a quirk, in the sound there are additional sharp clicking noises (like shot noise, electrical discharges) when audio is played.[/COLOR]
[COLOR=#333333]- Screen works, (brightness set to max) ending up in portrait but it can be solved by going into settings->screen and changing the setting. The login screen is still portrait but when logged in it switches to my last setting (have tried /usr/share/X11/[/COLOR][COLOR=#333333]xorg.conf.d/10-monitor.conf[/COLOR][COLOR=#333333] described above gives correct orientation at login but another quirk).  [/COLOR]
[COLOR=#333333]- Touchscreen works in portrait but in landscape the input coordinates are not transposed (learned that it can be fixed with [/COLOR][FONT=courier new][COLOR=#333333]xinput set-prop 'SIS0457:00 0457:1133' 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0 1[/COLOR][/FONT][COLOR=#333333])[/COLOR]
[COLOR=#333333]- Trackpad works but not multi-touch, I miss the two finger scrolling.[/COLOR]
[COLOR=#333333]- Cameras not tested, have not researched this, but nothing related to a camera has appeared automagically in Ubuntu so far...[/COLOR]
[COLOR=#333333]- Volume buttons don't work.[/COLOR]
[COLOR=#333333]- Taking it out of the dock and inserting it again works.[/COLOR]

[COLOR=#333333]In conclusion I feel that I have working mini Laptop with Ubuntu running now...[/COLOR]

---

### Post by swan-match on 2017-02-13
Hi,

I am Japanese, so I can't write English well.
sorry...

First, I use ubuntu 14.04 to raise the kernel to 4.5 series.

Brightness is there.
/sys/class/backlight/intel-backlight/brightness
But this file is sometimes missing...
In such a case please restart several times.

Sample to change the brightness.
> $ echo 30 > /sys/class/backlight/intel-backlight/brightness
This command must be run as root.
Therefore, the following command is executed on the terminal before execution.
> sudo bash
(I think that it is also possible to use the "sudo" and "tee" command.)

Please refer.(sorry japanese...)
[http://swan-match.hatenablog.com/entry/2016/06/13/234747](http://swan-match.hatenablog.com/entry/2016/06/13/234747)

Enjoy your Ubuntu life.

---

### Post by romis on 2017-02-26
> **larer said:**
> I'm reposting the first half of what I've posted on [Transformerforum]("http://www.transformerforums.com/forum/asus-transformer-book-t100-alternate-os-s-development/48417-any-success-alternative-os-t100ha-6.html").

[COLOR=#333333]First a confirming report saying the same thing as others have reported since end of January, aiming at making others confident in starting a new Ubuntu install on the T100HA is fairly easy so we can build momentum and get progress. I successfully booted into "try without install" with the pre-release 17.04 Alpha 2 zesty-ubuntu-desktop-alpha-270117[/COLOR][COLOR=#333333]-linuxium.iso[/COLOR][COLOR=#333333] from [/COLOR][linuxium]("http://www.linuxium.com.au/how-tos/runningubuntuontheintelcomputestick")[COLOR=#333333] and it worked without having to give any options to GRUB (my thanks to Ian Morrison for having builds available). So I installed it, leaving only the EFI partition intact and letting Ubuntu have the rest... It looks lovely and works OK so it is promising.[/COLOR]

[COLOR=#333333]Here comes my list of "confirmed" functionality:[/COLOR]
[COLOR=#333333]- WiFi works out of the box.[/COLOR]
[COLOR=#333333]- Micro SD card reader, works out of the box.[/COLOR]
[COLOR=#333333]- Bluetooth does not work.[/COLOR]
[COLOR=#333333]- Sound works out of the box, but there is a quirk, in the sound there are additional sharp clicking noises (like shot noise, electrical discharges) when audio is played.[/COLOR]
[COLOR=#333333]- Screen works, (brightness set to max) ending up in portrait but it can be solved by going into settings->screen and changing the setting. The login screen is still portrait but when logged in it switches to my last setting (have tried /usr/share/X11/[/COLOR][COLOR=#333333]xorg.conf.d/10-monitor.conf[/COLOR][COLOR=#333333] described above gives correct orientation at login but another quirk).  [/COLOR]
[COLOR=#333333]- Touchscreen works in portrait but in landscape the input coordinates are not transposed (learned that it can be fixed with [/COLOR][FONT=courier new][COLOR=#333333]xinput set-prop 'SIS0457:00 0457:1133' 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0 1[/COLOR][/FONT][COLOR=#333333])[/COLOR]
[COLOR=#333333]- Trackpad works but not multi-touch, I miss the two finger scrolling.[/COLOR]
[COLOR=#333333]- Cameras not tested, have not researched this, but nothing related to a camera has appeared automagically in Ubuntu so far...[/COLOR]
[COLOR=#333333]- Volume buttons don't work.[/COLOR]
[COLOR=#333333]- Taking it out of the dock and inserting it again works.[/COLOR]

[COLOR=#333333]In conclusion I feel that I have working mini Laptop with Ubuntu running now...[/COLOR]

So if things like sound work, with those patches, what needs to happen or what's the timeline on the patches being in the main kernel not requiring a non-standard iso?

---

### Post by mörgæs on 2017-03-01
Normally the developers don't post here so I think that few people are able to answer.

Is there any progress when booting the daily build of 17.04?

---

### Post by romis on 2017-03-20
> **mörgæs said:**
> Normally the developers don't post here so I think that few people are able to answer.

Is there any progress when booting the daily build of 17.04?

The latest 17.04 daily boots just fine, albeit in the wrong orientation (easily correctable) but the same issues, at least as far as sound not working, persist.

EDIT: Upon trying the patched kernel builds, sound was indeed working, and is identified as "chtrt5645" in the sound settings screen. I don't entirely know if this is applicable, but [http://lkml.iu.edu/hypermail/linux/kernel/1702.2/04904.html](http://lkml.iu.edu/hypermail/linux/kernel/1702.2/04904.html) has some references to that number, and if that's the case, planned for Linux kernel 4.11 version.

---

### Post by sputnikuk on 2017-04-17
Hi Everyone.Following the release of Kernel 4.11-rc6 i have a working implementation of inbuilt wifi and sound on the t100ha.  Link is at [www.feedthepenguin.org/t100ha.html](www.feedthepenguin.org/t100ha.html)

---

### Post by xdeidara1 on 2017-05-01
I made short tutorial for installing Manjaro on Asus T100HA.  Almost everything works, including backlight adjustment, built-in wifi ,bluetooth and sound. There are some minor bugs but after installing linux this  notebook works noticeable faster.

[https://github.com/TomaszBochenek/asus-t100ha-linux](https://github.com/TomaszBochenek/asus-t100ha-linux)

---

### Post by sweve on 2017-07-12
Thanks to sputnkuk I now have Ubuntu 17.04 running on my T100HA with touch screen, bluetooth, sound and wifi. All working brilliantly and I'm really pleased with the speed improvement over Windows 10.

Couple of observations that might assist. I downloaded the iso from the web but also got the v4.11.9 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). I then installed the OS. Rotated the screen and installed the updated kernel as well as the brmcfmac files provided by sputnik. Still didn't have working wifi so had to follows the steps provided by DebianOn at wiki.debian.org in relation to Asus X205TA where I copied the nvram file from /sys/firmware/efi/efivars to overwrite the brcm .txt file at /lib/firmware/brcm.

This step gave me working wifi but no connection to the internet! This turned out to be a known bug 1647031 where systemd uses the DNS stub resolver which fails to resolve CNAME records. I fixed this by hand editing the .conf file at /run/resolvfconf to use the OpenDNS nameservers, connected to the internet, udated and installed libnss-resolved which cures the issue.

I also noted that update-initramfs showed missing firmware files at /lib/firmware/i915/ which I obtained from [https://github.com/wkennington/linux-firmware/tree/master/i915](https://github.com/wkennington/linux-firmware/tree/master/i915)

update-initramfs: Generating /boot/initrd.img-4.11.9-041109-generic
W: Possible missing firmware /lib/firmware/i915/kbl_huc_ver02_00_1810.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_huc_ver01_07_1398.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_huc_ver01_07_1398.bin for module i915

I know have a great little pc that is blasting along. Hopefully this will help others in doing the same. Big thumbs up to sputnikuk

---

### Post by romis on 2017-09-07
As of 4.11 kernel there is official integrated (and functioning) audio over HDMI, but internal audio is still lacking. However, according to [http://lkml.iu.edu/hypermail/linux/kernel/1709.0/02777.html](http://lkml.iu.edu/hypermail/linux/kernel/1709.0/02777.html) it has been queued for addition in kernel version 4.14 (the next version, probably two or three months away) by Intel employee Pierre-Louis Bossart. Looking forward to that.

Note that 4.14 is also set to be an LTS kernel and also the kernel for Ubuntu's next LTS release.

---

### Post by Atulo on 2018-01-01
Much appreciation for posting this.  Wi-fi is working now, which is great.  Hope you have great day.

---

### Post by Br0wser on 2018-01-23
Hello, the link to the solution is broken. Could you tell me what you did to fix the Wifi? I am using the latest version of Ubuntu 17.10.

Thanks

---

### Post by wildmanne39 on 2018-01-23
Hi antoniomartinromer, you will have a much better chance of getting your wifi issue resolved by running the wireless script in my signature and posting the results in a new thread in the network section of the forum than posting in this large thread with more then one issue posted in it. 

Thanks

---

### Post by Atulo on 2018-02-13
What worked for me was to follow the steps at wiki.debian.org.  Just search for the Asus t100ha.

---

### Post by erotavlas on 2018-12-01
Hi,
I would like to install lubuntu 18.04 LTS 64 bit on this tablet. After several searches on the Web, I found that it still has some issues (wifi, camera, sound, bluetooth). Can you tell me what is the current status?
Otherwise I have to install windows 10 :(
Thank you

---

### Post by erotavlas on 2018-12-01
Hi,
I found the answer [https://drive.google.com/file/d/1VTzciobFlp7nO2A_M7RNoqYajN8c9AgR/view](https://drive.google.com/file/d/1VTzciobFlp7nO2A_M7RNoqYajN8c9AgR/view). It should work. I will report later.

---

### Post by touche3 on 2019-01-09
Is there a way to get the screen rotated permanent? 
For now I use the "xrandr -o left" command in startup application, but the problem is that if I put the laptop to sleep/close the lid and then put it on again, the screen is back to portrait mode.
I then have to logout and login again to get it back to landscape.

I tried editing /etc/gdm3/Init/Default but couldn't get it to work.


Also, is anyone having success to get hibernation to work? It would be nice to have that because right now, if I close the lid and the laptop is suppose to be in sleep mode, battery still drains.

---

### Post by boscarlu on 2019-01-12
> **erotavlas said:**
> Hi,
I found the answer [https://drive.google.com/file/d/1VTzciobFlp7nO2A_M7RNoqYajN8c9AgR/view](https://drive.google.com/file/d/1VTzciobFlp7nO2A_M7RNoqYajN8c9AgR/view). It should work. I will report later.

Hi, I have a T100TAF and followed the guide you posted. I managed to install everything but can't get the sound to work! On the Google Drive link in the guide, the folder with the sound files for the T100TAF is empty. So I tried with the general sound files and didn't work, then tried with both solutions A and B in the troubleshooting section and nothing changed.

I probably need the right files, but can't figure out which files and where... can you help?

-- EDIT --

FIXED by using the bytcr-rt5640 files at this link [https://drive.google.com/drive/folders/0B4DiU2o72FbudmZtSHRYNDdqZzQ](https://drive.google.com/drive/folders/0B4DiU2o72FbudmZtSHRYNDdqZzQ)
Audio files for other versions are also available at the same link.

---

### Post by jsmith87 on 2019-04-10
If you have an Asus Transformer Mini T102HA let me save you some time and trouble: it has a 64 bit UEFI boot loader (not 32 bit EFI) and installs out of the box with Ubuntu 18.10 (64-bit) off a live USB created from Rufus with an iso written to the usb in GPT format. You don't need to do any of those weird UEFI 32 bit hacks.


Nearly all of the hardware issues mentioned in these old T100 threads have been fixed. As of April 2019 there's still an issue with suspend/resume on lid close but UEFI boot loader, suspend/resume via the power menu, 5ghz wifi, touch screen, keyboard, and sound all work without tweaks.


If you happen to be trying other efi loaders and get a black screen that sends you back to the Aptio bios firmware setup, it's likely you have a 32 bit efi that you're trying to load with a 64 bit only UEFI on the T102HA. This cost me hours of pain and was not obvious, since all the instructions lead you down the old jwells bootia32.efi (32 bit UEFI) workaround. Occam&#8217;s razor killed me. If you're looking for additional bootloader info, check out refind, jwells posts, and a post from AdamW about how UEFI works.

---

### Post by Raditude on 2019-12-31
I have the T-100TAF. I ultimately want to install Ubuntu 18.04 LTS to run a Pi-Hole Server (for network-wide adblocking) and Home Bridge (to use unsupported devices with Apple HomeKit). I've found this site: [https://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](https://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html) and followed the tutorial to boot 13.04. I was able to get to GRUB, and when I chose "Try Ubuntu" I got this error: [IMG]http://raditu.de/img/ubuntu_error.jpg[/IMG]


It currently has Windows 8.1 installed, and there's files I need to backup, but the files are locked when booted into Windows. I want to boot to Live CD so I can back them up, before wiping and installing Ubuntu. I initially tried booting to 18.04, but it wouldn't get to GRUB. I found the tutorial above, and figured if I can get that (or any older version) to work, I can upgrade to 18.04 LTS.

Anyone have any insight as to why this won't boot, and detailed instructions to make it work? Please and thank you.

---

