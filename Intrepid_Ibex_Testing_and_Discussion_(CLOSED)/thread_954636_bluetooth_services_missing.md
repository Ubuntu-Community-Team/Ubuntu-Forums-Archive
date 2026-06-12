---
title: "bluetooth services missing"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by m.hataj on 2008-10-21
i can't configure services by bluetooth-applet, the services tab is missing.

that's been a neat thing on hardy to set up bt-networking - why is it missing?

it's an actual intrepid ubuntu
Linux corona 2.6.27-7-generic #1 SMP Fri Oct 17 22:24:30 UTC 2008 x86_64 GNU/Linux

bluetooth-services are available, i need pan and dunroot@corona:/etc/bluetooth# sdptool browse local
Browsing FF:FF:FF:00:00:00 ...
Service Name: Headset Audio Gateway
Service RecHandle: 0x10000
Service Class ID List:
"Headset Audio Gateway" (0x1112)
"Generic Audio" (0x1203)
Protocol Descriptor List:
"L2CAP" (0x0100)
"RFCOMM" (0x0003)
Channel: 12
Profile Descriptor List:
"Headset" (0x110
Version: 0x0100

Service Name: Audio Source
Service RecHandle: 0x10001
Service Class ID List:
"Audio Source" (0x110a)
Protocol Descriptor List:
"L2CAP" (0x0100)
PSM: 25
"AVDTP" (0x0019)
uint16: 0x100
Profile Descriptor List:
"Advanced Audio" (0x110d)
Version: 0x0100

Service Name: AVRCP TG
Service RecHandle: 0x10002
Service Class ID List:
"AV Remote Target" (0x110c)
Protocol Descriptor List:
"L2CAP" (0x0100)
PSM: 23
"AVCTP" (0x0017)
uint16: 0x103
Profile Descriptor List:
"AV Remote" (0x110e)
Version: 0x0103

Service Name: AVRCP CT
Service RecHandle: 0x10003
Service Class ID List:
"AV Remote" (0x110e)
Protocol Descriptor List:
"L2CAP" (0x0100)
PSM: 23
"AVCTP" (0x0017)
uint16: 0x103
Profile Descriptor List:
"AV Remote" (0x110e)
Version: 0x0103

Service Name: BlueZ PANU service
Service Description: BlueZ PAN service
Service RecHandle: 0x10004
Service Class ID List:
"PAN User" (0x1115)
Protocol Descriptor List:
"L2CAP" (0x0100)
PSM: 15
"BNEP" (0x000f)
Version: 0x0100
SEQ16: 800 806
Language Base Attr List:
code_ISO639: 0x656e
encoding: 0x6a
base_offset: 0x100
Profile Descriptor List:
"PAN User" (0x1115)
Version: 0x0100

Service Name: BlueZ GN service
Service Description: BlueZ PAN service
Service RecHandle: 0x10005
Service Class ID List:
"PAN Group Network" (0x1117)
Protocol Descriptor List:
"L2CAP" (0x0100)
PSM: 15
"BNEP" (0x000f)
Version: 0x0100
SEQ16: 800 806
Language Base Attr List:
code_ISO639: 0x656e
encoding: 0x6a
base_offset: 0x100
Profile Descriptor List:
"PAN Group Network" (0x1117)
Version: 0x0100

Service Name: BlueZ NAP service
Service Description: BlueZ PAN service
Service RecHandle: 0x10006
Service Class ID List:
"Network Access Point" (0x1116)
Protocol Descriptor List:
"L2CAP" (0x0100)
PSM: 15
"BNEP" (0x000f)
Version: 0x0100
SEQ16: 800 806
Language Base Attr List:
code_ISO639: 0x656e
encoding: 0x6a
base_offset: 0x100
Profile Descriptor List:
"Network Access Point" (0x1116)
Version: 0x0100

---

### Post by gds on 2008-10-25
I see the same things - no services tab at all. Bluetooth is pretty broken for me in the current release candidate; anyone got a suggestion for where I should start looking?

---

### Post by gatman3 on 2008-10-25
Same here.

hcitool appears to work.  I can find devices (two cellphones):

 > hcitool scan
Scanning ...
        00:19:79:32:27:6A       Nokia N75
        00:1C:43:0E:6A:D6       SGH-A707

And the bluetooth daemon is running:

 6550 ?        S      0:00 /usr/bin/python /usr/bin/kblueplugd
 6563 ?        S      0:00 kbluetooth4
 8331 ?        Ss     0:00 /usr/sbin/bluetoothd

But no icon in the tray, and no obvious way to try to pair with devices or perform OBEX transfers.

Worked fine in hardy.

Anyone know what's going on?

---

### Post by autocrosser on 2008-10-25
Open up Synaptic & download anything OBEX or bluetooth--that finally got it to where I could connect with my phone.

---

### Post by gatman3 on 2008-10-25
Synaptic.  Hmmm...  I use KDE.  Maybe that's the problem.

Installing gnome, going to see if bluetooth works under gnome.  Stay tuned.

---

### Post by inportb on 2008-10-25
You're installing Gnome just so you could use Synaptic? I like your style...

---

### Post by FuturePilot on 2008-10-26
Missing here too. Where did it go?

---

### Post by ^[H3ad-Tr1p]^ on 2008-10-26
up

I have the similar problem on my intrepid ibex on laptop

here is my 3d [http://ubuntuforums.org/showthread.php?p=6037002#post6037002](http://ubuntuforums.org/showthread.php?p=6037002#post6037002)

---

### Post by maschnitz on 2008-10-27
Chiming in with a "me too".  It was working before I upgraded to Intrepid, and not working after.

The USB Bluetooth dongle is visible via lsusb (both the HID and HCI versions), and the mouse is visible through hcitool dev.  I've tried installing everything Bluetooth/OBEX related in Synaptic; I've tried disabling HID2HCI in /etc/default/bluetooth.  bluetoothd is running.  (It's a MX1000 Dell/Logitech mouse, BTW.)

Do we have any idea what this is? Is there some sort of manual workaround? Any diagnostics we can run?

---

### Post by FuturePilot on 2008-10-27
From what I've heard the Services tab is no longer needed because of the changes with the new bluetooth stack, so that's why that tab went away. I guess the goal here is for everything to "just work" without needing to configure services and stuff.

---

### Post by ^[H3ad-Tr1p]^ on 2008-10-27
> **maschnitz said:**
> Chiming in with a "me too".  It was working before I upgraded to Intrepid, and not working after.

The USB Bluetooth dongle is visible via lsusb (both the HID and HCI versions), and the mouse is visible through hcitool dev.  I've tried installing everything Bluetooth/OBEX related in Synaptic; I've tried disabling HID2HCI in /etc/default/bluetooth.  bluetoothd is running.  (It's a MX1000 Dell/Logitech mouse, BTW.)

Do we have any idea what this is? Is there some sort of manual workaround? Any diagnostics we can run?

is precisely wath was succeded

---

### Post by ^[H3ad-Tr1p]^ on 2008-10-27
> **FuturePilot said:**
> From what I've heard the Services tab is no longer needed because of the changes with the new bluetooth stack, so that's why that tab went away. I guess the goal here is for everything to "just work" without needing to configure services and stuff.

why then,we have the same problem?

---

### Post by mihai.ile on 2008-10-27
They replaced services (being able to send from phone to pc) with a browse device button (take files from the phone with the pc) but it's not the same thing...
My phone for example doesen't grant acces to the photos folder this way (shows as empty) so right now I am unable to have my photos taken with the phone on the pc. How could I solve this?

Well for me "just work" is so automatic that doesen't even work! is it possible to install the old applet?

---

