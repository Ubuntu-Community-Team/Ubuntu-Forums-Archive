---
title: "HTC Shift"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by wollloch on 2010-12-11
Hello everybody,
I'm trying to run ubuntu netbook remix 10.10 on an HTC Shift X9500. Installation so far has worked flawlessly from an USB flash device. And fortunately nearly everything is working out of the box. I also followed [this manual]("http://pof.eslack.org/blog/2008/04/14/linux-on-htc-shift/") to get things running. But it is rather outdated and leaves some things unresolved.
I have the following issues left for which I kindly ask if anybody knows any solution:

**[1] Touch screen**
It is identified correctly by xinput. However, calibration is off, the y-axis is reversed. In addition, the mouse pointer performs movements pretty jumpy. Its just not smooth.
I installed the 10.04 package of [xinput_calibrator]("http://www.freedesktop.org/wiki/Software/xinput_calibrator") to calibrate the screen. It works, however, on each reboot I need to calibrate the screen again. xinput_calibrator suggests the following:

```
--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
    Identifier    "calibration"
    MatchProduct    "HTC Shift EC TouchScreen"
    Option    "Calibration"    "56 2008 1975 79"
EndSection

```But there is no /etc/X11/xorg.conf.d/ in 10.10. I tried using /etc/X11/Xsession.d but without success. Does anybody know how to do touchscreen calibration in 10.10 properly and with permanent effect?
Also, when rotating the screen, the touch input doesn't adapt to the new orientation. Which means, when moving in one direction on the screen the pointer moves any other direction (depending on the new orientation). Is there a way to fix that?

**[2] TouchPad**
In addition to the ordinary pri and sec mouse buttons the shifts SynPS/2 Synaptics TouchPad has two extra buttons (sometimes referred to as the 'shift buttons'). They are recognized and work.
```

$ xinput test "SynPS/2 Synaptics TouchPad"
button press   1 
button release 1 
button press   3 
button release 3 
button press   6 
button release 6 
button press   5 
button release 5 

```However, they do not perform any action. I want to assign commands to buttons 5 and 6. Button 6 should execute the command '[hsect2]("http://pof.eslack.org/blog/2008/06/11/shiftbuttons-htc-shift-hardware-buttons-control/")' while button 5 should execute 'shift-rotate.sh' (which is a script rotating the screen 90 degrees left or back to normal). So far I have not found out how to map commands to touchpad button presses although I think it should be fairly easy. Could anybody tell me how to do this?
PS: I am aware of [shiftbuttons]("http://pof.eslack.org/blog/2008/06/11/shiftbuttons-htc-shift-hardware-buttons-control/"). However, this tool doesn't work anymore in 10.10. Error: 'Cannot access shared memory. Is SHMconfig enabled?'. Afaik due to missing xorg.conf[B]

[3] Wifi Marvell SD8686 Wireless Lan SDIO[/B]
This is by far the most annoying missing part. Apparently this thing is connected via internal usb to an internal sdio interface. What a mess. Anyhow, my system doesn't even recognize it or show it anywhere. I turned wifi on using hsect2 (see above). But still no luck (Bluetooth is working fine though). I tried ndiswrapper which installs the drivers but reports: 'Hardware present: no'. The manual [here]("http://pof.eslack.org/blog/2008/04/14/linux-on-htc-shift/") suggests using [ubuntu modules]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.24/") and a proprietary firmware from [Marvell]("http://www.marvell.com/drivers/driverDisplay.do?dId=200&pId=38"). But the modules are quite outdated and the link to Marvell's firmware is dead. I tried the support search function on their page but without luck. Google also just finds threads with 'Any luck?' :D. So I am stuck here. Has anybody figured out how to get this wifi adapter running under linux? If yes (kudos!) then how?

Finally some system information:
```

$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; HTC Shift EC TouchScreen                    id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Apple, Inc Apple Keyboard                   id=10    [slave  keyboard (3)]
    &#8627; Apple, Inc Apple Keyboard                   id=11    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                              id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

``````

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:06.0 SD Host controller: C-guys, Inc. CG200 Dual SD/SDIO Host controller device (rev 09)

``````

$ lsusb
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
Bus 001 Device 007: ID 05ac:0221 Apple, Inc. Aluminum Keyboard (ISO)
Bus 001 Device 006: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 005: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 001 Device 004: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Thank you all for the time of reading and thinking about this. Any help with either of the problems is highly appreciated!

wollloch

---

