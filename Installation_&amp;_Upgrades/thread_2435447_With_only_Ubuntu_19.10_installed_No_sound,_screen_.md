---
title: "With only Ubuntu 19.10 installed: No sound, screen brightness control and wifi"
date: 2020-01-21
forum: Installation &amp; Upgrades
---

### Post by pclarke58 on 2020-01-21
Dear Everyone !

I had Windows installed on a 1 TB internal hard drive inside a 
HP Pavilion laptop.

Everything was working fine.

I replaced the 1TB internal hard drive with a 2TB internal hard drive.

After installing only Ubuntu 19.10 on the 2TB internal hard drive  (with 
no Windows or Mac operating systems installed alongside Ubuntu 19.10).

I now have no sound control.  Also, when I  try to play an audio file VLC 
media player says:
   Audio output failed.  The audio device default could not be used.  
   No such file or directory.

I only have Ethernet connection no wifi internet connection,

I also have no screen brightness control.

Very disappointing compared to the Windows installation.

All of these kind of hardware drivers issues makes it extremely hard
work for a member of "Joe Public !!" to install and use Linux.

I reckon it must put a lot of people of from persisting in doing so.

Thereby making many people more inclined to go back to using 
Windows or Mac OSX where hardware drivers appear to install 
themselves more by "Magic" !!

Can anyone please help me with these issues.

Thanks !!

Paul Clarke

---

### Post by Impavidus on 2020-01-21
On most hardware Ubuntu just works, but sometimes you've bad luck. Hardware manufacturers always make sure their devices work with the current Windows versions, or nobody would sell computers with those devices, but they (not all; some actually provide good Linux drivers or enough technical data for others to write those drivers) pay less attention to Linux. For older hardware there often are good reverse engineered drivers, but with the latest hardware you may be less lucky.

At least you've got wired internet. Can you try the "additional drivers" utility (it's in your software sources) to search for additional, proprietary drivers? Maybe something is available for your hardware. Some information on your hardware will help too; maybe there's someone around here familiar with your devices. If you're unsure, this command will give some details:```
inxi -ANGz
```

---

### Post by pclarke58 on 2020-01-21
:confused:

Dear Impavidus

Thanks for your response.

In terminal window the command "inxi -ANGZ" gets following response:

```
pclarke@HP-Pavilion:~$ inxi -ANGZ
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] driver: amdgpu 
  v: kernel 
  Display: x11 server: X.Org 1.20.5 driver: amdgpu,ati 
  unloaded: fbdev,modesetting,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD STONEY (DRM 3.33.0 5.3.0-26-generic LLVM 9.0.0) 
  v: 4.5 Mesa 19.2.1 
Audio:
  Device-1: AMD driver: snd_hda_intel 
  Device-2: AMD Family 15h Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.3.0-26-generic 
Network:
  Device-1: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169 
  Device-2: Intel Wireless 3165 driver: N/A 
  Device-3: ASIX AX88772 type: USB driver: asix 
pclarke@HP-Pavilion:~$ 
```

    _____________________________________________________

In Software & Updates window under Additional Drivers appears:

Intel Corporation: Wireless 3165 (Dual Band Wireless AC3165)
    This device is using an alternative driver:
    Using iwliifi driver backport in DKMS format from backport-iwlwifi-dkms (open source)

    Do not use this device ("is greyed out")

No proprietary drivers are in use.   Options to "revert" or "apply changes" are greyed out.

A proprietory driver has private code that Ubuntu developers can't review or improve.
Security and other updates are dependent on the driver vendor.

    _______________________________________________________

On restarts of laptop I get an Ubuntu window saying:

System problem detected 
Do you want to report the problem now ?

I have clicked yes several times to this message during the last couple 
days

   _______________________________________________________

I hope this is of use to you.

Kind regards

Paul Clarke

---

### Post by slickymaster on 2020-01-21
*Thread moved to **Installation & Upgrades**.*

---

### Post by P-I H on 2020-01-21
This might be the problem

