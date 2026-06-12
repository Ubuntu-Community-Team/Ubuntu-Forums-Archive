---
title: "Acer Aspire 5745G"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by DisDis on 2010-07-04
My Problems and Solutions so far for the Acer Aspire 5745G running Ubuntu 10.04 (32-bit).

Much information is taken from here:
[Acer Aspire 4820TG TimelineX Thread]("http://newyork.ubuntuforums.org/showthread.php?t=1495123")

lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0a29] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be2] (rev a1)
02:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

```

**Installation**:**Smooth**!
**Problem 1:Ethernet not working**
Download new drivers(>=1.0.1.9)
[http://partner.atheros.com/Drivers.aspx]("http://partner.atheros.com/Drivers.aspx")
Unpack the driver into a folder "AR81F".
```

cd AR81F
sudo make install
sudo modprobe atl1e

```

**Problem 2: Multitouch**
Thanks marm0tte and  giova.86, it works.
Create touchpad.sh
```

#!/bin/sh
sleep 5

xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 2 8 0   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
xinput --set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3 4 5 6 7 8 9 

```

**Problem 3: Internal mic**
```

sudo apt-get install linux-backports-modules-alsa-lucid-generic-pae

```

**Problem 4:AC Adapter Status always showed as plugged in/Battery status not available**
[Either battery status icon not being shown, or the icon showing "Laptop battery is charged"]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/577825")
UP: BIOS 1.15 fixed

**Problem 5: Wifi works but it's disabled at logon**
BIOS 1.15 fixed

**Problem 6: "Special" button - not ejected DVD**
After installing "linux-backports-modules-alsa-lucid-generic", button disabled:(
UP(13.09.2010):
@lorped
latest udev update (151-12.1) fixes the "eject" button issue.
Now it works

**Problem 7: Fn+F3 disable Wifi but doesn't re enable it**
rfkill config?
UP:I installed the new kernel 2.6.35-6, bug fix.

**Problem 8: HDMI audio**
[Fix]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")
Edit /etc/modprobe.d/alsa-base.conf
```

options snd-hda-intel probe_mask=0xffff,0xfff2

```
Edit /etc/pulse/default.pa
```

load-module module-alsa-sink device=hw:1,3

```
Reboot.
Working(HDMI Video+Audio Stereo) fine on my Philips 32PFL7404

**Problem 9: Bluetooth**
Fix: New BIOS 1.16

---

### Post by clrg on 2010-07-04
Problem 0: You make people read too much. Please remove the solved stuff. Also, your thread's title isn't telling what kind of problem you have. Try "different issues with Acer Aspire 5745G notebook" or so
Problem 0.1: Don't buy Acer notebooks. They are of a very bad build quality. If I were to name the computer manufacturer the people I support have most problems with, it'd be Acer.

Problem 4: Your BIOS is buggy? I'm not sure I understood correctly. If so, update it.
Problem 6: You could use "wodim -eject"
Problem 7: Please "tail -f /var/log/messages", disable and try to re-enable the wireless, and show me the output.

Greetings

---

### Post by DisDis on 2010-07-04
> **clrg said:**
> Problem 0: You make people read too much. Please remove the solved stuff. Also, your thread's title isn't telling what kind of problem you have. Try "different issues with Acer Aspire 5745G notebook" or so

Problem 0.1: Don't buy Acer notebooks. They are of a very bad build quality. If I were to name the computer manufacturer the people I support have most problems with, it'd be Acer.

Problem 4: Your BIOS is buggy? I'm not sure I understood correctly. If so, update it.
Problem 6: You could use "wodim -eject"
Problem 7: Please "tail -f /var/log/messages", disable and try to re-enable the wireless, and show me the output.



4: My BIOS is last version(1.11)
Unplugged AC Adapter - Not show battery icon.

Battery is detected.
grep . /proc/acpi/battery/*/*
```

