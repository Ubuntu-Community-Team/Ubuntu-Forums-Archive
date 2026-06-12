---
title: "Acer Aspire 4820TG TimelineX Thread"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by Amivit on 2010-05-27
My Problems and Solutions so far for the Acer Aspire TimelineX 4820TG running Ubuntu 10.04 (32-bit).
I created this thread because this laptop is very new, but I see high potential in it and think more and more user will show up with the 4820TG aswell. Please share your solutions/problems and feel free to help me try solving any of these problems.
I am very new to linux and would love to start using it for real, but until I solve these problems I'm unfortunately going to keep on using Windows in my dual-boot setup.

Installation:Smooth!
**Problem 1:Ethernet not working**
Solution:
Download driver, specifically "AR81Family Linux Driver" from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx).
```
tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
sudo su
apt-get install build-essential
apt-get install linux-generic-header
make install
modprobe atl1e
```

**Problem 2:AC Adapter Status always showed as plugged in/Battery status not available**
Solution:
???
**Problem 3: Power consumption way higher than necessary**
Because this laptop has switchable graphics, and I am only interested in using the low-power intel onboard and not the ATI 5470. Can't find out how to only use the intel and deactivate the ATI. Not possible through BIOS, only possible to deactivate the Intel to only use the ATI :( Getting 2 hours instead of the promised 5-8 hours.
Solution:
???

---

### Post by giova.86 on 2010-05-28
Hy I have the same notebook. I had already resolve the problem of Ethernet card. I don't know how to fix the battery problem, but I can help you with this:

**Problem 4: Multitouch**

1) create a file named .touchpad.sh in your  home
2) open the file and copy these line into it:

```
#!/bin/sh

sleep 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
```

The sleep time is necessary.
3) make the file executable with
```
chmod u+x ./.touchpad.sh
```
4) add the file file in autostart application: system->preference->autostart application

---

### Post by Amivit on 2010-05-28
giova.86, awesome! I didn't even realize it wasen't working as I didn't even know the laptop had that feature. I testet it in Windows and it worked. After applying your fix it worked in Ubuntu aswell! :) One step closer to being able to use Ubuntu fulltime :b 

Keep it coming people! One of the things I admire with the Linux community, everyone being able to help eachother ^^

---

### Post by jeffysg on 2010-05-30
any 4820TG users got their wifi working?:o

---

### Post by Amivit on 2010-05-30
> **jeffysg said:**
> any 4820TG users got their wifi working?:o

Mine worked by default. Even injection with aircrack :O
What does your lspci say?

---

### Post by jeffysg on 2010-05-31
I've requested for help in this thread as well.
[URL="http://ubuntuforums.org/showthread.php?p=9368364#post9368364"]http://ubuntuforums.org/showthread.php?p=9368364#post9368364
[/URL]



00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by jeffysg on 2010-05-31
bump!](*,)

---

### Post by jeffysg on 2010-06-01
bump!

---

### Post by jeffysg on 2010-06-02
bump bump bump!

---

### Post by rufferson on 2010-06-09
> **Amivit said:**
> **Problem 3: Power consumption way higher than  necessary**
Because this laptop has switchable graphics, and I am only interested in  using the low-power intel onboard and not the ATI 5470. Can't find out  how to only use the intel and deactivate the ATI. Not possible through  BIOS, only possible to deactivate the Intel to only use the ATI :( Getting 2 hours  instead of the promised 5-8 hours.
Solution:
???

You can check [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/) for switchable  graphic solution example.
 Kernel >=2.6.34 (containing switcheroo) is available via ppa - f.i.  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc7-lucid/")

---

### Post by Amivit on 2010-06-11
bump, would love help finding a solution to my 2 unsolved issues :confused:

---

### Post by marm0tte on 2010-06-11
Hello all and first of all, sorry for my French's bad English :)


I join this post because, I've a 4820TG too and of course the same problems :(


**Problem 1:Ethernet not working**

Thanks Amivit, my Ethernet card works like a charm now ;)
I've used the following commands :

```
sudo apt-get install build-essential
### Download the linux driver AR81Family-Linux-v1.0.1.9.tar.gz
cd ~/Downloads
mkdir AR81Family-Linux-v1.0.1.9
mv AR81Family-Linux-v1.0.1.9.tar.gz AR81Family-Linux-v1.0.1.9
cd AR81Family-Linux-v1.0.1.9
tar xvzf AR81Family-Linux-v1.0.1.9.tar.gz
cd src
make
sudo make install
sudo modprobe atl1e
```
**Problem 2:AC Adapter Status always showed as plugged in/Battery status not available**

I'm working on it. It seems that this is the most complicated problem, and it will be hard to solve.

I've upgraded the BIOS from v1.02 to 1.04_A_A but it doesn't solved the problem ...
This problem seems to came from the DSDT in the BIOS/Setup of this ACER laptop because it's buggy.

So, I've extracted the DSDT from the BIOS and recompiled it and here is the result :

> ~/Downloads/acpica-unix-20100528/tools/acpixtract$ ../../compiler/iasl -tc DSDT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Jun 11 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

DSDT.dsl  2545:                     0x00000000,         // Length
Error    4122 -                              ^ Invalid combination of Length and Min/Max fixed flags

DSDT.dsl  2552:                     0x00000000,         // Length
Error    4122 -                              ^ Invalid combination of Length and Min/Max fixed flags

DSDT.dsl  5231:                     Method (_Q0E, 0, NotSerialized)
Warning  1088 -                                ^ Not all control paths return a value (_Q0E)

DSDT.dsl  6596:                                 Name (_T_0, Zero)
Remark   5111 -            Use of compiler reserved name ^  (_T_0)

DSDT.dsl  6600:                                     Name (_T_1, Zero)
Remark   5111 -                Use of compiler reserved name ^  (_T_1)

DSDT.dsl  6659:                                 Name (_T_0, Zero)
Remark   5111 -            Use of compiler reserved name ^  (_T_0)

DSDT.dsl  6663:                                     Name (_T_1, Zero)
Remark   5111 -                Use of compiler reserved name ^  (_T_1)

DSDT.dsl  6831:                                 Name (_T_0, Zero)
Remark   5111 -            Use of compiler reserved name ^  (_T_0)

DSDT.dsl  6835:                                     Name (_T_1, Zero)
Remark   5111 -                Use of compiler reserved name ^  (_T_1)

DSDT.dsl  6894:                                 Name (_T_0, Zero)
Remark   5111 -            Use of compiler reserved name ^  (_T_0)

DSDT.dsl  6898:                                     Name (_T_1, Zero)
Remark   5111 -                Use of compiler reserved name ^  (_T_1)

DSDT.dsl  7777:                     Name (_T_0, Zero)
Remark   5111 -                              ^ Use of compiler reserved name (_T_0)

DSDT.dsl  7870:                     Name (_T_0, Zero)
Remark   5111 -                              ^ Use of compiler reserved name (_T_0)

DSDT.dsl  7874:                         Name (_T_1, Zero)
Remark   5111 -    Use of compiler reserved name ^  (_T_1)

DSDT.dsl  7941:                         Name (_T_2, Zero)
Remark   5111 -    Use of compiler reserved name ^  (_T_2)

DSDT.dsl  8008:                 Method (OEMN, 0, NotSerialized)
Warning  1088 -                            ^ Not all control paths return a value (OEMN)

DSDT.dsl  8105:                     Name (_T_0, Zero)
Remark   5111 -                              ^ Use of compiler reserved name (_T_0)

DSDT.dsl  9124:                         Name (_T_0, Zero)
Remark   5111 -    Use of compiler reserved name ^  (_T_0)

DSDT.dsl  9152:                             Name (_T_1, Zero)
Remark   5111 -        Use of compiler reserved name ^  (_T_1)

DSDT.dsl  9182:                     Name (_T_0, Zero)
Remark   5111 -                              ^ Use of compiler reserved name (_T_0)

DSDT.dsl  9248:                 Method (_WED, 1, NotSerialized)
Warning  1088 -                            ^ Not all control paths return a value (_WED)

DSDT.dsl  9248:                 Method (_WED, 1, NotSerialized)
Warning  1081 -                            ^ Reserved method must return a value (Integer/String/Buffer required for _WED)

DSDT.dsl  9254:                             Return (OEMN ())
Warning  1093 -                                        ^ Called method may not always return a value

DSDT.dsl  9399:                 Method (WMBH, 3, NotSerialized)
Warning  1088 -                            ^ Not all control paths return a value (WMBH)

DSDT.dsl  9456:                 Method (WMBI, 3, NotSerialized)
Warning  1088 -                            ^ Not all control paths return a value (WMBI)

DSDT.dsl  9518:                 Method (WMBJ, 3, NotSerialized)
Warning  1088 -                            ^ Not all control paths return a value (WMBJ)

DSDT.dsl  9616:             Name (_T_0, Zero)
Remark   5111 -                      ^ Use of compiler reserved name (_T_0)

DSDT.dsl  9661:             Name (_T_0, Zero)
Remark   5111 -                      ^ Use of compiler reserved name (_T_0)

ASL Input:  DSDT.dsl - 12143 lines, 396315 bytes, 5129 keywords
Compilation complete. 2 Errors, 8 Warnings, 18 Remarks, 6 Optimizations
It seems that the acer developers had compile the dsdt with errors and warnings. Windows get ride of it because it accepts bugs in DSDT but the Linux kernel ignore it !


I've tried to solved the 2 errors but I'm blocked with the warnings ...
**I need help from a ASL (language used by to develop DSDT) guru**

Maybe the 2 errors solved are sufficient to make working the battery status ???
I will test it soon.


**Problem 3: Power consumption way higher than necessary**

Linked to the 2nd problem (DSDT / ACPI problems)
I will test the rufferson proposition


**Problem 4: Multitouch**

Thanks giova.86, it works.


**Problem 5: Wifi works but it's disabled at logon**

To solve this :
```
sudo aptitude install wicd
sudo aptitude remove network-manager network-manager-gnome
sudo reboot
## Open wicd, under your wifi network name check the box "Connect automatically to this network" and join your wifi network.
```
**Problem 6: Fn+F3 disable Wifi but doesn't re enable it**

Do not use this key combination ???
Solve the ACPI DSDT problem ???


**Problem 7: Sometime the touchpad make mouse crazy ...**

Go into "System" / "Preferences" / "Mouse"
Check the box "Disable touch-pad while typing on the keyboard"
Unckeck "Activate Mouse Clicks with the touch-pad"
Uncheck "Activate the horizontal scrolling"



Is anyone have test the webcam, the jack headphone and the sound card input microphone ???

---

### Post by rufferson on 2010-06-14
Hi **marm0tte**, thanks for a nice follow-up. I have a question however in view of
> **marm0tte said:**
> **Problem 6: Fn+F3 disable Wifi but doesn't re enable it**

Do not use this key combination ???
Solve the ACPI DSDT problem ???


It does enable it actually, but it doesn't send any kind of acpi/hal/udev/dbus notification/event so you need to re-enable it manually after enabling via Fn - executing f.i. ifdown wlan0;ifup wlan0;

I don't use network manager but have configured wifi in system scripts (/etc/network/interfaces + /etc/wpa.conf) and wifi works on boot. I guess it is the same consequence of acpi initialisation or missing event so software relying on that part is missing its turn.

My question is - how to enable Bluetooth adapter under linux? Fn+F3 toggles WiFi interface only, and BT is not seen neither by me witn lspci/lsusb nor by bluetoothd/hciconfig.
Moreover, sometimes (actually once so far) after booting from Linux to Windows even Win can't see BT adapter any more and Fn+F3 switches WiFi only as well. Power-cycling returned BT back in Win, but Linux ignores it persistently.

There are also some useful links here: [https://help.ubuntu.com/community/AspireTimeline](https://help.ubuntu.com/community/AspireTimeline)

---

### Post by giova.86 on 2010-06-15
**Problem 8: integrated microphone**
If you have some problems with the integrated microphone, to solve it you have to update the alsamixer to version 1.0.23. And if you need a guide, look this: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

---

### Post by marm0tte on 2010-06-15
Giova.86,

alsamixer is in version 1.0.22 on my laptop and the microphone jack and webcam inputs work.
Maybe because I've upgrade the bios/setup from v1.02 to v1.04 and also installed the ubuntu updates


Thanks rufferson, you're right, ifup will be the best and quickest way to re-enable wifi after the Fn+F3 combination, lol
But anyway I like the command line so it will rocks ;)

Otherwise, for the BT question, do you mean that you have bluetooth integrated in your laptop ? If yes witch laptop version do you have ?


Talking about the vgaswitchero, i've try to recompil my kernel but compiler crash after 1 hour, I thought I have uncheck to many modules in the make menuconfig :lolflag:  I will try again this week end.
Do you know how to integrate vgaswitcheroo module without recompiling the kernel and using the ppa ubuntu kernel deb files ?


For the DSDT problem, I have debug 2 errors but again 18 warnings and cannot found the solution to debug it. So I've inject the DSDT.aml file into my kernel 2.6.34 and ... It doesn't solve the battery detection problem :( but the Fn+F3 works well and it seems faster. Also the dmesg show less ACPI errors.
I also attach the DSDT for those who want to test it.
Here is a post explaining how to inject it into the kernel :
[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)


Is someone can know a ASL / DSDT / ACPI guru who can help me ?

---

### Post by rufferson on 2010-06-16
Yes, I mean integrated BT BCM92046 into 4820TG-436G64Mn. Under windows pressing Fn+F3 switches wireless adapters in following order: WiFi on, WiFi + BT on, WiFi + BT off. I.e. you can have either wifi + bt or wifi only (but not bt only).
Under linux i see that Fn switches wifi only (in output of iwconfig, after pressing Fn+F3 TX Power becomes off). 
The same behaviour i faced once after booting to win from lin - Fn was toggling wifi from off to on, skipping that intermediate state with BT.
As I understand, when BT is switched off, it is disconnected from USB bus, so one can never see it in list of devices, but there should be some way to switch it on - i guess some kind of acpi message or register switching - not quite familliar with that stuff yet %)

BTW, just fired up kopete and realised my webcam works like a charm without any additional chanting.
PS. My laptop had bios 1.06 before I "upgraded" it to 1.04 %) I thought updater will at least ask me if i.m sure to replace bios or some, but it immediately started flashing, so no way back %)
But anyway, iasl coredumps on attempt to disassemble dsdt file
```

root@BOX:~# iasl -d dsdt.dat

Intel ACPI Component Architecture
AML Disassembler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file dsdt.dat
Acpi table [DSDT] successfully installed and loaded
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions)
...<snip>
Parsing completed

Found 8 external control methods, reparsing with new information
Segmentation fault
root@BOX:~#

```