There has been a bug that selects hdmi audio after boot
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1847570](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1847570)
[COLOR=#333333][FONT=monospace]This bug was fixed in the package pulseaudio - 1:13.0-1ubuntu1.1

I suppose audio will work after an upgrade
Open a terminal with Ctrl+Alt+T and do **sudo apt update** and **sudo apt upgrade**

[/FONT][/COLOR]

---

### Post by pclarke58 on 2020-01-23
Dear All

After sudo apt update and sudo apt upgrade, still no audio sound or screen control
or wifi connection available.

With a plugable USB audio adapter (which does work on a separate Windows laptop) 
now also plugged into a USB port, the command

inxi -ANGZ 

gets following reply from a terminal window:

```
pclarke@HP-Pavilion:~$ inxi -ANGz
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] driver: amdgpu 
  v: kernel 
  Display: x11 server: X.Org 1.20.5 driver: amdgpu,ati 
  unloaded: fbdev,modesetting,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD STONEY (DRM 3.33.0 5.3.0-26-generic LLVM 9.0.0) 
  v: 4.5 Mesa 19.2.1 
Audio:
  Device-1: AMD driver: snd_hda_intel 
  Device-2: AMD Family 15h Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.3.0-26-generic 
Network:
  Device-1: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169 
  Device-2: Intel Wireless 3165 driver: N/A 
  Device-3: ASIX AX88772 type: USB driver: asix 
pclarke@HP-Pavilion:~$ 
```

So Ubuntu operating system seems to be able to recognise and see the 
hardware.  But, appears not to have the s/w drivers to use them.

It should not be such a struggle for the "public" to get hardware working with
Linux.  They might flee back to suppliers of other operating systems where such
matters appear more straight forward.

Kind regards

Paul Clarke

---

### Post by pclarke58 on 2020-01-31
Dear Everyone !

After a few sudo apt update and sudo apt upgrade terminal commands,
during the past week, together with using the command 
"pulseaudio --start":

     volume sound and  wifi are "for now" working.

However, problem of no screen brightness control still persists.

Terminal command "inxi -ANGZ" now gets reply:

```
pclarke@HP-Pavilion:~$ inxi -ANGZ
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] driver: amdgpu 
  v: kernel 
  Display: x11 server: X.Org 1.20.5 driver: amdgpu,ati 
  unloaded: fbdev,modesetting,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD STONEY (DRM 3.33.0 5.3.0-29-generic LLVM 9.0.0) 
  v: 4.5 Mesa 19.2.8 
Audio:
  Device-1: AMD driver: snd_hda_intel 
  Device-2: AMD Family 15h Audio driver: snd_hda_intel 
  Device-3: C-Media type: USB driver: hid-generic,snd-usb-audio,usbhid 
  Device-4: JMTek LLC. type: USB driver: hid-generic,snd-usb-audio,usbhid 
  Sound Server: ALSA v: k5.3.0-29-generic 
Network:
  Device-1: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169 
  Device-2: Intel Wireless 3165 driver: iwlwifi
```

So it appears that the graphics video driver still needs an update to enable 
screen brightness control for Ubuntu 19.10.

Please advise.

Thanks !

Paul Clarke

---

### Post by slickymaster on 2020-01-31
@pclarke58

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting terminal output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by pclarke58 on 2020-01-31
Dear Slickymaster

I had no knowledge of what code tags are.

I will try to put the terminal output for command "inxi -ANGZ" 
into code tags.

Here goes:

```
pclarke@HP-Pavilion:~$ inxi -ANGZ
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] driver: amdgpu 
  v: kernel 
  Display: x11 server: X.Org 1.20.5 driver: amdgpu,ati 
  unloaded: fbdev,modesetting,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD STONEY (DRM 3.33.0 5.3.0-29-generic LLVM 9.0.0) 
  v: 4.5 Mesa 19.2.8 
Audio:
  Device-1: AMD driver: snd_hda_intel 
  Device-2: AMD Family 15h Audio driver: snd_hda_intel 
  Device-3: C-Media type: USB driver: hid-generic,snd-usb-audio,usbhid 
  Device-4: JMTek LLC. type: USB driver: hid-generic,snd-usb-audio,usbhid 
  Sound Server: ALSA v: k5.3.0-29-generic 
Network:
  Device-1: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169 
  Device-2: Intel Wireless 3165 driver: iwlwifi 
pclarke@HP-Pavilion:~$
```

Thanks for your reply.

Paul Clarke

---

### Post by pclarke58 on 2020-02-01
Dear Everyone

I have another issue.  A bluetooth dongle is recognized as a usb device 
that is plugged in.

Terminal command "lsusb" gets response.

```
pclarke@HP-Pavilion:~$ lsusb
Bus 001 Device 006: ID 8087:0a2a Intel Corp. 
Bus 001 Device 004: ID 05c8:038e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 007: ID 0d8c:0024 C-Media Electronics, Inc. 
Bus 001 Device 005: ID 045e:076c Microsoft Corp. Comfort Mouse 4500
Bus 001 Device 010: ID 04f2:0116 Chicony Electronics Co., Ltd KU-2971/KU-0325 Keyboard
Bus 001 Device 009: ID 0c76:120b JMTek, LLC. 
Bus 001 Device 008: ID 045b:0209 Hitachi, Ltd 
Bus 001 Device 003: ID 045b:0209 Hitachi, Ltd 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 1058:25a1 Western Digital Technologies, Inc. Elements / My Passport (WD20NMVW)
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pclarke@HP-Pavilion:~$ 
```

It is recognized as the Cambridge Silicon Radio, Ltd Bluetooth Dongle.

But, in Settings>Bluetooth the message "No Bluetooth Found.  Plug in 
a dongle to use Bluetooth" is displayed.

So, it appears that this bluetooth dongle needs an update to be made 
useable by Ubuntu 19.10.

Please advise.

Thanks

Paul Clarke

---