/proc/acpi/battery/BAT1/alarm:alarm:                   300 mAh
/proc/acpi/battery/BAT1/info:present:                 yes
/proc/acpi/battery/BAT1/info:design capacity:         4400 mAh
/proc/acpi/battery/BAT1/info:last full capacity:      4400 mAh
/proc/acpi/battery/BAT1/info:battery technology:      rechargeable
/proc/acpi/battery/BAT1/info:design voltage:          11100 mV
/proc/acpi/battery/BAT1/info:design capacity warning: 300 mAh
/proc/acpi/battery/BAT1/info:design capacity low:     132 mAh
/proc/acpi/battery/BAT1/info:capacity granularity 1:  32 mAh
/proc/acpi/battery/BAT1/info:capacity granularity 2:  32 mAh
/proc/acpi/battery/BAT1/info:model number:            BAT1      
/proc/acpi/battery/BAT1/info:serial number:           11        
/proc/acpi/battery/BAT1/info:battery type:            11        
/proc/acpi/battery/BAT1/info:OEM info:                11        
/proc/acpi/battery/BAT1/state:present:                 yes
/proc/acpi/battery/BAT1/state:capacity state:          ok
/proc/acpi/battery/BAT1/state:charging state:          charged
/proc/acpi/battery/BAT1/state:present rate:            unknown
/proc/acpi/battery/BAT1/state:remaining capacity:      unknown
/proc/acpi/battery/BAT1/state:present voltage:         10000 mV

```

7: 
Does not change /var/log/messages/ when press Fn+F3(WiFi control), but network-manager-gnome applet disabled/enabled menu(right mouse click) item "Wireless".

@wings:~$ rfkill list
```

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Fn+F3 - disabled menu item "Wireless"

@wings:~$ rfkill list
```

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

Fn+F3 - enabled menu item "Wireless"
```

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

When click to menu item "Wireless"
/var/log/messages/:
```

Jul  4 15:10:42 wings kernel: [  507.785700] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  4 15:10:49 wings kernel: [  514.876280] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```
WiFi connected and WiFi LED ON(fron panel)

---

### Post by tallmtt on 2010-07-17
Regarding the touchpad.sh section:

1. Save the file anywhere.
2. Make it executable (chmod +x touchpad.sh)
3. Have it autostart (system->preference->autostart application)

Thanks for the help - really helped me out today!

I also changed the last line in the script from:

xinput --set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3 4 5 6 7 8 9

to:

#xinput --set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3 4 5 6 7 8 9

As it added unwanted features :)  Like not focusing the window I wanted and closing tabs in Firefox.

---

### Post by erikkwonke2 on 2010-07-17
I also got an acer aspire 1. The problem.. when i try to install any OS my acer wont load up the disk. it goes straight to the safe mode option. ive tryied f1-f12 and i still cant get the instlation option to show up

---

### Post by terajiv on 2010-07-20
Hello DisDis
I could not get Wifi working...
Can you please explain about getting new kernel? I tried that but could not find new kernel for Ubuntu 10.04

---

### Post by DisDis on 2010-07-21
> **terajiv said:**
> Hello DisDis
I could not get Wifi working...
Can you please explain about getting new kernel? I tried that but could not find new kernel for Ubuntu 10.04

The new kernel is available here: 
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

Be prepared for the unexpected. After installing a new kernel (2.6.35-7), sound system always off at boot os.

---

### Post by terajiv on 2010-07-27
Thanks for the info DidDis
Any Idea how to get sound system working again?
Rajiv

---

### Post by DisDis on 2010-07-27
> **terajiv said:**
> Thanks for the info DidDis
Any Idea how to get sound system working again?
Rajiv
Sound is working, but always off at boot os.
Sorry for my english.

---

### Post by terajiv on 2010-07-28
Thanks DisDis
Much appreciated!
Rajiv

---