There is a bug filed for AC Adapter [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578894](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578894) 
And this looks pretty similar [http://bugzilla.kernel.org/show_bug.cgi?id=14233](http://bugzilla.kernel.org/show_bug.cgi?id=14233)

---

### Post by rufferson on 2010-06-16
As for bluetooth - seems here it is 
root@BOX:~# rfkill list
0: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

under name acer-wireless soft blocked, though i cannot unblock it (rfkill unblock does nothing) it also listed under 
root@BOX:~# cat /sys/class/rfkill/rfkill0/uevent
RFKILL_NAME=acer-wireless
RFKILL_TYPE=wlan
RFKILL_STATE=0
echo 1 > state does nothing as well. Strange thing why it has type wlan instead of bluetooth

---

### Post by Snake231088 on 2010-06-18
Hi! I have Acer Aspire 5745G and i have the same problem.
I recompiled my DSDT table, but the kernel custom doesn't work!
I will try in this day.

---

### Post by Snake231088 on 2010-06-18
I have recompiled the kernel with a dsdt fix! But i have the same problem!

---

### Post by rufferson on 2010-06-20
So far I've managed to disassemble DSDT under windows with MS ASL and iASL(win version) - both produced sources with errors which coukd not be compiled back
```

c:\lin>asl dsdt.ASL
Microsoft ACPI Source Language Assembler Version 4.0.0NT [Aug 28 2009, 18:36:36]

Copyright (c) 1996,2009 Microsoft Corporation
Compliant with the ACPI 4.0 Specification

dsdt.ASL:

 2470:                         If(CondRefOf(HDOS, ))
                                                  ^***
dsdt.ASL(2470): error: expecting argument type "SuperName"

```
and
```

c:\lin>iasl dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [May 28 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

dsdt.dsl  2545:                     0x00000000,         // Length
Error    4122 -                              ^ Invalid combination of Length and Min/Max fixed flags

dsdt.dsl  2552:                     0x00000000,         // Length
Error    4122 -                              ^ Invalid combination of Length and Min/Max fixed flags

```

---

### Post by marm0tte on 2010-06-20
Hello,


I'd the same problems , 2 errors , 18 warnings. 


**2 x Error 4122 at line 2545 and 2552 :**
> DSDT.dsl  2545:                     0x00000000,         // Length
Error    4122 -                              ^ Invalid combination of  Length and Min/Max fixed flags

For the 4122 error, this tread give me the solution :
[http://www.insanelymac.com/forum/lofiversion/index.php/t189272-100.html](http://www.insanelymac.com/forum/lofiversion/index.php/t189272-100.html)



Buggy Code :
```
DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0xFEAFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
```


Lenght must be the result of this formula :
Max Range - Min Range + 1 

So at line 2545, Length will be 0xFEAFFFFF - 0x00000000 + 1 = 0xFEB00000


Arranged Code (maybe not the best solution) :
```
DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed,  Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0xFEAFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0xFEB00000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
```


For the line 2552, I've put Lenght = 0xFED44FFF - 0xFED40000 + 1 = 0x00005000



Recompil and you will have 0 errors but 18 warnings !


For the warnings I think we need help of someone experimented like in this tread :
[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by rufferson on 2010-06-23
This morning my Win7 hanged during reboot so I've power-cycled into linux. And guess what - bluetooth is working and toggling by Fn just the same way as in win. I wonder why haven't I tryed it earlier. probably because rebooting win itself doesn't break BT. Might be they have different init vectors so reinit of BT fails, don't know. Thus, still pending problem is AC/BAT info reporting by acpi.

---

### Post by Green Mars on 2010-06-23
I've got the 4820T and my wireless is turned off by default. Fn-F3 doesn't seem to do anything. Is there any other way I can enable it manually?

---

### Post by rufferson on 2010-06-23
Check with iwconfig if it is recognized by OS. If you have it there - check what Tx-power is showing, if Off - press Fn+F3 (Tx-Power should change in several seconds to some dBm) and start setting up your wireless either manually or via network manager

---

### Post by rufferson on 2010-06-24
So I've downloaded and built vanilla 2.6.34 with switcheroo enabled - now i'm able to boot normally into switchable mode %) Xorg is not working yet since I haven't rebuilt fglrx under new kernel yet, neither configured intel drivers. Bad news now come again form my bluetooth - after I configured it in linux its radio is not working any more. Probably coincidence - but it doesn't work neither in win nor in lin. Adapter reports proper working, is seen by OS without any problem, but adapter itself cannot see any bluetooth device now. Even my mobile phone sees my bt mouse, but laptop doesn't see neither mouse, nor phone, nothing. I bought bt mouse to avoid using usb dongle, but seems i'll be obliged to use usb dongle anyway, bt or mouse's %(
I also compiled into kernel DSDT file, don't know whether because of this or just bcz of new kernel - but AC is seen now. Ethernet adapter works as well without additional drivers loading.
```

root@BOX:~# acpitool
  Battery #1     : charged, 0.00%
  AC adapter     : on-line
  Thermal zone 1 : ok, 40 C
root@BOX:/usr/src/linux-2.6.34# ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full


```

---

### Post by rufferson on 2010-06-25
Also after loading radeon driver i see switch is enabled
```

root@BOX:~# cat /sys/kernel/debug/vgaswitcheroo/switch
0:+:Pwr:0000:00:02.0
1: :Pwr:0000:01:00.0
root@BOX:~#

```
switch showing currently active card is onboard (PCI:0:0:2) Intel card. And switching:
```

root@BOX:~# echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
root@BOX:~# cat /sys/kernel/debug/vgaswitcheroo/switch
0: :Off:0000:00:02.0
1:+:Pwr:0000:01:00.0
root@BOX:~# dmesg | tail -2
[17815.585947] fbcon: Remapping primary device, fb1, to tty 1-63
[17816.075748] i915: switched off
root@BOX:~# echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
root@BOX:~# dmesg | tail -2
[17894.401107] fbcon: Remapping primary device, fb0, to tty 1-63
[17894.401262] radeon: switched off
root@BOX:~# cat /sys/kernel/debug/vgaswitcheroo/switch
0:+:Pwr:0000:00:02.0
1: :Off:0000:01:00.0
root@BOX:~#

```

---

### Post by rufferson on 2010-06-26
wow, my BT started to work again, now only under linux. under win still sees nothing. It drives me crazy %)
Now I can proceed with script to replace radeon drivers with catalyst after switching to ATI card %)
... after ati release drivers for 34th kernel %(

---

### Post by Snake231088 on 2010-06-30
See: [https://bugzilla.kernel.org/show_bug.cgi?id=16218](https://bugzilla.kernel.org/show_bug.cgi?id=16218)

---

### Post by Amivit on 2010-07-01
> **rufferson said:**
> Also after loading radeon driver i see switch is enabled

Wow, does this mean it is possible to use the low-power intel gpu instead of the ati? :D If so, maybe you could put together a guide on how a linux-noob would manage this ^^
2400 views already :O, seems we are not alone, so a nice guide would most likely be greatly appreciated by many others :)

---

### Post by Snake231088 on 2010-07-03
The battery state is OK!!!!
The ACPI is recognized by Ubuntu with the patch here: [http://wiki.archlinux.org/index.php/Acer_TimelineX#Issues](http://wiki.archlinux.org/index.php/Acer_TimelineX#Issues).
This patch is for kernel 2.6.33!

---

### Post by Amivit on 2010-07-03
> **Snake231088 said:**
> The battery state is OK!!!!
The ACPI is recognized by Ubuntu with the patch here: [http://wiki.archlinux.org/index.php/Acer_TimelineX#Issues](http://wiki.archlinux.org/index.php/Acer_TimelineX#Issues).
This patch is for kernel 2.6.33!

Wow, looks promising! I'll take a go at it. Am I right that I have to follow this guide [http://www.howtoforge.com/kernel_compilation_ubuntu?&?]("http://www.howtoforge.com/kernel_compilation_ubuntu?&")
Or how exactly do I apply the patch? Thanks in advance!

---

### Post by DisDis on 2010-07-05
I have Acer Aspire 5745G.
I installed the new kernel 2.6.35-6.

Problem 2:AC Adapter Status always showed as plugged in/Battery status not available - **present**:(
Problem 5: Wifi works but it's disabled at logon - **fixed**.
Problem 6: Fn+F3 disable Wifi but doesn't re enable it  - **fixed**.

---

### Post by dsmex on 2010-07-06
Hi,

I'm considering buying an Acer TimelineX 4820TG or 5820TG (The hardware seem to be be the same, just bigger screen). My other option is a Samsung R580 (core i5-430M and Nvidia 330M). Can anyone with an acer 4820/5820TG give me some advice:

1. I cannot tell from this thread if all issues with linux/ubuntu have been solved. Can anyone summarize what works or doesn't work with the latest ubuntu? Specifically does switching graphic card work (rufferson?) and sleep/suspend?

2. Do you recommend this laptop in general? Does it have any issues I should be aware of?

I would appreciate any feedback.

Thanks

---

### Post by rufferson on 2010-07-07
> **Snake231088 said:**
> The battery state is OK!!!!
The ACPI is recognized by Ubuntu with the patch here: [http://wiki.archlinux.org/index.php/Acer_TimelineX#Issues](http://wiki.archlinux.org/index.php/Acer_TimelineX#Issues).
This patch is for kernel 2.6.33!

Yes, confirming it is working for 2.6.34 (manually applied due to different line numbers)
detecting AC state (plugging off ac cord)
```

ruff@BOX:~$ acpitool -a
  AC adapter     : on-line 
ruff@BOX:~$ acpitool -a
  AC adapter     : off-line 
ruff@BOX:~$ acpitool -a
  AC adapter     : on-line 
ruff@BOX:~$ 

```
and battery status
```

ruff@BOX:~$ acpitool -B
  Battery #1     : present
    Remaining capacity : 8380 mAh, 100.0%
    Design capacity    : 9000 mAh
    Last full capacity : 8380 mAh, 93.11% of design capacity
    Capacity loss      : 6.889%
    Present rate       : 0 mA
    Charging state     : charged
    Battery type       : rechargeable, 02A7
    Model number       : 32 mAh
    Serial number      : AS10E7E
ruff@BOX:~$ 

```

And yes, i'm running on intel kernel/Xorg drivers
```

ruff@BOX:~$ grep DRI /var/log/Xorg.0.log
(II) Loading extension XFree86-DRI
(II) Loading extension DRI2
(II) intel(0): [DRI2] Setup complete
(II) intel(0): direct rendering: DRI2 Enabled
ruff@BOX:~$ 

```
I can provide deb packages for kernel 2.6.34 with patch applied built for (my) 4820TG

---

### Post by Janiskeisari on 2010-07-07
Hi,

I'm new to linux/ubuntu. Could you explain (or link a page with some tutorial) how to apply that patch manually or how to modify it so that it works? I'm going to compile the 2.6.34 kernel, but that patch can't be installed, because of the line-numbers you mentioned.

Thank you!

---

### Post by rufferson on 2010-07-07
And here is battery drain with default settings (ATI on, intel active)
```

ruff@BOX:/usr/src/linux-2.6.34$ acpitool -B
  Battery #1     : present
    Remaining capacity : 8236 mAh, 98.28%, 03:15:33
    Design capacity    : 9000 mAh
    Last full capacity : 8380 mAh, 93.11% of design capacity
    Capacity loss      : 6.889%
    Present rate       : 2527 mA
    Charging state     : discharging
    Battery type       : rechargeable, 02A7
    Model number       : 32 mAh
    Serial number      : AS10E7E
ruff@BOX:/usr/src/linux-2.6.34$ cat /sys/kernel/debug/vgaswitcheroo/switch 
0: :Pwr:0000:01:00.0
1:+:Pwr:0000:00:02.0
ruff@BOX:/usr/src/linux-2.6.34$

```
and after switching off ATI card
```

root@BOX:/usr/src/linux-2.6.34# echo OFF >/sys/kernel/debug/vgaswitcheroo/switch
root@BOX:/usr/src/linux-2.6.34# 
root@BOX:/usr/src/linux-2.6.34# acpitool -B
  Battery #1     : present
    Remaining capacity : 8176 mAh, 97.57%, 05:16:29
    Design capacity    : 9000 mAh
    Last full capacity : 8380 mAh, 93.11% of design capacity
    Capacity loss      : 6.889%
    Present rate       : 1550 mA
    Charging state     : discharging
    Battery type       : rechargeable, 02A7
    Model number       : 32 mAh
    Serial number      : AS10E7E
root@BOX:/usr/src/linux-2.6.34# cat /sys/kernel/debug/vgaswitcheroo/switch
0: :Off:0000:01:00.0
1:+:Pwr:0000:00:02.0
root@BOX:/usr/src/linux-2.6.34# 

```

---

### Post by rufferson on 2010-07-07
patch for 2.6.34
```

--- drivers/acpi/ec.c.orig	2010-05-16 23:17:36.000000000 +0200
+++ drivers/acpi/ec.c	2010-07-07 08:19:51.222523203 +0200
@@ -854,6 +854,14 @@
 {
 	struct acpi_ec *ec = NULL;
 	int ret;
+	acpi_status status;
+	union acpi_object arg_objs[] = {
+		{ACPI_TYPE_INTEGER},
+		{ACPI_TYPE_INTEGER}
+	};
+	struct acpi_object_list args = { 2, arg_objs };
+	arg_objs[0].integer.value = 3;
+	arg_objs[1].integer.value = 1;
 
 	strcpy(acpi_device_name(device), ACPI_EC_DEVICE_NAME);
 	strcpy(acpi_device_class(device), ACPI_EC_CLASS);
@@ -884,6 +892,10 @@
 	if (!first_ec)
 		first_ec = ec;
 	device->driver_data = ec;
+	status = acpi_evaluate_object (ec->handle, "_REG", &args, NULL);
+	if (ACPI_FAILURE(status)){
+		printk (KERN_INFO "@@@@@@@@@@@@@ _REG\n");
+	}
 	acpi_ec_add_fs(device);
 	pr_info(PREFIX "GPE = 0x%lx, I/O: command/status = 0x%lx, data = 0x%lx\n",
 			  ec->gpe, ec->command_addr, ec->data_addr);

```

---

### Post by rufferson on 2010-07-07
Here are packed deb files - just install with dpkg -i <file.deb> and it should work. I guess
* [linux-headers-2.6.34-aspire-4820tg_1_amd64.deb](http://photo.uamailpost.com/linux-headers-2.6.34-aspire-4820tg_1_amd64.deb)
* [linux-image-2.6.34-aspire-4820tg_1_amd64.deb](http://photo.uamailpost.com/linux-image-2.6.34-aspire-4820tg_1_amd64.deb)
* [linux-source-2.6.34-aspire-4820tg_1_all.deb](http://photo.uamailpost.com/linux-source-2.6.34-aspire-4820tg_1_all.deb)
You only need image file by default, if you have some restricted-modules or just for compling some other 3d party mods you also need headers. And if you want to build kernel by your own - you need only source.
PS: kernel has ext4 as built-in and ext2 and ext3 as modules, so if you have boot/root in other than ext4 - it won't work without initrd

---

### Post by tawmas on 2010-07-09
@rufferson: I have problems at shutdown with your kernel packages. Does it work fine for you and others?

On a more positive note, I reported this bug earlier on Launchpad as [https://bugs.edge.launchpad.net/linux/+bug/578894](https://bugs.edge.launchpad.net/linux/+bug/578894), and yesterday, after finding this thread, I mentioned the existing patch in a bug comment.

As a result, a kernel developer is now looking into this. The bug has a link to patched kernel packages to test. I invite you all to try them out and report back on the mentioned bug.

Cheers!

---

### Post by rufferson on 2010-07-10
@tawmas: yes, it works fine for me, haven't noticed any issue with reboot or shutdown. What is the problem? Does it hang or panic? Maybe try to remove radeon driver before shutdown, or fglrx if you have it... bcz i'm using patched version of fglrx with switcheroo support (it doesn't work yet actually, just injected pieces of switcheroo code from radeon driver to turn the card off)

---

### Post by tawmas on 2010-07-10
On shutdown, I see error messages scrolling away too fast to read them (I think it's the same one repeated forever), after which the computer reboots.

Right now I'm running on the patched 2.6.32 packages linked from the bug to help test them.

Thank you!

---

### Post by rufferson on 2010-07-10
Ah, yes, I've mentioned that issue to switcheroo maillist
Is it something like this?
```

[ 3430.695445] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[ 3430.697491] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CAE2 (len 62, WS 0, PS 0) @ 0xCAFE

```
If yes - it's not an issue, just slows down a little things when second card is powered off %) You can add to shootdown/reboot sequence script command to pwron second card (echo ON > /sys/kernel/...) - it should resolve the issue with this flood.

---

### Post by tawmas on 2010-07-11
> **rufferson said:**
> Ah, yes, I've mentioned that issue to switcheroo maillist
Is it something like this?

Oh, yes, it looks like that indeed.

> **rufferson said:**
> If yes - it's not an issue, just slows down a little things when second card is powered off %) You can add to shootdown/reboot sequence script command to pwron second card (echo ON > /sys/kernel/...) - it should resolve the issue with this flood.

Hum... Here the system reboots instead of shutting down, and it also happened before I learned how to power off the second card. I do consider this to be an issue.

I will try to power on the second card before shutdown and report back.

---

### Post by rufferson on 2010-07-11
By "not an issue" I mean there is no harm in this message except time consuming, it will flood your console with this crap for about a minute (depends on speed of tty) and then continue.
Try following sequence - ensure discrete card is powered (check output of /sys/... should be Pwr on both cards, if not - make echo ON > /sys/...) then remove radeon driver (rmmod radeon) and try to shootdown/reboot or wherever you saw those messages.

---

### Post by mupi_foerster on 2010-07-11
Nice laptop indeed!

Did not even bother to look at the preinstalled W7 on it, instead installed Lucid (fully encrypted, with the alternate installer)

Then I did encounter some problems, some of which I was able to solve (some solutions in this thread), others still open. I summarise (might be helpful for others):

**a) No network card detected**

Solved with [http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)

In short:
Downloaded driver from [http://partner.atheros.com/Download.aspx?id=125](http://partner.atheros.com/Download.aspx?id=125) , transferred tar-file to laptop with usb-stick, then followed instructions in above thread, especially answer #6

After this, Ethernet worked, and I was able to download updates via  Update Manager. This included a restricted driver for the wireless.

**b) Wireless does not work with WPA**

I had already troubles connecting to WPA networks on Karmic, but this was on my old laptop, which had a few hardware issues. However, same behaviour on this new laptop with lucid:
Network is displayed, I can select it, enter WPA key, however, it does not manage to connect. After a while, the password prompt appears again.

After checking a few threads, I could not find much help except a few solutions with lots of copy/pasting of commands and compilation stuff - nothing I like to do.

Nevertheless, I found an easier way:
In Synaptic, look for the package "wpasupplicant", which should already be installed, and mark it for reinstallation. Apply, and afterwards, wireless with WPA worked like a charm.

Caveat: Fn+F3 does NOT activate/deactivate my wireless - only bluetooth comes up with it. And I have to manually enable wireless after every start up. I can live with that.

**c) Inbuilt microphone does not work**

I noticed this when testing skype. However, the inbuilt mic did not work as well when using Sound Recorder. Went to Synaptic and installed linux-backports-modules-alsa-lucid-generic
Now Microphone works with Sound Recorder, however not yet with Skype - will work on that. 

**d) FGLRX graphic driver - blank screen after booting**

When I enabled the FGLRX proprietary graphics driver, I ended up with a blank screen after reboot. I did not manage to repair this and had to reinstall (I'm not a Linux professional...).  Power consumption is low with the inbuilt card, so I'm quite happy with the standard card. I did not try to find a  solution for this, as I am not keen on reinstalling again. Still sad for a nice piece of hardware not used.

**d) Battery state and running on battery is not recognised at all**

This is the most annoying so far - laptop is running for about 6 hours, then shuts down all of a sudden. Ubuntu is not aware how much power is left, it does not even recognise it is running on battery.
Still looking for an easy to follow, low maintenance solution to this! Help appreciated.

---

### Post by Amivit on 2010-07-11
Thanks for contributing :)

> **mupi_foerster said:**
> Still looking for an easy to follow, low maintenance solution to this! Help appreciated.

I'm still waiting like a little child aswell ^^

---

### Post by marm0tte on 2010-07-11
Hello,

@all :
If you have a problems with your 4820 under Ubuntu lucid x86_64, I invite you to test the rufferson kernel compiled package.

@ruffersion :
Thanks a lot for your kernel 2.6.34 x6_64 package !
Now etherithing works like a charm;) (ehernet, wifi, Fn+F3, microphone, batery state ...)

Just one thing remains : The two gaphics card are reconize but I can't switch them !

```
# cat /sys/kernel/debug/vgaswitcheroo/switch
0:+:Pwr:0000:00:02.0
1: :Pwr:0000:01:00.0
```

```
echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
```

```
# cat /sys/kernel/debug/vgaswitcheroo/switch
0:+:Pwr:0000:00:02.0
1: :Pwr:0000:01:00.0
```

---

### Post by rufferson on 2010-07-12
Actually there is no sense to switch to ATI card since a) radeon/radeonhd kernel/xorg drivers are not supporting 5xxx series yet, b) fglrx does not support hybrid graphic yet. But for me switching worked fine, fbcon was switching to radeon (as in output I posted several posts above).
You have Xorg running on intel I presume thus having "delayed switch" - i.e. as soon as intel card will become unused it will switch to second card. Check dmesg.
Does it switch power of second card? Try echo OFF and see how status is changed.

---

### Post by acelan on 2010-07-12
Rufferson,

I sent you a priv. message about the kernel patch for the AC adapter status and battery charge status (LP #578894) (I'm not familiar with this forum, so I'm not sure if the msg is sent correctly). I would like to know the status of the patch, please reply me if you have time, thanks.

---

### Post by Treviño on 2010-07-12
Hello, you want I've compiled also the 2.6.35-rc7 ubuntu maverik kernel with the ACPI workaround patch and it's available here:
[http://download.tuxfamily.org/3v1deb/acer-timelinex/](http://download.tuxfamily.org/3v1deb/acer-timelinex/)
With this kernel you could also switch / turn-off the video card using the switcheroo sys-node (more [here]("http://asusm51ta-with-linux.blogspot.com/")) reducing a lot the power usage.

It should allow you to use also the internal microphone... Otherwise update alsa to 1.0.23 (you can use this ppa: [https://launchpad.net/~ricotz/+archive/unstable]("https://launchpad.net/%7Ericotz/+archive/unstable")).

To use the internal microphone with Skype you need to uncheck the flag to "Let Skype adjust my sound device settings" and use [FONT=Courier New]alsamixer[/FONT] (or [FONT=Courier New]pavucontrol[/FONT]) to reduce the volume of a channel: run it, go to Capture view pressing tab, select the Capture bar and press "y" until you'll have reduced completely the left channel. After that, the pulse audio input volume meter will move and Skype will record your voice (note that if you change the input volume from the pulse audio configurator, you'll loose the recording ability again).

Bye

---

### Post by rufferson on 2010-07-13
@acelan: I've replied to you via mail, will resend the mail again.

---

### Post by Treviño on 2010-07-13
If you want, I've built also some TuxOnIce suspend/resume (to disk!) enabled kernels, you can grab the debs at:

· [linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-image-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_amd64.deb")
· [linux-headers-2.6.35-7_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_all.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_all.deb")
· [linux-headers-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu1_amd64.deb")

The kernel should work as-is, but you can also install hibernate and tuxonice-userui packages (available in the official repositories or, more updated, in [this ppa]("https://edge.launchpad.net/%7Etuxonice/+archive/ppa/+packages")) for more controls over hibernate/resume process and for showing a graphic bar respectively.

---

### Post by RavensKrag on 2010-07-17
First of all, I really appreciate the debs of the new kernels.  Compiling a kernel is a rather time consuming process.

I read earlier in this thread that the binary drivers from ATI were not supported for the 5xxx series, but do they work? I read in another thread ([http://ubuntuforums.org/showthread.php?t=1422762](http://ubuntuforums.org/showthread.php?t=1422762)) that the 5650 worked just fine but there was just a watermark on the corner which said something about the card being unsupported.  If you switch to the ATI card using the switch in the new kernel can you install the ATI drivers?

EDIT:
Oh, by the way, is any one else having problems ejecting the optical drive? I can't seem to get that thing open >_< Even if I change the keyboard shortcut for "eject" the drive does not open, and I can see no physical button to open the drive.

---

### Post by lazerradial2003 on 2010-07-18
Could anyone point me in the direction of a tutorial on how to patch a 32 bit version of the kernel using the patch provided earlier in this thread?

---

### Post by RavensKrag on 2010-07-18
EDIT 2
My mistake, I wrote the wrong command >.< it has been fixed.  I just left out a "<" how careless...



Once you have the kernel source, navigate to the source directory in the terminal and then type.

patch -p1 < /path/to/patch

replacing /path/to/patch with the actual path to the file.



If you need more detailed instructions, look [here](http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/) but remember to add the ubuntu kernel configuration as explained [here]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild").

Feel free to ask for more detailed help if my instructions were not clear.  The instructions I provided were for the 2.6.30 kernel and the latest bleeding edge kernel from git, respectively, so you will have to change the part where the kernel source is downloaded to get the 2.6.34 source.

EDIT:
@lazerradial
I assume that you do not have this exact computer, because if you do I can see no reason for you to be using a 32 bit OS.

---

### Post by mupi_foerster on 2010-07-18
Thanks Trevino, Skype works now as well with internal microphone!

@RavnesKrag: Why does it not make sense to use this laptop with 32bit OS? (Well, at least it is delivered with W7 32bit).

---

### Post by RavensKrag on 2010-07-18
OMG, does it really come with W7 32 bit? I hope not, that would suck >.< the system has 4 gigs of ram.  If the OS is 32-bit you will only be able to access 3 gigs of it.  Also, it has a dual-core processor, which means the architecture (the CPU hardware) is 64 bit.  Thus, it would make sense to use a 64-bit OS.  

Still, on windows there are very few 64-bit programs, so the usage of a 32-bit OS kinda makes sense.  However, on Linux, 64-bit programs are everywhere, and if a 64-bit version is not available and the project is open-source, you can compile your own.  Even with the slight Windows issue of not having enough 64-bit programs, I believe most, if not all, 32-bit Windows apps work in 64-bit Windows.



Also, I have a question of my own.  What version of the kernel was the posted patch designed for? I am attempting to patch a vanilla 2.6.34.1 from kernel.org and it is not working.

---

### Post by RavensKrag on 2010-07-18
EDIT
Another note about the graphics.  What graphics card do you people have? I have a ATI 5650, but it seems that some of the older Aspire 4820tg computers shipped with ATI 5470.  Can anyone confirm this?


> **marm0tte said:**
> 
Just one thing remains : The two gaphics card are reconize but I can't switch them !


I don't know if you got this cleared up or not, but when you give that command, you have to log out before the change will take effect.  A minor setback, imo.

---

### Post by RavensKrag on 2010-07-20
Bump.


Sorry to triple post like this...
[s]How many of you have fixed the battery status problem? That's probably the biggest bug imo.[/s]

Edit:
Fixed it.  Apply the patch, boot the kernel with the patch, and then add acpi_osi=Linux to the GRUB command line.

Here's a step-by-step approach.
Type the following to open the grub config.
```
sudo gedit /etc/default/grub
```

Then replace
```
GRUB_CMDLINE_LINUX=""
```
with
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```

Update the changes to grub
```
sudo update-grub
```

Now reboot.  You have to shutdown and the power on again, as the computer has to go through GRUB for the change to take effect.  Thus, it may take two "reboots" to get this working.

Now, when you unplug the laptop from AC, the status will take a few seconds to update in the battery applet.  However, it should work.

Edit2:
The battery applet does not work properly, or at least not consistently.  Although, the correct status always shows if you run ```
acpi -b
```

---

### Post by lazerradial2003 on 2010-07-20
@RavensKrag - thanks for your reply, about to try it and I'll let you know. I'm running 32bit OS because I've had a few issues with 64 bit

---

### Post by RavensKrag on 2010-07-20
Ah, ok.  I understand.  I've had quite a few problems with Flash and the like.  It was magically working in Chromium on another computer, so hopefully I'll be able to replicate that.  Not holding my breath though.

Hope it works for you.

---

### Post by ks_b on 2010-07-21
Hi all, I am really new to ubuntu and I would like to fix battery problem. can someone give me instruction of how to fix this?

I am running kernel 2.6.32-23-generic, ubuntu 10.04 64bit
also how do i actually upgrade to newer kernel if i have to?

thanks

---

### Post by marincop on 2010-07-22
@Trevino
     I use the kernel you provide , two questions 

· [linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-image-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_amd64.deb")
· [linux-headers-2.6.35-7_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_all.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_all.deb")
· [linux-headers-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu1_amd64.deb")

  1. I can not find the switcheroo in the /sys/kernel/debug/.../vga_switcheroo file to enable the switch graphic card function.
  2. Is this kernel provide both vga cards driver ?  I can not change the "extra" in the "Visual Effects".

  Is any procedure I need to follow ? 
BTW, my timelinex 4820tg BIOS upgrade to version 1.13 , is this cause the problem ?


    Albert

---

### Post by Treviño on 2010-07-23
> **marincop said:**
> @Trevino
     I use the kernel you provide , two questions 

· [linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-image-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_amd64.deb")
· [linux-headers-2.6.35-7_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_all.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_all.deb")
· [linux-headers-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu1_amd64.deb")

  1. I can not find the switcheroo in the /sys/kernel/debug/.../vga_switcheroo file to enable the switch graphic card function.
This is very strange... Are you sure that you've installed it  correctly? the [FONT="Courier New"]uname -r[/FONT] command should give back you something like [FONT="Courier New"]Linux <hostname> 2.6.35-7-generic #3v1ubuntu2~toi1 SMP Wed Jul 14 01:31:07 CEST 2010 x86_64 GNU/Linux[/FONT]
BTW the sys-node is in fact [FONT="Courier New"]/sys/kernel/debug/vgaswitcheroo/switch[/FONT] !

> **marincop said:**
> 
  2. Is this kernel provide both vga cards driver ?  I can not change the "extra" in the "Visual Effects".
  Is any procedure I need to follow ? 
By default the notebook uses the integrated Intel card to run X (check /var/log/Xorg.0.log), so all the effects should be provided by the opensource intel driver... All the effects work to me (also if some plugins, like the blur one are too invasive).

I've never tried to run the flgrx driver, but it should run (maybe using the [previous mentioned workaround]("http://ubuntuforums.org/showpost.php?p=8230858&postcount=17"))

> **marincop said:**
> 
BTW, my timelinex 4820tg BIOS upgrade to version 1.13 , is this cause the problem ?
My Aspire came with that BIOS and everything worked like I've described. I've updated also to BIOS version 1.15 (using freedos, since I've no Windows partitions in my NB) and nothing changed from the user point of view!

---

### Post by RavensKrag on 2010-07-23
@Trevino
About the pre-compiled kernel not having the switch:
I don't remember if I mentioned it in this thread already, but I had the same problem, forcing me to compile my own kernel.

@ks_b
I have posted a post in this thread previously with links to a few tutorials which show how to compile a custom kernel.  Do not be afraid, it's not that bad.  It just takes time to compile.

If you need step-by-step instructions, I will try to remember exactly what I did.  Do not hesitate to ask.

---

### Post by Treviño on 2010-07-23
> **RavensKrag said:**
> @Trevino
About the pre-compiled kernel not having the switch:
I don't remember if I mentioned it in this thread already, but I had the same problem, forcing me to compile my own kernel.
Try to do (if you don't have the debugfs mounted at all, and so no /sys/kernel/debug sysnode):
```
sudo mount -t debugfs none /sys/kernel/debug
```

---

### Post by RavensKrag on 2010-07-23
As that was mentioned in this thread before, I had already tried it.  /sys/kernel/debug was already mounted, but the vgaswitcheroo directory was not there.

It's no big deal, it's all working for me now.

---

### Post by marincop on 2010-07-24
@Trevino :
    Thanks your response, 
 I fix the problem. The root cause is 
    1. If we upgrade the BIOS from 1.04 to 1.13 or 1.15, we need do one thing is "Load the BIOS default value first".  I lose my Bluetooth after I upgrade to 1.13. after I "Load the BIOS default value" my Bluetooth come back again.
    2. the BIOS setting must be "Switch " , the vgaswitcheroo will show in the /sys/kernel/debug/.../switch

 Now I meet another problem , the VGA card can not switch. Someone meet the same situation like me .
Any suggestion ? 

  @ All:
    Thanks all you done.. :p

---

### Post by marincop on 2010-07-25
@Trevino 
 
   The switcher is OK now , Just need to exit to the and login again .
Intel integrated vga work perfect, but when I with to the ATI Radeon card . It's need a driver .
So I install the driver, but failed.
   I can install it on kernel 2.6.32 perfectly , but the when kernel upgrade to 2.6.35 it will cause errors.
I think it the vga card driver problem .
@All
   Is anyone successfully install the flgrx on 2.6.35 kernel ? or where I can get the newest flgrx driver?

   Albert

---

### Post by Treviño on 2010-07-25
> **marincop said:**
> @Trevino 
 
   The switcher is OK now , Just need to exit to the and login again .
Intel integrated vga work perfect, but when I with to the ATI Radeon card . It's need a driver .
So I install the driver, but failed.
   I can install it on kernel 2.6.32 perfectly , but the when kernel upgrade to 2.6.35 it will cause errors.
I've never tried to run the fglrx drivers yet... I had no time for trying them. However maybe they don't support the new kernel yet (damn, closed drivers!)
However if you want use the intel card by default saving power (and temperature), you can use scripts like these: [http://forum.ubuntu-it.org/index.php/topic,382092.msg3101266.html#msg3101266](http://forum.ubuntu-it.org/index.php/topic,382092.msg3101266.html#msg3101266)

---

### Post by marincop on 2010-07-25
@trevino 

   Thanks for your big help.  those information really help me to keep on in Ubuntu .

   Albert

---

### Post by Treviño on 2010-07-25
Hello, I've tried to run the FGLRX drivers in the laptop (for my first time in the timelineX...).

I don't know how they work using the default ubuntu kernel, but they doesn't work (due to install/build errors) in the kernel 2.6.35 I'm using (and that I've provided).

The drivers are easy to fix by the way, and you simply have to apply [this patch]("http://download.tuxfamily.org/3v1deb/acer-timelinex/fglrx-8.741-linux-2.6.35-support.patch") to the ATI's installer content (or to the files in /usr/src/fglrx-*/2.6.x/) to make DKMS work including the <linux/slab.h> file (where kmalloc and kfree are now defined).

You can download fixed drivers for amd64 in [my directory]("http://download.tuxfamily.org/3v1deb/"); they also include the [*remove watermark* binary fix]("http://ubuntuforums.org/showpost.php?p=8230858&postcount=17"):
 - [fglrx_8.741-0ubuntu1~3v1ubuntu1_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/fglrx_8.741-0ubuntu1~3v1ubuntu1_amd64.deb")
 - [fglrx-amdcccle_8.741-0ubuntu1~3v1ubuntu1_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/fglrx-amdcccle_8.741-0ubuntu1~3v1ubuntu1_amd64.deb")
 - [fglrx-dev_8.741-0ubuntu1~3v1ubuntu1_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/fglrx-dev_8.741-0ubuntu1~3v1ubuntu1_amd64.deb")
 - [fglrx-modaliases_8.741-0ubuntu1~3v1ubuntu1_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/fglrx-modaliases_8.741-0ubuntu1~3v1ubuntu1_amd64.deb")

Unfortuntely these drivers work only if you're running on the "Discrete card" BIOS mode.

You have to install the deb files and then run:
```
sudo aticonfig --initial
```

If you want go back to the intel card, you need to:
```
sudo apt-get remove fglrx fglrx-amdcccle fglrx-dev fglrx-modaliases
sudo rm -f /etc/X11/xorg.conf /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf.fglrx*
``` and reboot re-enabling the "Switchable" mode from BIOS.
[SIZE="1"]Ah, it is not strictly needed to remove the debs at all, you can also do simply [FONT="Courier New"]sudo update-alternatives --set gl_conf /usr/lib/mesa/ld.so.conf; sudo rm -f /etc/X11/xorg.conf /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf.fglrx*[/FONT][/SIZE]

Unfortunately with the fglrx drivers no switch on runtime is possible (it will be eventually possible using the radeon free drivers, when they will support our GFX card).

---

### Post by pemasu on 2010-07-26
Trevino.  linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb works fine with ubuntu lucid alternate and 5820tg.

One problem. Sudo echo OFF >/sys/kernel/debug/vgaswitcheroo/switch gives permission denied. Login as root same thing.
Mainly I would like to switch ATI HD 5660 off at startup to save my battery. Powertop shows almost 20 W saving after shutting that to 10-14 W usage. 

So your vgaswitch and vgaswitcher does not do anything. I believe because of that permission denied. When I chmod 666 /sys/kernel/debug/vgaswitcheroo/switch, Sudo echo OFF >/sys/kernel/debug/vgaswitcheroo/switch works.

root@ubuntu:~# cat /sys/kernel/debug/vgaswitcheroo/switch
0: :Off:0000:01:00.0
1:+:Pwr:0000:00:02.0
root@ubuntu:~# 

Workaroud. I did put those commands to cron. It executes them 5 minutes interval and shuts ATI down 5 minutes after startup.
But I would like to have runonce solution.
I havent tested yet vgaswitch and vgaswitcher as root but because of permission denied probably they dont work as root also.
Mainly I try to use ubuntu with normal user account. Quite difficult after using Puppy Linux.

---

### Post by Treviño on 2010-07-26
> **pemasu said:**
> Trevino.  linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb works fine with ubuntu lucid alternate and 5820tg.

One problem. Sudo echo OFF >/sys/kernel/debug/vgaswitcheroo/switch gives permission denied. Login as root same thing.
Mainly I would like to switch ATI HD 5660 off at startup to save my battery. Powertop shows almost 20 W saving after shutting that to 10-14 W usage. 

It doesn't work due to ubuntu security options. You can by the way run that with
```
sudo bash -c "echo OFF > /sys/kernel/debug/vgaswitcheroo/switch"
```

> **pemasu said:**
> 
So your vgaswitch and vgaswitcher does not do anything. I believe because of that permission denied. When I chmod 666 /sys/kernel/debug/vgaswitcheroo/switch, Sudo echo OFF >/sys/kernel/debug/vgaswitcheroo/switch works.
You should chmod them as "+x" simply...

---

### Post by pemasu on 2010-07-26
```
sudo bash -c "echo OFF > /sys/kernel/debug/vgaswitcheroo/switch"
```

That did it. I did put above to /etc/rc.local file and rebooted. ATI was down.

Thank you Trevino. Subshell usage to give permission for whole command was what I needed.

---

### Post by marincop on 2010-07-29
&#65312;Trevino &#65306;

   The ATI driver work for me , thanks for your great help !!!
:p

---

### Post by av.korkin on 2010-07-29
@ Trevino: I can not solve the problem
I installed
· Linux-image-2.6.35-7-generic_2.6.35-7.11 ~ lucid1.3v1ubuntu2 ~ toi2_amd64.deb
· Linux-headers-2.6.35-7_2.6.35-7.11 ~ lucid1.3v1ubuntu2 ~ toi2_all.deb
· Linux-headers-2.6.35-7-generic_2.6.35-7.11 ~ lucid1.3v1ubuntu2 ~ toi2_amd64.deb

But when I install virtualbox 3.2 an error occurs.

[2755.635117] vboxdrv: disagrees about version of symbol misc_deregister
[2755.635122] vboxdrv: Unknown symbol misc_deregister (err -22)
[2755.635812] vboxdrv: disagrees about version of symbol misc_register
[2755.635814] vboxdrv: Unknown symbol misc_register (err -22)
[3085.751699] vboxdrv: disagrees about version of symbol misc_deregister
[3085.751709] vboxdrv: Unknown symbol misc_deregister (err -22)
[3085.754068] vboxdrv: disagrees about version of symbol misc_register
[3085.754074] vboxdrv: Unknown symbol misc_register (err -22)

What to do?

---

### Post by Gilberoni on 2010-07-31
Hi everybody,

I also bought an Acer 4820Tg and with this I wanted to get familiar with Ubuntu so I'm an absolute newbie! My apologies if I did something completely stupid.

I decided for dual boot win7/ubuntu and installed ubuntu 10.04 LTS 64bit alternate, which is the kernel (?) 2.6.32-21-generic.

Neither lan nor wlan work ... apart from the further problems with switchable graphics etc..
I followed the steps discribed in this thread as well as [http://ubuntuforums.org/showthread.php?t=870123](http://ubuntuforums.org/showthread.php?t=870123) in order to get the wlan working. However, nothing works for me.

Since I have no connection to the internet I installed build-essential and linux-headers-generic (instead of linux-generic-header, right?) from the cd as described in #4 in [http://ubuntuforums.org/showthread.php?p=228601](http://ubuntuforums.org/showthread.php?p=228601) but I got the impression they where already installed. aptitude update did essentially nothing since I have no connection. When executing aptitude install build-essential I got several errors like
```
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427.1)/ma
in g++4.4 4.4.3-4ubuntu5
File not found
``` where the 'g++...' varied. Could this be the problem? If yes, what should I do?

locate alt1e.ko gives:
```
/lib/modules/2.6.32-21-generic/kernel/drivers/net/atl1e/atl1e.ko
```as it should be, right?

In /etc/modules I tried both
```
alias eth0 atl1e
atl1e
``` or only ```
atl1e
```.

ifconfig even shows me that eth0 has the right Mac adress but iwconfig shows that eth0 is/has (?) no wireless extension and I don't see any wireless networks. The only thing that happens is that sometimes when I changed the modules the 'No network connection' icon is substituted by speaker volume icon (only after the first reboot). :-?

I also had the idea that the wlan could probably just be switched off so after I found [http://www.linuxquestions.org/questions/linux-networking-3/n00b-how-to-turn-on-wireless-ubuntu-703961/](http://www.linuxquestions.org/questions/linux-networking-3/n00b-how-to-turn-on-wireless-ubuntu-703961/) I tried
```
sudo ifconfig eth0 up
``` without any effect. Is this relevant, does it help or does it harm?

Can somebody please help me? Am I the only person who has problems with the (wired) lan? (ifconfig does not show any Mac address for wired lan connection 'lo'.) Does somebody know how to fix this so that I could at least load all the packages on the same pc instead of switching between two PCs all the time?

PS: When starting up the Ubuntu logo and the 'loading dots' have weird neon green borders. Should I be concerned?



Edit: Now I installed build-essential and linux-headers-generic by ```
sudo dpkg -i package.deb
``` from a USB stick. Synaptics also shows that both packages are installed properly. To be sure I did again ```
sudo su
make clean
make
make install
modprobe atl1e
``` but wlan still does not work. I also tried again the different possibilities in /etc/modules. Any ideas??

---

### Post by davelosm on 2010-08-01
Hey, I'm trying to apply this patch, but I do not have a linux/drivers/ directory, and so no acpi files to patch. I can't find the ec.c file anywhere else either. Am I missing something, I'm pretty new to all this..

Any help would be great

Oh, by that i mean this patch:

--- linux/drivers/acpi/ec.c.old  2010-03-23 18:33:12.919349214 +0800
+++ linux/drivers/acpi/ec.c      2010-03-23 18:33:21.711475718 +0800
@@ -829,6 +833,14 @@
 {
        struct acpi_ec *ec = NULL;
        int ret;
+       acpi_status status;
+       union acpi_object arg_objs[] = {
+               {ACPI_TYPE_INTEGER},
+               {ACPI_TYPE_INTEGER}
+       };
+       struct acpi_object_list args = { 2, arg_objs };
+       arg_objs[0].integer.value = 3;
+       arg_objs[1].integer.value = 1;
 
        strcpy(acpi_device_name(device), ACPI_EC_DEVICE_NAME);
        strcpy(acpi_device_class(device), ACPI_EC_CLASS);
@@ -859,6 +871,10 @@
        if (!first_ec)
                first_ec = ec;
        device->driver_data = ec;
+       status = acpi_evaluate_object (ec->handle, "_REG", &args, NULL);
+       if (ACPI_FAILURE(status)){
+               printk (KERN_INFO "@@@@@@@@@@@@@ _REG\n");
+       }
        acpi_ec_add_fs(device);
        pr_info(PREFIX "GPE = 0x%lx, I/O: command/status = 0x%lx, data = 0x%lx\n",
                          ec->gpe, ec->command_addr, ec->data_addr);

---

### Post by davelosm on 2010-08-01
Ok, if you're like me, you've tried to update kernels and patches and one thing's worked and not the other.
I've just updated using the below packages, and can confirm that the following are fixed:

Battery charged/ACPI problem
Brightness problem
Suspend problem

Hope this helps, it helped me:
[http://download.tuxfamily.org/3v1deb/acer-timelinex/](http://download.tuxfamily.org/3v1deb/acer-timelinex/)

Credits to whoever made these

---

### Post by lukasw on 2010-08-08
RavensKrag. Ejecting the optical drive with the eject button above the keyboard(or any other key) doesn't  work for me neither. The only way it works is typing 'eject' in a terminal. Did you try this?

---

### Post by Elysius on 2010-08-09
> **davelosm said:**
> Ok, if you're like me, you've tried to update kernels and patches and one thing's worked and not the other.
I've just updated using the below packages, and can confirm that the following are fixed:

Battery charged/ACPI problem
Brightness problem
Suspend problem

Hope this helps, it helped me:
[http://download.tuxfamily.org/3v1deb/acer-timelinex/](http://download.tuxfamily.org/3v1deb/acer-timelinex/)

Credits to whoever made these

I've got the Acer 4820T laptop (without the ATI card) and I'm also having the battery/acpi problems. I'm running the default 2.6.34 kernel drivers. How can I install "TimelineX-ACPI-fix.patch" from the link above?

---

### Post by lukasw on 2010-08-09
I think this patch is meant to be applied when building a new kernel.  You should instead install these packages(they contain the patch):

[linux-headers-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_amd64.deb")
[linux-headers-2.6.35-7_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_all.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_all.deb")
[linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-image-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_amd64.deb")

Thanks to Treviño for building them.

---

### Post by lyradmil on 2010-08-09
> **Treviño said:**
> Hello, you want I've compiled also the 2.6.35-rc7 ubuntu maverik kernel with the ACPI workaround patch and it's available here:
[http://download.tuxfamily.org/3v1deb/acer-timelinex/](http://download.tuxfamily.org/3v1deb/acer-timelinex/)
With this kernel you could also switch / turn-off the video card using the switcheroo sys-node (more [here]("http://asusm51ta-with-linux.blogspot.com/")) reducing a lot the power usage.


Thanks Trevino for your help in setting up my 5820TG for work with Ubuntu. Pretty much everything is up, including battery which is awesome. :) However, my battery life barely lasts 2 hours running ubuntu. I read up the article you posted ([http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)),as well as [http://forum.ubuntu-it.org/index.php/topic,382092.msg3101266.html#msg3101266](http://forum.ubuntu-it.org/index.php/topic,382092.msg3101266.html#msg3101266) and I couldn't make out what I was supposed to do. I wouldn't mind running the intel graphics at all times since it has low power consumption. Could you explain how to perform the switch functionality?

---

### Post by Elysius on 2010-08-09
> **lukasw said:**
> I think this patch is meant to be applied when building a new kernel.  You should instead install these packages(they contain the patch):

[linux-headers-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_amd64.deb")
[linux-headers-2.6.35-7_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_all.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_all.deb")
[linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-image-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_amd64.deb")

Thanks to Treviño for building them.

Awesome, fixed my battery problems as well.

However I got a package problem, "the package bcmwl-kernel-source failed to install or upgrade". Does anyone no a fix for that?

Will this issue (battery) also be solved in ubuntu version 10.10, is this known by the developers?

---

### Post by hshan on 2010-08-09
4820t here also. I also get same bcmwl warnings with Tevino's kernel. How to fix? 

For now running Ruf's kernel [http://ubuntuforums.org/showthread.php?t=1495123&highlight=aspire+4820t&page=4](http://ubuntuforums.org/showthread.php?t=1495123&highlight=aspire+4820t&page=4)

With this i have wifi.

---

### Post by lukasw on 2010-08-10
The bcmwl problem:
I also had this problem and didn't manage to get it working properly.
What I did: I just reinstalled Ubuntu and the first thing I did after that was installing Trevino's maverik kernel. Then the ethernet worked out of the box and I only had to install the wireless driver with jockey.
Hope this helps.

---

### Post by Elysius on 2010-08-10
> **hshan said:**
> 4820t here also. I also get same bcmwl warnings with Tevino's kernel. How to fix? 

For now running Ruf's kernel [http://ubuntuforums.org/showthread.php?t=1495123&highlight=aspire+4820t&page=4](http://ubuntuforums.org/showthread.php?t=1495123&highlight=aspire+4820t&page=4)

With this i have wifi.

If I can't get it to work with jockey, I'll install Ruf's kernel. Thanks for posting that up again.


> **lukasw said:**
> Then the ethernet worked out of the box and I only had to install the wireless driver with jockey.
Hope this helps.

Could you point out a FAQ (website) of jockey? I'm not familiar with it.

---

### Post by kittenslayer on 2010-08-10
Hi

Thanks to everybody helping out in this thread, without you my new 5820TG would have been a Windows 7 brick on my desk.

The only thing that still irks me is the lack of wifi. I did not come working out of the box so I tried meddling around. I think it's only a matter of a missing driver, but I am a noob so any help is greatly appreciated. 
I have tried  both rufferson's and Treviño's kernel without any luck. When using both of them, selecting System/Administration/Hardware_Drivers and enabling the "Broadcom STA wireless driver" yields an installation failed prompt with a log file:

```
2010-08-10 22:30:49,328 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-10 22:30:49,448 DEBUG: fglrx is not the alternative in use
2010-08-10 22:30:49,465 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-10 22:30:49,491 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-10 22:30:49,586 DEBUG: fglrx is not the alternative in use
2010-08-10 22:30:50,879 DEBUG: fglrx is not the alternative in use
2010-08-10 22:30:51,862 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-10 22:30:53,357 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-10 22:30:53,487 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-08-10 22:30:53,488 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-08-10 22:30:53,561 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-10 22:30:55,154 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-10 22:30:55,257 DEBUG: fglrx is not the alternative in use
2010-08-10 22:30:55,277 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-10 22:30:55,306 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-10 22:30:55,406 DEBUG: fglrx is not the alternative in use
```

Any1 know how to get the wifi working?

---

### Post by lyradmil on 2010-08-10
Have you flashed your BIOS to the latest version (1.15)? That's what I did with my 5820TG. Wifi is working great after Trevino's kernel was installed. Main observable issues I'm having is quick battery drain and the inability for drive eject. Still waiting for assistance on these issues guys!

---

### Post by ari197 on 2010-08-11
I used your package for my ACER Aspire 4745G and it worked!

you rock man .. thanks a lot ..

> **rufferson said:**
> Here are packed deb files - just install with dpkg -i <file.deb> and it should work. I guess
* [linux-headers-2.6.34-aspire-4820tg_1_amd64.deb](http://photo.uamailpost.com/linux-headers-2.6.34-aspire-4820tg_1_amd64.deb)
* [linux-image-2.6.34-aspire-4820tg_1_amd64.deb](http://photo.uamailpost.com/linux-image-2.6.34-aspire-4820tg_1_amd64.deb)
* [linux-source-2.6.34-aspire-4820tg_1_all.deb](http://photo.uamailpost.com/linux-source-2.6.34-aspire-4820tg_1_all.deb)
You only need image file by default, if you have some restricted-modules or just for compling some other 3d party mods you also need headers. And if you want to build kernel by your own - you need only source.
PS: kernel has ext4 as built-in and ext2 and ext3 as modules, so if you have boot/root in other than ext4 - it won't work without initrd

---

### Post by ari197 on 2010-08-11
@Trevino,

Can I have your prepatch source kernel package? Your compiled kernel is working for my Acer 4745G except for my wireless card ( Network controller: Broadcom Corporation Device 4357) and for my virtualbox (the vboxdrv module is not there) ..

thanks

---

### Post by ari197 on 2010-08-11
@Trevino

so I've managed to get VirtualBox running by installing from the source directly .. but I still cant' have my wifi working. When I tried to compiled the driver, it's missing the "linux/autoconf.h" files from your header ..

> **ari197 said:**
> @Trevino,

Can I have your prepatch source kernel package? Your compiled kernel is working for my Acer 4745G except for my wireless card ( Network controller: Broadcom Corporation Device 4357) and for my virtualbox (the vboxdrv module is not there) ..

thanks

---

### Post by ari197 on 2010-08-11
it turns out, that I've to patch the module source code.. now, my notebook is running perfect :D

> **ari197 said:**
> @Trevino

so I've managed to get VirtualBox running by installing from the source directly .. but I still cant' have my wifi working. When I tried to compiled the driver, it's missing the "linux/autoconf.h" files from your header ..

---

### Post by hshan on 2010-08-11
ari97 thanks for your diligence , but would you mind explaining your procedures and steps for others coming to this thread?

---

### Post by enno_bohnesorg on 2010-08-12
Dear All,

Just wanted to post success using Trevino's (Mille Grazie !) provided packages. I'm running an Aspire 4820T-434G32Mn. This model has no ATI graphics card. WiFi works immediately now (no need to right-click on Network Manager and enable it) and connects to the preferred network after login.
Everything related to the battery recognition seems to work fine, however: I can't seem to get those reputed 8 hours of battery life out of it, more like 3-4. I will gather more empirical data as the days and weeks go on, but was wondering if other users can post their battery life and/or confirm mine.
My usage is certainly not 'heavy', just normal web browsing, and some application usage. No kernel compilations or anything like that, so battery life should really be in excess of 3 hours.
Looking forward to your feedback.

Enno

---

### Post by lyradmil on 2010-08-12
@enno: Yes, I can confirm the drop in battery life when running on ubuntu. I have the 5820TG and it consumes more battery due to the larger display and I am looking at somewhere between 2-3 hours. However, Trevino has posted a script on [http://forum.ubuntu-it.org/index.php/topic,382092.msg3101266.html#msg3101266](http://forum.ubuntu-it.org/index.php/topic,382092.msg3101266.html#msg3101266) . Perhaps you can make sense out of it cos I can't. I want to get my battery up and running to maximum performance too. Also, is your optical drive working fine? I can't seem to eject nor detect it under ubuntu.

---

### Post by enno_bohnesorg on 2010-08-12
@lyradmil
That is the one thing not working right now, I can't eject the drive using the button. I have to type 'eject' in the shell to get it working. 
I am fairly sure that we're seeing more of the same old Windows-centric manufacturer policy that brings us things like corrupt battery status code and other 'hacked' hardware-OS interaction - things you don't notice when using the default Windows 7 install. For what it's worth, I will send an email to Acer asking them to re-think their policy and supply the customers with more user-friendly hardware.
I am sure it will not amount to much - besides an automated response. But, in the words of Gandhi: "You must be the change you want to see in the world !"
;)

---

### Post by lyradmil on 2010-08-12
@enno: That's strange ***. I tried doing that in the shell but it ain't working for me either. Bummer. I'm more concerned about the battery life in any case. That's what we got the TimelineX for!

Anyone?

---

### Post by Roadrun on 2010-08-12
> **rufferson said:**
> Here are packed deb files - just install with dpkg -i <file.deb> and it should work. I guess
* [linux-headers-2.6.34-aspire-4820tg_1_amd64.deb](http://photo.uamailpost.com/linux-headers-2.6.34-aspire-4820tg_1_amd64.deb)
* [linux-image-2.6.34-aspire-4820tg_1_amd64.deb](http://photo.uamailpost.com/linux-image-2.6.34-aspire-4820tg_1_amd64.deb)
* [linux-source-2.6.34-aspire-4820tg_1_all.deb](http://photo.uamailpost.com/linux-source-2.6.34-aspire-4820tg_1_all.deb)
You only need image file by default, if you have some restricted-modules or just for compling some other 3d party mods you also need headers. And if you want to build kernel by your own - you need only source.
PS: kernel has ext4 as built-in and ext2 and ext3 as modules, so if you have boot/root in other than ext4 - it won't work without initrd

Hi 
I have a Acer 4820TG, BIOS 1.15 and I´m using kernel 2.6.34-aspire-4820tg. But I have a problem with vga_switcheroo. It looks like something is wrong with Radeon card. There is a part from dmesg:

[    6.990601] [drm] radeon defaulting to kernel modesetting.
[    6.990603] [drm] radeon kernel modesetting enabled.
[    6.990642] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[    6.990681] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[    6.990689] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.990694] radeon 0000:01:00.0: setting latency timer to 64
[    6.994557] [drm] initializing kernel modesetting (CEDAR 0x1002:0x68E0).
[    6.994722] [drm] register mmio base: 0xDC400000
[    6.994724] [drm] register mmio size: 131072
[    6.994725] vga_switcheroo: enabled
[    6.994864] radeon atpx: version is 1
[    6.994955] reserve_ram_pages_type failed 0x100000000-0x100001000, track 0x10, req 0x10
[    6.994956] ioremap reserve_memtype failed -16
[    6.994997] ACPI Error: Could not map memory at 0000000100000103, size EFD (20100121/exregion-178)
[    6.995001] ACPI Exception: AE_NO_MEMORY, Returned by Handler for [SystemMemory] (20100121/evregion-474)
[    6.995005] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.GFX0.ATRM] (Node ffff880133a750c0), AE_NO_MEMORY
[    6.995058] failed to evaluate ATRM got AE_NO_MEMORY
[    6.995173] radeon 0000:01:00.0: Invalid ROM contents
[    6.995265] radeon 0000:01:00.0: Invalid ROM contents
[    6.995319] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM
[    6.995364] radeon 0000:01:00.0: Fatal error during GPU init
[    6.995406] [drm] radeon: finishing device.
[    6.995442] vga_switcheroo: disabled
[    6.995596] radeon 0000:01:00.0: PCI INT A disabled
[    6.995601] radeon: probe of 0000:01:00.0 failed with error -22


Anyone know what is wrong? Thanks for help.

---

### Post by ari197 on 2010-08-13
> **hshan said:**
> ari97 thanks for your diligence , but would you mind explaining your procedures and steps for others coming to this thread?

1. I installed all the package that Trevino provide.
2. For my virtual box, I downloaded the latest version from its website ([http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)). Don't select according to your distribution, select All Distribution that will gives you the source. Just follow the doc to install it.
3. Download the broadcom driver and patches from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) .. patch the driver source, compile and install.

---

### Post by lyradmil on 2010-08-13
> **marincop said:**
> @Trevino 
 
   The switcher is OK now , Just need to exit to the and login again .
Intel integrated vga work perfect, but when I with to the ATI Radeon card . It's need a driver .
So I install the driver, but failed.
   I can install it on kernel 2.6.32 perfectly , but the when kernel upgrade to 2.6.35 it will cause errors.
I think it the vga card driver problem .
@All
   Is anyone successfully install the flgrx on 2.6.35 kernel ? or where I can get the newest flgrx driver?

   Albert

When I tried launching the script, Both integrated and discrete did not show any information on my graphics card. I get the pop-up dialog but it shows: 

Choose Hybrid Graphic Card
=================
Integrated:  : 
Discrete: ( ) - Power ON : 

Did you experience this? My BIOS is set to Switch, I have the switch file in the VGAswitcheroo dir.

===
EDIT: Navigate to "cd sys/kernel/debug/vgaswitcheroo". I managed to switch the cards manually in the shell using:
$ echo DDIS > switch #discrete
$ echo DIGD > switch #integrated
$ echo OFF > switch
In order for this to work, you will be required to logout and login again. An easier way, which I did was to modify the /etc/rc.local file. This tells the system to load with the discrete card turned off, enabling only the integrated one. I simply added:

chown "username" /sys/kernel/debug/vgaswitcheroo/switch #change "username" to your username
echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

However, the above-mentioned script is unable to do the switching for me. It only informs me of which card is currently activated. So I use it to quickly check if my discrete card is turned off. In any case, the default activation is the integrated (lower-powered) Intel VGA. To maximize battery power, turn off the discrete card from the command above. I got an extension in battery life. I have yet to confirm the actual battery span but will get back to you guys again.

EDIT2: I managed to eject the CD tray using this command "eject /dev/dvd1". Created a launcher for it and all is good. If your eject command is not working like me before, use "ls -l /dev | grep '\->'" (without the quotes) If your cd/dvd drive is properly configured, it will be on that list. On my system, I have dev/cdrom1, dev/cdrw1, dev/dvd1 and dev/dvdrw1 which all works. :D

==

Hope it helps! So that's extended battery life! Still waiting for feedback on how to enable the proper display of the graphics card information on the window prompt.

---

### Post by Roadrun on 2010-08-14
I have the same problem. I cant´ compile because of missing autoconf.h. How do I get it?

   Thanks

> **ari197 said:**
> @Trevino

so I've managed to get VirtualBox running by installing from the source directly .. but I still cant' have my wifi working. When I tried to compiled the driver, it's missing the "linux/autoconf.h" files from your header ..

---

### Post by ari197 on 2010-08-14
it's because since linux-2.6.34 (i think), Linus move the autoconf.h to another directory .. also there are some lib that aren't compatible ..

download the patches from broadcom page and apply it to the source..

> **Roadrun said:**
> I have the same problem. I cant´ compile because of missing autoconf.h. How do I get it?

   Thanks

---

### Post by Elepferd on 2010-08-14
> **ari197 said:**
> it's because since linux-2.6.34 (i think), Linus move the autoconf.h to another directory .. also there are some lib that aren't compatible ..

download the patches from broadcom page and apply it to the source..

Use "[Patch for kernel 2.6.33 and higher]("http://www.broadcom.com/docs/linux_sta/sta_5.60.48.36_2.6.33_kernel_patch.zip")" and "[Multicast patch for kernel 2.6.34 and higher]("http://www.broadcom.com/docs/linux_sta/sta_5.60.48.36_2.6.34_multicast_kernel_patch.zip")" on [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and see README.TXT for further information.

---

### Post by Fshy on 2010-08-14
Sorry if this has already been answered somewhere else, but I had the same issue as this person -- 

> 
d) FGLRX graphic driver - blank screen after booting

When I enabled the FGLRX proprietary graphics driver, I ended up with a blank screen after reboot. I did not manage to repair this and had to reinstall (I'm not a Linux professional...). Power consumption is low with the inbuilt card, so I'm quite happy with the standard card. I did not try to find a solution for this, as I am not keen on reinstalling again. Still sad for a nice piece of hardware not used.


I've tried the graphics driver twice now, and it always black screens after a reboot. I *am* capable of resetting back to Intel drivers via the startup options area, but I wasn't able to find a way to fix this. Again, sorry if this has already been answered somewhere and I missed it, but it really is a shame to not use this excellent card. -- Fshy

---

### Post by Roadrun on 2010-08-14
OK. I have downloaded the paches, apply them, created wl.ko, put it it to /lib/modules/2.6.35-7-generic/kernel/net/wireless and when I tried insmod wl.ko, I got message:

insmod: error inserting 'wl.ko': -1 Invalid parameters

And in logs I can see this lines:

wl: disagrees about version of symbol create_proc_entry
wl: Unknown symbol create_proc_entry (err -22)
wl: disagrees about version of symbol remove_proc_entry
wl: Unknown symbol remove_proc_entry (err -22)

Any idea whats wrong?

> **ari197 said:**
> it's because since linux-2.6.34 (i think), Linus move the autoconf.h to another directory .. also there are some lib that aren't compatible ..

download the patches from broadcom page and apply it to the source..

---

### Post by hshan on 2010-08-14
> **Elepferd said:**
> Use "[Patch for kernel 2.6.33 and higher]("http://www.broadcom.com/docs/linux_sta/sta_5.60.48.36_2.6.33_kernel_patch.zip")" and "[Multicast patch for kernel 2.6.34 and higher]("http://www.broadcom.com/docs/linux_sta/sta_5.60.48.36_2.6.34_multicast_kernel_patch.zip")" on [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and see README.TXT for further information.

> **ari197 said:**
> 1. I installed all the package that Trevino provide.
2. For my virtual box, I downloaded the latest version from its website ([http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)). Don't select according to your distribution, select All Distribution that will gives you the source. Just follow the doc to install it.
3. Download the broadcom driver and patches from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) .. patch the driver source, compile and install.


Thanks guys, finally got wifi going on my 4820t with Travino's kernels

---

### Post by ari197 on 2010-08-14
do 
 - depmod -a
 - modprobe wl

> **Roadrun said:**
> OK. I have downloaded the paches, apply them, created wl.ko, put it it to /lib/modules/2.6.35-7-generic/kernel/net/wireless and when I tried insmod wl.ko, I got message:

insmod: error inserting 'wl.ko': -1 Invalid parameters

And in logs I can see this lines:

wl: disagrees about version of symbol create_proc_entry
wl: Unknown symbol create_proc_entry (err -22)
wl: disagrees about version of symbol remove_proc_entry
wl: Unknown symbol remove_proc_entry (err -22)

Any idea whats wrong?

---

### Post by Roadrun on 2010-08-15
Sorry, didn´t work. I´m geting this error:

FATAL: Error inserting wl (/lib/modules/2.6.35-7-generic/kernel/net/wireless/wl.ko): Invalid argument
FATAL: Error running install command for wl

And in logs I heve the same error:

wl: disagrees about version of symbol create_proc_entry
wl: Unknown symbol create_proc_entry (err -22)
wl: disagrees about version of symbol remove_proc_entry
wl: Unknown symbol remove_proc_entry (err -22)

I didn´t find anything useful about this error. 

Thanks

> **ari197 said:**
> do 
 - depmod -a
 - modprobe wl

---

### Post by ari197 on 2010-08-15
how did you put the "wl.ko" file to the /lib/module directory? did you copy it or did you do "make install" ?

> **Roadrun said:**
> Sorry, didn´t work. I´m geting this error:

FATAL: Error inserting wl (/lib/modules/2.6.35-7-generic/kernel/net/wireless/wl.ko): Invalid argument
FATAL: Error running install command for wl

And in logs I heve the same error:

wl: disagrees about version of symbol create_proc_entry
wl: Unknown symbol create_proc_entry (err -22)
wl: disagrees about version of symbol remove_proc_entry
wl: Unknown symbol remove_proc_entry (err -22)

I didn´t find anything useful about this error. 

Thanks

---

### Post by Roadrun on 2010-08-15
I have tried both ways, but non worked. Always the same errors

> **ari197 said:**
> how did you put the "wl.ko" file to the /lib/module directory? did you copy it or did you do "make install" ?

---

### Post by ari197 on 2010-08-15
> **Roadrun said:**
> I have tried both ways, but non worked. Always the same errors

hmmm ... sorry mate .. don't know what's wrong then :(

maybe you could contact broadcom support .. that's how I know that I need to patch the source first ..

---

### Post by Roadrun on 2010-08-16
OK, I solved it. I had installed kernel linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb and it some have did not work. I changed it for linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu1_amd64.deb and now it works. There are still some problems with suspend mode but that I will try to resolve later when I will have more time.

> **ari197 said:**
> hmmm ... sorry mate .. don't know what's wrong then :(

maybe you could contact broadcom support .. that's how I know that I need to patch the source first ..

---

### Post by Elysius on 2010-08-19
> **Roadrun said:**
> I changed it for linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu1_amd64.deb and now it works. 

Where'd you get this kernel from?

---

### Post by Roadrun on 2010-08-19
I found this link in one of the posts here.

[http://download.tuxfamily.org/3v1deb/acer-timelinex/](http://download.tuxfamily.org/3v1deb/acer-timelinex/)


> **Elysius said:**
> Where'd you get this kernel from?

---

### Post by flo4s on 2010-08-20
thanks to [COLOR=Black]Trevino, his kernel ([http://ubuntuforums.org/showpost.php?p=9586610&postcount=52](http://ubuntuforums.org/showpost.php?p=9586610&postcount=52)) get my lovely computer work fine.

But I still have two majors problems : 
1 - on battery time : just 2 hours... 

2 - fans : they are always on... may be cause for 1...

some searches on 2 give me : 
[/COLOR]```
[COLOR=Black]- sudo pwmconfig
```[/COLOR][COLOR=Black]
==> /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

[/COLOR]```
[COLOR=Black]- sudo sensors-detect
```[/COLOR][COLOR=Black]
==> Sorry, no sensors were detected.

and
[/COLOR]```
[COLOR=Black]- sensors
```[/COLOR][COLOR=Black]
==>
acpitz-virtual-0
Adapter: Virtual device
temp1:       +54.0°C  (crit = +105.0°C) 

Any other in front of that ? 
Any guru to give a workaround ? 

Thanks for any help


[/COLOR]

---

### Post by mike81 on 2010-08-24
> **Fshy said:**
> Sorry if this has already been answered somewhere else, but I had the same issue as this person -- 



I've tried the graphics driver twice now, and it always black screens after a reboot. I *am* capable of resetting back to Intel drivers via the startup options area, but I wasn't able to find a way to fix this. Again, sorry if this has already been answered somewhere and I missed it, but it really is a shame to not use this excellent card. -- Fshy

I had the same problem but went into the BIOS and switched the Graphics mode from 'switchable' to 'discrete'. I don't know exactly what that means but it loads alright now and I can get to the catalyst control centre alright.

[COLOR="Red"]Update. Oops, just saw #72.[/COLOR]

---

### Post by RavensKrag on 2010-08-29
Ah, sorry I wasn't around to help you guys with your wireless problems.  I thought I had made a post about the need to compile new wireless drivers but I guess not.  Also, I was able to bind the command "eject cdrom" to a keyboard shortcut using ubuntutweak in order to allow me to open the drive.

Has anyone been able to get the discrete card to shut off on startup? I have had to do this manually and it's a bit of a pain...I believe you can get about 5 hours if the discrete card is off.  However, I think the claim of 8 hours applies to other models in the TimelineX series and not the one I have.  Has anyone actually been able to get 8 hours, even in windows?

@Mike81
Discrete mode in BIOS will turn off the integrated video card and only enable the discrete card.  This will give you better performance, but worse battery life.  Also, you will be unable to switch back and forth in windows, if that is an issue.

---

### Post by Karajan on 2010-08-29
Shutting off the discrete card worked for me with this guide: [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
Some easier ways failed, most times I wasn't able to use my mouse or my keyboard after a reboot.


I get about 7 hours (discrete card off) on Ubuntu (with 60 Wh). But this was only doning some simple tasks, watching a DVD gave me only 3 hours, listening to music maybe 5? Don't remember.

Also I don't have a usual install, I installed Ubuntu Server and did 'sudo apt-get install ubuntu-desktop --no-install-recommends' -- this way I only have the software I really need and not too much running in the background. Plus the Server version is more power-saving (of course ;))

Maybe not the easiest way but getting 7 hours is possible :P

---

### Post by RavensKrag on 2010-08-29
I also was able to figure out the switch.  I just needed to put a simple script into /etc/init.d/ which accepted one argument which was either start, stop, or restart.  Then i ran sudo update-rc.d NAME_OF_SCRIPT defaults.  Now the card powers off and on with shutdown and startup respectively.

@Karajan
Does the server version really have better power saving? I was under the impression that the desktop version would, especially if you install the laptop power saving packages.  I believe the server version is really just the minimal command-line version, or am I mistaken?

Also, I sort of figured that 7-8 would be at the top of the range, meaning that you would only get those numbers on minimal usage.  That's fine with me though ^_^

---

### Post by Karajan on 2010-08-29
Well, I'm not sure if it's really more power-efficient. I read something about the server-kernel being specially tuned to be power saving... My main reason to do this was to have a "minimal" Ubuntu.

Yes, you have nothing but a command-line but after 'sudo apt-get install ubuntu-desktop --no-install-recommends' it's just like a normal Ubuntu install -- with only a few programs installed.

---

### Post by Cpasjuste on 2010-09-01
Hi, i compiled a kernel for ubuntu i386 cpus, with the acpi/power patch and vga switcheroo activated. I tought it could be usefull to share so here is the links :

[linux-headers-2.6.35.4-switcheroo_2.6.35.4-switcheroo-10.00.Custom_i386.deb]("http://mydedibox.fr/_stuff/acer4820tg/linux-headers-2.6.35.4-switcheroo_2.6.35.4-switcheroo-10.00.Custom_i386.deb")
[linux-image-2.6.35.4-switcheroo_2.6.35.4-switcheroo-10.00.Custom_i386.deb]("http://mydedibox.fr/_stuff/acer4820tg/linux-image-2.6.35.4-switcheroo_2.6.35.4-switcheroo-10.00.Custom_i386.deb")

---

### Post by lukasw on 2010-09-02
Today I managed to open my (empty) disc drive by pressing the eject button over the numpad. Don't know how, it just worked. Just wanted to tell you it's possible.

BTW: I removed plymouth by using the mountall package of [this ppa]("https://launchpad.net/%7Edtl131/+archive/mediahacks"). Ubuntu starts much faster now :D

Edit: At the moment ejecting is working again but 'eject'(in a terminal) doesn't work anymore.

Edit 2: Seems like since I removed plymouth, the eject button does it's job fine.

---

### Post by lordamit on 2010-09-03
> **Cpasjuste said:**
> Hi, i compiled a kernel for ubuntu i386 cpus, with the acpi/power patch and vga switcheroo activated. I tought it could be usefull to share so here is the links :

[linux-headers-2.6.35.4-switcheroo_2.6.35.4-switcheroo-10.00.Custom_i386.deb]("http://mydedibox.fr/_stuff/acer4820tg/linux-headers-2.6.35.4-switcheroo_2.6.35.4-switcheroo-10.00.Custom_i386.deb")
[linux-image-2.6.35.4-switcheroo_2.6.35.4-switcheroo-10.00.Custom_i386.deb]("http://mydedibox.fr/_stuff/acer4820tg/linux-image-2.6.35.4-switcheroo_2.6.35.4-switcheroo-10.00.Custom_i386.deb")

hi there :) I am using acer 4745
I have installed your package with the hope that the laptop's battery state notification will become more realistic.(i.e. always "laptop battery is charged).

after installation and restarting, now when I use acpi -b, it shows 

```

Battery 0: Discharging, 95%, 03:08:35 remaining

```But when I right click on the gnome-power-manager, it still shows "laptop battery is charged".


here are some more information:

before instlallation:
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      unknown
present voltage:         10000 mV
**cat /proc/acpi/battery/BAT1/info** gives:
     Code:
     present:                 yes
design capacity:         4400 mAh
last full capacity:      4400 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 300 mAh
design capacity low:     132 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            BAT1      
serial number:           11        
battery type:            11        
OEM info:                11 

after installation:
```

cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1322 mA
remaining capacity:      4118 mAh
present voltage:         12093 mV
```and
```

present:                 yes
design capacity:         4400 mAh
last full capacity:      4401 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 300 mAh
design capacity low:     0 mAh
cycle count:          0
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            AS10B73
serial number:           0CAF
battery type:            LION
OEM info:                SIMPLO

```So, the acpi knows about the present battery state now, but somehow, gnome power manager is not being notified. I tried restarting gnome-power-manager through kill and then restarting it, but it didn't work.

Any suggestions?



Edit:
I tried to hibernate just now. And it after a while showed a black screen with this text:

```


[33.111880] ata2.00: exception Emask 0x0 SAct 0x0 Serr 0x0action 0x6 frozen
[33.113573] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[33.113575]              res  40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4
[33.116771] ata2.00L status {DRDY}

```Then I had to shut it down by pressing the power button.
When I booted, i found that the pc state was not saved like it was supposed to in shutdown. 

However, then the battery state started working via gnome-power-manager.



edit 2:

Another hibernate and it does not show any error. But it does not shut down nor save the state either. Other than that, the battery state is working fine :)

---

### Post by RavensKrag on 2010-09-03
@lordamit
I have that problem sometimes as well.  If the computer is started on battery power, this does not seem to be an issue.  

On the issue of hibernation, do you have an amount of swap space >= your amount of RAM?

---

### Post by lordamit on 2010-09-04
Yes. My laptop's RAM is 2GB ddr3, and swap space is around 6GB. 
BTW, thanks a lot for preparing this package. 

Oh on another note, when I tried to hibernate, it was stuck, so I had to shutdown it using the power button. when I rebooted, it showed 


init: ureadahead main process(X) terminated with status 5

where X is some process number here, starting from 400

I studied about this for a while, and apparently, there was something with the hdd state. I unmounted the ntfs drives as well, but it didn't help.

So I  rebooted using the previous kernel, and it somehow fixed the error issue.


Edit:

I reinstalled ubuntu and right after that installed your packages. because of some experiments.. my ubuntu was a lot more slower, and at boot time gave a resume: libgcrypt version 1.4.4 message.

But I noticed that after installing your packages, the wireless connection issue is fixed.(no "enable wireless" clicking needed from network manager applet after login to connect to wireless)

Edit:
:| I am awed. After installing your packages, I didn't have to go through Alsa upgrade script. it automatically somehow managed to become 1.0.23(it is normally 1.0.21 in ubuntu 10.04)


Edit2: 
This 2.6.35 kernel is almost perfect. it fixed up the battery, wifi and alsa issue.
And After a fresh install, hibernate works as well. It gives some error messages in the blank screen when Bluetooth is turned on, and on several cases, but it works and now resumes.


Thanks a lot :)

---

### Post by nytbis on 2010-09-04
Thanks Trevino!

---

### Post by lordamit on 2010-09-04
I am getting a ureadahead main process terminated error with status 5 now. is there any suggestion?

---

### Post by Furunes on 2010-09-06
Hey

Could really need some help.
Don't have a wlan interface. 
My wired network, work fine. (ethernet)
Can't get it to work(wireless network).

RutilT gives me this message: 
can't find any wireless network interface.
Code: -3

And at startup its "disconnected"!(message)

Tryed #[marm0tte's tricks without any luck]("http://ubuntuforums.org/member.php?u=923524")

What to do?

Please help

---

### Post by lordamit on 2010-09-06
> **wcharlot said:**
> status 5 usually means that you have /var mounted on a separate partition, is that true?
 The mountall errors are a knock-on effect of an earlier bug that  should already be fixed, did exiting from this shell fix the issue for  you?


Nope, the whole ubuntu is installed in one partition. I have some ntfs partitions which are all mounted  automatically using ntfs config. But turning them off didn't solve this issue.

Exiting from the shell, i do not understand that part.

---

### Post by lordamit on 2010-09-06
> **wcharlot said:**
> status 5 usually means that you have /var mounted on a separate partition, is that true?
 The mountall errors are a knock-on effect of an earlier bug that  should already be fixed, did exiting from this shell fix the issue for  you?


Nope, the whole ubuntu is installed in one partition. I have some ntfs partitions which are all mounted  automatically using ntfs config. But turning them off didn't solve this issue.

Exiting from the shell, i do not understand that part.

---

### Post by shantzg001 on 2010-09-08
Seems like there is a new bios 1.18 out from Acer for 4820TG. Anyone tried it yet?

---

### Post by whargoul on 2010-09-08
> **shantzg001 said:**
> Seems like there is a new bios 1.18 out from Acer for 4820TG. Anyone tried it yet?

I just installed the new BIOS, and I booted up in a clean OpenSuse 11.3 install with NO kernel modifications. Guess what? Battery works like it should! Even better than that pesky patch which has been mentioned in this thread.

---

### Post by pemasu on 2010-09-08
Bios 1,18 fixes acpi problem also with my 5820tg

---

### Post by shantzg001 on 2010-09-08
Awesome.. I guess all will be well now with Maverick for this lappy. I have got it just yesterday and wading through all the different problem threads. I think that most other issues are resolved already with the new kernel coming in with maverick (including the vga switcheroo) and now we can also get battery working with the new BIOS. :) 
Will install maverick beta this weekend then..
BTW, any good links to dual boot win 7 with ubuntu on this lappy without crapping any recovery/other stuff? This is my first win 7 laptop and also the first that has a on-disk recovery partition so not completely sure..

---

### Post by lordamit on 2010-09-09
Hi.
I noticed that there is also a new BIOS update( 1.18 )
I just installed it from windows, and then restarted to switch to Ubuntu.
The bluetooth, and the battery problem is fixed. Though... I need to upgrade the Alsa sound thing now :)

---

### Post by Janiskeisari on 2010-09-10
Wow, thanks.

The bios-update worked fine with my 5820TG and fixed these issues:
[LIST]
[*]Bluetooth
[*]Wireless auto-enable
[*]Battery-state meter
[*]Possibly also the thermal meter
[/LIST]

Now I'm just waiting for Maverick, if it really has vgaswitcheroo built-in..

---

### Post by princealex on 2010-09-14
I am really glad with this new bios.

---

### Post by eyolf on 2010-09-20
> **flo4s said:**
> 
2 - fans : they are always on... may be cause for 1...


Any news on this? I have the same issue, and I must say, if I have to choose between a noisy linux or a silent windows, I'm inclined to go with the latter...

---

### Post by daveboy23 on 2010-09-21
a noob question here - since i've never updated a bios, just wanna make sure - does the latest version contains all previous fixes?
it seems like all updates are the same size (that's why i'm asking...)
or should i install each patch one after the other?
also have acer aspire 4820tg and not working with bat, wireless etc.

---

### Post by shantzg001 on 2010-09-21
^^ yup u need to install only the latest one..

---

### Post by an7on on 2010-09-24
> **giova.86 said:**
> **Problem 8: integrated microphone**
If you have some problems with the integrated microphone, to solve it you have to update the alsamixer to version 1.0.23. And if you need a guide, look this: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
Thank you! The link you gave is very helpful!

---

### Post by vrinse on 2010-10-02
Hi!
I'm french, so sorry for my english!

I read the thread, thanks a lot!

I erased all the harddisk, because i don't want windows (i will try to get back my money from acer). So, i have no windows anymore on that computer.

But i'd like to flash the bios, in order to solve all the problems.
The bios version 1.18 from the site of acer is only an exe, to run on windows…
Do anybody knows a trick to flash the bios without having windows on the machine?
Any link to download the good new version for bios runnable without windows?
Any link for explanation about how to install it?

Thanks!

---

### Post by marm0tte on 2010-10-02
Hello vrinse,


ASUS distribute there BIOS upgrades only compiled for Microsoft Windows or DOS.
I assume that you don't want to use a non open source OS  :)

It seems that the FreeDOS project can help you to flash your BIOS :cool:
Here is a good HOWTo :
[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

[B]The problem is that I've never test a BIOS flash from FreeDOS.
So be careful, It seems that FreeDOS is based in DOS 3.3 and not on the latest version 6.22 ...  ](*,)
[http://sourceforge.net/apps/mediawiki/freedos/index.php?title=FreeDOS_Spec](http://sourceforge.net/apps/mediawiki/freedos/index.php?title=FreeDOS_Spec)[/B]


Please keeping us informed of the outcome ...

---

### Post by vrinse on 2010-10-02
Hi marmotte!

Thanks a lot for the trail!
I found a page on the french wiki, with a tuto about how flashing the bios of an MSI computer with FreeDos.
But the process is supposed te be exactly the same with acer. So i followed the tuto, installing FreeDos on an usbkey with unetbootin, and so on.
I was a bit afraid… but i finally tried the flash. And it worked perfectly! :grin:
At the end, thanks a lot!!!

So… Viva el libre! F…**f windows! (and acer!) :P

_Edit_: French wikipedia say  about FreeDos that developers choose to base on Dos 3.3 because 4.x, 5.x and 6.x versions aren't strong changes about the core of Dos. Well, it worked for me, maybe they're right. :)

---

### Post by marm0tte on 2010-10-03
Happy to know that a flash of the BIOS is possible with FreeDOS :)
The next time I will use that.

Yes you're right Asus is not really fan of Linux, like many computer reseller/builder.
You're french like me, so you can read this document about good and bad computer reseller/builder :
[http://bons-constructeurs-ordinateurs.info/](http://bons-constructeurs-ordinateurs.info/)


And I wish a long life to open-source software :P

---

### Post by daveboy23 on 2010-10-05
hi everyone, flashing the bios works great with the batt (although doesn't fix everything - like multitouch etc.)
does anyone knows if all these problems are going to be fixed in 10.10? the ATI would work, the switch GPUs, the wireless (out of the box), i've heard someone here talk about fans and CPU temp?

---

### Post by nicolaary on 2010-10-05
Dear all,
   is anybody that has some time to make a quick summary of this long thread?

How to fix the battery issue?
How to fix the mic noise?
How to fix the enable wi-fi at the beginning?

Thank you very much :-)

Nicola

---

### Post by nicolaary on 2010-10-05
HI,
  Actually I can make a summary by myself also because after the new bios installation I do not have anymore the battery problem and the enable wi-fi issue.
For what is concerning the problem with the microphone I have upgraded to the [ALSA version 1.0.23 ]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/") but the record voice in Skype is still noisy!

Anybody has any idea on how to fix the mic?

A part of the skype issue now I can use my new Lin-Laptop!:guitar:

---

### Post by nicolaary on 2010-10-05
Hi,
  I made a summary of the thread in this blog:

[http://kblackhat.blogspot.com/2010/10/installing-kubuntu-1004-on-acer.html]("http://kblackhat.blogspot.com/2010/10/installing-kubuntu-1004-on-acer.html")

I hope I did not forget anything... in case please let me know and I will update it..
:)

---

### Post by moviglez on 2010-10-05
Problem with VGA switching with kernel 2.6.35 (Ubuntu 10.10) and BIOS 1.18 install Ubuntu Control Centre 0.5.1 [http://sites.google.com/site/ubuntucontrolcenter/downloads](http://sites.google.com/site/ubuntucontrolcenter/downloads)

-Changelog-

* Fixed error with opengl performance
* **New VGA Switching Module (needs kernel 2.6.35)**
* New category icons
* Small fixes on the interface

See this video [http://ubuntuforums.org/showpost.php?p=9670648&postcount=14](http://ubuntuforums.org/showpost.php?p=9670648&postcount=14)

Thanks :]

---

### Post by RavensKrag on 2010-10-06
Haven't been on this thread in a while, but it seems as if everything is going well for my fellow Acer users.  However, one question.  Has anyone been able to get 3D acceleration on the ATI card? I have a kernel with the switch, and can switch to it, but I do not know if I will get any 3D support.

I assume the open source drivers in-kernel work, but has anyone tried the latest proprietary ATI driver?

(I would like to be able to play games in linux again ^_^;)

---

### Post by daveboy23 on 2010-10-12
> **nicolaary said:**
> HI,
  Actually I can make a summary by myself also because after the new bios installation I do not have anymore the battery problem and the enable wi-fi issue.
For what is concerning the problem with the microphone I have upgraded to the [ALSA version 1.0.23 ]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/") but the record voice in Skype is still noisy!

Anybody has any idea on how to fix the mic?

A part of the skype issue now I can use my new Lin-Laptop!:guitar:
yap, i actually searched for that myself - here's the solution: go to skype and disable the automatic sound adjust thing then go to terminal - type alsamixer, press F4 (capture tab) - so to capture and put it all the way up (or to a volume you like) then (on the same column) press 'y' till you completely mute the left channel.  now skype works.  problem - if you change the volume from the pulse you loose this configuration so take care.

---

### Post by daveboy23 on 2010-10-12
i've checked this thread (didnt read everything i admit but most of it) and it seems to me like i'm the only one who can't install the ATI drivers.  i've tried installing the proprietary drivers in ubuntu 10.10 and the same thing happened - when i boot, after the splash screen i'm dropped into the terminal (in other words - now i don't have any graphics, windows etc.)  so, how can i fix that one? and is there a way to install the ATI?

---

### Post by marm0tte on 2010-10-12
Hello,


The same story arrive to me :P


When you start your computer and the boot loader grub appears, choose the kernel in recovery mode (named Ubuntu, with Linux 2.6.35-22-generic (recovery mode))

After, choose to start the graphical interface in degraded mode (don't remember exactly the name)
GNOME + XORG will show you the graphic interface and you will be able to uninstall the ATI Properatery drivers.


I don't search to install it anymore after this problem, but the open source driver for ATI is pretty good and fast so I will keep them ;)

---

### Post by RavensKrag on 2010-10-12
> **marm0tte said:**
> Hello,
I don't search to install it anymore after this problem, but the open source driver for ATI is pretty good and fast so I will keep them ;)

You say the driver is "good and fast" which is great to hear, but do you have 3D support? ie, can you enable desktop effects?

(Now that I think about it, I suppose I could just switch over and check, but I believe I'm running a slightly older kernel, so I might not get the same results.)

---

### Post by marm0tte on 2010-10-13
If you are under ubuntu 10.10 so by default, you will have the same kernel as me (2.6.35-22-generic).

The radeon (open source driver) of the ATI Radeon HD 5600 video card enable 3D effects. Compiz for exemple works like a charm. I've also install gnome-shell and it works.

---

### Post by RavensKrag on 2010-10-14
> **marm0tte said:**
> If you are under ubuntu 10.10 so by default, you will have the same kernel as me (2.6.35-22-generic).

The radeon (open source driver) of the ATI Radeon HD 5600 video card enable 3D effects. Compiz for exemple works like a charm. I've also install gnome-shell and it works.

Wow, that's great news.  I unfortunately have been very busy, so I'm still using 10.4 with kernel 2.6.34-1 which I compiled myself.  Does the kernel in 10.10 have the VGA Switcheroo and everything compiled in already as well?  Compiling a kernel is quite time consuming and I hope I don't have to do that again.

For clarification, which should help daveboy23 as well as myself, you mean the Radeon driver in the kernel right? By this I mean that you did not have to install a separate driver.  If I am correct, the ATI driver provided though jockey (the driver installation script-thing) does not have kernel mode setting.  What this basically boils down to is that it will not work with hybrid cards like the ATI Radeon HD 5650.

---

### Post by marm0tte on 2010-10-14
Yes, switcheroo is integrated in the kernel 2.6.35 provided in maverick by Canonical ;)

I've installed the ucc (ubuntu control center) that moviglez recommends and it's a pretty useful application. If you go in the category Hardware you will found a tool named VGA switching ... but it doesn't works :(

So, I've follow this thread : [http://www.phoronix.com/forums/showthread.php?t=21979](http://www.phoronix.com/forums/showthread.php?t=21979)

These commands works and switch the VGA between ATI and Intel cards :)

sudo su
mount -t debugfs none /sys/kernel/debug
cd /sys/kernel/debug/vgaswitcheroo
cat switch   # to see which card is active
echo DDIS > switch   # to go to discrete card (log off and then log in after this command)
echo DIGD > switch   # to go to integrated card (log off and then log in after this command)
echo OFF > switch   # to just poweroff the card you aren't using


**I will really appreciate if someone know a tool or a widget to do that stuff more friendly :P**

---

### Post by snarf77 on 2010-10-14
Hi All,

Great thread for happy owner of this laptop...

I'm still working on Ubuntu 10.04 since I bought this laptop and I follow this thread with interest. I'm planning to move on 10.10 in a few days but I'm not sure to fully understand if with this new version a BIOS update is still necessary or not ?

If it is does anyone has a good link on how to update the BIOS. I looked on Acer website but only found an ISO CD supposed to then load the right version but is this the way you proceed ? how to be sure to get the correct version (do you need to download it before ? where ??)

Sorry for stupid question but I'm not to familiar with that.

Thanks

Snarf

---

### Post by wizards on 2010-10-14
Hi :) this is some manual for update BIOS .. some little help for others :)

1.)go on [http://support.acer-euro.com/drivers/downloads_gd.html](http://support.acer-euro.com/drivers/downloads_gd.html)
(its hard - they site its not work very good for me)
2.) select type of notebook
3.) and download new bios
4.) for me   Acer Aspire 4820TG - last 1.19 (10.4.2010) 
5.) and install - I install it from Windows and its work :) its only exe files

And is this [U]necessary I thing yes :)its solved some problems :)
 [/U][U]


[/U]

---

### Post by RavensKrag on 2010-10-15
> **wizards said:**
>  I install it from Windows and its work :) its only exe files

I do believe there is a post a couple pages back on how to do it without a Windows install.  But if you have Windows on your computer still, that would be the best way to do it. It's really easy, just download and click, then wait for you machine to reboot.

---

### Post by wizards on 2010-10-15
Can somebody same problem like I? ..

I have installed
1.19 bios
64bit - Ubuntu 10.10
Ubuntu Control Centre 0.5.1 - from post from moviglez
and [B]ATI Catalyst™ 10.9 Proprietary Linux x86 Display Driver from ati page compiled with 
--listpkg[/B] and --buildpkg  and install packages ...

But sometimes (i thinkg twice or more day) graphics freeze and i must restart linux.  

Can somebody help me what can i must find (like some logs) or can i try to do... :/

---

### Post by eyolf on 2010-10-15
For what it's worth: 
When I upgraded my BIOS, the MBR was borked. I had a dual/triple boot setup with the pre-installed Win7 plus partitions with Ubuntu and Arch Linux. I flashed the BIOS from Windows, using the exe file from the acer site. Everything went smoothly - no warning, no nothing, but when it was finished -- successfully -- there was no contact with the computer. 

I can't remember what I did to solve it; I think perhaps I just reinstalled Ubuntu from a Live CD. It was a fresh install anyway, so I figured it would be quicker than to search out and burn some rescue CD from another computer etc., but I would hate to have had that happen on something other than a fresh install.

After the reinstall, everything is working fine, -- except that the fan is still blowing so heavily that I can't bear it. So I'm confined to Windows until that situation improves.

Just thought I'd mention it. I haven't heard of anyone else running into this, so it's probably just my bad luck, but I thought it should be added to the records.

---

### Post by whargoul on 2010-10-15
> **marm0tte said:**
> 
I've installed the ucc (ubuntu control center) that moviglez recommends and it's a pretty useful application. If you go in the category Hardware you will found a tool named VGA switching ... but it doesn't works :(


UCC works for me succesfully, although Intel is showed as a high performance card and ATI as powersaving card. But the opensource radeon driver does not have support for 3D for the 5000 series, so it is not really useful.
 
[QUOTE=wizards]
Can somebody same problem like I? ..

I have installed
1.19 bios
64bit - Ubuntu 10.10
Ubuntu Control Centre 0.5.1 - from post from moviglez
and ATI Catalyst&#8482; 10.9 Proprietary Linux x86 Display Driver from ati page compiled with 
--listpkg and --buildpkg and install packages ...

But sometimes (i thinkg twice or more day) graphics freeze and i must restart linux. 

Can somebody help me what can i must find (like some logs) or can i try to do... :/[/QUOTE]
The Catalyst does not currently have support for Xorg server 1.9 which Ubuntu uses. You'll have to wait for Catalyst 10.10.

EDIT:
Ah, sorry looked more into it, and Ubuntu does provide the 10.10 release, but this is an "early look". But the officiel 10.10 release will come later this month.

---

### Post by RavensKrag on 2010-10-15
> **whargoul said:**
> But the opensource radeon driver does not have support for 3D for the 5000 series, so it is not really useful.

Wait what? I thought someone just a couple posts back said that the 3D acceleration does in fact work o_O;

---

### Post by whargoul on 2010-10-16
> **RavensKrag said:**
> Wait what? I thought someone just a couple posts back said that the 3D acceleration does in fact work o_O;

Okay I was a bit quick on the keys when I wrote that. It does have *some* 3D support, but it is not very good. For example I tried to run Tuxracer and Neverball and it was really laggy. Also I don't have support for compositing. 
So you will be better off just running the intel card. Faster performance and lower power consumption.

---

### Post by marm0tte on 2010-10-16
Hello,


I'm on a fresh install of maverick 64 bits desktop and as I said 2days ago, the 3D acceleration works with the radeon opensource drivers !

TuxRacer works smoothly without any kind of problem, compiz too, gnome-shell, ...

---

### Post by crauto on 2010-10-18
hi marm0tte,
so ubuntu 10.10 64bit works great on your timelinex?
what have you done for make it working?
you have done only bios update and installed opensource driver for graphic card or you have done something else?
is everything working or there are still some problems?
thank you,
crauto

---

### Post by marm0tte on 2010-10-18
hi,

I've just upgrade the bios to 1.19 version.
I've made a fresh install of ubuntu maverick desktop 64 bits

That's all :)

---

### Post by wizards on 2010-10-19
......
I've just upgrade the bios to 1.19 version.
I've made a fresh install of ubuntu maverick desktop 64 bits

That's all :).....
 to crauto

Yes that's all but I have still some strenge problems with ubuntu...I hope you have everything ok :)

---

### Post by benjamimgois on 2010-10-19
> **whargoul said:**
> UCC works for me succesfully, although Intel is showed as a high performance card and ATI as powersaving card. But the opensource radeon driver does not have support for 3D for the 5000 series, so it is not really useful.
 

The Catalyst does not currently have support for Xorg server 1.9 which Ubuntu uses. You'll have to wait for Catalyst 10.10.

EDIT:
Ah, sorry looked more into it, and Ubuntu does provide the 10.10 release, but this is an "early look". But the officiel 10.10 release will come later this month.

hey, UCC works just fine with the opensource drivers. Take a look at the official video:

[http://www.youtube.com/watch?v=-S5-BVFk0G0](http://www.youtube.com/watch?v=-S5-BVFk0G0)

---

### Post by daveboy23 on 2010-10-20
ok, everyone says the open drivers work just fine - do you have the same computer i have? as in - acer 4820tg?
cause with my computer going to system->administration->additional drivers and enabling the ATI drivers makes my computer unable to boot again with graphix (so i need to revert back).  am i really the last guy without those drivers?

---

### Post by benjamimgois on 2010-10-20
> **daveboy23 said:**
> ok, everyone says the open drivers work just fine - do you have the same computer i have? as in - acer 4820tg?
cause with my computer going to system->administration->additional drivers and enabling the ATI drivers makes my computer unable to boot again with graphix (so i need to revert back).  am i really the last guy without those drivers?

Daveboy23, i have the same problem on my HP dv4 2080br. When go to admnistration > addtiononal driver you are installing the proprietary driver FGLRX from ATI and it will not work for anyone right now. Seens that the only way to use the FGLRX is to disable the onboard video driver on the system BIOS. In my case this option doesn't exist on my hp bios, so i have to wait for a solution.

---

### Post by RavensKrag on 2010-10-20
As has been said, the FGLRX drivers are the proprietary close-source drivers.  The open-source ATI drivers are part of the kernel, and thus are essentially pre-installed.  In short, do not install the drivers though jockey (the method you described).  The open-source drivers are the ones that work.

However, benjamimgois, you have a different laptop than us, so just to clarify, you have the ATI Mobility Radeon HD 5650 right? 'cause I'm not sure how well the driver works for other 5 series cards.  The 5 series support is a relatively new thing.  I believe it just started to roll out last month or something like that. It could work for you, I'm just not sure.

@daveboy23
Yeah, I have the same laptop, and I'm pretty sure the closed-source drivers will not work for a while, if ever.  The driver requires kernel mode setting (KMS) to switch graphics systems without restart.  Even with a restart, using drivers without KMS is annoying.  I had a sony vaio z which had that problem.

I tried to explain this difference before, but apparently I did not do a very good job.  Sorry for the confusion ^_^;

---

### Post by daveboy23 on 2010-10-20
ohhh ok, now i get it - it's my fault (didn't know the open source came built in) but you learn every day :-)

ok, so, now what? i've tried the UCC like in the video, but it doesn't seem to work for me (cause it can't find another card)

second - really? will never see support for that card? should that be a concern, or should i not care?

thx guys

---

### Post by RavensKrag on 2010-10-20
> **daveboy23 said:**
> ok, so, now what? i've tried the UCC like in the video, but it doesn't seem to work for me (cause it can't find another card)

Just double-checking, but what kernel are you running? I believe you need at least 2.6.35 to get 3D support, and at least 2.6.34 to get the card visible.  IMO, just having the card visible is kinda useless, as I'm using kernel 2.6.34-1 right now, and I never use the ATI card as it can't even do desktop effects.  I'm glad to hear that this problem is resolved in Maverick though.

> **daveboy23 said:**
> second - really? will never see support for that card? should that be a concern, or should i not care?

In terms of the close-source driver, perhaps.  However, as the open-source driver gets better and better, you might not need the closed-source drivers.  Especially if 3D acceleration is now possible with the OSS drivers.

---

### Post by benjamimgois on 2010-10-20
> **RavensKrag said:**
> 

However, benjamimgois, you have a different laptop than us, so just to clarify, you have the ATI Mobility Radeon HD 5650 right? 'cause I'm not sure how well the driver works for other 5 series cards.  The 5 series support is a relatively new thing.  I believe it just started to roll out last month or something like that. It could work for you, I'm just not sure.


Nope, my video card is a ATI Mobility HD 4550. The 3D acceleration works ok but the performance is very poor compared to FGLRX but it's better then the intel core i5, the VGA and HDMI outputs works too.

For a better performance and support on newer ATI gpus i would recomend to use the [X-Updates PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"). It brings the latest stable opensource drivers.

PS:  I´ll launch a update of ucc very soon, the latest kernel invert the order of gpus detection, so when you are using low performance graphics card it says that you are using the high performance one.

---

### Post by daveboy23 on 2010-10-22
> **RavensKrag said:**
> Just double-checking, but what kernel are you running? I believe you need at least 2.6.35 to get 3D support, and at least 2.6.34 to get the card visible.  IMO, just having the card visible is kinda useless, as I'm using kernel 2.6.34-1 right now, and I never use the ATI card as it can't even do desktop effects.  I'm glad to hear that this problem is resolved in Maverick though.



In terms of the close-source driver, perhaps.  However, as the open-source driver gets better and better, you might not need the closed-source drivers.  Especially if 3D acceleration is now possible with the OSS drivers.

i have ubuntu 10.10 (not sure how to check the kernel ver).  anyway, how do i check if both cards are working? is there something i can write in terminal? i just wanna make sure everything works.

also, tried UCC, don't see much change, how do i know which card is working?
thx guys

---

### Post by RavensKrag on 2010-10-22
...

---

### Post by RavensKrag on 2010-10-22
> **daveboy23 said:**
> i have ubuntu 10.10 (not sure how to check the kernel ver).  anyway, how do i check if both cards are working? is there something i can write in terminal? i just wanna make sure everything works.
thx guys

For future reference, you can check you kernel version (in gnome anyway) by opening the system monitor, then going to the "system" tab.  There is a command you can run, but I forgot what it is.

Regardless, as you are running Maverick, you should have a kernel which can switch to the ATI card.

Try running this to see if the switch mechanism is enabled in kernel.

sudo su
cat /sys/kernel/debug/vgaswitcheroo/switch

then use "exit" to exit the root shell.
If the cat command prints something like 

```
0:+:Pwr:0000:00:02.0
1: :Off:0000:01:00.0
```

Then you should be able to switch cards.

---

### Post by daveboy23 on 2010-10-23
cool, i've got these:
0: :Pwr:0000:01:00.0
1:+:Pwr:0000:00:02.0
is that ok? (i think it says both are on? what does it say anyway?)

something i just thought about - is there a smaller program that just have the switch graphix thing instead of the entire UCC?
and second - there is a button that should control the switch (the P next to the CD OUT button) would that work for switching? can i make it work somehow?

---

### Post by abbradar on 2010-10-24
Finally modified my DSDT table (taken from 1.19 BIOS ver.) and setted GRUB2 to load it on start. Result: working Bluetooth/WLAN switcher, both in Linux and Windows (Where it wasn't working from time to time). I have Arch Linux, not Ubuntu, but this is one of the biggest threads on my laptop, so let it be there :)
In attachments: modified DSDT source (0 Errors, 0 Warnings, 0 Remarks, 6 Optimizations) and ugly script for GRUB2 for table loading (place in /etc/grub.d)
Also, what about graphics? When I'm turning off Radeon card, system hangs up on the next X server start. Seems turning off Intel is OK for me, but it's a bit annoying.

---

### Post by wizards on 2010-10-24
New revision of ATI (from 22.10.2010) v.10.10  ;-)
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

but when i install - graphic interface of linux not started .. so maybe some users have more lucky then me :)

---

### Post by kemkem42 on 2010-10-25
Hello

I'm planning to purchase a 4820TG (434G64Mn version with ATI 5650)

I've read the entire thread, but I can't be really sure that this version is ok with ubuntu

According this page (link has been found in this thread) [http://kblackhat.blogspot.com/2010/10/installing-kubuntu-1004-on-acer.html](http://kblackhat.blogspot.com/2010/10/installing-kubuntu-1004-on-acer.html), this ATI card is ok

So I guess I can proceed :)

I am wrong ?

What is the status with other components (wifi/eth/acpi)?
I've quite sure that new bios provides fixes to these..

many thanks !

---

### Post by shantzg001 on 2010-10-25
> **abbradar said:**
> Finally modified my DSDT table (taken from 1.19 BIOS ver.) and setted GRUB2 to load it on start. Result: working Bluetooth/WLAN switcher, both in Linux and Windows (Where it wasn't working from time to time). I have Arch Linux, not Ubuntu, but this is one of the biggest threads on my laptop, so let it be there :)
In attachments: modified DSDT source (0 Errors, 0 Warnings, 0 Remarks, 6 Optimizations) and ugly script for GRUB2 for table loading (place in /etc/grub.d)
Also, what about graphics? When I'm turning off Radeon card, system hangs up on the next X server start. Seems turning off Intel is OK for me, but it's a bit annoying.

wi-fi/bt switching works fine for me on maverick without any changes with Stock 1.18 bios

---

### Post by abbradar on 2010-10-25
> **shantzg001 said:**
> wi-fi/bt switching works fine for me on maverick without any changes with Stock 1.18 bios

...and I have 1.19 BIOS, and bt is constantly not working for me (tried Kubuntu 10.10 too)... maybe it changes from model to model? (AFAIK on different models there are different WLAN/BT adapters installed). I have Foxconn BCM92846 BT and Atheros AR5B95 WLAN adapters.

---

### Post by abbradar on 2010-10-25
Removed modified table from GRUB2, loaded, catched similar bug. Shutted down computer, loaded, catched. Loaded default BIOS settings, loaded and - voila - switching properly working! Don't exactly know what was it connected with, but thanks for your answer.

---

### Post by RavensKrag on 2010-10-25
> **daveboy23 said:**
> cool, i've got these:
0: :Pwr:0000:01:00.0
1:+:Pwr:0000:00:02.0
is that ok? (i think it says both are on? what does it say anyway?)

something i just thought about - is there a smaller program that just have the switch graphix thing instead of the entire UCC?
and second - there is a button that should control the switch (the P next to the CD OUT button) would that work for switching? can i make it work somehow?


Ok, this means that your computer can switch graphics cards.  The specific info displayed means that the ATI card is active (as indicated by the + sign) and that both cards are on.  Assuming the open-source drivers are being used, and you're using Ubuntu Maverick, the 3D support should be working.

In order to switch graphics cards do the following.
First get root (for some reason using sudo isn't enough here)
```
sudo su
```
then pick a command depending on what you want to do.

To switch to the ATI card
```
echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
```
To switch to integrated Intel graphics
```
echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
```

Then, log out and back in again to complete the switch. (Technically, what you need to do is restart x for the change to take effect.) 

At this point, you can turn off the unused card using the following command
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
If you're using the Intel graphics, turning off the unused ATI card will save a lot of power, making your battery life much longer.

I assume this is basically what the UCC does.  However, I'm still trying to figure out a way to automate it.  There is a post on Phoronix on how to do it in Fedora, but it needs to be modified a little bit.



> **wizards said:**
> New revision of ATI...
...
but when i install - graphic interface of linux not started
Please, please at least try to read the last few pages of the thread before replying.  I have tried to explain that the closed source drivers most likely do not work and may never work with the ATI switchable graphics.  Could be wrong, but this is my understanding of the problem.  Try researching ATI and KMS and switchable graphics if you don't believe me/want to learn more.  However, the bottom line is that these drivers should not be necessary.

Would the maintainer of the table of stuff that works with this computer please make a note on your website explaining this.

---

### Post by elehcim on 2010-10-26
Hi!
There's a summary of what is contained in RavensKrag's post. In addiction there some scripts by Roberto Martinez for automate the switching.

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Maybe it can be useful.
I've not tried yet, I'll try as soon as possible.

Have a nice day,
Michele

---

### Post by RavensKrag on 2010-10-26
> **elehcim said:**
> Hi!
There's a summary of what is contained in RavensKrag's post. In addiction there some scripts by Roberto Martinez for automate the switching.

Nice find! This uses a much better method of turning of the unused card that what I've been using.  My computer spits out this odd error as it's starting up or logging out which I believe is a side-effect of the method I'm using.  The /etc/init.d/rc.local method is much better.

The only problem with that "turn both cards on before shutdown" script is that it has to be run manually before shutdown.  I have it set up so that my computer will automatically do that when you use the normal shut down command.  However, I sort of forgot what I did ^_^; when I have time to figure it out again, I'll post it here.

I had read the Martinez page directly before, but I personally think the layout of the information on the Ubuntu page makes the information easier to understand.

---

### Post by kemkem42 on 2010-10-26
Hi all,

According to the last posts, I understand that :

- Some of the Acer 4820TG have two graphic cards
- You can switch between them to reduce power consumption
- BUT switchable graphics are NOT supported by CLOSE SOURCE drivers

Am I right ?

Can it be applied to the ATI 5650 version of the 4820TG ?

By default, both cards are active and works, the real problem is to switch between them ?

---

### Post by RavensKrag on 2010-10-26
I believe all versions of the 4820tg have both the discrete ATI graphics and the integrated Intel graphics, but feel free to correct me if I'm wrong.

As long as you're using a relatively recent kernel (like the ones posted in this thread, or the one from Maverick) then the switch should work.  The problem is not switching, so much as having 3D support work with the ATI card, as far as I understand.  Without 3D support, using the ATI card just takes up more power without much benefit imo.

Speaking of which...
@daveboy23
Did you manage to get 3D support working on your computer with the ATI card?

---

### Post by daveboy23 on 2010-10-26
> **RavensKrag said:**
> I believe all versions of the 4820tg have both the discrete ATI graphics and the integrated Intel graphics, but feel free to correct me if I'm wrong.

As long as you're using a relatively recent kernel (like the ones posted in this thread, or the one from Maverick) then the switch should work.  The problem is not switching, so much as having 3D support work with the ATI card, as far as I understand.  Without 3D support, using the ATI card just takes up more power without much benefit imo.

Speaking of which...
@daveboy23
Did you manage to get 3D support working on your computer with the ATI card?

did
glxinfo | grep direct
direct rendering: Yes

so i'm guessing the answer is yes

---

### Post by RavensKrag on 2010-10-26
So you can enable desktop effects then, right?

Just want to clarify this issue once and for all.

---

### Post by daveboy23 on 2010-10-27
> **RavensKrag said:**
> So you can enable desktop effects then, right?

Just want to clarify this issue once and for all.

works like a charm

---

### Post by dalindro on 2010-11-01
Is it possible to connect a wide screen Full HD LCD-tv with an HDMI cable without the FGLRX proprietary drivers. I've tried it a couple of times with the built-in drivers but the TV just keeps flickering? this sucks because i have to switch to Windows every time i'd like to e.g. watch a movie.

---

### Post by moliones on 2010-11-01
> **dalindro said:**
> [FONT=Arial]Is it possible to connect a wide screen Full HD LCD-tv with an HDMI cable without the FGLRX proprietary drivers. I've tried it a couple of times with the built-in drivers but the TV just keeps flickering? this sucks because i have to switch to Windows every time i'dlike to e.g. watch a movie.[/FONT]

I have been unable to get that to work with switchable graphics, BUT if you enable discrete graphics in the BIOS then the radeon drivers (for me) manage to output video. Sadly, I couldn't get audio working over HDMI. The video and audio both work for me with the FGLRX drivers.

In fact, with the switchable graphics, and the ATI card, I was unable to get any usable output (like it isn't synchronised properly?), while with the intel graphics only the VGA output worked (like it can't see the HDMI output). Does anyone else have this working properly?

---

### Post by 41LY45 on 2010-11-01
anybody managed to get the desktop visual effects running??

Did installed the xserver drivers, but it doesn't work on mine.

---

### Post by rekettye on 2010-11-03
Hi,

My problem: so far i have used ubuntu 10.10 with fglrx drivers and experienced no issues at all. However, the newest kernel broke something, so i got only a blinking screen during the boot. I decided to switch to the open source driver, so i removed fglrx and set the graphics mode to switchable. I've also managed to get vga switching working. Now the integrated card works well, but the discrete doesn't (i.e. i can't enable desktop effects). I tried to reinstall the open source drivers, then xorg, with no luck. Also tried to set the graphics mode to discrete. My Xorg.0.log says:
RADEON(0): GPU accel disabled or not working, using shadowfb for KMS
RADEON(0): Direct rendering disabled
How did you get it working?

---

### Post by kugalskaper on 2010-11-05
Ok i hope im not being annoying now, but i would kindly ask for help. I have the 5820TG and i am thinking about migrating to Ubuntu. So my plan is to install Ubuntu through wubi, run it for a while, learn the system, and then install Ubuntu as my 2. OS if i like it. My problem is that i do not know much about linux and can't understand half of the posts here. 

I do not need to get stuff like switch-able graphics to work right now, but getting the ethernet/wifi and battery to properly work would be absolutely necessary for me. So if anyone has time to explain it in a step by step i would be very grateful. (i did update my Bios to 1.19, would this automatically fix the battery problem?).

Also wondering if people here with acer 5820tg installs the 32 bit or 64 bit version of ubuntu?

Thank you in advance

---

### Post by marm0tte on 2010-11-05
@kugalskaper


It's easy as a pie ;)

1/ Download wubi :
[http://releases.ubuntu.com/releases/10.10/wubi.exe](http://releases.ubuntu.com/releases/10.10/wubi.exe)

2/ Follow this howto
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)


After booting to ubuntu, don't be afraid if you find it slow, it's because wubi is not a native installation. In fact wubi will create a big file under your windows partition so due to ntfs fragmentation it can become slow.
For testing functionality it's a very good way :)


Welcome in a real "human software" :p

---

### Post by kugalskaper on 2010-11-05
@marm0tte. Thanks for the reply, but i think you misunderstood me :) 

My problem is not installing ubuntu with wubi (i actually did it right after posting). My problem is that like people in this thread i have problems with making some of the hardware work. Especially the fact that the wifi is not working is a big problem for me. I have read through this post, and i know that the answer is here, but im not able to understand how to proceed as i do not know anything about terminal commands and compiling and stuff like that. I would post in the beginners forum, but my goal right now is not learning anything, just being able to use wifi on my computer.

Im not afraid of a little trial and error and i want to learn, but when the wifi is not working in ubuntu its difficult, because I need an internet connection to search for solutions to the problems i am having. Now i have been reading possible solutions, restarting in ubuntu, it does not work, restarting in windows, find something new, restarting in ubuntu and yeah you get my drift so i was wondering if someone could explain in basic step by step turns how to make it work because im getting very confused and frustrated right now :).

---

### Post by marm0tte on 2010-11-05
Ok, sorry for the miss-understanding kugalskaper :-\"

So as far as I understood the wifi, ethernet, battery and video opensource drivers works well in a fresh native install mode of ubuntu 10.10 on the Aspire 4820TG.

For your 5820TG it seems that not. So here is some points that you have to clarify in order to troubleshoot your problems :

- Do you have already installed the 1.19 BIOS version ? It seems to be the same for 4820TG and 5820TG.
Here is the link for your 5820TG :
[http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_1.19_A_A.zip?acerid=634217844152767304&Step1=Notebook&Step2=Aspire&Step3=Aspire%205820TG&OS=721&LC=en&BC=Acer&SC=PA_6](http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_1.19_A_A.zip?acerid=634217844152767304&Step1=Notebook&Step2=Aspire&Step3=Aspire%205820TG&OS=721&LC=en&BC=Acer&SC=PA_6)

- Is the laptop wifi LED turned on ?

- In order to compare your hardware config with the 4820TG, could you send in attachment the result of this terminal command :
```
sudo lshw>~/lshw_5820TG.log
```
After the log file will be stored in your home directory

- Does the battery indicator is showed in the top right task bar of ubuntu when you unplug the power cable ?

---

### Post by kugalskaper on 2010-11-05
@marm0tte. Yes my bios is up to date. i will reboot in ubuntu and get the log file. will post back here soon. Thanks for trying to help btw :)

---

### Post by kugalskaper on 2010-11-05
I wasnt able to attach the .log file in the post (got invalid file type or something), so i saved it as a .doc. hope it doesnt matter

The battery seems to be working now, the indicator tells me approximately how much time is left, so i guessed the bios update did the trick there. :)

EDIT: oh and the orange wifi LED below the touchpad is not turned on in Ubuntu

---

### Post by hutini on 2010-11-06
Hi guys im new here but i red this thread for weaks:)
I have a 3820tg and with the latest bios and ubuntu 10.10 nearly everything works fine, but my ati graphics doesn't have the right performance. actually with the standard driver its slower that the i915. if i try to install the cataclyst driver it crushes my system after reboot.(no gui, only comandline)
so my question is: is there a chance to install the cataclyst or any other driver which could support my gpu (e.g. i read something about mesa drivers in an arch forum)
plz help me because this would be the last step to make my 3820tg ubuntu-only ^^
thx hutini

---

### Post by marm0tte on 2010-11-06
@kugalskaper

Ok, so it seems that the only difference between 5820TG and 4820TG is that the 5820 have a little bit faster CPU, a diffenrent screen size maybe and ...
the wifi network card is different :(

> -network UNCLAIMED
                 description: Network controller
                 product: BCM43225 802.11b/g/n
                 vendor: Broadcom Corporation
                 physical id: 0
                 bus info: pci@0000:03:00.0
                 version: 01
                 width: 64 bits
                 clock: 33MHz
                 capabilities: pm msi pciexpress bus_master cap_list
                 configuration: latency=0
                 resources: memory:da400000-da403fff
According to this howto, you have two diffenrent way to make the wifi card working :
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)


1/ Ethernet card work ?
If yes, just plug a RJ45 ethernet cable on your laptop to get acces to the web
After, just type theses commands in a terminal :
```

sudo apt-get update     # in order to update the repository cache from ubuntu package server to your laptop
sudo apt-get install bcmwl-kernel-source     # in order to install the wifi broadcom package

```After that, under the desktop menu System > Administration > Hardware/Additional Drivers, the STA drivers can be activated for use. Finally, you have to reboot.

2/ Ethernet card does not work
Insert the ubuntu 10.10 64 bits desktop CD (if you don't have dowload it from here :
[http://releases.ubuntu.com/maverick/ubuntu-10.10-desktop-amd64.iso](http://releases.ubuntu.com/maverick/ubuntu-10.10-desktop-amd64.iso)

Navigate in the cdrom folder :
pool/restriced/b/bcmwl

Double click on the file named "bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb"

After that, under the desktop menu System > Administration >  Hardware/Additional Drivers, the STA drivers can be activated for use.  Finally, you have to reboot.


Good luck ;)

---

### Post by marm0tte on 2010-11-06
@hutini

Hello,
What kind of ATI card do you have in your Acer 3820tg ?

---

### Post by kugalskaper on 2010-11-06
Thanks a lot mar0tte. Wifi is working perfectly now. 
I have another problem now. The fans seems to be running constantly, i browsed through this post and seems like im not the only one with this problem. no solution was posted though. do you have any idea?

---

### Post by marm0tte on 2010-11-06
I've no fans noise problem with my 4820TG under ubuntu 10.10 64bits

In the meantime, peoples reporting problems with fans were in 10.04 version without 1.19 BIOS, maybe the problem is solved for the 4820TG now ?

For your 5820TG laptop it seems that many people have a problem. I advise you to post under this forum :
[http://forum.notebookreview.com/acer/487954-acer-timeline-5820tg-issues-2.html](http://forum.notebookreview.com/acer/487954-acer-timeline-5820tg-issues-2.html)

---

### Post by kugalskaper on 2010-11-07
Hmm i dont think posting in that forum would do any good. I dont think its an issue with my laptop, i only have this problem in ubuntu. I have used my 5820TG for months now and have not had any issues with the fans in windows 7. Its not a really loud fan noise (they are not at 100%), but the fans always run, even when the computer is idle. Could it just be that running ubuntu even idle takes more power than windows 7?

---

### Post by hutini on 2010-11-07
hi i have a ati 5470 hd as discrete graphics card.
but the rest of the hardware should be the same als 4820tg and 5820tg.

---

### Post by NemesisFS on 2010-11-07
Hi,

im running ubuntu10.10 on an acer asprire timelinex 4820tg too. it all works fine, but i got problems switching the grafics....
cat /sys/kernel/debug/vgaswitcheroo/switch returns:
```
0: :Pwr:0000:01:00.0
1:+:Pwr:0000:00:02.0

```but when i enter
```
echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
/etc/init.d/gdm restart
```the system hangs...
when i switch via ctrl+alt+f1 and login, dmesg returns as last results this:
```
[  283.757060] vga_switcheroo: client 1 refused switch
[  283.757066] vga_switcheroo: setting delayed switch to client 0
[  290.128123] vga_switcheroo: processing delayed switch to 0

```as i expected after that, the cat command tells, that the graficcard wasnt switched...

can u help me?

EDIT: Pls excuse my bad english :D

---

### Post by grid_bug on 2010-11-07
As of 10.10 (and BIOS 1.19), most issues seem to be fixed on my 4820TG. 
From my not-at-all-rigorous testing...
[LIST=1]
[*]Ethernet--working
[*]WiFi--working
[*]Graphics Switching--working(but with occasional weirdness)
[*]Battery Status/ Charging--working
[*]Multitouch--working(but fails when I suspend or hibernate, rerunning the script seems to work
[*]Fn+F3--partial(disconnects from whatever network I'm on, but doesn't power down the card
[*]Bluetooth--not working(no hardware installed according to Bluetooth Settings)
[*]IntelHD graphics acceleration--working
[*]Radeon 5650 graphics acceleration--partial(glxinfo says it's there, but I can't enable desktop effects, and the flgrx driver doesn't get past tty, slower than th IntelHD)
[*]Battery life--not bad(5-7 hours on the IntelHD card, 2-3 hours on the Radeon, which I can't use :()
[*]Internal Mic--working(just don't be an idiot like me and mess with the sound settings so that it doesn't work)
[*]External Mic--not tested
[*]HDMI--not tested
[*]CD/DVD eject--working(both [FONT="Lucida Console"]eject[/FONT] and the button)
[/LIST]
Does the OSS radeon driver actually work? I've read that it does, but it doesn't for me.

---

### Post by hutini on 2010-11-07
exactly the same with my 3820tg 
i guess the last big issue is the driver for the ati card does anybody got that working`?

---

### Post by LintWad on 2010-11-07
I have been using Ubuntu on my 4820t for a few months and have generally been quite happy. However, I have noticed many of the problems listed above which seem to be covered by the BIOS update. Unfortunately, I no longer have windows on this machine. 

I attempted to utilize the procedure outlined here ( [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html) ), but the update file from Acer is larger than the 1.44 MB limit.

For those of you who have successfully flashed your BIOS from ubuntu, how did you overcome this limitation?

---

### Post by kemkem42 on 2010-11-08
Maybe you can flash bios using freedos (which is a clone of ms dos..)

instead of a floppy, use a usb key !
like this: [http://goebelmeier.de/bootstick/](http://goebelmeier.de/bootstick/)

---

### Post by marm0tte on 2010-11-08
@LintWad

Hello,


We have already discuss this subject on the page 15 :
[http://ubuntuforums.org/showthread.php?t=1495123&page=15](http://ubuntuforums.org/showthread.php?t=1495123&page=15)

---

### Post by LintWad on 2010-11-09
Using the procedure discussed on page 15 produces the exact problem I wish to avoid. 

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

Specifically, when I check to "see that everything went ok" it shows the entire file was not moved to the floppy image. It is too large (2.5 MB). Therefore, unless I am missing a step, that method does not work for me. Thus, my question above.

---

### Post by marm0tte on 2010-11-09
Ok, don't have time to test it but please try this how to:

[http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-linux-with-unetbootin/](http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-linux-with-unetbootin/)

---

### Post by garips on 2010-11-10
Hi,

i read almost the whole thread, but couldnt find a solution to my problems

even after upgrading bios and with ubuntu 10.10 swiching graphics is a problem with my 4820tg. Switching in a shell generally works (with reversed commands!), but without having an effect on power consumption. Switching with UCC is like throwing dice, sometimes it works sometimes it doesnt. sometimes it shows the correct gpu as active, sometimes it doesnt. and again, even if it works, no effekt on battery life.

another weird thing is that the power consumption when on battery is between 25W and 32W, but when on plug, it drops to 17,5.

hope that somebody can help
garips

---

### Post by marm0tte on 2010-11-10
@LintWad

So, I've completely test this howto and it works :
[http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-linux-with-unetbootin/](http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-linux-with-unetbootin/)

You might use a "good" usb stick. I mean that a noname usb key may not work.
I've tried the procedure with 2 noname sticks and in freedos when I list the c: drive (1st usb partition) the shell never returned to prompt and I had to reboot.

But, my PNY 8GB usb stick works well


Here is the process I use :

1/ In ubuntu, backup the datas of the usb stick.
Launch GParted :
sudo gparted

2/ Delete all the partitions. Create a FAT16 primary partition of 512MB for example.
Create a second NTFS or FAT32 partition with the rest of free space
Click Apply

3/ Set a boot flag on the FAT16 partition and close Gparted

4/
Download the last BIOS update for the Acer
Download FreeDOS base CD : [http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso)
Copy the BIOS .EXE file on the USB key

Install unetbootin :
sudo apt-get install unetbootin
and start it

5/ Select "Disk /image" and select "ISO" . Browse your disk to the fdbasecd.iso file
in the "drive" list, select your usb stick device (/dev/sdXX)
Click OK

6/ Restart. Go into the F2 BIOS Setup menu.
Select F12 Boot Menu => Enable
Save and exit

7/ Press F12 and select USB HDD in order to boot on the usb stick
In the next menu select FDos and select the 2nd option Start Freedos CD ...

8/ Be sure to have the Power supply plugged on your laptop
At the DOS prompt type :
C:
And launch the ZQ1_119.exe in order to flash BIOS


This is it ! :P

---

### Post by garips on 2010-11-11
battery and graphics issues are fixed, thanks to grid_bug.
i must have done something wrong using the switch_between_cards script.

---

### Post by LintWad on 2010-11-11
Thank you Marm0tte, I plan to try this as soon as I can (potentially, but hopefully not) go without my computer for a couple days.

---

### Post by Hantuosen on 2010-11-12
> **garips said:**
> battery and graphics issues are fixed, thanks to grid_bug.
i must have done something wrong using the switch_between_cards script.

Hi Garips!
Have the same problems with graphic switching (using UBC, power consumption never below 28W, no matter which card is in use). 
Could you elaborate on how you solved it? What's the grid_bug? Thank you

---

### Post by grid_bug on 2010-11-12
> **Hantuosen said:**
> Hi Garips!
Have the same problems with graphic switching (using UBC, power consumption never below 28W, no matter which card is in use). 
Could you elaborate on how you solved it? What's the grid_bug? Thank you
grid_bug would be me. read this for a useful explanation of how to use vgaswitcheroo to increase battery life 
[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics?action=show")

---

### Post by daveboy23 on 2010-11-13
> **grid_bug said:**
> grid_bug would be me. read this for a useful explanation of how to use vgaswitcheroo to increase battery life 
[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics?action=show")

ok, a little stupid question - i finished doing everything it says, but i can't seem to run the .sh script.  what should i do, put it in some folder? excute it? what?

---

### Post by kemkem42 on 2010-11-13
Hello

My 4820TG (ATI 5650 graphics) works quite well with ubuntu 10.10

But still have some problems :

First, I can't switch to ATI card. It can be powered ON/OFF only.
I've used this script (which is nice), but ATI card is never in use.
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
I haven't installed closed drivers, bios is set to "switchable".
Anyone have a clue ?

Second, hibernate function not working very well.
At the beginning, it seems to work. Now, when I shut down using "hibernate" option, the screen switch to a black console, nothing more..

Thanks..

---

### Post by LintWad on 2010-11-19
> **marm0tte said:**
> @LintWad

So, I've completely test this howto and it works :
[http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-linux-with-unetbootin/](http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-linux-with-unetbootin/)

You might use a "good" usb stick. I mean that a noname usb key may not work.
I've tried the procedure with 2 noname sticks and in freedos when I list the c: drive (1st usb partition) the shell never returned to prompt and I had to reboot.

But, my PNY 8GB usb stick works well


Here is the process I use :

1/ In ubuntu, backup the datas of the usb stick.
Launch GParted :
sudo gparted

2/ Delete all the partitions. Create a FAT16 primary partition of 512MB for example.
Create a second NTFS or FAT32 partition with the rest of free space
Click Apply

3/ Set a boot flag on the FAT16 partition and close Gparted

4/
Download the last BIOS update for the Acer
Download FreeDOS base CD : [http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso)
Copy the BIOS .EXE file on the USB key

Install unetbootin :
sudo apt-get install unetbootin
and start it

5/ Select "Disk /image" and select "ISO" . Browse your disk to the fdbasecd.iso file
in the "drive" list, select your usb stick device (/dev/sdXX)
Click OK

6/ Restart. Go into the F2 BIOS Setup menu.
Select F12 Boot Menu => Enable
Save and exit

7/ Press F12 and select USB HDD in order to boot on the usb stick
In the next menu select FDos and select the 2nd option Start Freedos CD ...

8/ Be sure to have the Power supply plugged on your laptop
At the DOS prompt type :
C:
And launch the ZQ1_119.exe in order to flash BIOS


This is it ! :P

For the record, this method works. Well. 

A couple things I was unfamiliar with that may help others. Both the bios update and the freedos are loaded on the same partition (FAT 16). After setting your boot order the screen will sit for a few moments until the freedos load button will show. Choose freedos, then choose the standard option. Command prompt will show up and the rest is just like described.

---

### Post by andy12345 on 2010-11-24
I have been having problems with my graphics card, heres the post [http://ubuntuforums.org/showthread.php?t=1629799](http://ubuntuforums.org/showthread.php?t=1629799)

---

### Post by Xanfer on 2010-11-24
Hello
Does anybody know how the bug with bt can be won?
It seems that at the first boot to ubuntu after windows(with working bt) it turns on for 1 second when I press Fn+F3 several times. But after it turns down, and I can't make him switch on again.
Also, after that bt doesn't working in win7 too...but all returns in normal state(working in win, and not working in ubuntu) when win7 downloads and installs some updates.

---

### Post by andy12345 on 2010-11-25
> **Xanfer said:**
> Hello
Does anybody know how the bug with bt can be won?
It seems that at the first boot to ubuntu after windows(with working bt) it turns on for 1 second when I press Fn+F3 several times. But after it turns down, and I can't make him switch on again.
Also, after that bt doesn't working in win7 too...but all returns in normal state(working in win, and not working in ubuntu) when win7 downloads and installs some updates.

Mine works normally with Fn+F3.

I am having some problems, are there any solutions to these?

1. Laptop heats up pretty fast (in an hour of surfing only it hits upto 60-65, while in windows even after a movie its just at 47 (deg cel)). To clear up any confusion, the fan works perfectly in ubuntu.

2. I am unable to run games through wine (I have checked the supported games list and CS and warcraft was there, I have also tried searching), I am using a 64 bit Ubuntu 10.10

3.**SOLVER WITH BIOS UPDATE***Battery/AC power is not displayed.(I have tried help and some commands, it shows that gdm power manager is running)*
Solution:- First you need to check if you have the acpi. To check type in terminal
```
acpi
```
If not install it will tell you to type the following to install
```
sudo apt-get install acpi
```


4. The ATI card issue remains unsolved for me.(how to switch to intels?)

---

### Post by wizards on 2010-11-26
> **Xanfer said:**
> Hello
Does anybody know how the bug with bt can be won?
........

Hi, 
for my BT works fine with ubuntu 10.10 64bit(bios 1.19).When i press (once or twice - i don't know exatly)start wifi and bluetooth.Bluetooth communication with my android on HTC HD2 fine.Which version Ubuntu you have?

> **andy12345 said:**
> .......

Problem with AC power/Battery solved bios 1.19.

---

### Post by andy12345 on 2010-11-26
How to switch between graphics cards? ATI's heats up pretty fast.

---

### Post by Xanfer on 2010-11-27
> **wizards said:**
> Hi, 
for my BT works fine with ubuntu 10.10 64bit(bios 1.19).When i press (once or twice - i don't know exatly)start wifi and bluetooth.Bluetooth communication with my android on HTC HD2 fine.Which version Ubuntu you have?


I have 10.10 and bios 1.19 too. Pressing F3+fn sometimes turns it on, but only for one moment. And i can't resolve this :(

---

### Post by nicolaary on 2010-11-28
> **daveboy23 said:**
> yap, i actually searched for that myself - here's the solution: go to skype and disable the automatic sound adjust thing then go to terminal - type alsamixer, press F4 (capture tab) - so to capture and put it all the way up (or to a volume you like) then (on the same column) press 'y' till you completely mute the left channel.  now skype works.  problem - if you change the volume from the pulse you loose this configuration so take care.



Hi DaveBoy23,
  sorry for my late reply!

Now it works in Skype and also in Google Talk!

I have added your post in my summary blog ...[http://kblackhat.blogspot.com/]("http://kblackhat.blogspot.com/")

Bye

Nicola :popcorn:

---

### Post by roshats on 2010-11-28
Hello. Looking for information about this model I frequently came to this page [http://www.linlap.com/wiki/acer+aspire+4820+timelinex](http://www.linlap.com/wiki/acer+aspire+4820+timelinex) . I see high potential in this laptop. Other people would came to this page too. Can someone clarify data in it? Does 'tested' in table mean 'works'? Can someone summarize one need to do to fix solved problems?
Good luck.

---

### Post by daveboy23 on 2010-11-29
> **nicolaary said:**
> Hi DaveBoy23,
  sorry for my late reply!

Now it works in Skype and also in Google Talk!

I have added your post in my summary blog ...[http://kblackhat.blogspot.com/](http://kblackhat.blogspot.com/)

Bye

Nicola :popcorn:
i'm glad to know i did my small part to help the community

> **roshats said:**
> Hello. Looking for information about this model I frequently came to this page [http://www.linlap.com/wiki/acer+aspire+4820+timelinex](http://www.linlap.com/wiki/acer+aspire+4820+timelinex) . I see high potential in this laptop. Other people would came to this page too. Can someone clarify data in it? Does 'tested' in table mean 'works'? Can someone summarize one need to do to fix solved problems?
Good luck.
not problem on clarifying the data - the computer works perfectly after the bios 1.19 and various fixes (easily performed) from this website (from the first quote)
[http://kblackhat.blogspot.com/](http://kblackhat.blogspot.com/)

---

### Post by andy12345 on 2010-11-29
Almost all of my issues have been solved. I have to still test games which I will do so after my exams (after 23rd dec).
For anyone having problems I suggest the following
Problems & solutions for Ubuntu 10.10 on 4820TG
1. Battery/Power issues
 Get the latest BIOS from acer and install (I did it through my windows, really easy, just have to execute a file)
Log in ubuntu and install acpi and reboot.
2. Card switching issues.
This is [my post(click me)]("http://ubuntuforums.org/showthread.php?t=1629799") realted to the problem which has been now solved.
This is the [solution.(click me)]("http://asusm51ta-with-linux.blogspot.com/")
Thats all the basic issues I had. I have compared the copy speeds and ubuntu is just a bit faster(normal test nothing fancy with lots of runs or anything).
I have also ready that game fps are good for ubuntu rather than windows (I saw the WoW video), so I will try some games out later.
I would really like to thank the ubuntu community for their help in resolving my problems.

---

### Post by roshats on 2010-11-29
It's amazing. You've done a great work. As i understood all now works fine after upgrading BIOS, installing acpi and doing steps written on [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/) . Even wifi and ethernet works? How long can a laptop run on battery power? Thanks.

---

### Post by andy12345 on 2010-11-30
> **roshats said:**
> It's amazing. You've done a great work. As i understood all now works fine after upgrading BIOS, installing acpi and doing steps written on [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/) . Even wifi and ethernet works? How long can a laptop run on battery power? Thanks.
I get around 7 to 8 hours with wifi on and 60% brightness.(just surfing and downloading)

---

### Post by roshats on 2010-11-30
Awesome battery life. Thanks for quick reply.

---

### Post by grid_bug on 2010-12-07
I'm having some issues getting bluetooth working(I cant seem to find the hardware, either in linux or Windows). is there some output from lshw or lspci that I should be seeing?

---

### Post by favt on 2010-12-08
Anybody try run "**switch_before_shutdown.sh**" (or only echo ON > /sys/kernel/debug/vgaswitcheroo/switch[FONT=Verdana]) from [/FONT] [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/) [FONT=Verdana]in automatic shutdown with gnome-applet [FONT=monospace]?[/FONT][/FONT]
I try put script (echo ON > /sys/kernel/debug/vgaswitcheroo/switch) in rc0.d and rc6.d, but has not effect.
P.S. Sorry for my English.

---

### Post by Xanfer on 2010-12-08
> **grid_bug said:**
> I'm having some issues getting bluetooth working(I cant seem to find the hardware, either in linux or Windows). is there some output from lshw or lspci that I should be seeing?

My bt isn't working too and I have nothing about it in lshw, but dmseg write about some problems with initialization config files when Fn+F3 is pressed.

---

### Post by Xirev on 2010-12-08
Has anyone tried the following fix for mulitouch with Ubuntu 10.10? It's not working on my laptop for some reason. Perhaps it only works on 10.04.

**EDIT:** Nevermind, it seemed to have fixed itself. I fiddled with some settings using *synclient* which helped a little but did not completely fix the problem. I then restart the laptop and for all you know the thing works like a charm using the script below.

> **giova.86 said:**
> 
1) create a file named .touchpad.sh in your  home
2) open the file and copy these line into it:

```
#!/bin/sh

sleep 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
```The sleep time is necessary.
3) make the file executable with
```
chmod u+x ./.touchpad.sh
```4) add the file file in autostart application: system->preference->autostart application

---

### Post by Xirev on 2010-12-11
Ok 2 issues:

**Touchpad:** I just discovered that contrary to what my post above says, my touchpad on the 4820t is not working properly. It seems to be a matter of luck really. Sometimes I restart and it's working great, other times when I put two fingers on it the mouse pointer goes nuts. Today for instance I sent it to sleep than after wake up it's working properly. I'm really at loss to what could be causing this.

**Battery Indicator:** When I unplug the charger Ubuntu does not know what happened at first and continues normally. However when I plug it in again and then take it out, it detects the battery is discharging. Anyone encountered this strange behaviour?

---

### Post by Xanfer on 2010-12-15
Does anybody know what should i do to enable bt?
upgrading bios didn't help...neither on 1.19 nor on 1.22 it doesn't work...
dmesg write, when Fn+F3 is pressed:
```

[  147.668810] usb 2-1.5: new full speed USB device using ehci_hcd and address 3
[  147.824506] Bluetooth: Atheros AR30xx firmware driver ver 1.0
[  148.130542] usbcore: registered new interface driver ath3k
[  148.236058] usb 2-1.5: USB disconnect, address 3
[  149.712508] usb 2-1.5: new full speed USB device using ehci_hcd and address 4
[  149.850097] Bluetooth: Core ver 2.15
[  149.850123] NET: Registered protocol family 31
[  149.850125] Bluetooth: HCI device and connection manager initialized
[  149.850127] Bluetooth: HCI socket layer initialized
[  149.862429] Bluetooth: Generic Bluetooth USB driver ver 0.6
[  149.862753] usbcore: registered new interface driver btusb
[  149.972721] Bluetooth: L2CAP ver 2.14
[  149.972725] Bluetooth: L2CAP socket layer initialized
[  150.007664] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  150.007669] Bluetooth: BNEP filters: protocol multicast
[  150.029658] Bluetooth: SCO (Voice Link) ver 0.6
[  150.029664] Bluetooth: SCO socket layer initialized
[  150.282887] usb 2-1.5: USB disconnect, address 4
[  150.282920] btusb_intr_complete: hci0 urb f0982680 failed to resubmit (19)
[  150.282988] btusb_bulk_complete: hci0 urb f0982780 failed to resubmit (19)
[  150.282995] btusb_bulk_complete: hci0 urb f0982480 failed to resubmit (19)

```

---

### Post by kamakshaiah on 2010-12-16
does this bios 1.18 works for Aspire 4745, and also tell me how to upgrade it. 
Please help me.
 
MKamakshaiha

---

### Post by Roadrun on 2010-12-16
Does anyone got HDMI video working under Integrated (Intel) VGA card?

---

### Post by daveboy23 on 2010-12-17
hi guys, just checked the acer website today and guess what - there is a new bios out there (1.22).  anyone has any clue what it's all about? anyone tried it yet?

anyone has any idea what's been updated?

---

### Post by marm0tte on 2010-12-19
I've just ask to the support, I will keep you informed.

---

### Post by oczer on 2010-12-21
> **Roadrun said:**
> Does anyone got HDMI video working under Integrated (Intel) VGA card?

HDMI dosent work for intel card in windows 7 either. It's probably only for ATI card

---

### Post by marm0tte on 2010-12-21
still no answer from the Acer support :(

---

### Post by wizards on 2010-12-21
> **daveboy23 said:**
> hi guys, just checked the acer website today and guess what - there is a new bios out there (1.22).  anyone has any clue what it's all about? anyone tried it yet?

anyone has any idea what's been updated?


Its strange they have don't write what's patch .. :/..i think its some mistake from they.
Its difficult  to say whats exactly to this :(
I patch to 1.22 from Windows and averything seems allrigh .. but i still don't know what exactly change in this version

---

### Post by marm0tte on 2010-12-22
lol, the Acer support sucks, here is what they answer :

> 12/19/2010 9:56 PM Automatic Response
 Title: Using Protector Suite QL
 Link: [http://acer-fr.custhelp.com/app/answers/detail/a_id/4439](http://acer-fr.custhelp.com/app/answers/detail/a_id/4439)

 Title: Setting up a PC to send audio via HDMI in Windows Vista and Windows 7
 Link: [http://acer-fr.custhelp.com/app/answers/detail/a_id/4185](http://acer-fr.custhelp.com/app/answers/detail/a_id/4185)

 Title: Setting up a PC to send audio via HDMI in Windows XP
 Link: [http://acer-fr.custhelp.com/app/answers/detail/a_id/4183](http://acer-fr.custhelp.com/app/answers/detail/a_id/4183)

 Title: Windows Product Activation
 Link: [http://acer-fr.custhelp.com/app/answers/detail/a_id/5338](http://acer-fr.custhelp.com/app/answers/detail/a_id/5338)

 Title: Troubleshooting the Windows Vista audio missing
 Link: [http://acer-fr.custhelp.com/app/answers/detail/a_id/4228](http://acer-fr.custhelp.com/app/answers/detail/a_id/4228)

---

### Post by daveboy23 on 2010-12-22
so the update is basically for windows users?

---

### Post by marm0tte on 2010-12-23
no, it was an automatic answer from Acer robots and moreover responses had nothing to do with what I asked

---

### Post by dboneke on 2010-12-23
> **marm0tte said:**
> no, it was an automatic answer from Acer robots and moreover responses had nothing to do with what I asked

Hi Marmotte,

I want to first of all express my huge gratitude for starting this thread, I doubt you thought it will turn out to be so big for so many ppl :) and of all forums and threads, I've never seen any forum where everyone contributes somehow. Props to all you guys!

My question...
I've read the entire thread and it seem to me that downloading BIOS 1.19 is the fastest and easiest way to solving all the problems that I currently have. However, I'm not sure if I will still need to manually turn off ATI or Intel to get 7 hours, or if with BIOS I will have that automatically solve?

I tried to download the BIOS 1.19 from the acer website [http://us.acer.com/ac/en/US/content/drivers](http://us.acer.com/ac/en/US/content/drivers) but when I click on the arrow to download, the browser looks like is loading but it does not download the file. Would you guys please give a link that works?

---

### Post by marm0tte on 2010-12-23
Hello,

This one works for the Aspire 4820TG v1.19 BIOS  :
[http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_1.19_A_A.zip?acerid=634217844152767304&Step1=Notebook&Step2=Aspire&Step3=Aspire%204820TG&OS=722&LC=en&BC=Acer&SC=PA_6](http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_1.19_A_A.zip?acerid=634217844152767304&Step1=Notebook&Step2=Aspire&Step3=Aspire%204820TG&OS=722&LC=en&BC=Acer&SC=PA_6)

---

### Post by andy12345 on 2010-12-24
Major Bug,
I switched on my laptop after 28 days, started windows, everythings fine.
I thought I might as well update ubuntu, when I started it,
1st time, frozen at splash screen.
2nd time, froze at login screen with weird ..um scrambled pixels or graphics.
3rd time, frozen at login screen.
4th time FINALLY! works.
any idea why this occurred?

---

### Post by Confusered on 2010-12-24
I've updated to the 1.22 bios from 1.19, but there seems to be no changes at all. Also, I discovered a new trend. If I leave my laptop off for 3 hours or so and start it back on and try to boot into Ubuntu, what happens is that I will get a blank screen after ubuntu tries to boot and i will have to use the emergency reboot. It will only successfully boot into ubuntu after the emergency reboot. And if i turn it off for a few hours again, and turn it on to boot into Windows first, it will successfully boot into Windows. After doing a restart from Windows, and booting into Ubuntu, it will boot successfully. Does anyone else have this problem too?

---

### Post by Confusered on 2010-12-24
> **Xirev said:**
> Ok 2 issues:

**Touchpad:** I just discovered that contrary to what my post above says, my touchpad on the 4820t is not working properly. It seems to be a matter of luck really. Sometimes I restart and it's working great, other times when I put two fingers on it the mouse pointer goes nuts. Today for instance I sent it to sleep than after wake up it's working properly. I'm really at loss to what could be causing this.

**Battery Indicator:** When I unplug the charger Ubuntu does not know what happened at first and continues normally. However when I plug it in again and then take it out, it detects the battery is discharging. Anyone encountered this strange behaviour?

I haven't tried the battery, but I'm definitely experiencing the issues you mentioned for touchpad. Multi touch is intermittent, and sometimes it works fine but other times when i put two fingers on it the cursor jumps about crazily from one end to another.

---

### Post by shaeiki on 2010-12-25
Can driver for ATI be used now?

I installed it once, it didn't work and I had to reinstall ubuntu. So I'm afraid to install the driver again. :(

Sorry for my bad English.

---

### Post by Foxcow on 2011-01-02
I just installed BIOS 1.22 and everything seems a-ok.  I haven't noticed anything different really.

---

### Post by Foxcow on 2011-01-04
> **Xirev said:**
> 

**Battery Indicator:** When I unplug the charger Ubuntu does not know what happened at first and continues normally. However when I plug it in again and then take it out, it detects the battery is discharging. Anyone encountered this strange behaviour?



I have the same issue.  I thought installing ACPI would fix it, but no such luck.

---

### Post by CrazyDesi on 2011-01-04
> **Foxcow said:**
> I have the same issue.  I thought installing ACPI would fix it, but no such luck.


I'm having the same problem.  I am using the 32 bit version of 10.10.  Could that be the problem?

---

### Post by Foxcow on 2011-01-04
> **CrazyDesi said:**
> I'm having the same problem.  I am using the 32 bit version of 10.10.  Could that be the problem?



I don't think so because I'm running 10.10 64-bit

---

### Post by Silentzor on 2011-01-07
> **andy12345 said:**
> Major Bug,
I switched on my laptop after 28 days, started windows, everythings fine.
I thought I might as well update ubuntu, when I started it,
1st time, frozen at splash screen.
2nd time, froze at login screen with weird ..um scrambled pixels or graphics.
3rd time, frozen at login screen.
4th time FINALLY! works.
any idea why this occurred?

I sort of have the same error. I have 10.10 x64, bios 1.22 and most times i log-in it either gets stuck on the splash screen with the dots, or stuff on the top gnome bar are missing (like the battery, sound etc.). Takes about 3-4 manual restarts for the system to boot. Is there a fix for that?

---

### Post by Xanfer on 2011-01-09
I found solutions for two my problems 
1. The first was bluetooth problem.
Arch linux wiki for TimelineX helped with this: 
> Symptoms include "usb disconnect" messages in dmesg, and the adapter not showing up in hcitool dev.) In this case, copying /lib/firmware/ath3k-2.fw to /lib/firmware/ath3k-1.fw helps

2. And the second was enabling graphic effects with ati card:
I just had added repository from ubuntu-tweak: "xorg-edgers fresh X.crack" and updated my system.

---

### Post by ckuerste on 2011-01-20
Hi there,

Awesome thread. Thank you all for the great informations.

I'm running Ubuntu 10.10 64-bit and have a problem with the network driver. After upgrading from 10.04 to 10.10 I wanted to re-compile the Atheros driver (v1.0.1.14) but got the following error.

```
make -C ./src 
make[1]: Entering directory `/home/user/AR81Family-linux-v1.0.1.14/src'
Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.
make[1]: Leaving directory `/home/user/AR81Family-linux-v1.0.1.14/src'
make: *** [all] Error 2
```Kernel is 2.6.35-24-generic.

I installed all the necessary libraries (or at least I think so). What I read somewhere is that they changed something in the kernel and that there is no autoconf.h file anymore.

Did anybody manage to compile the driver?

---

### Post by Foxcow on 2011-01-20
Just out of curiosity, do you have the latest version of BIOS?  It cures a lot of ills.

---

### Post by ckuerste on 2011-01-20
> Just out of curiosity, do you have the latest version of BIOS?  It cures a lot of ills.      No. I will update today and see if anything changes.

**Update:** Updated to the latest BIOS and wired network works again. Thanks Foxcow!

---

### Post by RavensKrag on 2011-01-20
> **ckuerste said:**
> I installed all the necessary libraries (or at least I think so). What I read somewhere is that they changed something in the kernel and that there is no autoconf.h file anymore.

Did anybody manage to compile the driver?

I did this before, and thought I mentioned how earlier in this thread.  However, I can't seem to find it, sorry.  Still, if you use ubuntu 10.10, there should be no reason to build the driver yourself.

I do remember it had something to do with changing a line in the source code though...



Also, if you want the ATI card powered of on init automatically, and then powered back on right before shutdown (to avoid strange error messages) do the following.

Copy the following into a bash file.
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          graphics-shutdown
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Example initscript
# Description:       This file should be used to construct scripts to be
#                    placed in /etc/init.d.
### END INIT INFO

# Do NOT "set -e"

if [ "$1" = "start" ]; then
	echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
elif [ "$1" = "stop" ]; then
	echo ON > /sys/kernel/debug/vgaswitcheroo/switch
else
	echo ON > /sys/kernel/debug/vgaswitcheroo/switch
fi

```

Then, make it executable, then, run the following commands.
```

sudo cp PATH_TO_FILE /etc/init.d/
sudo update-rc.d NAME_OF_FILE defaults 98 02

```
Using the appropriate name of the file, of course.  This is very similar to the instructions I posted before, except now there are a couple of extra numbers at the end, which specify when to run the script.

---

### Post by jziliox on 2011-01-24
Hi everyone,

i'm using ubuntu 10.04 with kernel 2.6.35.
First off all, thanks to everyone who contribute in this topic.

Regarding the automatic swicht off, the solution provided by RavensKrag seems to work very well.

I've just a question : how can we be sure the discrete vga adapter is powered off? I mean, ok, this is written in the /sys/kernel/debug/vgaswitcheroo/switch file, but is there a mean to be sure?

I've tried powertop in order to see the laptop power consumption but i've a strange message telling me there is no available estimation for the electric consumtion.

any idea?

---

### Post by RavensKrag on 2011-01-24
> **jziliox said:**
> I've just a question : how can we be sure the discrete vga adapter is powered off? I mean, ok, this is written in the /sys/kernel/debug/vgaswitcheroo/switch file, but is there a mean to be sure?

Other than looking at that file, I'm not sure of a definitive way of doing it.  However, my laptop runs longer and cooler with the VGAswitcheroo code being used to power off the ATI card, so I would say that's a pretty intuitive way of measuring power usage, even if it's not precisely quantifiable.

---

### Post by jziliox on 2011-01-24
And besides that, do you encounter any freeze of the system since that? mine is very unstable...

---

### Post by RavensKrag on 2011-01-24
I don't believe I have.  I had one odd freeze recently, but I believe that was related to improper shutdown.

However, I am using 10.10, so perhaps the kernel I am using (as it was compiled by the folks working on Ubuntu, who I assume know much more about this stuff than I do) is more stable?

This is really just a stab in the dark in case you couldn't tell...

---

### Post by jziliox on 2011-01-24
Maybe i'll try 10.10.
Thanks

---

### Post by gncs91 on 2011-02-02
[INDENT]Hi guys,

I am running Ubuntu 10.10 on an acer 4820tg and I am having serious problems with my wifi and apparently I am the only one who is experiencing this.

Problem: My wifi disconnects every other minute when the signal is weak under ubuntu; however, in windows everything works perfectly fine. So, within the same range from the router, ubuntu is having problems connecting, whereas windows is doing fine.

The network has no WPA, only a standard WEP and the network manager I am using is wicd. When connecting, I realised that it takes a while at the following "stage": None: validating authentication.
It stays connected for a few seconds, until it stays disconnected eventhough the "Automatically connect to this network"-field is checked.

I am surprised that nobody else has problems with this, so I would like to know what you guys are doing to get your wifi working.

For what its worth: I bought the 4820tg model with the SSD, not the one with the 320gb. 

I am totally lost, very inexperienced and there is no way I can move any closer to the router^^ so any help is highly appreciated.
Thanks,

Georg
[/INDENT]

---

### Post by Foxcow on 2011-02-02
> **gncs91 said:**
> [INDENT]Hi guys,

I am running Ubuntu 10.10 on an acer 4820tg and I am having serious problems with my wifi and apparently I am the only one who is experiencing this.

Problem: My wifi disconnects every other minute when the signal is weak under ubuntu; however, in windows everything works perfectly fine. So, within the same range from the router, ubuntu is having problems connecting, whereas windows is doing fine.

The network has no WPA, only a standard WEP and the network manager I am using is wicd. When connecting, I realised that it takes a while at the following "stage": None: validating authentication.
It stays connected for a few seconds, until it stays disconnected eventhough the "Automatically connect to this network"-field is checked.

I am surprised that nobody else has problems with this, so I would like to know what you guys are doing to get your wifi working.

For what its worth: I bought the 4820tg model with the SSD, not the one with the 320gb. 

I am totally lost, very inexperienced and there is no way I can move any closer to the router^^ so any help is highly appreciated.
Thanks,

Georg
[/INDENT]


Wifi worked out of the box for me.  What version of BIOS are you running?  You can check by entering:

```
sudo lshw
```

Toward the top under BIOS, you can see version firmware is in use.

---

### Post by gncs91 on 2011-02-03
From the output of:
```
sudo lshw
``````

     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: V1.19 (09/08/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
```Is it that what you wanted me to show you? The BIOS should be fairly uptodate as the vendor updated it to the latest version when I had to get my laptop fixed.
I am considering using an external wifi adapter/stick in future, and wanted to know how I can make my computer use that one for wifi and not the internal one. There is definitely a driver for this adapter in ubuntu 10.10 because it works with my other computer, but not with this one, as it keeps using the onboard one. So this would be an alternative if I cant get to work.
Thanks alot,

George

---

### Post by Foxcow on 2011-02-03
> **gncs91 said:**
> From the output of:
```
sudo lshw
``````

     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: V1.19 (09/08/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
```Is it that what you wanted me to show you? The BIOS should be fairly uptodate as the vendor updated it to the latest version when I had to get my laptop fixed.
I am considering using an external wifi adapter/stick in future, and wanted to know how I can make my computer use that one for wifi and not the internal one. There is definitely a driver for this adapter in ubuntu 10.10 because it works with my other computer, but not with this one, as it keeps using the onboard one. So this would be an alternative if I cant get to work.
Thanks alot,

George

Yep, thats what I wanted to see.  The most up-to-date BIOS is 1.22 but I'm not sure if that will fix your issue.  A BIOS flash to the latest version fixed most people's hardware issues.  Have you considered or tried a fresh install?  Your wifi ought to work strait away.  Even during installation, if you enter a password for the access point you are using, you can download updates and extra packages while Ubuntu installs.


One more question, are you running 32 or 64 bit?

---

### Post by gncs91 on 2011-02-03
I am running Ubuntu 10.10 32-Bit. I reinstalled the system a few days ago hoping it would fix this problem, but it did not.

I will update my BIOS to 1.22 but I am not sure if this will fix the problem because, as you said, the wifi worked during the installation process, but had the same problems as now: it was disconnecting every other minute/second so that I had to abort some updates during the installatino process. I updated the system when I had the chance to get closer to the router.
I will let you guys know as soon as I updated the BIOS!

This is not the correct forum for this, I know, but can anybody tell me which driver is being used for this wifi card or where I can find this out? Because if the BIOS update does not work, I will go for the wifi adapter option and for this I need to know how to disable the onboard one.

Thanks in advance,

George

---

### Post by Chrilleee on 2011-02-03
Is there any ATI-drivers that can be installed? just installed 11.1 and after that the computer won't event start...

---

### Post by Foxcow on 2011-02-03
> **gncs91 said:**
> I am running Ubuntu 10.10 32-Bit. I reinstalled the system a few days ago hoping it would fix this problem, but it did not.

I will update my BIOS to 1.22 but I am not sure if this will fix the problem because, as you said, the wifi worked during the installation process, but had the same problems as now: it was disconnecting every other minute/second so that I had to abort some updates during the installatino process. I updated the system when I had the chance to get closer to the router.
I will let you guys know as soon as I updated the BIOS!

This is not the correct forum for this, I know, but can anybody tell me which driver is being used for this wifi card or where I can find this out? Because if the BIOS update does not work, I will go for the wifi adapter option and for this I need to know how to disable the onboard one.

Thanks in advance,

George


Have you considered installing 64 bit?  For the heck of it, I tried 32 bit on the Timeline and had enough problems that I went back to 64 after a few days.  64 runs and feels better.

---

### Post by gncs91 on 2011-02-03
> **Chrilleee said:**
> Is there any ATI-drivers that can be installed? just installed 11.1 and after that the computer won't event start...
What do you mean by "wont even start"? Does it freeze at "checking battery state" or somewhere there?
If yes, did you change the graphics mode from "switchable" to "discrete" in the BIOS? I had that problem and found out that this is due to the switchable graphics card the driver can't handle. Changing that option solved it for me!

---

### Post by Chrilleee on 2011-02-04
> **gncs91 said:**
> What do you mean by "wont even start"? Does it freeze at "checking battery state" or somewhere there?
If yes, did you change the graphics mode from "switchable" to "discrete" in the BIOS? I had that problem and found out that this is due to the switchable graphics card the driver can't handle. Changing that option solved it for me!
Well, where the login screen should show up it just freezes. I can Ctrl + Alt + F2 to get there, but there seems to be no graphics running... When turning back to F7 it's still like that!

So, changing to discrete in bios would put the graphic in ATi-mode only? Or am I wrong?

---

### Post by gncs91 on 2011-02-04
> **Chrilleee said:**
> Well, where the login screen should show up it just freezes. I can Ctrl + Alt + F2 to get there, but there seems to be no graphics running... When turning back to F7 it's still like that!

So, changing to discrete in bios would put the graphic in ATi-mode only? Or am I wrong?

Yep, that should solve it for you. I had exactly the same problem.
F2 -> BIOS
You'll find it, it's one change, "switchabel" -> "discrete". Done!
Hope that helps.

George

---

### Post by daveboy23 on 2011-02-12
hi everyone.
weird stuff has been happening to my ubuntu 10.10 system.  it's been randomly (as far as i can tell) freezing in the past couple of days.  is this happening to anyone else?

i have to actually force power down the computer to continue work...
anyone has any idea what i should check for?

---

### Post by Pat Benson on 2011-02-16
> **gncs91 said:**
> Yep, that should solve it for you. I had exactly the same problem.
F2 -> BIOS
You'll find it, it's one change, "switchabel" -> "discrete". Done!
Hope that helps.

George

I just ordered this one (Acer prod.ID LX.PSE02.353) and I'm curious on how long the battery lasts when running the ATI card only, full settings, bright screen etc. 
As far as I can tell from this and other posts, with 10.10 it should run more or less out of the box?
A minor curiosity, what's your opinion about the case (is it called that?) the finish of it, from what it looks like it's all aluminium, what's the general feel of it?(some Acer machines I've had my hands on give a plastic impression and easily breakable)

---

### Post by Foxcow on 2011-02-16
> **daveboy23 said:**
> hi everyone.
weird stuff has been happening to my ubuntu 10.10 system.  it's been randomly (as far as i can tell) freezing in the past couple of days.  is this happening to anyone else?

i have to actually force power down the computer to continue work...
anyone has any idea what i should check for?

Are you running 32 or 64 bit?  I tried 32 bit for a few weeks and had stability issues.  A clean install of 64-bit fixed my issues.

---

### Post by daveboy23 on 2011-02-18
nope, using good ol 64 bit.  basically, it's gone now, been using the computer for a week and nothing happened.

i'm guessing there are bugs with using the comp after hibernate...
ever since i stopped using that feature the comp is working fine.

---

### Post by jalanbuntu on 2011-02-20
I've just tried to install at my friend's Acer Aspire 4820TG. no proble at all. try 64 bit version.. :popcorn:

---

### Post by Pat Benson on 2011-02-21
> **marm0tte said:**
> @kugalskaper

Ok, so it seems that the only difference between 5820TG and 4820TG is that the 5820 have a little bit faster CPU, a diffenrent screen size maybe and ...
the wifi network card is different :(

According to this howto, you have two diffenrent way to make the wifi card working :
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)


1/ Ethernet card work ?
If yes, just plug a RJ45 ethernet cable on your laptop to get acces to the web
After, just type theses commands in a terminal :
```

sudo apt-get update     # in order to update the repository cache from ubuntu package server to your laptop
sudo apt-get install bcmwl-kernel-source     # in order to install the wifi broadcom package

```After that, under the desktop menu System > Administration > Hardware/Additional Drivers, the STA drivers can be activated for use. Finally, you have to reboot.

2/ Ethernet card does not work
Insert the ubuntu 10.10 64 bits desktop CD (if you don't have dowload it from here :
[http://releases.ubuntu.com/maverick/ubuntu-10.10-desktop-amd64.iso](http://releases.ubuntu.com/maverick/ubuntu-10.10-desktop-amd64.iso)

Navigate in the cdrom folder :
pool/restriced/b/bcmwl

Double click on the file named "bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb"

After that, under the desktop menu System > Administration >  Hardware/Additional Drivers, the STA drivers can be activated for use.  Finally, you have to reboot.


Good luck ;)

Oooh sweet man! Fixed my wifi issue after several hours of troubleshooting! You deserve a beer :) Thank you! (none of the howtos show this, that I could find)

...and this solved my multitouch 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/comments/116](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/comments/116)

---

### Post by lnxtx on 2011-02-25
Folks, anybody has the recent model with Radeon 6550 and AR5BBU12 Bluetooth chip? Anybody got Bluetooth working?

There is a patch claiming to support it: [https://lkml.org/lkml/2011/2/14/550](https://lkml.org/lkml/2011/2/14/550) but I have not found a suitable firmware.

And no, the one extracted from MS Windows driver does not work. Any thoughts on obtaining a proper firmware?

---

### Post by lnxtx on 2011-03-02
And some bad news even for those, who have the old BT chip:    [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commit;h=4bbe08c2a7bbaa35ee9501c72badb7e928c65cb0](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commit;h=4bbe08c2a7bbaa35ee9501c72badb7e928c65cb0)    ath3k-2.fw removed and no longer available.

---

### Post by Treviño on 2011-03-08
New 1.23 bios: [http://go.3v1n0.net/fKqsA3](http://go.3v1n0.net/fKqsA3) ;)

---

### Post by marm0tte on 2011-03-08
ok, I've installed the 1.23 version and the update works.
I haven't notice any change (fans make the same noise , but I don't find them so noisy) ...

---

### Post by daveboy23 on 2011-03-09
hi there people
how did you install the bios? still have windows on the machine? or did you do it through ubuntu? cause if so - could you explain how?

---

### Post by marm0tte on 2011-03-09
hi, here it is :)
no need to use Windows, but during the update make sure to plug the power cord !

[http://ubuntuforums.org/showpost.php?p=10099676&postcount=223](http://ubuntuforums.org/showpost.php?p=10099676&postcount=223)

---

### Post by daveboy23 on 2011-03-12
> **marm0tte said:**
> hi, here it is :)
no need to use Windows, but during the update make sure to plug the power cord !

[http://ubuntuforums.org/showpost.php?p=10099676&postcount=223](http://ubuntuforums.org/showpost.php?p=10099676&postcount=223)

thanks so much, works like a charm

---

### Post by daveboy23 on 2011-03-19
ok, so i've been checking debian and ubuntu for a while now.

can anyone please tell me why oh why don't we have a working proprietary drivers? it's driving me nuts.  is it the computer's hardware choice? the proprietary drivers are !@#? what is it?
also - i must have followed 3 diff guides (the debian one, the ATI wiki one and the ubuntu one) and none worked... we have to do something about this.

---

### Post by lnxtx on 2011-03-24
> **lnxtx said:**
> Folks, anybody has the recent model with Radeon 6550 and AR5BBU12 Bluetooth chip? Anybody got Bluetooth working?

I was lucky enough to get it working with btusb/ath3k from 2.6.38 and ath3k-1.fw from [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=summary)

Not as stable as I would like it to be, but seems to be working. I appreciate if someone else with AR5BBU12 hardware let us know his/her status.

---

### Post by kuangweizhang on 2011-03-26
There are two cards in 4820tg for network.
AR8185 and Broadcom 802.11n. AR8185 is for wired and Broadcom is for wireless.
Do not try to install AR8185 on 10.10 64bit, it won't work. It worked on 10.04 64 bit.
For Broadcom, there is a official linux driver online. Search it and install it with instructions.

---

### Post by shantzg001 on 2011-04-04
Are any of you guys able to get n mode working on your acer 4820TG? My wi-fi card (Broadcom 43225) works only in g mode. If I put my router in "n-only" mode, it doesn't connect at all and if I put it in "auto" mode, then it connects at 54mbps

---

### Post by Foxcow on 2011-04-04
> **shantzg001 said:**
> Are any of you guys able to get n mode working on your acer 4820TG? My wi-fi card (Broadcom 43225) works only in g mode. If I put my router in "n-only" mode, it doesn't connect at all and if I put it in "auto" mode, then it connects at 54mbps



How do you check which mode you're in and how do you change it?

---

### Post by shantzg001 on 2011-04-04
> **Foxcow said:**
> How do you check which mode you're in and how do you change it?

That's the problem. I'm not sure how to check which mode I am in. The only indication I have is the link speed at which I am connecting which is showing up as 54 mbps and that too only when I set the router to work in g+n mode (doesn't connect at all when router is set to n only). This makes me believe that I am in g mode.

---

### Post by marm0tte on 2011-04-06
hi all, it seems to be a very good news for 4820TG owners , isn't it ?
[http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ](http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ)

I'm under natty beta1, FYI compiz is very bugged :D but the ubuntu devs make a great job and patch / updates appears often (nearly each hours)

I will try to install adm ati driver ...

---

### Post by Treviño on 2011-04-07
Well, using opensource drivers works well too (you can test them [using a 2.6.38 kernel in maverick]("http://askubuntu.com/questions/30196/is-it-possible-to-use-a-2-6-38-kernel-with-10-10") too).

However, [Bios 1.25](http://go.3v1n0.net/fKqsA3) upgrade ;)

---

### Post by scorpio2002 on 2011-04-07
Hi there guys! I'm going to buy a Acer TimelineX 4820T... can some of you summarize the current situation?

What works out of the box with the latest updates? What issues are there and how to solve them? Does the camera work?

---

### Post by Foxcow on 2011-04-07
Excellent, I love the fact that they keep updating unlike some OEMs (Samsung).

Will flash today.

---

### Post by Foxcow on 2011-04-07
> **scorpio2002 said:**
> Hi there guys! I'm going to buy a Acer TimelineX 4820T... can some of you summarize the current situation?

What works out of the box with the latest updates? What issues are there and how to solve them? Does the camera work?




I have the 4820T and love it.  The first thing I recommend doing is flash to the latest BIOS.

Everything works out of the box except:
-multi touch on the touchpad
-internal microphone
-the camera works but is hit or miss with Google Chat

The TimelineX is an improvement over the original Timeline (my wife has one) and I recommend it to anyone that asks.

---

### Post by scorpio2002 on 2011-04-07
So, you're telling me that if I install the latest Ubuntu everything will be recognised out of the box?

Do I need to flash the BIOS? Mic and Camera ok? The Intel card ok? Ethernet and wireless ok?

Sorry to ask all these questions, but my last experience with a laptop (Toshiba) has been aweful and this is the reason why I am getting rid of it to buy a new one...

---

### Post by scorpio2002 on 2011-04-07
> **Foxcow said:**
> I have the 4820T and love it.  The first thing I recommend doing is flash to the latest BIOS.

Everything works out of the box except:
-multi touch on the touchpad
-internal microphone
-the camera works but is hit or miss with Google Chat

The TimelineX is an improvement over the original Timeline (my wife has one) and I recommend it to anyone that asks.

So, are there tutorials on how to get the camera and the microphone to work with skype and Google Talk? This is very important for me!

---

### Post by Foxcow on 2011-04-07
> **scorpio2002 said:**
> So, are there tutorials on how to get the camera and the microphone to work with skype and Google Talk? This is very important for me!



I'm doing some testing right now.  So far, I have been using this for fixes:

[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)


I got the internal mic working with the sound recorder.

trying Google chat and Skype now...

---

### Post by scorpio2002 on 2011-04-07
> **Foxcow said:**
> I'm doing some testing right now.  So far, I have been using this for fixes:

[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)


I got the internal mic working with the sound recorder.

trying Google chat and Skype now...

Well, I'm waiting for the results. Are u using the new Beta?

---

### Post by Foxcow on 2011-04-07
> **scorpio2002 said:**
> Well, I'm waiting for the results. Are u using the new Beta?




Yep, new beta.  I don't have enough time to troubleshoot but I couldn't get Skype to pick up my mic.  The camera and microphone both work with Cheese and Sound Recorder, respectively.

---

### Post by scorpio2002 on 2011-04-07
> **Foxcow said:**
> Yep, new beta.  I don't have enough time to troubleshoot but I couldn't get Skype to pick up my mic.  The camera and microphone both work with Cheese and Sound Recorder, respectively.

This really puts me off the idea of buying the laptop. I need skype and gmail talk. I live abroad and that's the only thing I use to communicate with my family :(

So, with the beat everything else works fine? Wireless and Ethernet fine? Any overheating issue?

---

### Post by Foxcow on 2011-04-07
> **scorpio2002 said:**
> This really puts me off the idea of buying the laptop. I need skype and gmail talk. I live abroad and that's the only thing I use to communicate with my family :(

So, with the beat everything else works fine? Wireless and Ethernet fine? Any overheating issue?


I can understand that.  Hopefully, there is a fix that I overlooked and or these issues are resolved in 11.04.

---

### Post by scorpio2002 on 2011-04-07
> **Foxcow said:**
> I can understand that.  Hopefully, there is a fix that I overlooked and or these issues are resolved in 11.04.

Well, it looks like apparently nobody's got the mic to work correctly with Skype and gmail so far... can anybody confirm this? 


I've learned my lesson with my Toshiba and I won't do the same mistake again. I can't imagine throwing my money away a second time... :(

---

### Post by daveboy23 on 2011-04-07
> **scorpio2002 said:**
> Well, it looks like apparently nobody's got the mic to work correctly with Skype and gmail so far... can anybody confirm this? 


I've learned my lesson with my Toshiba and I won't do the same mistake again. I can't imagine throwing my money away a second time... :(


yap, answered earlier in this thread - but just for you :-) and yes - if you change the mic settings outside of alsa (or let skype do it for you) you'll have to repeat the entire thing


> **daveboy23 said:**
> yap, i actually searched for that myself - here's the solution: go to skype and disable the automatic sound adjust thing then go to terminal - type alsamixer, press F4 (capture tab) - so to capture and put it all the way up (or to a volume you like) then (on the same column) press 'y' till you completely mute the left channel. now skype works. problem - if you change the volume from the pulse you loose this configuration so take care.

---

### Post by scorpio2002 on 2011-04-07
Can anybody confirm if Skype and GoogleTalk are fixed with this:

[http://askubuntu.com/questions/31572/skype-doesnt-find-my-audio-input](http://askubuntu.com/questions/31572/skype-doesnt-find-my-audio-input)

I need to buy the laptop soon to get a good price.. so plz, if you can try this as soon as possible I'd be grateful to you!

---

### Post by scorpio2002 on 2011-04-08
Ok, I'm writing just to confirm that I installed Ubuntu 11.04 Beta 1 on the Acer 4820T. All the hardware got recognised and it is working well. The issue with the mic is solved by that workaround I pointed out before.

There's an issue with the webcam... it is incredibly dark... can u confirm this? I didn't have time to try it in Windows, but chances are it's gonna be better.

As far as Natty is concerned, I'm getting used to Unity, even if I might consider switching back to the classical interface.

---

### Post by marm0tte on 2011-04-08
hi, same for me 4820tg under ubuntu 11.04 beta1. The webcam is dark, did you tried this ?
[http://ubuntuforums.org/showthread.php?t=651075](http://ubuntuforums.org/showthread.php?t=651075)

Compiz crashed also, but I seems to be solved under the beta2 and ati/amd drivers doesn't works with 3D acceleration :(

radeon free driver works but switcheroo doesn't, under beta2 there will be the new ati drivers version and with switch apps :
[http://ubuntuforums.org/showpost.php...&postcount=223]("http://ubuntuforums.org/showpost.php?p=10099676&postcount=223")

---

### Post by scorpio2002 on 2011-04-09
> **marm0tte said:**
> hi, same for me 4820tg under ubuntu 11.04 beta1. The webcam is dark, did you tried this ?
[http://ubuntuforums.org/showthread.php?t=651075](http://ubuntuforums.org/showthread.php?t=651075)


What is in that topic doesn't seem to apply. I can't change the colors settings, probably something has changed since 2008.

---

### Post by andy12345 on 2011-04-11
> **marm0tte said:**
> hi, same for me 4820tg under ubuntu 11.04 beta1. The webcam is dark, did you tried this ?
[http://ubuntuforums.org/showthread.php?t=651075](http://ubuntuforums.org/showthread.php?t=651075)

Compiz crashed also, but I seems to be solved under the beta2 and ati/amd drivers doesn't works with 3D acceleration :(

radeon free driver works but switcheroo doesn't, under beta2 there will be the new ati drivers version and with switch apps :
[http://ubuntuforums.org/showpost.php...&postcount=223]("http://ubuntuforums.org/showpost.php?p=10099676&postcount=223")

Hi 4820tg user,
I kinda fiddled around ubuntu for a while but left =(
Wasn't able to stop the i915 turbo error thing at the boot.
Also the lapto heated up unusually on ubuntu (do you experience this?), but I have been following this thread.
One more problem I encountered was update, Ihave a college wifi connection wherein we are given a proxy IP and port and a ID pass to connect. My wifi gets connected and I can surf by using the proxy in mozilla, but when I put the proxy settings in Network Proxy and apply system wide, the updates wont work, I have also changed the proxy in synaptic pacakge manager, but in vain.
I have currently formatted my linux partition and m back to windows. I also had a question my SATA mode is AHCI when i switch to IDE windows show BSoD and dies before it completely boots up (& maybe thats the reason I am not able to do a boot install of ubuntu and have to install it as an app in windows). I have tried this stuff with 10.10.
Any help for my problems is appreciated(I have also tried googling but nothing came up, if anyone can tell me how to get ANY linux distro working on this lap which has a simple GUI I can get my work done).
Regards
--Andy

---

### Post by marm0tte on 2011-04-11
hi andy12345,

We cannot let you down under Windows like this ! :D


For the i915 pb did you try to change the graphic card from switchable to discrete and the vice versa in the BIOS ? 

You have a 4820TG right ? so first did you upgrade the BIOS to the lastest version 1.25 here : [http://go.3v1n0.net/fKqsA3](http://go.3v1n0.net/fKqsA3) ? It will fix your heating problem.

Do you use the  64 bits version of Ubuntu ? On my 4820TG, I had no problem to install Ubuntu 10.10 what error message did you have ?

For the proxy maybe the network admin filter the ubuntu updates domains or port, did you ask him ?

And to answer your question about BSOD, it is totally normal because Windows7 was installed by Acer with AHCI SATA driver so never disable the AHCI in the BIOS.
Keep in mind that if you make a BIOS upgrade you will loose all the BIOS parameters and you will have to reconfigure it after.

---

### Post by andy12345 on 2011-04-12
> **marm0tte said:**
> hi andy12345,

We cannot let you down under Windows like this ! :D


For the i915 pb did you try to change the graphic card from switchable to discrete and the vice versa in the BIOS ? 

You have a 4820TG right ? so first did you upgrade the BIOS to the lastest version 1.25 here : [http://go.3v1n0.net/fKqsA3](http://go.3v1n0.net/fKqsA3) ? It will fix your heating problem.

Do you use the  64 bits version of Ubuntu ? On my 4820TG, I had no problem to install Ubuntu 10.10 what error message did you have ?

For the proxy maybe the network admin filter the ubuntu updates domains or port, did you ask him ?

And to answer your question about BSOD, it is totally normal because Windows7 was installed by Acer with AHCI SATA driver so never disable the AHCI in the BIOS.
Keep in mind that if you make a BIOS upgrade you will loose all the BIOS parameters and you will have to reconfigure it after.

Glad that someone is interested in helping me out :D Thank you so much!!

Yes I have the latest BIOS (1.25) and I tried ubuntu with it before formatting, the heat issue was there, I will try reinstall today (What do you suggest installation inside windows or BOOT install?) for BOOT install Whenever I boot the CD it hangs somehwere sometimes during the start screen or somewhere else. I will again do some more tests later today and keep you posted.
Also yes I am using 64bit Ubuntu 10.10. and I usually use my laptop on battery so using the ATI card kills the battery pretty fast. Can you tell me what exactly to do after the install to get the switch graphics thing working? during my very first install on my new machine I messed up something and used the switching script to switch the cards (the head issue remained), but during recent installs the switch was also not working. As for the wifi I tried the servers via windows, nope they are not blocked or anything.
If everything goes well and I get ubuntu to work by the end of this week I will sum up the procedure and put it up in a guide of some sort.
--Andy


2nd Edit
I used this [http://ubuntuforums.org/showthread.php?t=1642504](http://ubuntuforums.org/showthread.php?t=1642504)
I think it works. Testing... IT WORKS!! :D
 Unsolved Issues :-
Heats up fast, really fast ...

---

### Post by marm0tte on 2011-04-12
Good to know that the proxy works :)

For install, I will said that wubi (inside windows) is easy and good for newcomers but native boot install is much better because you will have performances and no fragmentation ...
Do you know [unetbootin]("http://unetbootin.sourceforge.net/") or [tuxboot]("http://tuxboot.org/download/files-on-sf.php") ? this will help you to create a usb boot stick to install ubuntu easily.

I have no problem of heating, but maybe you can buy one of these notebook cooling pads ?

Also, tomorrow the ubuntu 11.04 beta2 will be released, try to install, it could to solve your heating pb ...

---

### Post by andy12345 on 2011-04-14
> **marm0tte said:**
> Good to know that the proxy works :)

For install, I will said that wubi (inside windows) is easy and good for newcomers but native boot install is much better because you will have performances and no fragmentation ...
Do you know [unetbootin]("http://unetbootin.sourceforge.net/") or [tuxboot]("http://tuxboot.org/download/files-on-sf.php") ? this will help you to create a usb boot stick to install ubuntu easily.

I have no problem of heating, but maybe you can buy one of these notebook cooling pads ?

Also, tomorrow the ubuntu 11.04 beta2 will be released, try to install, it could to solve your heating pb ...

I already have a cooler pad, but its for table use and I don't need it when its on the table as as the heat doesn't bother me then, but when in college campus i use it on my lap or lawn, when on lap it kinda heats up my legs xD.
Anyway, the LAN thing does work, but not COMPLETELY some of the updates get restarted , maybe its my connection I will retry and post the the results.
As for the boot stick, I already installed it on my main HDD, so nvm, I just hope I won't have to remove it now, now that its stable just the heat problem bothers me. And I haven't used the switching scripts and enabled discreet in BIOS, are you able to switch without problems? If yes, can you tell a step by step procedure of what you did to get it working?

---

### Post by marm0tte on 2011-04-14
hum in fact the beta of natty cause me problems crash when using hybrid video cards but you will find more info in the previous treads of this topic, i mean you have to search into the 34 pages of this topic :D

Also you will found infos here :
[http://askubuntu.com/questions/21455/how-to-manage-two-video-cards-on-a-laptop-ati-and-intel](http://askubuntu.com/questions/21455/how-to-manage-two-video-cards-on-a-laptop-ati-and-intel)

---

### Post by marm0tte on 2011-04-15
hi andy12345, so did you read the 34 pages of the topic :p
I will summarize how to use switcheroo on your 4820TG

The good news is that since I have upgraded natty 64bits from beta1 to beta2 I've no more crash of compiz.
The "bad" news is that it works but sometime it doesn't switch on the card you choose ... and also the ubuntu graphic interface doesn't works when the power cable is plugged after booting (black screen and system is frozen) ...

Follow this topic, it will explain you how to setup your laptop to use switcheroo, the script they provide is very good: [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
But you have to enter your password and logout / re-login each time you will switch your video card.

Moreover you will find more infos here : [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)


For the rest of the 4820TG problems resolution you will found more infos here :
[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)
[http://www.linlap.com/wiki/acer+aspire+4820+timelinex](http://www.linlap.com/wiki/acer+aspire+4820+timelinex)
[http://kblackhat.blogspot.com/2010/10/installing-kubuntu-1004-on-acer.html](http://kblackhat.blogspot.com/2010/10/installing-kubuntu-1004-on-acer.html)
[https://wiki.archlinux.org/index.php/Acer_TimelineX#Issues](https://wiki.archlinux.org/index.php/Acer_TimelineX#Issues)

---

### Post by andy12345 on 2011-04-16
> **marm0tte said:**
> hi andy12345, so did you read the 34 pages of the topic :p
I will summarize how to use switcheroo on your 4820TG

The good news is that since I have upgraded natty 64bits from beta1 to beta2 I've no more crash of compiz.
The "bad" news is that it works but sometime it doesn't switch on the card you choose ... and also the ubuntu graphic interface doesn't works when the power cable is plugged after booting (black screen and system is frozen) ...

Follow this topic, it will explain you how to setup your laptop to use switcheroo, the script they provide is very good: [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
But you have to enter your password and logout / re-login each time you will switch your video card.

Moreover you will find more infos here : [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)


For the rest of the 4820TG problems resolution you will found more infos here :
[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)
[http://www.linlap.com/wiki/acer+aspire+4820+timelinex](http://www.linlap.com/wiki/acer+aspire+4820+timelinex)
[http://kblackhat.blogspot.com/2010/10/installing-kubuntu-1004-on-acer.html](http://kblackhat.blogspot.com/2010/10/installing-kubuntu-1004-on-acer.html)
[https://wiki.archlinux.org/index.php/Acer_TimelineX#Issues](https://wiki.archlinux.org/index.php/Acer_TimelineX#Issues)

Very strange, those scripts used to work on earlier installs now when i run them, nothing happens!!
refer my old post [http://ubuntuforums.org/showthread.php?t=1629799&page=2](http://ubuntuforums.org/showthread.php?t=1629799&page=2)
I followed the last post of that thread, it worked now I suppose I am permanently switched to Intel HD? (I would love it that way).
and I am also getting osme update problem, will check into  that later.
--Andy

PS- I forgot to mention that the heat thing is not yet solved.. also the i915 errors at start up

PPS- Also I get really slow download speeds with ubuntu for updating (havent checked anything else), using the main server.(ON windows my average download speed is 800 KBps- 1.2 MBps on ubuntu I haven´t seen it cross 200KBps) & using the update manager is way to slow and it stop in between downloading lot of times, so I use the following terminal commands
sudo apt-get update
sudo apt-get upgrade
BUT after these if I use apt-get clean and then apt-get update & apt-get upgrade, the same amount of downloads need to be done to update,so whenever I use clean, I need to redownload all the packages? I mean clean kinda busted my updates

---

### Post by marm0tte on 2011-04-16
Use the switcheroo script to switch to the intel card.
little tip, chmod +x the switch_between_cards.sh and in its shortcut prefix the .sh script with gksudo for eg. :
gksudo ~/switch_between_cards.sh
because the switch script need root access to the debugfs folder ;)

Finally, optimize your laptop consumption (and for sure the laptop will stop heating :)   )  install and search on the web for powertop optimizations.

Now my 4820TG consume about 10 to 15 W and the battery life is about 4 hours ! But I'm far away of the 8 hours promise by Acer :(


PS: if you speak French here are some docs :
[http://doc.ubuntu-fr.org/laptop_mode](http://doc.ubuntu-fr.org/laptop_mode)
[http://doc.ubuntu-fr.org/energie](http://doc.ubuntu-fr.org/energie)

---

### Post by Foxcow on 2011-04-16
I just flashed BIOS 1.25 using this method:
[http://ubuntuforums.org/showpost.php?p=10099676&postcount=223](http://ubuntuforums.org/showpost.php?p=10099676&postcount=223)

The first method outlined on page 15 of this thread didn't work because the dos executable is too big.

---

### Post by marm0tte on 2011-04-17
hi everybody, I've 2 bugs with the 4820tg under natty b2, do you have these problems too ?

1/  
If I shutdown the laptop with the power supply cable plugged. Unplug the cable, switch on the PC => the screen stay black. Ctrl+Alt+F1 => no tty appears, screen stay black => Ctrl + Alt + F7 and a stack dump is showed.
After I have to press the Alt + SysRq + B magic keys combination to restart the PC. I plug the power cable, start the PC, and it works !

2/
If I configure the screensaver to random, let the PC going to suspend mode, come back, resume doesn't works, the scrensaver image is showed and the PC seems frozen. So I press the Alt + SysRq + B magic keys combination to restart the PC


FYI :
In the CMOS BIOS Setup, the graphic cards are set to switchable.
In the OS I'm under the intel i915 card. The radeon card is off.
Ubuntu Natty 64bits beta2
Using the linux kernel 2.6.38-8-generic

---

### Post by Foxcow on 2011-04-18
It seems that BIOS 1.25 has solved this issue:
> 
Originally Posted by Xirev View Post

Battery Indicator: When I unplug the charger Ubuntu does not know what happened at first and continues normally. However when I plug it in again and then take it out, it detects the battery is discharging. Anyone encountered this strange behaviour?


Since updating, whenever I unplug, the power state instantly changes from charging to battery.  Can anyone else corroborate this?

---

### Post by marm0tte on 2011-04-18
under natty battery indicator works like a charm, the informations are accurate.

But I've more informations about the problem that I told you (black screen when booting) it happens only under the 2.6.38-8
If I boot under the 2.6.38-7 kernel it doesn't hapen, so it is a regression for us :(

I've open a bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765216](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765216)

---

### Post by andy12345 on 2011-04-20
> **marm0tte said:**
> Use the switcheroo script to switch to the intel card.
little tip, chmod +x the switch_between_cards.sh and in its shortcut prefix the .sh script with gksudo for eg. :
gksudo ~/switch_between_cards.sh
because the switch script need root access to the debugfs folder ;)

Finally, optimize your laptop consumption (and for sure the laptop will stop heating :)   )  install and search on the web for powertop optimizations.

Now my 4820TG consume about 10 to 15 W and the battery life is about 4 hours ! But I'm far away of the 8 hours promise by Acer :(


PS: if you speak French here are some docs :
[http://doc.ubuntu-fr.org/laptop_mode](http://doc.ubuntu-fr.org/laptop_mode)
[http://doc.ubuntu-fr.org/energie](http://doc.ubuntu-fr.org/energie)
My consumption after using the intel card is 12.2 w avg but still it heats.... maybe its normal nvm, when i type sensors i get 45 deg C
so anyway moving on, any idea about the speed and internet issue?? 
Whenever I use the update manager, I now have 98.2 MB something left of updates and whenever I update it restarts after sometime.... any help? this is most prolly because of the newtwork proxy I think? but the network is awesome and works out of the box in windows.
And I don't use the switch script I have perma changed it to intel.

---

### Post by Foxcow on 2011-04-28
Has anyone upgraded to 11.04 yet?  If so, how is battery life and performance with the new kernel?

---

### Post by Spacetech326 on 2011-04-29
I've been following this thread for a while, I own the 4820TG and have had Ubuntu on it ever since I bought it.
This thread has been a great help!

> **Foxcow said:**
> Has anyone upgraded to 11.04 yet?  If so, how is battery life and performance with the new kernel?

I'm upgrading mine now and I will report back tomorrow.

---

### Post by rimez on 2011-04-29
> **Foxcow said:**
> Has anyone upgraded to 11.04 yet?  If so, how is battery life and performance with the new kernel?

Ugh, upgraded last night (clean install) and have had nothing but issues. 

The key issue for me is the performance. Whenever I open a program, it takes a LONG time to load (esp., with multiple applications. I've looked at the system monitor and there doesn't seem to be anything out of the norm. 

Tried using the same fixes used on Meerkat for the switchable graphics but they don't seem to work now (esp., cannot dim the monitor).

I cannot recommennd the upgrade just yet. 

This weekend I'll try another clean install.

---

### Post by Foxcow on 2011-04-29
> **rimez said:**
> Ugh, upgraded last night (clean install) and have had nothing but issues. 

The key issue for me is the performance. Whenever I open a program, it takes a LONG time to load (esp., with multiple applications. I've looked at the system monitor and there doesn't seem to be anything out of the norm. 

Tried using the same fixes used on Meerkat for the switchable graphics but they don't seem to work now (esp., cannot dim the monitor).

I cannot recommennd the upgrade just yet. 

This weekend I'll try another clean install.




Thanks.

---

### Post by marm0tte on 2011-04-29
Foxcow, in my opinion, the most important problem is this bug :
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/765216]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765216")

Battery life, perf for me are good.

---

### Post by Spacetech326 on 2011-04-29
I did a clean install on my computer with the 64bit version of 11.04
It seems to be working perfect, it has many drivers that needed manual installs built in now. The battery life seems about the same, I will need to run it longer to really see how well it is.
I wouldn't recommend running an upgrade, you are better off with a clean install.

---

### Post by Foxcow on 2011-04-29
> **marm0tte said:**
> Foxcow, in my opinion, the most important problem is this bug :
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/765216]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765216")

Battery life, perf for me are good.



Thats a pretty big bug.  I'll stick with 10.10 for now.

---

### Post by marm0tte on 2011-04-29
the importance of the bug [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/765216](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/765216) is not decided

But i've solved it by installing another kernel in 6 commands, here it is ;)

```
cd && wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804_2.6.38-02063804.201104221009_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-image-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

sudo dpkg -i linux-image-2.6.38-02063804*
sudo reboot
```

---

### Post by Foxcow on 2011-04-29
> **marm0tte said:**
> the importance of the bug [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/765216](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/765216) is not decided

But i've solved it by installing another kernel in 6 commands, here it is ;)

```
cd && wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804_2.6.38-02063804.201104221009_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-image-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

sudo dpkg -i linux-image-2.6.38-02063804*
sudo reboot
```


Beautiful!  I'll have to give it a shot tonight.  Thanks.

---

### Post by RavensKrag on 2011-04-29
Has anyone gotten the ATI Catalyst 11.4 drivers to work yet?  I tried it a couple of times but just ended up with an error I did not understand.

---

### Post by Confusered on 2011-04-29
> **RavensKrag said:**
> Has anyone gotten the ATI Catalyst 11.4 drivers to work yet?  I tried it a couple of times but just ended up with an error I did not understand.

I have tried the proprietary FGLRX drivers and it works. But these are the steps I took. 

1) Go to BIOS.
2) Change graphics options from "Switchable" to "Discrete".
3) Reboot.
4) Boot into Ubuntu (normal mode, not recovery).
5) Open terminal window, type in "sudo apt-get install update"
6) After completion, type in "sudo apt-get install fglrx"
7) Upon completion, reboot Ubuntu.
8) Graphics driver should be working properly, and typing "amdcccle" in terminal will launch Catalyst.

However, switching BIOS option back to "Switchable" will cause Ubuntu to boot into classic mode.

---

### Post by RavensKrag on 2011-04-29
Ah... see, that's the thing.  I'd like to be able to switch, as I like having both battery life and performance.  Honestly, the battery life is more important to me right now.

Thanks for the info though.  It's good to know that the driver works, even if the switching doesn't.

Also, I can confirm that the vga-switcheroo allows switching into the open-source ATI driver.  I tried to play And Yet it Moves, and I just got a mess of ugly lines.  Minecraft ran, but the performance was no better than on the integrated card.  glxgears was getting about 60fps when maximized.

---

### Post by flooo on 2011-04-30
Hi,

I've bought a 4820TG but I cannot get my Wifi run. Using the Fn+F3 key combination only bluetooth is activated/deactivated. Windows says that it is a broadcom device.
In previous replies I saw that the results of the following commands could be helpful - so here it is. Before I forget it: I'm running Kubunto 10.10
I would be really happy if somebody can help me.

Greetings
Florian

```
lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```


```
iwconfig                                                                                                                                                                          
lo        no wireless extensions.                                                                                                                                                                                                                                                                                                                                                            
eth0      no wireless extensions.
```

---

### Post by RavensKrag on 2011-04-30
Did you enable the broadcom restricted driver?

---

### Post by Foxcow on 2011-04-30
> **flooo said:**
> Hi,

I've bought a 4820TG but I cannot get my Wifi run. Using the Fn+F3 key combination only bluetooth is activated/deactivated. Windows says that it is a broadcom device.
In previous replies I saw that the results of the following commands could be helpful - so here it is. Before I forget it: I'm running Kubunto 10.10
I would be really happy if somebody can help me.

Greetings
Florian

```
lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```


```
iwconfig                                                                                                                                                                          
lo        no wireless extensions.                                                                                                                                                                                                                                                                                                                                                            
eth0      no wireless extensions.
```



What BIOS version do you have?

run this to find out:
```

sudo lshw

```

---

### Post by flooo on 2011-05-01
> **RavensKrag said:**
> Did you enable the broadcom restricted driver?

Unfortunately I do not know how to do that. What do I need to do?

Regarding the BIOS version: I already checked it and it is 1.19. As I read before it shall be at least 1.18 so I thought this would be ok.

Best regards
Florian

---

### Post by Foxcow on 2011-05-01
> **flooo said:**
> Unfortunately I do not know how to do that. What do I need to do?

Regarding the BIOS version: I already checked it and it is 1.19. As I read before it shall be at least 1.18 so I thought this would be ok.

Best regards
Florian

The latest bios is 1.25.  I think you ought to give that a whirl.

---

### Post by flooo on 2011-05-01
Hi,

I updated my bios to 1.25 but there is no change. It seems that I only need to activate the driver, but I do not know how.

Greetings
Florian

---

### Post by Foxcow on 2011-05-01
> **flooo said:**
> Hi,

I updated my bios to 1.25 but there is no change. It seems that I only need to activate the driver, but I do not know how.

Greetings
Florian


Try checking: System > Administration > Additional Drivers

Like someone else mentioned, you may need to enable the restricted drive.

---

### Post by marm0tte on 2011-05-01
hi flooo, it seems that your broadcom BCM43225 works only with a closed driver.

So if your Ethernet network card is well recognized and if you can plug it to a kind of router :D , follow these instructions :
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20Internet%20access)

But if you doesn't have any Internet access, follow this :
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

Finally, if none of the previous solves your problem :confused: , follow the ndiswrapper workaround explain by ElDuderino here :
[http://translate.google.fr/translate?hl=fr&sl=fr&tl=en&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D2121106%23p2121106](http://translate.google.fr/translate?hl=fr&sl=fr&tl=en&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D2121106%23p2121106)

Good luck !

---

### Post by RavensKrag on 2011-05-01
EDIT2:
Nope, still getting the black screen even with new kernel and new BIOS. Also, wireless has stopped working.

EDIT:
With older kernel, the system is able to rectify it's battery status error after a few seconds.  Still got the black screen bug, but I got past it with a couple or REISUBs as opposed to the 10~ I've had to do as of earlier today.  Hopefully even that much was a result of switching over to this kernel for the first time.  Thanks for the help guys, I was getting ready to go back to Maverick.


Keep getting that horrible black screen on bootup bug.  Gonna DL and try that older kernel right now.

Also, with the 2.6.38-8-generic kernel and 1.25 BIOS, unplugged the power, only to have my computer tell me it was in a critical power state.  It then immediately went into hibernation.  Hopefully this is a regression which will be fixed by reverting to the older kernel as well.  Has anyone else encountered this problem?

---

### Post by RavensKrag on 2011-05-01
Ah, so about that wireless error.

One of the reasons it might not be working is because of those commands to install the older kernel which were posted earlier.  They download the kernel headers and image, but only install the image.  You need those headers to compile the wireless driver.

Once you install the headers you should be able to enable the broadcom wireless driver through Jockey.

---

### Post by Beyla on 2011-05-02
I was also having trouble with the WiFi and the battery indicator on 11.04.

Updating the BIOS to 1.25 fixed both of these issues, if anyone else is having these problems try updating your BIOS to the latest first.

---

### Post by Foxcow on 2011-05-02
I also found that BIOS 1.25 fixed the power state issue that many people were having.  Prior to 1.25, when the laptop was unplugged, it took a few seconds/minutes/hours/never before it would change to the on-battery profile.  With 1.25, the change is instantly.

---

### Post by flooo on 2011-05-03
Hi,

thanks. It worked out when I did like described in the first link.
As soon as I had my wifi-connection running I wanted to update the software. The system offered me to update on natty 11.04 - what I did. Unfortunately after the update has finished without problems and after rebooting, the system starts with the kubuntu-screen with 5 dots under it but went then to the terminal-modus only (no colourful ;) desktop anymore :( )
What did I do wrong - want can I do?

Thanks
Florian

> **marm0tte said:**
> hi flooo, it seems that your broadcom BCM43225 works only with a closed driver.

So if your Ethernet network card is well recognized and if you can plug it to a kind of router :D , follow these instructions :
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20Internet%20access)

But if you doesn't have any Internet access, follow this :
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

Finally, if none of the previous solves your problem :confused: , follow the ndiswrapper workaround explain by ElDuderino here :
[http://translate.google.fr/translate?hl=fr&sl=fr&tl=en&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D2121106%23p2121106](http://translate.google.fr/translate?hl=fr&sl=fr&tl=en&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D2121106%23p2121106)

Good luck !

---

### Post by marm0tte on 2011-05-03
looks bad, please post the following logs in attachment /var/log/dist-upgrade/* and /var/log/dmesg /var/log/Xorg*

---

### Post by lnxtx on 2011-05-05
Under 10.10 it was toggling both BT and WiFi when pressing Fn+F3, under 11.04 toggles WiFi only, have to manually invoke rfkill to enable BT. Anyone else has the same problem?

---

### Post by RavensKrag on 2011-05-05
Same here.  I've actually just been going to the indicator and turning BT off.  Don't know if that saves as much power though.

---

### Post by Silentzor on 2011-05-05
Hey,

shortly after I upgraded my ubuntu from 10.10 to 11.04, my system started acting very weirdly:

I could have the laptop on for 10 hours or 10 minutes, but for sure at some point it would show up the shutdown prompt where you choose from suspend/hibernate/shutdown or cancel on it's own, without me pressing anything, and then after I would press cancel it would pop up again and again, and eventually the computer would shut down (probably from the 60 second counter?). THEN, the most weird thing would happen:

The laptop wouldn't turn on for a few hours. It looked like it was dead, but if I unplugged the battery and plugged the charger it would instantly turn on (without me pressing anything, again), and then die after 2 seconds (the BIOS wasn't loaded by the time it died so I couldn't press anything). I was forced to wait a couple of days and eventually remove ubuntu and use windows 7 so that the laptop wouldn't die.

Do you have ANY clue why this would happen? Again, it only happened in 11.04, not 10.10.

Silentzor

P.S. After upgrading, I booted to 10.10 via a USB drive, and the same thing happened again.

---

### Post by Foxcow on 2011-05-07
I've moved back to 10.10 64-bit until some of the major issues in 11.04 have been worked out.

---

### Post by basharat on 2011-05-07
> **marm0tte said:**
> @LintWad

So, I've completely test this howto and it works :
[http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-linux-with-unetbootin/](http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-linux-with-unetbootin/)

You might use a "good" usb stick. I mean that a noname usb key may not work.
I've tried the procedure with 2 noname sticks and in freedos when I list the c: drive (1st usb partition) the shell never returned to prompt and I had to reboot.

But, my PNY 8GB usb stick works well


Here is the process I use :

1/ In ubuntu, backup the datas of the usb stick.
Launch GParted :
sudo gparted

2/ Delete all the partitions. Create a FAT16 primary partition of 512MB for example.
Create a second NTFS or FAT32 partition with the rest of free space
Click Apply

3/ Set a boot flag on the FAT16 partition and close Gparted

4/
Download the last BIOS update for the Acer
Download FreeDOS base CD : [http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso)
Copy the BIOS .EXE file on the USB key

Install unetbootin :
sudo apt-get install unetbootin
and start it

5/ Select "Disk /image" and select "ISO" . Browse your disk to the fdbasecd.iso file
in the "drive" list, select your usb stick device (/dev/sdXX)
Click OK

6/ Restart. Go into the F2 BIOS Setup menu.
Select F12 Boot Menu => Enable
Save and exit

7/ Press F12 and select USB HDD in order to boot on the usb stick
In the next menu select FDos and select the 2nd option Start Freedos CD ...

8/ Be sure to have the Power supply plugged on your laptop
At the DOS prompt type :
C:
And launch the ZQ1_119.exe in order to flash BIOS


This is it ! :P

Thanks, worked like a charm

---

### Post by DarkTide on 2011-05-15
I use the kernel 

· [linux-image-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-image-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_amd64.deb")
· [linux-headers-2.6.35-7_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_all.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7_2.6.35-7.11%7elucid1.3v1ubuntu2%7etoi2_all.deb")
· [linux-headers-2.6.35-7-generic_2.6.35-7.11~lucid1.3v1ubuntu2~toi2_amd64.deb]("http://download.tuxfamily.org/3v1deb/acer-timelinex/linux-headers-2.6.35-7-generic_2.6.35-7.11%7elucid1.3v1ubuntu1_amd64.deb")

  1. I can not find the switcheroo in the /sys/kernel/debug/.../vga_switcheroo file to enable the switch graphic card function.
  2. Is this kernel provide both vga cards driver ?  I can not change the "extra" in the "Visual Effects".

  Is any procedure I need to follow ? 
BTW, my timelinex 4820tg BIOS upgrade to version 1.13 , is this cause the problem ?

---

### Post by RavensKrag on 2011-05-15
You need to update both your BIOS and your kernel.  The kernels built by Canonical do not have the VGA Switcheroo built in until the Maverick release.  The updated BIOS will help you with other problems, as discussed earlier in this thread, but it is not the main source of your graphics problem.  If you are unsure about upgrading to Natty, I would suggest at least upgrading to Maverick.

---

### Post by Pat Benson on 2011-05-17
> **Foxcow said:**
> I've moved back to 10.10 64-bit until some of the major issues in 11.04 have been worked out.

I had a very strange issue. I thought it was graphic problem at first but it was connected to the WiFi driver. Maybe the link can help someone else.

[http://bigbrovar.aoizora.org/index.php/2011/04/30/turning-wireless-on-causes-laptop-to-freeze-on-ubuntu-11-04-natty-narwhal-my-work-around/]()

---

### Post by Foxcow on 2011-05-17
> **Pat Benson said:**
> I had a very strange issue. I thought it was graphic problem at first but it was connected to the WiFi driver. Maybe the link can help someone else.

[http://bigbrovar.aoizora.org/index.php/2011/04/30/turning-wireless-on-causes-laptop-to-freeze-on-ubuntu-11-04-natty-narwhal-my-work-around/]()

I wasn't having that issue but thanks! :)  Like you said, hopefully someone else can benefit.

---

### Post by daveboy23 on 2011-05-26
hi, did anyone else had the following problem:
when i restart, sometimes the computer hangs on bios screen and the fan gets really loud

anyone has a clue as to what could be the problem?

---

### Post by marm0tte on 2011-05-26
> **daveboy23 said:**
> hi, did anyone else had the following problem:
when i restart, sometimes the computer hangs on bios screen and the fan gets really loud

anyone has a clue as to what could be the problem?

hi daveboy23, witch Ubuntu version do you use, witch kernel, and Acer bios ?

---

### Post by daveboy23 on 2011-05-27
it's a problem i had stating with ubuntu 10.04 (now 10.10) but it also occurs in debian squeeze.
bios ver 1.25 since of yesterday

am not sure, but i think the new bios fixed the problem, but i'm not sure.  i think it's linked with unplugging the power while restarting

the computer stays on bios screen and the fan goes wild (really loud)

edit:
just checked and i think it's fixed, if someone with bios ver 1.23 (or 1.25) could check to make sure - restart the computer while unplugging the computer from the AC, then wait till the bios starts and see if it hangs on the bios screen (the big acer logo) and the fan starts to work loudly

---

### Post by grid_bug on 2011-05-30
Just out of curiosity, how well does 3D acceleration on the ATI chip work for most of you? I get about 100fps running glxgears, which feels kinda low to me.

---

### Post by Honza-m on 2011-05-30
Hi guys, sry for the question, but did someone solve the problem with HDMI? I wanna use switchable graphics, so I can't use ATI drivers. Anythink I can do with it?

---

### Post by clemsaklumpen on 2011-05-31
is it possible to run ubuntu(wubi) or any other dual boot linux dist on this computer whith fully working hardware?

if yes where do i find the drivers?

regards /clemsaklumpen

---

### Post by ewarci on 2011-06-06
HI,

last week i bought the Acer Aspire 4820TG TimelineX. I like this notebook, but unfortunately it doesn't cooperate with Ubuntu very well.

My Setup:
Ubuntu 11.04 64Bit
Bios 1.25

I read serveral pages of this thread, but most posts refer to Ubuntu 10.04 or 10.10. So I hope you have some informations, which can help me to get along with the combination of this laptop and ubuntu 11.04.

I have the "bootproblem", when my notebook boots it often freezes and the screen turns black. Is there a possibility to avoid this bug?

My second problem: the hybridgraphic. Is there a solution, which works with ubuntu 11.04 ?

I hope you can help me because I don't like to use windows. But if i'm forced to boot 10 times to get to ubuntu i have to abandon.

grtz Marcel

---

### Post by Foxcow on 2011-06-06
> **ewarci said:**
> HI,

last week i bought the Acer Aspire 4820TG TimelineX. I like this notebook, but unfortunately it doesn't cooperate with Ubuntu very well.

My Setup:
Ubuntu 11.04 64Bit
Bios 1.25

I read serveral pages of this thread, but most posts refer to Ubuntu 10.04 or 10.10. So I hope you have some informations, which can help me to get along with the combination of this laptop and ubuntu 11.04.

I have the "bootproblem", when my notebook boots it often freezes and the screen turns black. Is there a possibility to avoid this bug?

My second problem: the hybridgraphic. Is there a solution, which works with ubuntu 11.04 ?

I hope you can help me because I don't like to use windows. But if i'm forced to boot 10 times to get to ubuntu i have to abandon.

grtz Marcel

edit:  Earlier in this thread, another member suggested using a slightly older version of the kernel that comes by default with 11.04 by using these commands:
```

cd && wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804_2.6.38-02063804.201104221009_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-image-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

sudo dpkg -i linux-image-2.6.38-02063804*
sudo reboot

```


Or...

Try using this guide to update to kernel 2.6.39-0
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/)

If that doesn't help, I'd suggest moving back to 10.10 64-bit.

---

### Post by ewarci on 2011-06-07
Thanks for your answer  @Foxcow!

I updated the kernel, but this doesn't solve my problem!

---

### Post by Foxcow on 2011-06-07
> **ewarci said:**
> Thanks for your answer  @Foxcow!

I updated the kernel, but this doesn't solve my problem!

You're welcome.  Did you manually select the different kernels?  I'm assuming you clean installed and ubuntu is the only os on the drive?  If so, you can get into the grub menu this way:

[www.insidesocal.com/click/2010/03/so-here.html](www.insidesocal.com/click/2010/03/so-here.html)

Try both kernels.

---

### Post by lnxtx on 2011-06-08
> **ewarci said:**
> 
I have the "bootproblem", when my notebook boots it often freezes and the screen turns black. Is there a possibility to avoid this bug?

My second problem: the hybridgraphic. Is there a solution, which works with ubuntu 11.04 ?


Blacklist radeon module in modprobe config and it won't freeze on boot (something goes wrong during the radeon init).

Re: hybrid graphics, have no idea, switcheroo works, using it for turning the radeon off (requires explicit modprobe since radeon.ko blacklisted to avoid boot freezes). Never actually used radeon, so cannot give any valuable advice here.

P.S. running it for a while, the only thing annoying me in 11.04 -- haven't found a way to toggle bluetooth via a hot key.

---

### Post by ewarci on 2011-06-09
> **lnxtx said:**
> Blacklist radeon module in modprobe config and it won't freeze on boot (something goes wrong during the radeon init).
Thank you @lnxtx i blacklisted radeon and it boots! 

 @Foxcow I manually installed the 2.6.39-0 kernel. Ubuntu isn't the only OS i've installed, there is also a Windows 7 partition. The Problem wasn't that i don't see grub: I saw grub, but after ubuntu started booting the screen turened black, but with the hint from @lnxtx this problem is now solved!

---

### Post by wizards on 2011-06-11
Is there another solution to switch on safe mode (intel card) like switcheble script or every time logging off when changing card?

I think this time is fine :))) but I have low cpu and other detail of system .. but 8 hours is nice:D
```

Battery #1     : present
    Remaining capacity : 7272 mAh, 91.07%, 08:04:15
    Design capacity    : 9000 mAh
    Last full capacity : 7985 mAh, 88.72% of design capacity
    Capacity loss      : 11.28%
    Present rate       : 901 mA
    Charging state     : discharging
    Battery type       : rechargeable 
    Model number       : 32 mAh
    Serial number      : AS10E7E

```

---

### Post by RavensKrag on 2011-06-11
Right now logging off is the only way.  But it's much better than it used to be.  In the past with this sort of thing you would have to completely shut down first.  Still not as nice as the switching you get in windows, I'll admit, but it's progress.

You get 8 hours? o_O; Is that with wireless and bluetooth off? What's your screen brightness?

---

### Post by Foxcow on 2011-06-11
> **wizards said:**
> Is there another solution to switch on safe mode (intel card) like switcheble script or every time logging off when changing card?

I think this time is fine :))) but I have low cpu and other detail of system .. but 8 hours is nice:D
```

Battery #1     : present
    Remaining capacity : 7272 mAh, 91.07%, 08:04:15
    Design capacity    : 9000 mAh
    Last full capacity : 7985 mAh, 88.72% of design capacity
    Capacity loss      : 11.28%
    Present rate       : 901 mA
    Charging state     : discharging
    Battery type       : rechargeable 
    Model number       : 32 mAh
    Serial number      : AS10E7E

```



Holy cow!  Where did you get that battery from?

---

### Post by wizards on 2011-06-12
:p Battery is original :) 
I have 30% display, powersafe on all cpu, bluetooth off and wifi on.

------>
-> 7-8 hours on battery - only no load on pc, like read some documents, using browser, read rss and similiar work.
-> 5-6 hours on battery - little using pc, like bash (installing or using other programs)
-> all other time is using pc more(cpu or hdd) - virtualbox and other SW(downloader SW)

---

### Post by Foxcow on 2011-06-12
> **wizards said:**
> :p Battery is original :) 
I have 30% display, powersafe on all cpu, bluetooth off and wifi on.

------>
-> 7-8 hours on battery - only no load on pc, like read some documents, using browser, read rss and similiar work.
-> 5-6 hours on battery - little using pc, like bash (installing or using other programs)
-> all other time is using pc more(cpu or hdd) - virtualbox and other SW(downloader SW)



I thought that all came with 6000 mAh batteries

```

Battery 0: Charging, 87%, 00:24:52 until charged
Battery 0: design capacity 6000 mAh, last full capacity 5663 mAh = 94%
Adapter 0: on-line
Thermal 0: ok, 39.0 degrees C

```


Also, what command did you use to get that detail battery info?  I just used:
```
 acpi -V
```

---

### Post by wizards on 2011-06-12
@Foxcow
I have used similar:
```
acpitool -B
```

I have original 9000 mAh batteries (in my country sell with this capacity) so that is the reason why i have this big time.

---

### Post by Foxcow on 2011-06-12
> **wizards said:**
> @Foxcow
I have used similar:
```
acpitool -B
```I have 9000 mAh (in my country sell with this capacity) so that is the reason why i have this big time.




Thanks.  I wish that battery size were an option here.

---

### Post by DatBaer on 2011-06-12
You can buy the battery online at the acer shop. It costs about 200€ .
Just got mine today :D

---

### Post by Foxcow on 2011-06-12
> **DatBaer said:**
> You can buy the battery online at the acer shop. It costs about 200€ .
Just got mine today :D



Good call!  Does this replacement stick out much further than the stock one?



For everyone in the US, here is the link:
[http://us-store.acer.com/product.aspx?pn=AK.009BT.083](http://us-store.acer.com/product.aspx?pn=AK.009BT.083)

I'll definitely be getting this.

---

### Post by DatBaer on 2011-06-12
About 2.5 cm.

You can compare the difference with a Keyboard with some of these little turnable pillars. 
Have fun with extra 3000mAh  :D

---

### Post by andy12345 on 2011-06-28
Did anyone try 11.04 on 4820TG, if yes any problems?

---

### Post by Foxcow on 2011-07-15
Have any 11.04 users noticed any changes with the fairly recent kernel update to 2.6.38-10?

---

### Post by RavensKrag on 2011-07-15
> **Foxcow said:**
> Have any 11.04 users noticed any changes with the fairly recent kernel update to 2.6.38-10?

I'm running it right now, and it seems pretty good. It disabled my little script to turn the ATI card off on startup, but that's pretty minor.  I got a black screen a couple of times while trying to start up, but no more than when I was using the older kernel linked to earlier in this thread.  It's just a bit jarring, as with the older kernel I at least got some text on screen.  With this one, it's just black.

Once it's up though, it seems to run fine.

I've been plugged in almost constantly though, so I can't comment on the battery life.

---

### Post by Foxcow on 2011-07-16
> **RavensKrag said:**
> I'm running it right now, and it seems pretty good. It disabled my little script to turn the ATI card off on startup, but that's pretty minor.  I got a black screen a couple of times while trying to start up, but no more than when I was using the older kernel linked to earlier in this thread.  It's just a bit jarring, as with the older kernel I at least got some text on screen.  With this one, it's just black.

Once it's up though, it seems to run fine.

I've been plugged in almost constantly though, so I can't comment on the battery life.

Thanks.  I'm really curious about the battery life though.  Is Unity behaving better?

---

### Post by v1ctory on 2011-07-29
To use switchable graphics use latest AMD video driver, it has powerXpress, that allows you to switch from intergrated to discrete and from discrete to intergrated.

---

### Post by shantzg001 on 2011-08-02
> **v1ctory said:**
> To use switchable graphics use latest AMD video driver, it has powerXpress, that allows you to switch from intergrated to discrete and from discrete to intergrated.

AFAIK, powerxpress supports only 2 ATI cards and not 1 ATI + 1 Intel combo. So it won't work for us.

---

### Post by jomari74 on 2011-08-26
Hi! I'm new here and I am also a user of Acer Aspire 4820TG TimelineX. I have been using it for almost a year with the Win7 OS. Yesterday, I tried installing Ubuntu 11.04 side to side with the Win7 and it seemed to be installed successfully. However, there are some issues I have encountered:

1. ) The battery seemed to drain alot quicker when using Ubuntu compared to Win7.
2. ) The some of the Fn hotkeys are not working (An example is the Bluetooth for Fn+F3, it just deactivates the wifi).
3. ) The bluetooth is always turned on. (Is there a way to turn it off automatically at startup and just turn it on manually if needed to be used? [not the BIOS approach])
4. ) I don't know how to enable the Compiz features (especially the Scale).
5. ) The mic is not functioning?
6. ) Touchpad multi-gesture is not working?

Are there solutions to these problem? I am not much familiar on tinkering with files in this OS. Thanks! :)

*I am trying to read from the first page of the thread and it seems to be a tedious task to read all the 41 pages. I just tried to do the solution to #6 but there is no Autostartup selection.

---

### Post by Foxcow on 2011-08-31
Is anyone having wake from suspend issues with 11.04?  It seems like 1 of 3 times, my machine will not wake from a suspend correctly.  The machine is getting power but nothing is displayed.  I always have to hard reboot.  

I started having trouble with this when kernel 2.6.38-11 came about.  Anyone else?

---

### Post by moliones on 2011-09-02
> **Foxcow said:**
> Is anyone having wake from suspend issues with 11.04?  It seems like 1 of 3 times, my machine will not wake from a suspend correctly.  The machine is getting power but nothing is displayed.  I always have to hard reboot.  

I started having trouble with this when kernel 2.6.38-11 came about.  Anyone else?

I also have this issue occasionally, not as often as 1 in 3, more like 1 in 10. It is fairly annoying, and I don't have much idea how to tackle it.
Once I managed to `debug' it (following Debug Suspend on the Ubuntu Wiki), and it indicated the last thing loaded was fbcon, but that's as far as I got.

---

### Post by Foxcow on 2011-09-02
> **moliones said:**
> I also have this issue occasionally, not as often as 1 in 3, more like 1 in 10. It is fairly annoying, and I don't have much idea how to tackle it.
Once I managed to `debug' it (following Debug Suspend on the Ubuntu Wiki), and it indicated the last thing loaded was fbcon, but that's as far as I got.


Thanks for that info.  I think I figured it out and will use your suggestion to confirm it.  I started using Xpad as a replacement for Gnome sticky notes when this problem started.  Whenever I have notes visible on the desktop, the computer has issues waking from suspend.  Whenever I don't have them visible, no problem.

---

### Post by vinaym815 on 2011-09-25
[SIZE=3]i,,m running on ubuntu natty and bios version 1.25 . i have put [/SIZE]  [SIZE=3][FONT=&quot]echo OFF > /sys/kernel/debug/vgaswitcheroo/switch in rc.local so that my discrete graphic card swithes off everytime i boot . but if i shutdown i get some atom bios stuck error which slows down the shutdown to 20secs whose solution was to switch on graphic card again and i can shutdown in flat 4 secs.  so i tried to put a shell having [/FONT][/SIZE]  
[SIZE=3][FONT=&quot]echo ON > /sys/kernel/debug/vgaswitcheroo/switch 
[/FONT][/SIZE]
[SIZE=3][FONT=&quot]exit 0[/FONT][/SIZE]
[SIZE=3][FONT=&quot]into the rc0.d and rc6.d but the problem is i read on net that name of file should begin with K99 where k stands for kill or should start with S and also read they are executed in alphabetical order but i could make things work  therefore i decided to make a shell with[/FONT][/SIZE]
[SIZE=3][FONT=&quot]echo ON > /sys/kernel/debug/vgaswitcheroo/switch[/FONT][/SIZE]
[SIZE=3][FONT=&quot]sudo halt[/FONT][/SIZE]
[SIZE=3][FONT=&quot]exit 0[/FONT][/SIZE]
[SIZE=3][FONT=&quot]and place it on the desktop so that i can shutdown by running the shell but the problem is it is not executed as it requires root privileges so i tried to  visudo  as root and allow vinay(user) the right to execute the commands as well as shell script but couldnt work that also out . so anyone [SIZE=4]plz[/SIZE] help me either to to execute the command automatically via rc0.d and rc0.6 directory or please help me execute the shell script as root  so i can shutdown my laptop in a fast and hassle free manner[/FONT][/SIZE]

[SIZE=3][FONT=&quot][/FONT][/SIZE]
[SIZE=3][FONT=&quot]thank you
[/FONT][/SIZE]

---

### Post by elehcim on 2011-10-04
Hi, I have suspension trouble too. It's quite annoying because you cannot trust your computer. Anyone has tried if it happens also with the new kernel that is going to go out with 11.10? Anyone has tried Oneiric Beta? Thanks.

---

### Post by lukasw on 2011-10-05
Hi,

I don't know a solution for the suspension problem, either.
But I use to press Ctrl+Alt+1 (open a terminal) and, next to that, press Ctrl+Alt+7 to close the terminal. For me, after doing this, everything is working fine again. :)

---

### Post by micio on 2011-10-08
Hi all,
I'm installing ubuntu for the first time on my acer 4820tg and I got some problem to properly setup my graphic cards.

At first boot it loads the intel driver and system is working fine (I didn't tried yet the battery drain)
After that I installed flgrx driver from "additional driver hardware" and then I cannot run unity..
I looked at xorg configuration and I saw a very poor config, so I ran "aticonfig --initial -f" and now X won't start neither in low graphics mode.
Then I looked at Xorg.0(1).log where there are:

```
(EE): Screen 1 deleted because of no matching config section
(EE): fglrx(0): PowerXpress: Failto switch libGL link files.
```

and then a seg fault...

I tried also to install official catalyst 11.9 from ati website but X didn't come up and I'm stuck in the shell just like before.

So my question is.. Is there any guide that I can follow to properly setup ati5470 card and switch to intel (and back)?

Thanks in advance!

---

### Post by Foxcow on 2011-10-14
Anyone upgrade to 11.10 final yet?

---

### Post by wizards on 2011-10-15
> **Foxcow said:**
> Anyone upgrade to 11.10 final yet?

Is there any reason to upgrade to this? Some important reason?....:confused:
I hate Unity and Gnome3 and when i read many topic on internet in 11.10 haven't gnome2.
In 11.04 haven't to, but is there some way to instal, but i think in 11.10 isn't any way.

So i don't plan using 11.10. :P ...Maybe Iam wrong... time show:(

---

### Post by Foxcow on 2011-10-15
> **wizards said:**
> Is there any reason to upgrade to this? Some important reason?....:confused:
I hate Unity and Gnome3 and when i read many topic on internet in 11.10 haven't gnome2.
In 11.04 haven't to, but is there some way to instal, but i think in 11.10 isn't any way.

So i don't plan using 11.10. :P ...Maybe Iam wrong... time show:(



I won't discuss the merits or drawbacks of Unity or an upgrade to 11.10 but if you want to install Gnome Classic:

```
sudo apt-get install gnome-session-fallback
```

Log out, select Gnome classic and you're done.

---

### Post by RavensKrag on 2011-10-16
EDIT3:
Heat problem fixed for Intel graphics, running on ATI is still very hot.  Getting temperatures of ~50 degrees Celsius on Intel, and ~80 on ATI. So if you really need HDMI out for some reason, go ahead and use vgaswitcheroo to switch over to the discrete video.  It works fine, and video outputs to HDMI without any problems.  The video in general lags more, and your overall system will be hotter though.

So basically, the drivers are much better, but are still not good yet.  Hopefully by the LTS the FOSS drivers will have advanced to the point where everything runs smoothly.

EDIT2:
Ok, I think this fixes the heat problem, at least for me.  ATI card is still hotter than I would like (aka, hotter than in W7), but I haven't crashed yet. *crosses fingers*
[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)


EDIT:
Actually, the Intel card generates a good deal of heat too.... =/

So... good news: Open source driver for ATI in Ubuntu 11.10 makes the ATI card actually work.  3D support as well as HDMI out.

Bad news:
It fails to cool the computer properly, resulting in crashes due to overheating.  I'm currently trying to find a way to manually increase the fan speed, as well as monitor the card temperature.

If anyone knows of a way, I'd appreciate it.

---

### Post by hdarama on 2011-10-20
Hi there. I'm a 4820TG user too. I downloaded ubuntu 11.10 and installed. vgaswitcheroo doesnt worked for me. I cant find anything about it. please help.
Regards.

---

### Post by DatBaer on 2011-10-20
You need to have a sudo shell
as a normal user I cant get beyond /sys/kernel/debug , but with sudo -s before everything works fine.

Is it only me or doesn't vgaswitcheroo doesn't switch the cards anymore?
I can turn the second one on and off but it won't switch.

But I'm happy with the lifetime of my battery(The big 9Ah one),  at all it's about half an hour less then with 10.10 (I skipped 11.04) but that's okay.

A Usefull link for arranging the new system is [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by Foxcow on 2011-10-20
Is anyone getting constant freezes and wake from suspend issues?  I am experiencing both with Unity and Gnome Shell.

This is really discouraging...

---

### Post by hdarama on 2011-10-21
> **DatBaer said:**
> You need to have a sudo shell
as a normal user I cant get beyond /sys/kernel/debug , but with sudo -s before everything works fine.

Is it only me or doesn't vgaswitcheroo doesn't switch the cards anymore?
I can turn the second one on and off but it won't switch.

But I'm happy with the lifetime of my battery(The big 9Ah one),  at all it's about half an hour less then with 10.10 (I skipped 11.04) but that's okay.

A Usefull link for arranging the new system is [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)
Thanks. After removed Ati catalyst drivers, its working now. Thanks a lot.

---

### Post by vinaym815 on 2011-10-26
JUST INSTALLED UBUNTU 11.10 FRESH ON MY ACER 4820TG HAVING BIOS VERSION 1.25 . THE FIRST THING THAT BUGGED ME WAS THAT EVEN AFTER TURNING THE ATI CARD OFF VIA VGA_SWITCHEROO WAS RUNNING AT CONSTANT SPEED THOUGH THE FAN SPEED GOT REDUCED ,  EVEN WHEN MY LAPTOP WAS AT NORMAL TEMP THE FAN WAS RUNNING CONSTANTLY.  AFTER A LOT OF GOOGLING I FOUND  [http://www.forums.toshiba.com/t5/Computer-Troubleshooting/Laptop-cooling-fan-constantly-on/td-p/135754/page/9](http://www.forums.toshiba.com/t5/Computer-Troubleshooting/Laptop-cooling-fan-constantly-on/td-p/135754/page/9) which suggest that this constant running of fan can be corrected either by bios Editing or by modifying drivers in acpi . I don,t want to mess up with my bios cause i don,t have windows installed and i will mess it up it,s going to be a huge trouble.   ](*,)  .

[http://www.youtube.com/watch?v=uKi1YHAq3wM](http://www.youtube.com/watch?v=uKi1YHAq3wM)     just going to try out this.   hey is there anyone having same fan problem ?

one can check [http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)    this for an idea to how to solve the fan speed problem . if anyone have solved this type of problem please help

---

### Post by vinaym815 on 2011-10-27
my cpu temp is 46cesius and the fan is still going on plz help

---

### Post by Foxcow on 2011-10-27
> **vinaym815 said:**
> my cpu temp is 46cesius and the fan is still going on plz help



How are you determining your CPU temp?

---

### Post by vinaym815 on 2011-10-27
by puttin command sensors in terminal .  i get something like

vinay@dark-star:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +46.0°C  (crit = +105.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:       -128.0°C

the problem is fan should be switched on at about 55.0°C but it,s on everyone though it,s speed gets adjusted from fast to slow

---

### Post by Foxcow on 2011-10-27
Well, a temperature of 46 C is not at all outrageous.  My machine is routinely in that neighborhood depending on the activity with some fan activity.

If you haven't recently done this, I recommend you get a can of canned air and blow out your vents and clean the computer up in general (with it off of course) and see if that helps.  One strategically placed piece of dust/debris can drastically alter the way the machine cools itself.  The One of the reasons the Timeline series gets such good battery because "smart cooling" or something like that has been incorporated into the chassis design.

---

### Post by daveboy23 on 2011-10-28
been a long time since i've been on this thread... which means everything is running fine...

here's why i'm here again - has anyone tried Coreboot bios? i'd love to hear if anyone tried and what was his\her's exp with it

thanks guys

---

### Post by Foxcow on 2011-10-28
Does coreboot support our chipset?  If it does, I can't find it.

---

### Post by qiou on 2011-10-30
On my laptop, previously running on 11.04 but now on ArchLinux, I reach 54°C on high CPU usage, with ATI deactivated using vga_swictheroo.

On idle/internet(no flash animations) I reach 35-45°C.
My fan turn on but on slow mode at 35°C, and on idle turn off at 30°C.

It's when AC is plugged, and power management is on performance mode. On battery, I've got a limitation to 50% on CPU power.

---

### Post by vinaym815 on 2011-11-19
hey i,m trying this other linux os meego and evrything seems to be working fine but ir don,t support hybrid graphics so can you plz tell me how to blacklist ati graphic card , i guess it,s the sam e procedure as it is in ubuntu but i was never able to blacklist in ubuntu also . any sought of help would be appreciated

---

### Post by vinaym815 on 2011-11-19
and i have this network proxy 10.0.0.253 with port 808 , but when i enter that in network proxy in ubuntu , firefox works fine , but the update manager and terminal and ubuntu software centre does not use this proxy , i googles it a lot but no solution seems to workout for me

---

### Post by DatBaer on 2012-01-08
Good morning,

Could some try to regulate the brightness of their display through the terminal with

sudo setpci -s 00:02.0 F4.B=xx

xx means the procentage value of the brightness. so xx is between 1 and 99

If you're using the Radeon graphic card, you have to replace 00:02.0 with 01:00.0 

It doesn't work for me with Ubuntu 11.10 Gnome 3 

On my girlfriends netbook with Ubuntu 11.10 Unitiy it is working.

It would be great if someone could help me with this.

---

### Post by Foxcow on 2012-01-08
The function key to change brightness or volue do not work?

---

### Post by DatBaer on 2012-01-09
Volume is just working fine, but the brightness is a problem.
I can only change between total minimum, 50% and maximum.

---

### Post by Foxcow on 2012-01-09
> **DatBaer said:**
> Volume is just working fine, but the brightness is a problem.
I can only change between total minimum, 50% and maximum.


Do you have the latest BIOS version?

---

### Post by DatBaer on 2012-01-09
I have 1.23.

Is 1.25 stable?

Edit: But is the setpci command working on your laptop?

---

### Post by Foxcow on 2012-01-10
> **DatBaer said:**
> I have 1.23.

Is 1.25 stable?

Edit: But is the setpci command working on your laptop?


1.25 is the best version yet.  I've been using it since April 2011.  It fixed a lot of small, nagging things for a lot of people.

---

### Post by DatBaer on 2012-01-10
After updating the Bios, there are two possible things to happen if I want to change the brightness.

Number 1 : The Symbol appears and I can change between 0, 50 and 100% Brightness.

Number 2: The Symbol doesnt appear and i can change between 0, 20, 40, 60, 80 and 100 % Brightness.


Someone got an idea how to solve this?

---

### Post by Foxcow on 2012-01-10
> **DatBaer said:**
> After updating the Bios, there are two possible things to happen if I want to change the brightness.

Number 1 : The Symbol appears and I can change between 0, 50 and 100% Brightness.

Number 2: The Symbol doesnt appear and i can change between 0, 20, 40, 60, 80 and 100 % Brightness.


Someone got an idea how to solve this?


Did you upgrade from a previous version or clean install?  Honestly, after BIOS 1.25, I've never had any trouble whatsoever.  When I used to run Ubuntu (last version was 11.10 for a month), I clean installed between versions and had no trouble.

---

### Post by DatBaer on 2012-01-11
I made an update from cd from version 10.10. 
At the beginning everything worked fine but with an update it got the way it is now.

---

### Post by Foxcow on 2012-01-11
> **DatBaer said:**
> I made an update from cd from version 10.10. 
At the beginning everything worked fine but with an update it got the way it is now.



I recommend a clean install.

---

### Post by DatBaer on 2012-01-17
Ok.
I'll have to wait till april until I can make a clean install due to some licenses which I really need.
But thank you.

If someone got to know why setpci isn't working, it would be great to know.

---

### Post by wizards on 2012-02-24
Is anybody running on Ubuntu 11.10 - latest version?

Have this some critical bugs? Iam runnig on 11.04 but sometimes i think about change.

---

### Post by Foxcow on 2012-02-24
> **wizards said:**
> Is anybody running on Ubuntu 11.10 - latest version?

Have this some critical bugs? Iam runnig on 11.04 but sometimes i think about change.


I think you'd be better off with 11.04 and waiting for 12.04.  11.10 is what made me switch from Ubuntu altogether.  One of the things that really turned me off about 11.10 was the lack of customizability of Unity.  12.04 is supposed to be an improvement but that is what was promised with 11.10.

---

### Post by wizards on 2012-02-26
Ok thanks. So I'am wait. Do you know anything about switchable graphics and fans in 12.04? Now i have 11.04  switchable graphics ok and fans (i think is ok too) but sometimes i hear in 11.10 fans and graphics does not work very well.

---

### Post by Foxcow on 2012-02-26
I'm not at all sure about 12.04 but if history is any indicator, I'd bet that switching doesn't work since the walkaround didn't work for 11.10.  Hopefully, we are all pleasantly surprised since this is a LTE release.

---

### Post by daniel488 on 2012-04-29
Hi,
do you know any way to run 12.04 on integrated graphics card? How to disable Radeon?
I have now Ubuntu 11.04 with 11.8 driver version from AMD and it works perfect. Long time couldn't boot Ubuntu 11.10 because of that common LightDM fail, but finally I tried upgrade one more time and fixed it. In Ubuntu 11.10 card drivers didn't worked and two card were enableb. Then I upgrade to 12.04 and hoped that new driver (12.4) will be ok, but with it graphic mode even don't start. When I cleaned Xorg.conf, I have 12.04 with Unity2D (3D mode don't start window manager, I have only wallpaper and conky) and two cards enabled. Cores temperature gets to 100 degrees...

---

### Post by RavensKrag on 2012-04-30
Both cards work in 12.04 using vgaswitcheroo.  It is enabled in this kernel by default, and seems to work fine.  I'm using the ATI card now to output to an external monitor over HDMI.  I have occasional problems, like not coming back quickly after the automatic screen blanking and lock due to inactivity, but I think that has to do with my personal memory leaking problems more thank anything else (too many tabs >.<).  There is also a problem that sometimes my internal display will reduce it's refresh rate, but that can be resolved by simply unplugging the HDMI cable and plugging it back in.

The ATI card can be disabled using vgaswitcheroo.  I've been using that method for the last few releases, and it seems to work fine.

I find it interesting that you got it to work on 11.04.  Much like yourself, I had problems with 11.10 and 12.04 when using the ATI closed-source driver.

---

### Post by daniel488 on 2012-04-30
Good to know it is worth fighting. I think I should consider fresh installation, because all solutions I found didn't worked. But first need to find some disc for backup.

---

### Post by EricOdhiambo on 2012-05-25
Hi,

I just started using ubuntu 12.04 on my Aspire Timelinex, which is my first time to use ubuntu at all. Unfortunately, the battery status cannot be displayed though I already tried out all programms available in the software center. Can anybody help?
Thanks
Odhiambo

---

### Post by stodthagen on 2012-06-01
Hi,

first of all, I wish to thank the people that already have spent much time on getting all features to run on this great notebook. I have used all solutions and had a running machine since this thread exists. Thank you all for this! :)

Now i updated from ubuntu 11.10 to ubuntu 12.04, and I think it is time to participate a bit here. The update lead into some problems...

My BIOS was configured to use only the ATI card when I started.

- aptoncd did not work until I installed hal
- wlan and bluetooth worked instantly

Because I want to reduce power consumption, I switched on both gfx cards in the BIOS and had to reconfigure X. The fglrx package is still installed, and I think, this is why the vgaswitheroo does not work right now. Can somebody give me the steps to get vgaswitcheroo running again? I'll try to remove the fglrx package and see what happens until you rescue me. ;)

The cooling fan is extremely annoying. Do you know a way to control it's speed?

cu soon,

Bernd

---

### Post by CoronaAdvances on 2012-06-01
I have the same problem

---

### Post by stodthagen on 2012-06-01
Hi again,

to get the vgaswitcheroo functionality back again, I  removed the fglrx-updates package. After a reboot vgaswitcheroo is back and almost works!  The X server was reconfigured automatically.  

Further I installed the package indicator-cpufreq and used the applet to  set the cpu(s) to power saving mode. I still think that the fan speed  is changing too often and to extreme RPM values, i.e. increasing the cpu  load only a little bit results in the fan being turned up to full  speed.

At my first attempt, the power consumption went below 10W. After a reboot, it was and stayed at 17W (both with power saving mode set, display brightness at its minimum and the discrete gfx card turned off - bluetooth and wlan on)
Just for completeness, this is the content of /sys/kernel/debug/vgaswitcheroo/switch:
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

When windows is running the dvd drive is turned off. This should be possible in ubuntu too. Who knows how to do it???

I still have problems with the X configuration when switching back to the discrete sound card:
After switching to the discrete card, I logged out and got back to the login manager. I logged in and the gnome-session started but didn't react to my mouse clicks and keyboard inputs. Several times I killed the gnome-session from the console and retried - no change, the desktop still hangs. 
After a reboot, the desktop came up and ran normally (with the discrete card). I managed to switch to the internal card again and wanted to write my "report" here before I examine any further. ;)

I still use an older set of scripts to switch between the cards. Wouldn't it be a good idea to provide a package with these scripts???

If you think that I mess up too many things in one single post, please tell me! B)

Regards,
Bernd

---

### Post by DatBaer on 2012-07-20
Hello,

Even though uvcvideo is blacklisted Powertop shows a Power Usage of ~3 W for the Webcam. Does anyone have this Problem too or knows a Solution to this?

Is this a Problem of Powertop or of the Webcam?

Greetings,
Philipp.

---

### Post by kanaziwok on 2012-09-22
Hi there,

I don't know if I will definitly jump into the ubuntu world.
I've tried several times in the past and none of these attempts let me stay on Ubuntu.

For these reasons :
[LIST]
[*]Lifetime of the battery (about 2h30 instead of 7h, I have a 9 cell battery)
[*]Multi-touch gestures not really functionnal for a daily use (only scroll feature available)
[*]Card reader was not functionnal
[*]Wifi was not working
[/LIST]

But that, it was like 2 years ago, and I hope, thanks to the huge community things are not like they were anymore =).

So my question, is it worth now to try another jump ? because Windows 8 is coming, and I don't like it so much :(

Thank you

---

### Post by WiuEmPe on 2012-12-15
This is my bug report about resume: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090373](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090373)

edit:
and this is my fix: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090373/comments/5](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090373/comments/5)

---

### Post by 27CaseyCZ on 2013-03-13
Hey! Seems like every one of u has 100% working system huh? 
[indent]I am using Xubuntu 12.04 64-bit (TimelineX 5820tg, first gen i5, ATI 5650 & Intel) Volume changing, microphone, brightness are good, wi-fi, ethernet etc are good... But goddamn I can't figure out how to switch that sh*t ATI off forever...  coz I just wanna use Intel. Any help?[/indent]I edited /etc/rc.local and pasted before exit 0:[INDENT]chown -R $casey:$casey /sys/kernel/debug[/INDENT]
[INDENT]if [ "$1" = "start" ]; then[/INDENT]
[INDENT]echo OFF > /sys/kernel/debug/vgaswitcheroo/switch              [/INDENT]
[INDENT]echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch [/INDENT]
[INDENT]elif [ "$1" = "stop" ]; then     [/INDENT]
[INDENT]echo ON > /sys/kernel/debug/vgaswitcheroo/switch [/INDENT]
[INDENT]fi[/INDENT]
I tried like a hundred of combinations but sometimes they're still both on. I mean like intel on and ATI off does work sometimes... but sometimes does not and I don't wanna reboot it all the time.HELP! :(

---

### Post by refle on 2013-05-01
[COLOR=#000000]Hi I use Ubuntu 12.04 (64bit) on Acer Timeline TG3820.[/COLOR]
[COLOR=#000000]Sometimes Ubuntu just doesnt wake up from suspend. But not always...[/COLOR]
[COLOR=#000000]Any issues like that already known?[/COLOR]
[COLOR=#000000]Thank you!

PS
[/COLOR][COLOR=#000000]i think itmust be something with the graphics (although i have installed the proprietary driver)... because when i wake up from suspend the screen turns on to black, than off again, again on to black and then i can log in ... and sometimes it stays just off... this is so strange[/COLOR]

---

### Post by cRaZyBisCuiT on 2013-06-18
> **27CaseyCZ said:**
> Hey! Seems like every one of u has 100% working system huh?[INDENT]I am using Xubuntu 12.04 64-bit (TimelineX 5820tg, first gen i5, ATI 5650 & Intel) Volume changing, microphone, brightness are good, wi-fi, ethernet etc are good... But goddamn I can't figure out how to switch that sh*t ATI off forever...  coz I just wanna use Intel. Any help?
...
[/INDENT]

You can use a modded BIO and disable the AMD graphics. This is what I did in my GFs notebook. But just because she'd like to play games under linux as well I am still looking for a solution to switch...

**Is there a way to switch any 4820TG now using fglrx?** Has AMD managed to provide suitable drivers not matter if you habe a muxed setup? :/

EDIT: I just sent a support request for muxed setups to ATI. Please do the same. Maybe they consider to do something if many people are effected. I also sent a link to this thread so they'll read my call. That's not a problem I assume. But still ATI: Please provide nice linux drivers for us and we will by your hardware because it's the better one. But as long as you don't support linux good enough many people will think twice before buying your hardware in the future. And linux could be the OS of the future. I guess you know that.

---

### Post by mi-bentlage on 2013-08-14
> **27CaseyCZ said:**
> [INDENT] [...] But goddamn I can't figure out how to switch that sh*t ATI off forever...  coz I just wanna use Intel. Any help? [...]
[/INDENT]

I know I am late to answer, but I just now found an upstart-script to turn the ATI off during boot. Works almost flawlessly. (Sometimes after this script, the USB-mouse doesn't work until I manually replug it. Weird.)

```

description "Workaround for ATi Mobility Radeon card, switches off discrete card
 using vgaswitcheroo"
author "Ruslan N. Marchenko <me(o)ruff.mobi>"

start on virtual-filesystems
stop on runlevel [!2345]

pre-start exec modprobe radeon
post-start script
    echo -en "Switching off discrete VGA card."
    until grep Off /sys/kernel/debug/vgaswitcheroo/switch
    do
        sleep 1
        echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
        echo -en "."
    done
    echo " Done"
end script

post-stop script
    echo ON > /sys/kernel/debug/vgaswitcheroo/switch
end script

```

Just put it in a file like [FONT=courier new]/etc/init/radeon.conf[/FONT] and you're done.
I want to make clear that this is not my work. Some nice guy put it on his webspace: [http://ruff.mobi/go/ubuntu/upstart.html](http://ruff.mobi/go/ubuntu/upstart.html)

---

### Post by DeeKey on 2014-05-02
I upgraded to Ubuntu 14.04 on my notebook Acer 3820tg.
System is mostly usable but following annoying problems exist:

1) black screen when running System Parameters;
2) random black occurs screen during power on or resume from hibernate. The system is not halted but there is a black screen. I can still do software reboot.

The problem might be connected with hybrid graphics (ATI + discreet)
I have already filled a bugreport:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1314506](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1314506)

Any suggestions on the issue?

---

### Post by Vikram_Bankar on 2014-06-08
> **Amivit said:**
> Mine worked by default. Even injection with aircrack :O
What does your lspci say?

Hey which os were you using? which version? I am trying hard to get the injection with aircrack working.

---

### Post by mi-bentlage on 2014-11-04
I don't remember precisely, but I think starting with Ubuntu 14.04, I can't get the discrete graphics card to shutdown completely. The fix I wrote about a few posts up doesn't work anymore.
 I know about the new powersaving functions (radeon.runpm=0 and radeon.dpm=0) the radeon module offer, but they don't shutdown the card completely or worse, don't let the graphical login show-up at all. (The best I got was DynOFF, but the fans stay on.) 
Does anybody know a fix to this?

---

### Post by lorek123 on 2015-01-18
Hey, i have a problem with fan, when i boot on ubuntu it's beeing disabled and everything is getting hot. Is anyone have any idea what's wrong? I have acer 5820tg on 1.25 BIOS.

---

