---
title: "Mouse behaving bad after video driver reinstall"
date: 2014-03-28
forum: Installation &amp; Upgrades
---

### Post by childintime on 2014-03-28
Hello everyone,

After reinstalling nouveau graphics driver for my geforce 740m in my laptop, after several days I noticed that my mouse is behaving really bad. It's often clicking twice or releasing cursor randomly. I cannot use mouse to scroll cause it's releasing the cursor by itself at random times. I don't have xorg.conf file anymore also if that matter.

Do you have an idea how I shoot troubleshoot this problem?

---

### Post by GigabyteProduction on 2014-03-28
I don't think that could possibly be the graphics card driver, maybe look into testing if the problem persists with another driver, like the proprietary drivers for nvidia cards. You can either get the ones directly from nvidia at [http://www.geforce.com/drivers](http://www.geforce.com/drivers) or you can install an ubuntu package nvidia-319 that fixes problems with programs recognizing features but the ubuntu package is not fully up to date, an up to date ppa package exists but also causes a problem that makes you unable to start a user interface unless you remove a program called bumblebeed and remove the bumblebee file from modprobe.d (i had this problem but with the fix i am using the nvidia-331 package and it seems alright)

if the problem goes away, then it was the driver and you might have to stick with the proprietary driver if that's what you've gone with (and might be a better choice if you're a gamer), but if the problem persists, which is what i predict will happen, it might be something like a mouse driver or just plain out the mouse settings and i'll need more info on your hardware.

---

### Post by childintime on 2014-03-29
> **GigabyteProduction said:**
> I don't think that could possibly be the graphics card driver, maybe look into testing if the problem persists with another driver, like the proprietary drivers for nvidia cards. You can either get the ones directly from nvidia at [http://www.geforce.com/drivers](http://www.geforce.com/drivers) or you can install an ubuntu package nvidia-319 that fixes problems with programs recognizing features but the ubuntu package is not fully up to date, an up to date ppa package exists but also causes a problem that makes you unable to start a user interface unless you remove a program called bumblebeed and remove the bumblebee file from modprobe.d (i had this problem but with the fix i am using the nvidia-331 package and it seems alright)

if the problem goes away, then it was the driver and you might have to stick with the proprietary driver if that's what you've gone with (and might be a better choice if you're a gamer), but if the problem persists, which is what i predict will happen, it might be something like a mouse driver or just plain out the mouse settings and i'll need more info on your hardware.

I have a very bad luck with nvidia drivers. I tried installing nvidia-331 and nvidia-319 and after install all I get is black screen after login, and nothing can fix this. I also tried to manually download nvidia driver and install, same problem, that's why I don't want to even touch nvidia drivers for now (at least not until 14.04 comes out).

Now I just want to fix my mouse.

---

### Post by GigabyteProduction on 2014-03-29
If you installed nvidia-331 first, that's why it's all broken. I had the same problem, but if the problem really did come directly from the driver, then that's the only solution i can think of for this kind of problem.

---

### Post by childintime on 2014-03-29
> **GigabyteProduction said:**
> If you installed nvidia-331 first, that's why it's all broken. I had the same problem, but if the problem really did come directly from the driver, then that's the only solution i can think of for this kind of problem.

So I was looking for a solution, but could not find yet.

---

### Post by GigabyteProduction on 2014-03-29
The nvidia driver is my solution for the mouse, my solution for nvidia driver is: ```
 sudo add-apt-repository ppa:xorg-edgers/ppa ; sudo apt-get update ; sudo apt-get install nvidia-331 ; sudo apt-get remove bumblebee ; sudo rm /etc/modprobe.d/bumblebee.conf 
```

---

### Post by childintime on 2014-03-29
Thank you sir, but I literally tried every single guide on askubuntu on how to install nvidia driver and not a single one worked for me. Everytime I get black screen after login. So I am not trying my luck once again unless someone can 100% guarantee that this will work (which is probably not possible to guarantee anything).

That said, it should be a way to fix a mouse issues without reinstalling the driver right? Before I had nouveau driver and everything worked just fine.

---

### Post by GigabyteProduction on 2014-03-29
I'm sorry. Can i have the output of lspci -nnk?

---

### Post by childintime on 2014-03-29
Sure.

```
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
    Kernel driver in use: pcieport
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: i915
00:04.0 Signal processing controller [1180]: Intel Corporation 3rd Gen Core Processor Thermal Subsystem [8086:0153] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
01:00.0 3D controller [0302]: NVIDIA Corporation GK107M [GeForce GT 740M] [10de:0fdf] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: nouveau
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2c97]
    Kernel driver in use: ath9k
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5289] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: rtsx_pci
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: r8169
mosquito@mosquito-K56CB:~$ 
mosquito@mosquito-K56CB:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
    Kernel driver in use: pcieport
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: i915
00:04.0 Signal processing controller [1180]: Intel Corporation 3rd Gen Core Processor Thermal Subsystem [8086:0153] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
01:00.0 3D controller [0302]: NVIDIA Corporation GK107M [GeForce GT 740M] [10de:0fdf] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: nouveau
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2c97]
    Kernel driver in use: ath9k
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5289] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: rtsx_pci
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: r8169



```

---

### Post by GigabyteProduction on 2014-03-29
I'm sorry, it's not in this list, i didn't realize trackpads didn't register as pci until i just looked it up, i need cat /proc/bus/input/devices

---

### Post by childintime on 2014-03-29
```
cat /proc/bus/input/devicesI: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/LNXVIDEO:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input6
U: Uniq=
H: Handlers=event6 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0011 Vendor=0002 Product=000e Version=0000
N: Name="ETPS/2 Elantech Touchpad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input8
U: Uniq=
H: Handlers=mouse0 event8 
B: PROP=5
B: EV=b
B: KEY=e420 10000 0 0 0 0
B: ABS=661800011000003


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus WMI hotkeys"
P: Phys=asus-nb-wmi/input0
S: Sysfs=/devices/platform/asus-nb-wmi/input/input9
U: Uniq=
H: Handlers=rfkill kbd event9 
B: PROP=0
B: EV=100013
B: KEY=80000 0 800000000000 0 0 a1606f00900000 8200027800501000 e000000000000 0
B: MSC=10


I: Bus=0003 Vendor=13d3 Product=5165 Version=0823
N: Name="USB Camera"
P: Phys=usb-0000:00:1a.0-1.2/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0003 Vendor=04d9 Product=2011 Version=0110
N: Name="USB Keyboard"
P: Phys=usb-0000:00:14.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input41
U: Uniq=
H: Handlers=sysrq kbd event11 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=04d9 Product=2011 Version=0110
N: Name="USB Keyboard"
P: Phys=usb-0000:00:14.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input42
U: Uniq=
H: Handlers=kbd event12 
B: PROP=0
B: EV=13
B: KEY=300a000002000 0 0 78002044000 603878d801d6e9 1e000000000000 0
B: MSC=10


I: Bus=0003 Vendor=22d4 Product=2100 Version=0111
N: Name="Laview Co. Spawn_108a"
P: Phys=usb-0000:00:14.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input43
U: Uniq=
H: Handlers=mouse1 event13 
B: PROP=0
B: EV=17
B: KEY=7f0000 0 0 0 0
B: REL=103
B: MSC=10


I: Bus=0003 Vendor=22d4 Product=2100 Version=0111
N: Name="Laview Co. Spawn_108a"
P: Phys=usb-0000:00:14.0-3/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/input/input44
U: Uniq=
H: Handlers=sysrq kbd event14 
B: PROP=0
B: EV=120013
B: KEY=e080ffdf01cfffff fffffffffffffffe
B: MSC=10
B: LED=1f



```

---

### Post by GigabyteProduction on 2014-03-29
There is an open bug related to your touchpad in the kernel [https://bugzilla.kernel.org/show_bug.cgi?id=48161](https://bugzilla.kernel.org/show_bug.cgi?id=48161) check if you have the lost-sync symptoms that are shown here, if you do, then i think that means it's this bug or a variation of this same bug.

---

### Post by childintime on 2014-03-29
> **GigabyteProduction said:**
> There is an open bug related to your touchpad in the kernel [https://bugzilla.kernel.org/show_bug.cgi?id=48161](https://bugzilla.kernel.org/show_bug.cgi?id=48161) check if you have the lost-sync symptoms that are shown here, if you do, then i think that means it's this bug or a variation of this same bug.

Does not look like it. My problem is that mouse (and same for touchpad) cursor is often double click when I click just once or releases and immediately reapplies the pointer when I am holding it.

---

### Post by GigabyteProduction on 2014-03-29
Well i thought desyncronization could have applied to the machine suddenly thinking you released and then catching back up to realize that you're holding it. You could look into dmesg and see if errors are coming from the kernel driver. Could you boot into another os like windows and see if maybe your trackpad is going bad?

---

### Post by childintime on 2014-03-30
> **GigabyteProduction said:**
> Well i thought desyncronization could have applied to the machine suddenly thinking you released and then catching back up to realize that you're holding it. You could look into dmesg and see if errors are coming from the kernel driver. Could you boot into another os like windows and see if maybe your trackpad is going bad?

I tried Windows 8, everything works perfectly over there.

---

### Post by GigabyteProduction on 2014-03-30
It looks like you're always going to want a driver called synaptics to be loaded for these touchpads, and it looks like it might be a mouse driver issue if windows works but ubuntu isn't. Try synclient in the terminal and see if it says, "Couldn't find synaptics properties. No synaptics driver loaded?"

---

### Post by childintime on 2014-03-30
> **GigabyteProduction said:**
> It looks like you're always going to want a driver called synaptics to be loaded for these touchpads, and it looks like it might be a mouse driver issue if windows works but ubuntu isn't. Try synclient in the terminal and see if it says, "Couldn't find synaptics properties. No synaptics driver loaded?"

Didn't get that message.

```
Parameter settings:    LeftEdge                = 129
    RightEdge               = 3120
    TopEdge                 = 120
    BottomEdge              = 2103
    FingerLow               = 1
    FingerHigh              = 1
    MaxTapTime              = 180
    MaxTapMove              = 173
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 78
    HorizScrollDelta        = 78
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.050813
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 19
    VertHysteresis          = 19
    ClickPad                = 1
    RightButtonAreaLeft     = 1624
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 1822
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0



```

---

### Post by GigabyteProduction on 2014-03-30
Try adjusting the properties

man synaptics:
```
       Option "FingerLow" "integer"
              When  finger  pressure drops below this value, the driver counts
              it as a release. Property: "Synaptics Finger"

       Option "FingerHigh" "integer"
              When finger pressure goes above this value, the driver counts it
              as a touch. Property: "Synaptics Finger"
```

I think the read pressure when you're using it is just on the edge of "touched?" vs "not touched?", so maybe making it a little more sensitive would help
```
SYNOPSIS
       synclient [-lV?] [var1=value1 [var2=value2] ...]
```
```
synclient FingerLow=0.5 FingerHigh=0.5
```

---

### Post by childintime on 2014-03-30
> **GigabyteProduction said:**
> Try adjusting the properties

man synaptics:
```
       Option "FingerLow" "integer"
              When  finger  pressure drops below this value, the driver counts
              it as a release. Property: "Synaptics Finger"

       Option "FingerHigh" "integer"
              When finger pressure goes above this value, the driver counts it
              as a touch. Property: "Synaptics Finger"
```

I think the read pressure when you're using it is just on the edge of "touched?" vs "not touched?", so maybe making it a little more sensitive would help
```
SYNOPSIS
       synclient [-lV?] [var1=value1 [var2=value2] ...]
```
```
synclient FingerLow=0.5 FingerHigh=0.5
```

I can try, but does it have any impact on mouse? If not then it's obviously not a problem.

---

### Post by GigabyteProduction on 2014-03-30
That has impact on the sensitivity of the trackpad. if it doesn't help at all then it might just be misreadings from the mouse and i'll have to look for a command that'll show the direct input from the mouse (like jstest but for synaptics instead of a controller), but it's worth trying.

---

### Post by childintime on 2014-03-30
> **GigabyteProduction said:**
> That has impact on the sensitivity of the trackpad. if it doesn't help at all then it might just be misreadings from the mouse and i'll have to look for a command that'll show the direct input from the mouse (like jstest but for synaptics instead of a controller), but it's worth trying.

So I just enter: [COLOR=#000000][FONT=Ubuntu Mono]synclient FingerLow=0.5 FingerHigh=0.5

[/FONT][/COLOR]And so far everything works without any problem. :D

I am going to test it some more time, and update if that indeed solved the problem, so far looks like it did!

Thank you sir for you help.

---

### Post by GigabyteProduction on 2014-03-30
Yay! I think you also need to add those options to your xorg.conf, though, otherwise it'll reset at logout. I think i saw people mentioning a synaptics file in /etc/X11/xorg.conf.d/

---

### Post by childintime on 2014-03-30
> **GigabyteProduction said:**
> Yay! I think you also need to add those options to your xorg.conf, though, otherwise it'll reset at logout. I think i saw people mentioning a synaptics file in /etc/X11/xorg.conf.d/

The problem is I don't have xorg.conf file, do I need to create it?

Now what's inside /etc/X11:

```
app-defaults             xorg.conf.nvidia-xconfig-originalcore                     Xreset
cursors                  Xreset.d
default-display-manager  Xresources
fonts                    Xsession
rgb.txt                  Xsession.d
X                        Xsession.options
xinit                    XvMCConfig
xkb                      Xwrapper.config



```

---

### Post by GigabyteProduction on 2014-03-30
Yes, you can just make an xorg.conf file inside /etc/X11, but you have to do it as root, and there's also a structure to the file.

So looking at the manpage for synaptics:
```
       Section "InputDevice"
         Identifier "devname"
         Driver "synaptics"
         Option "Device"   "devpath"
         Option "Path"     "path"
         ...
       EndSection
```

While looking at the post where i got the hardware id for your mouse:
> **sladeinflame7 said:**
> ```
cat /proc/bus/input/devicesI: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/LNXVIDEO:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input6
U: Uniq=
H: Handlers=event6 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0011 Vendor=0002 Product=000e Version=0000
N: Name="ETPS/2 Elantech Touchpad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input8
U: Uniq=
H: Handlers=mouse0 event8 
B: PROP=5
B: EV=b
B: KEY=e420 10000 0 0 0 0
B: ABS=661800011000003


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus WMI hotkeys"
P: Phys=asus-nb-wmi/input0
S: Sysfs=/devices/platform/asus-nb-wmi/input/input9
U: Uniq=
H: Handlers=rfkill kbd event9 
B: PROP=0
B: EV=100013
B: KEY=80000 0 800000000000 0 0 a1606f00900000 8200027800501000 e000000000000 0
B: MSC=10


I: Bus=0003 Vendor=13d3 Product=5165 Version=0823
N: Name="USB Camera"
P: Phys=usb-0000:00:1a.0-1.2/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0003 Vendor=04d9 Product=2011 Version=0110
N: Name="USB Keyboard"
P: Phys=usb-0000:00:14.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input41
U: Uniq=
H: Handlers=sysrq kbd event11 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=04d9 Product=2011 Version=0110
N: Name="USB Keyboard"
P: Phys=usb-0000:00:14.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input42
U: Uniq=
H: Handlers=kbd event12 
B: PROP=0
B: EV=13
B: KEY=300a000002000 0 0 78002044000 603878d801d6e9 1e000000000000 0
B: MSC=10


I: Bus=0003 Vendor=22d4 Product=2100 Version=0111
N: Name="Laview Co. Spawn_108a"
P: Phys=usb-0000:00:14.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input43
U: Uniq=
H: Handlers=mouse1 event13 
B: PROP=0
B: EV=17
B: KEY=7f0000 0 0 0 0
B: REL=103
B: MSC=10


I: Bus=0003 Vendor=22d4 Product=2100 Version=0111
N: Name="Laview Co. Spawn_108a"
P: Phys=usb-0000:00:14.0-3/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/input/input44
U: Uniq=
H: Handlers=sysrq kbd event14 
B: PROP=0
B: EV=120013
B: KEY=e080ffdf01cfffff fffffffffffffffe
B: MSC=10
B: LED=1f



```

it shows these two paths for your mouse: ```
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input8
```

I think we need the one that says Phys, but it doesn't have any prefix to it (like /dev, which is what the Device option expects) so i want to test whether or not that's actually in /dev, so could you give the the output of: ```
ls /dev/
```

---

### Post by childintime on 2014-03-30
Sure

```
autofs              port      tty1   tty5       ttyS30block               ppp       tty10  tty50      ttyS31
bsg                 psaux     tty11  tty51      ttyS4
btrfs-control       ptmx      tty12  tty52      ttyS5
bus                 pts       tty13  tty53      ttyS6
cdrom               ram0      tty14  tty54      ttyS7
char                ram1      tty15  tty55      ttyS8
console             ram10     tty16  tty56      ttyS9
core                ram11     tty17  tty57      uhid
cpu                 ram12     tty18  tty58      uinput
cpu_dma_latency     ram13     tty19  tty59      urandom
disk                ram14     tty2   tty6       usb
dri                 ram15     tty20  tty60      v4l
ecryptfs            ram2      tty21  tty61      vboxdrv
fb0                 ram3      tty22  tty62      vboxnetctl
fd                  ram4      tty23  tty63      vboxusb
full                ram5      tty24  tty7       vcs
fuse                ram6      tty25  tty8       vcs1
hidraw0             ram7      tty26  tty9       vcs2
hidraw1             ram8      tty27  ttyprintk  vcs3
hidraw2             ram9      tty28  ttyS0      vcs4
hidraw3             random    tty29  ttyS1      vcs5
hpet                rfkill    tty3   ttyS10     vcs6
input               rtc       tty30  ttyS11     vcs7
kmsg                rtc0      tty31  ttyS12     vcsa
kvm                 sda       tty32  ttyS13     vcsa1
log                 sda1      tty33  ttyS14     vcsa2
loop0               sda2      tty34  ttyS15     vcsa3
loop1               sda3      tty35  ttyS16     vcsa4
loop2               sda4      tty36  ttyS17     vcsa5
loop3               sda5      tty37  ttyS18     vcsa6
loop4               sda6      tty38  ttyS19     vcsa7
loop5               sda7      tty39  ttyS2      vga_arbiter
loop6               sg0       tty4   ttyS20     vhost-net
loop7               sg1       tty40  ttyS21     video0
loop-control        shm       tty41  ttyS22     vmci
mapper              snapshot  tty42  ttyS23     vmmon
mcelog              snd       tty43  ttyS24     vmnet0
mei                 sr0       tty44  ttyS25     vmnet1
mem                 stderr    tty45  ttyS26     vmnet8
net                 stdin     tty46  ttyS27     vsock
network_latency     stdout    tty47  ttyS28     zero
network_throughput  tty       tty48  ttyS29
null                tty0      tty49  ttyS3



```

---

### Post by GigabyteProduction on 2014-03-30
isa0060 isn't there, so i'm really not sure what to put for the Device option... i need to research some more

---

### Post by GigabyteProduction on 2014-03-30
i think i figured it out
> To find out, go to /dev/input/by-id or /dev/input/by-path and do a ls -l  to find out which symlink points to which event<*>
and i did this on my system to figure out if it's by-path or by-id, it's by-id that gives you the event path. So could you please do:
```
ls -l /dev/input/by-id/
``` and give me the output?

---

### Post by childintime on 2014-03-30
```
total 0lrwxrwxrwx 1 root root 10 Mar 29 16:15 usb-04d9_USB_Keyboard-event-if01 -> ../event12
lrwxrwxrwx 1 root root 10 Mar 29 16:15 usb-04d9_USB_Keyboard-event-kbd -> ../event11
lrwxrwxrwx 1 root root 10 Mar 25 12:37 usb-Azurewave_USB_Camera_NULL-event-if00 -> ../event10
lrwxrwxrwx 1 root root 10 Mar 29 16:15 usb-Laview_Co._Spawn_108a-event-mouse -> ../event13
lrwxrwxrwx 1 root root 10 Mar 29 16:15 usb-Laview_Co._Spawn_108a-if01-event-kbd -> ../event14
lrwxrwxrwx 1 root root  9 Mar 29 16:15 usb-Laview_Co._Spawn_108a-mouse -> ../mouse1



```

---

### Post by GigabyteProduction on 2014-03-30
So the thing we have to do has to be terminal based because we're going to generate an xorg.conf which requires the x server not to be running, so it might be a good idea to get another pc and maybe ssh into this computer so you can use the paste ability (if you're going to use ssh, install a package named openssh-server on this computer and just use the command "ssh yourUserName@yourLocalIpAddress" of if on windows, use a program called putty).

You're going to need this data handy for your mouse:
```
       Section "InputDevice"
         Identifier "ETPS/2 Elantech Touchpad"
         Driver "synaptics"
         Option "Device"   "/dev/input/event13"
         Option "[COLOR=#000000][FONT=Ubuntu Mono]FingerLow[/FONT][/COLOR]"   "0.5"
         Option "[COLOR=#000000][FONT=Ubuntu Mono]FingerHigh[/FONT][/COLOR]"   "0.5"
       EndSection
```

I've never had an xorg.conf file generate the correct amount of screens, and requires some work to make wok correctly, but it still gives a file to start with. To generate your xorg.conf file, you're going to have to stop the currently running x server. You can do all of this from ssh if you choose to use ssh. ```
sudo service lightdm stop
``` And to generate the xorg.conf file: ```
sudo X -configure
``` The xorg.conf file should be in your home folder and called xorg.conf.new, open a terminal based text editor from your virtual terminal or ssh session. ```
nano ~/xorg.conf.new
``` Here is the generated xorg.conf.new file from my dell inspiron mini 10 with the changes i had to make:

```
### You need this entire section ###[COLOR=#008000][B]
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0[/B][/COLOR]
### Remove Extra X Screens (All but X Screen 0) ###
 [COLOR=#a52a2a]   Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    Screen      3  "Screen3" RightOf "Screen2"[/COLOR]
[COLOR=#008000][B]    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
[/B] **EndSection**[/COLOR]

### Keep the detected required files ###
[COLOR=#008000][B]Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection[/B][/COLOR]

### Keep the detected modules ###
[COLOR=#008000][B]Section "Module"
    Load  "glx"
EndSection[/B]
[/COLOR]### Keep the keyboard ###[COLOR=#008000][B]
Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection[/B]
[/COLOR]
### This is what you're going to replace with the mouse section we made at the beginning of the post ###
[COLOR=#800080]Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection[/COLOR]

### Keep the first monitor ###
[COLOR=#008000][B]Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection[/B][/COLOR]
[COLOR=#800000]
[/COLOR]### Remove Extra Monitors (only 1 Monitor per X Screen, which is why we keep first) ###[COLOR=#800000]
Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor3"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection
[/COLOR]
### Keep the first graphics card, this is your actual graphics card ###
[COLOR=#008000][B]Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "DRI"                    # <str>
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "VSync"                  # [<bool>]
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "ReprobeOutputs"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "VirtualHeads"           # <i>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection[/B][/COLOR]

### Remove extra graphics cards (1 Device per X Screen, which is why we keep the first one) ###
[COLOR=#800000]Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card1"
    Driver      "modesetting"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card2"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card3"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection[/COLOR]

### Keep only the first X Screen ###
[COLOR=#008000][B]Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"[/B][/COLOR]
### Remove these extra Display SubSections (All you want is the one with Depth 24 inside of it)
[COLOR=#800000]    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection[/COLOR][COLOR=#008000][B]
    SubSection "Display"[/B][/COLOR]
### Remove Viewport, let this be auto-detected ###
[COLOR=#800000]        Viewport   0 0[/COLOR][COLOR=#008000]
[B]        Depth     24
    EndSubSection
EndSection[/B][/COLOR]

### Remove extra X Screens ###
[COLOR=#800000]Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen3"
    Device     "Card3"
    Monitor    "Monitor3"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection[/COLOR]


```

If you're really lost while doing this, you can attach the xorg.conf.new file to your next post and have me try it. You can do ```
sudo service lightdm start
``` to get your gui back, and since we didn't put the file inside /etc/X11/ nothing's going to change, and since we restarted the X server, your mouse might go back to it's original settings and you might need to do synclient [COLOR=#000000][FONT=Ubuntu Mono]FingerLow=[/FONT][/COLOR]0.5 [COLOR=#000000][FONT=Ubuntu Mono]FingerHigh=[/FONT][/COLOR]0.5 again until we make the final xorg.conf file again.

If you do finish modifying your xorg.conf.new file, do ```
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf ; sudo service lightdm start
``` but if you get a black screen with a blinking cursor, something in the xorg.conf file is wrong. If this happens, do: ```
sudo mv /etc/X11/xorg.conf ~ ; sudo service lightdm start
``` and send me the file after your gui starts back up.

---

### Post by childintime on 2014-03-31
Now before we do that, I just wanted to say that now touch click on touchpad is not responsive at all. If I want to click somewhere I must use hardware button, because just tapping no longer registers as a click.

Edit: mouse started behaving bad again, and I entered that command again, but this time no help. So maybe it was just a coinsidence :(

---

### Post by GigabyteProduction on 2014-03-31
When it acts like this, try running synclient and see if any of the properties are changing

---

### Post by childintime on 2014-04-01
> **GigabyteProduction said:**
> When it acts like this, try running synclient and see if any of the properties are changing

```
Parameter settings:    LeftEdge                = 129
    RightEdge               = 3120
    TopEdge                 = 120
    BottomEdge              = 2103
    FingerLow               = 0
    FingerHigh              = 0
    MaxTapTime              = 180
    MaxTapMove              = 173
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 78
    HorizScrollDelta        = 78
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.050813
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 19
    VertHysteresis          = 19
    ClickPad                = 1
    RightButtonAreaLeft     = 1624
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 1822
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

```

Don't know if that's the reason but FingerLow and FingerHigh is 0. If I enter your command:
[COLOR=#000000][FONT=Ubuntu Mono]synclient FingerLow=0.5 FingerHigh=0.5
[/FONT][/COLOR]Those values still remain 0.

Edit: what's interesting that if I want to select select text and mark text from left to right, it most of the time works well, but if I mark text from right to left 90% if cannot mark normally. I tried to record it but now it worked other way around, so not sure if it's coincidence.

[IMG]http://i.imgur.com/txyEWV9.gif[/IMG]

I am holding cursor here all the time but the mouse releases and reaplies it my itself.

---

### Post by GigabyteProduction on 2014-04-01
I'm really unsure what could be causing the problem here. I feel like it'd have everything to do with the fact that the synaptics values but being at 0 should make it more sensitive to touch than 0.5. I'm not sure what to try now; the only thing i can think of is that xorg thing, because that'll make sure the value is what it should at the start of the driver, so if the value gets stuck or something stupid like this, it's not stuck at some crap value. Do you want to generate the xorg.conf.new and have me set up the file for you?

---

### Post by childintime on 2014-04-02
> **GigabyteProduction said:**
> I'm really unsure what could be causing the problem here. I feel like it'd have everything to do with the fact that the synaptics values but being at 0 should make it more sensitive to touch than 0.5. I'm not sure what to try now; the only thing i can think of is that xorg thing, because that'll make sure the value is what it should at the start of the driver, so if the value gets stuck or something stupid like this, it's not stuck at some crap value. Do you want to generate the xorg.conf.new and have me set up the file for you?

Well what can you do? I don't have second computer right now to login via ssh. By the way, I don't understand why my touchpad touch-click does not work anymore. I think it's after I input that command.

---

### Post by childintime on 2014-04-04
Does anyone have an idea? :(

---

### Post by childintime on 2014-04-06
Bump

---

### Post by childintime on 2014-04-13
Last bump

---

### Post by childintime on 2014-04-17
So I made fresh install of 14.04 LTS after wiping off 13.10, but still the same problem with the mouse :(

---