### Post by phz_swe on 2010-08-19
Firstly, thanks for this thread! It saved me a lot of time with these problems, enabling me to focus on other problems :-)

I have an Acer 5745G, running Ubuntu 10.04 with kernel 2.6.35-15 from [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa).

> **DisDis said:**
> 
Installation:Smooth!

Yes it was. I decided on a dual boot layout and partitioned the drive through GParted before starting the installation without a hitch.

> **DisDis said:**
> 
Problem 1:Ethernet not working
Download new drivers(>=1.0.1.9)
...

This driver isn't needed with kernel 2.6.35-15, so I guess this step will disappear with Ubuntu 10.10, for future reference. From what I've found, the atl1c driver (which is the one that 2.6.35 automatically loads) is broken in 2.6.32.

Right now, the step is needed to get access to a new kernel though, unless one puts the kernel .deb:s on the USB stick instead. I'd prefer the Ethernet driver way.

> **DisDis said:**
> 
Problem 2: Multitouch
Thanks marm0tte and  giova.86, it works.
Create touchpad.sh

The documentation for the different attributes is found at [http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html). I run a slightly modified version of touchpad.sh. Not very different, but I give it here in the open source spirit:
```

xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 2
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 1 0 0
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 2 0 1 0 0
xinput --set-button-map "SynPS/2 Synaptics TouchPad" 1 2 3 4 5 6 7 8 9
```
Compared to the version in the thread's original post, this lowers the two-finger pressure, makes a top-left corner tap simulate a "middle button" click and enables vertical scrolling with the touchpad's right edge.

I created a wrapper script:
touchpad.sh-gnomewrapper
```

#!/bin/sh
sleep 5
touchpad.sh

```
for startup purposes in Gnome specifically, since the "sleep 5" doesn't seem to be needed in other WM:s (and it is quite annoying during testing).

> **DisDis said:**
> 
Problem 3: Internal mic

Seems to be supported directly in the new kernel. There is, however, some quirks.

For the internal mic to work in Skype, I needed to start alsamixer, go to capture devices and lower the _left_ channel of "CAPTURE" to 0. Mic boost should also be off, otherwise the sound gets wildly distorted. Quite the same issue as at [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/459982/comments/17](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/459982/comments/17), more info on why it happens there.

For some strange reason the internal mic works in Gnome Sound Recorder without this workaround. It's hard to call it a bug when it actually does a better job than expected.

> **DisDis said:**
> 
[B]Problem 4:AC Adapter Status always showed as plugged in/Battery status not available
[Either battery status icon not being shown, or the icon showing "Laptop battery is charged"]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/577825")
Any ideas?

**Yes!** With the newly (2010-08-16) released BIOS update 1.15 for the Acer 5745G, the battery monitor started working! I guess they finally fixed their faulty code for the battery communication.

You find the new BIOS version through Acer's homepage (I don't want to link directly to the file because of the risk of someone blindly installing the wrong BIOS version for their computer). Be very aware of what you are doing when you update the BIOS. Acer even states that the warranty is out the window if one bricks the computer with a new BIOS version if their support hasn't explicitly suggested you to update BIOS.

The update scared me when the automatic reboot after update didn't work, and neither did Ctrl+Alt+Del, even though the lights flashed as if it rebooted. Only a power off through the power button made the computer usable again. Be warned.

After the BIOS update, you can see that it works either directly in the Gnome application, or by running
```

watch -d grep . /proc/acpi/battery/BAT1/*

```
which gives nice and informative terminal output.

> **DisDis said:**
> 
Problem 5: Wifi works but it's disabled at logon
...
UP:I installed the new kernel 2.6.35-6, bug fix.

I also needed to install the version of bcmwl-source found at [https://launchpad.net/ubuntu/+source/bcmwl/5.60.48.36+bdcom-0ubuntu5/+build/1781445](https://launchpad.net/ubuntu/+source/bcmwl/5.60.48.36+bdcom-0ubuntu5/+build/1781445). I installed the .deb:s from that page, after that WLAN worked after "sudo modprobe wl" (this is with the updated kernel version I run), and automatically after each reboot.

> **DisDis said:**
> 
Problem 6: "Special" button - not ejected DVD
...
Any ideas?

This works out-of-the-box with the new kernel version.

The button doesn't even generate an X event so it seems like the eject function is done completely by hardware. Even if the drive is busy, it ejects with a push of the button. It sounds weird that it stopped working after a software change as you described, there probably is more to it than my analysis, or maybe there is a hardware problem on your laptop. Does your button work in Windows/other OS:es in its current state?

> **DisDis said:**
> 
Problem 8: HDMI audio

I don't have the possibility to test this, but from what it seems it should work directly with this kernel via setup in Gnome's sound properties.

--

_**Other issues:**_

**Graphics**: With "Switchable" graphics enabled in the BIOS setup, I couldn't get the Nvidia graphics card to work. I fiddled for quite a while, encountering many strange behaviours and bugs, before I settled with just setting "Graphics: Discrete" in the BIOS setup. I haven't experimented with the vga_switcheroo module yet, I guess it might solve some of my problems, if not all.

Update: I got the functionality to turn off/on the Nvidia graphics card using [http://github.com/mkottman/acpi_call](http://github.com/mkottman/acpi_call). I can't, however, get X to utilize the Nvidia card in "Switchable" mode, still running into the main problem (from dmesg):
```

kernel: NVRM: failed to copy vbios to system memory.
kernel: NVRM: RmInitAdapter failed! (0x30:0xffffffff:909)
kernel: NVRM: rm_init_adapter(0) failed

```
and
```

NVIDIA(0): Failed to initialize the NVIDIA graphics device!

```
left behind in /var/log/Xorg.0. I have to specify
```

BusID "PCI:01:00:00"

```
in /etc/X11/xorg.conf to make the system even look at the Nvidia card instead of the Intel circuit, but as I showed it doesn't solve everything. I am left to writing this down as a BIOS bug of some kind.

It isn't a world of difference in power consumption between Intel (with Nvidia switched off through acpi_call) and Nvidia graphics, but it does give an extra hour or so of battery life on a full charge according to calculations. If I'm really desperate some time, "Switchable" and acpi_call might be a good option to have. The Nvidia card does quite a good job in clocking itself down under light load though (as is seen in nvidia-settings->PowerMizer), minimizing power consumption.

**Flash**: This isn't a 5745G specific issue I guess, but the Flash performance with the Nvidia card was crap with the Flash version included in Ubuntu (32-bit) (on the Intel card it was much better, but fullscreen video didn't work at all). I followed [http://www.sucka.net/2010/04/proper-install-of-flash-for-x64-ubuntu/](http://www.sucka.net/2010/04/proper-install-of-flash-for-x64-ubuntu/) to get HD playback running smoothly also with Nvidia (in the crystal ball I can see the day I will cope without Flash, but the WebM support isn't especially convincing today, either from Youtube or the browsers, so I torment myself with Flash plugins in the meantime).

---

### Post by DisDis on 2010-08-26
Great, the BIOS update has decided many issues.

---

### Post by Harrold on 2010-08-31
I have the 5745PG laptop and I ran the update for the 1.15 bios. Since then my laptop gets really hot and I can't turn the switchable graphics in the bios on or off. The function is grayed now for me... Any ideas how to fix this?

@phz_swe
Did you get the nvidia card running? I still get the message "NVIDIA(0): Failed to initialize the NVIDIA graphics device!" even with BusID PCI:1:0:0...

---

### Post by lorped on 2010-09-09
latest udev update (151-12.1) fixes the "eject" button issue.
Now it works

---

### Post by DisDis on 2010-09-11
New BIOS 1.16
Fixed Bluetooth and fixed:
```
Sep  9 21:29:19 wings kernel: [   78.666073] ACPI Error (dswload-0781): [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS
Sep  9 21:29:19 wings kernel: [   78.666112] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20090903/psloop-230)
Sep  9 21:29:19 wings kernel: [   78.666117] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.WMID.WMBA] (Node f741a1c8), AE_ALREADY_EXISTS
Sep  9 21:29:19 wings kernel: [   78.666137] ACPI: Marking method WMBA as Serialized because of AE_ALREADY_EXISTS error
```

This error sometimes crashing system, after booting.

---

### Post by DisDis on 2010-09-11
> **Harrold said:**
> I have the 5745PG laptop and I ran the update for the 1.15 bios. Since then my laptop gets really hot and I can't turn the switchable graphics in the bios on or off. The function is grayed now for me... Any ideas how to fix this?

@phz_swe
Did you get the nvidia card running? I still get the message "NVIDIA(0): Failed to initialize the NVIDIA graphics device!" even with BusID PCI:1:0:0...

You are using the NVIDIA driver or nouveau?
The NVIDIA driver blocked starting intel driver libs. Only way using nouveau.

---

### Post by rasmus91 on 2010-09-24
Hi.

I've had a problem enabling the nvidia graphics driver. but im gonna try enabling discrete in the bios, and install the nvidia graphics driver once again.

Im running 64 bit Ubuntu, and so far my computer haven't been able to get past the: Checking battery state in the startup process when the nvidia has been installed.

If anyone would like to have a closer look at my problem, look here: [http://ubuntuforums.org/showthread.php?t=1488705&page=8]("http://ubuntuforums.org/showthread.php?t=1488705&page=8")

I'll post here again once i've tried it. i hope you'll help me out. 

Thanks, Rasmus.

---

### Post by rasmus91 on 2010-09-24
phz_swe you're a genious!

Your discrete solution helped me greatly.

If you by some point get able to switch between the intel and the nvidia graphics, please, by all means give me a guide on how to do it!

Thanks for the help!

---

### Post by Caleb.Robertson on 2010-09-24
> **Harrold said:**
> I have the 5745PG laptop and I ran the update for the 1.15 bios. Since then my laptop gets really hot and I can't turn the switchable graphics in the bios on or off. The function is grayed now for me... Any ideas how to fix this?

@phz_swe
Did you get the nvidia card running? I still get the message "NVIDIA(0): Failed to initialize the NVIDIA graphics device!" even with BusID PCI:1:0:0...

How hot is your laptop getting? Mine is doing the same thing, I was thinking about updating the BIOS to 1.6 to see if it would help. It wasn't doing it out of the box. I turned it off at 65C-70C last night. Anyone else having this issue, or know a fix for it?

---

### Post by DisDis on 2010-09-25
Maybe it's GPU hot?
set PowerMizer minimal in xorg.conf:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    Option         "RegistryDwords" "PowerMizerDefaultAC=0x3"
EndSection
```
My GPU ~ 40C

---

### Post by Snake231088 on 2010-10-16
The PowerMizer shows always performance because the lcd is not recognized fine!
If you connect an external monitor and make the external monitor primary and disable the lcd of the laptop, the powermizer switch to powersave!
I also have the Aspire 5745G and i have a problem with ethernet.
When i connect at 1 Gb speedand for example watch a mkv on the network or i exchange a lot of data on the network, the connection stop to work!
Some help??? (sorry for my English)

---

### Post by DisDis on 2010-10-16
> **Snake231088 said:**
> The PowerMizer shows always performance because the lcd is not recognized fine!
If you connect an external monitor and make the external monitor primary and disable the lcd of the laptop, the powermizer switch to powersave!
I also have the Aspire 5745G and i have a problem with ethernet.
When i connect at 1 Gb speedand for example watch a mkv on the network or i exchange a lot of data on the network, the connection stop to work!
Some help??? (sorry for my English)
PowerMizer:
Switch to manual in powersave.[http://ubuntuforums.org/showpost.php?p=9886874&postcount=20]("http://ubuntuforums.org/showpost.php?p=9886874&postcount=20")
Ethernet:
1)Show logs.
2)What ethernet(AR8151) version of drivers?
3)Download new drivers.[http://partner.atheros.com/Drivers.aspx]("http://partner.atheros.com/Drivers.aspx")

---

### Post by Snake231088 on 2010-10-16
I can't install the new driver because i have Ubuntu 10.10 and when i try to compile the source of AR81Family i get an error.
Manually powersaving work fine but is only a workaround.

---

### Post by DisDis on 2010-10-16
> **Snake231088 said:**
> I can't install the new driver because i have Ubuntu 10.10 and when i try to compile the source of AR81Family i get an error.
Manually powersaving work fine but is only a workaround.
Powermizer:
NVidia drivers 260?
(Maybe 260 is broken. Try to revert to earlier versions.) 
Ethernet:
I now try to install.
...Error ```
Makefile:105: *** Linux kernel source not configured - missing autoconf.h.
```

---

### Post by Snake231088 on 2010-10-16
I have the same problem with the Ethernet.
What version of nvidia driver have you?
The only driver that worked fine was the first in ubuntu 10.04 (maybe 195.36.15).

---

### Post by DisDis on 2010-10-16
> **Snake231088 said:**
> I have the same problem with the Ethernet.
What version of nvidia driver have you?
The only driver that worked fine was the first in ubuntu 10.04 (maybe 195.36.15).
I have long install version 260.19.06, powermizer not work correct.

---

### Post by Snake231088 on 2010-11-14
I have long install version 260.19.12, powermizer not work correct.
PowerMizer always stay to max.
Any help?

---

### Post by rorenzo on 2010-11-20
Hi, thanks a lot for this forum... it's so much interesting... I have a question I have an Aspire 5745G and I'd like to know if it's possible to use the switch button to switch between intel and nvidia graphic card... I've upgraded the bios to solve the problem with eject button and others... thanks.

---

### Post by DisDis on 2010-11-24
> **rorenzo said:**
> Hi, thanks a lot for this forum... it's so much interesting... I have a question I have an Aspire 5745G and I'd like to know if it's possible to use the switch button to switch between intel and nvidia graphic card... I've upgraded the bios to solve the problem with eject button and others... thanks.

Hi.
At the moment it is not possible with nvidia proprietary drivers.

---

### Post by rorenzo on 2010-11-24
ok, thaks :)

---

### Post by david42 on 2011-02-13
Just to be sure I understand correctly, as I am considering buying this laptop:
it is not possible to switch between the nvidia and the intel video cards on the fly, however it is possible to use the nvidia card alone, with the nvidia proprietary drivers (with 3d acceleration and cuda support). Is this correct?

I am asking because in similar models, with both an intel and nvidia video cards, it is not possible to use the nvidia card, as the switching between the two must be handled by a (windows 7 only) software think called "optimus", which is not available under linux.

thank you

---

### Post by roshats on 2011-03-03
Do all work well especially wifi and lan after bios update and switching to discrete video card?

---

### Post by charafantah on 2011-03-23
I have an Acer 5745G and i had the same mic problem, i followed the steps, i adjusted alsamixer and it worked, however the mic was still not working in skype
so i had to remove the package pulseaudio, kill the remaining session, restart skype and choose my mic from skype settings, it worked that way.

---

### Post by phz_swe on 2011-03-24
> **david42 said:**
> Just to be sure I understand correctly, as I am considering buying this laptop:
it is not possible to switch between the nvidia and the intel video cards on the fly, however it is possible to use the nvidia card alone, with the nvidia proprietary drivers (with 3d acceleration and cuda support). Is this correct?

I am asking because in similar models, with both an intel and nvidia video cards, it is not possible to use the nvidia card, as the switching between the two must be handled by a (windows 7 only) software think called "optimus", which is not available under linux.

thank you
I'm running the Nvidia card only, by setting "Graphics"="Discrete" in the BIOS setup. If I choose "Switchable", only the Intel "card" is utilized.

> **roshats said:**
> Do all work well especially wifi and lan after bios update and switching to discrete video card?
For me: yes. I had no WLAN/LAN problem before BIOS update either, but I did have to install special drivers. I don't know if this is still the case with recent Ubuntu versions, or if everything works out of the box.

---

### Post by endlessz33 on 2011-04-01
hi guys, I have an interesting problem, i did a fresh install of ubuntu 10.10 and updated whichever suggested updates that the ubuntu 10.10 posted and installed them. 

the problem started when the OS suggested I activate the driver for the nvidia card. once the installation finished and I restarted I was stuck in the terminal.

asking me for login and password and it just sat there.

I can't get back to the GUI mode.

does anybody have any experience with this? how would I go about fixing it?

i have bios v1.16 and it doesn't seem to have an option to toggle between intel graphics and nvidia graphcis.

any input is much appreciated

thanks in advance

---

### Post by endlessz33 on 2011-04-01
anyone?

---

### Post by endlessz33 on 2011-04-02
bump

---

### Post by phz_swe on 2011-04-03
> **endlessz33 said:**
> hi guys, I have an interesting problem, i did a fresh install of ubuntu 10.10 and updated whichever suggested updates that the ubuntu 10.10 posted and installed them. 

the problem started when the OS suggested I activate the driver for the nvidia card. once the installation finished and I restarted I was stuck in the terminal.

asking me for login and password and it just sat there.

I can't get back to the GUI mode.

does anybody have any experience with this? how would I go about fixing it?

i have bios v1.16 and it doesn't seem to have an option to toggle between intel graphics and nvidia graphcis.

any input is much appreciated

thanks in advance
1.16 should still have the option to set the graphics mode to "Discrete" in the BIOS setup. For me it's the bottom option in the second screen in the setup. You press F2 during startup to reach the setup.

In case this doesn't work, you could try in text mode:
```
sudo modprobe -r nvidia
sudo service gdm start
```
or
```
sudo aptitude purge nvidia-current
sudo service gdm start
```

---

### Post by endlessz33 on 2011-04-04
> **phz_swe said:**
> 1.16 should still have the option to set the graphics mode to "Discrete" in the BIOS setup. For me it's the bottom option in the second screen in the setup. You press F2 during startup to reach the setup.

In case this doesn't work, you could try in text mode:
```
sudo modprobe -r nvidia
sudo service gdm start
```or
```
sudo aptitude purge nvidia-current
sudo service gdm start
```

Thanks for the Reply! as far as the bios options, the only option is see is SATA configuration and the choices are AHCI and IDE, was that it?

also to elaborate more on the problem, I get the problem when i activate the driver or if I download the driver directly from nvidia (.run extension). 

I suppose my question now is two-fold for me: 


[LIST]
[*]if there is a certain way you're suppose to install the nvidia drivers for this laptop?
[/LIST]
(I have done it through linux hardware drivers and nvidia website)


[LIST]
[*]is it possible to just switch to using nvidia for graphics processing once I manage t get it running?
[/LIST]
Thanks!

---

### Post by endlessz33 on 2011-04-05
bump.

---

### Post by phz_swe on 2011-04-06
> **endlessz33 said:**
> Thanks for the Reply! as far as the bios options, the only option is see is SATA configuration and the choices are AHCI and IDE, was that it?

also to elaborate more on the problem, I get the problem when i activate the driver or if I download the driver directly from nvidia (.run extension). 

I suppose my question now is two-fold for me: 


[LIST]
[*]if there is a certain way you're suppose to install the nvidia drivers for this laptop?
[/LIST]
(I have done it through linux hardware drivers and nvidia website)


[LIST]
[*]is it possible to just switch to using nvidia for graphics processing once I manage t get it running?
[/LIST]
Thanks!
1. There is no special way to install the Nvidia driver. It's supposed to be done in the usual way. The package manager should work fine, probably better than the "official" Nvidia way nowadays.

2. There are som experimental approaches regarding switching cards on and off after boot, se my earlier posts in this thread. I haven't been able to get anything good out of it though.

--

As I said, you're supposed to be able to switch graphics mode in the BIOS setup, even with 1.16. The choice is below the one you mentioned about SATA on my laptop. I have BIOS 1.15.

Are you sure you have a version of the laptop with the Nvidia circuit? It seems that Acer also sells a model wih only the integrated Intel graphics (I guess that's the one called just "5745" as compared to "5745G"). It would be very logical if that's what you have, except the part where Ubuntu suggested the Nvidia driver.

```
lspci | grep VGA
``` should tell you something about the graphics circuit. If nothing Nvidia related is mentioned by lspci, and you don't have an option to explicitly enable Nvidia graphics in the BIOS setup, then you should remove the Nvidia drivers and run on Intel graphics.

If the Nvidia circuit demonstrably works in Windows, then something is weird. Without that information it could be eiher a faulty circuit, a laptop without Nvidia graphics or a new laptop revision without possibility to reveal the Nvidia chip.

---

### Post by endlessz33 on 2011-04-07
I do have the nvidia graphics chip as stated by that command also the sticker on the laptop also the box says so as well.

my speculation is that bios 1.16 did away with the option of switching between Intel and nvidia. in which case I got screwed right off the bat since I bought the laptop fairly recent and it had bios 1.16 installed already.

bugger....anyway. I've decided to wait it out and just run integrated Intel graphics in the meantime as there are no solutions for my issue as far as I know

Thank you for your thoughts!

---

### Post by phz_swe on 2011-04-10
> **endlessz33 said:**
> I do have the nvidia graphics chip as stated by that command also the sticker on the laptop also the box says so as well.

my speculation is that bios 1.16 did away with the option of switching between Intel and nvidia. in which case I got screwed right off the bat since I bought the laptop fairly recent and it had bios 1.16 installed already.

bugger....anyway. I've decided to wait it out and just run integrated Intel graphics in the meantime as there are no solutions for my issue as far as I know

Thank you for your thoughts!
As a final step in the error seeking procedure, I'd try to start Windows and confirm that the Nvidia circuit works there.

There is also a fairly recent BIOS update available (1.18 ). Could be worth a shot, regardless of what the changelog says.

EDIT: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics) - you can also try this. I haven't had any luck, but it was a long time (in computer time measured) since I tested it.

---

### Post by terajiv on 2011-04-21
How to Install BIOS without Windows OS? I have completely wiped out Windows from Laptop and I have only got Ubuntu 10.10
How can I install BIOS?

---

### Post by phz_swe on 2011-04-27
> **terajiv said:**
> How to Install BIOS without Windows OS? I have completely wiped out Windows from Laptop and I have only got Ubuntu 10.10
How can I install BIOS?
If you don't have any problems with your current BIOS, of course you don't need to update. Only do it if it is truly needed.

Acer provides an DOS-compatible update file. Boot your laptop into DOS via USB or something (google for the procedure, not a specific Ubuntu question) and run the file.

I think your luck with Wine or virtualization would be slim. In the worst case it could corrupt your BIOS firmware, which would be Bad, "return your laptop to the manufacturer"-bad.

---

### Post by phz_swe on 2011-06-17
I ran into [http://ubuntuforums.org/showpost.php?p=10950523&postcount=7](http://ubuntuforums.org/showpost.php?p=10950523&postcount=7) (my problem and solution) with this laptop after upgrading to 11.04. It concerned reboots when using the WLAN card on battery power.

---

