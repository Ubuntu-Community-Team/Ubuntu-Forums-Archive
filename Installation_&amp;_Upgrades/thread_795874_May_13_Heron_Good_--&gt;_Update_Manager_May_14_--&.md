---
title: "May 13 Heron Good --&gt; Update Manager May 14 --&gt; Bluetooth Mouse Bad :-("
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by x86_64 on 2008-05-15
UPDATE:  This turned out to be a Lenovo T61 issue, not a Hardy issue -- it just coincidentally happened at the same time as I'd updated Hardy...

Fyi for any other Lenovo T61 users, the issue was that somehow the physical wireless on/off switch (on the front left of the laptop) was failing to turn Bluetooth back on (WiFi *was* getting turned back on but not Bluetooth even though it's supposed to turn all "wireless" on/off simultaneously)... to fix this I needed to hit Fn-F5 (a few times because initially things were out of sync, i.e., hitting Fn-F5 once would then enable Bluetooth but disable WiFi, etc. but eventually all went back in sync)  I then needed to re-join my Bluetooth mouse and all is good.  Apologies for the Hardy update libel ;-)  Though my observation about Hardy hibernation failing miserably still holds ;-)

Here is the original post:


Bluetooth mouse has worked perfectly with Gutsy forever...

Upgraded recently to Hardy and also working perfectly but then applied all Update Manager updates on May 14 and lost my bluetooth mouse :-(

Hardware = Lenovo T61

Anyone else have this happen to them?

Note that I also tried to hibernate Heron for the first time on May 14 and this failed miserably with garbage written to screen and system hang upon awaken... maybe this is the culprit?

$ sudo /usr/sbin/hcid -x -s -n -d
hcid[8023]: Bluetooth HCI daemon
hcid[8023]: Enabling debug information
hcid[8023]: Starting SDP server
hcid[8023]: Adding rec : 0x646e70
hcid[8023]: with handle : 0x1
hcid[8023]: Adding rec : 0x646dd0
hcid[8023]: with handle : 0x0
hcid[8023]: Service classes 0x00
hcid[8023]: Created local server at unix:abstract=/var/run/dbus-BUew6B31qe,guid=3d7f942f554564b229cb9796482ce566
hcid[8023]: Registering service object: ident=network, name=Network service (/org/bluez/service_network)
hcid[8023]: Registering service object: ident=input, name=Input service (/org/bluez/service_input)
hcid[8023]: /usr/lib/bluetooth/bluetoothd-service-input executed with PID 8024
hcid[8023]: Registering service object: ident=serial, name=Serial service (/org/bluez/service_serial)
hcid[8023]: Registering service object: ident=audio, name=Audio service (/org/bluez/service_audio)
input[8024]: Bluetooth Input daemon
audio[8025]: Bluetooth Audio daemon
input[8024]: Registered input manager path:/org/bluez/input
input[8024]: Created input device: /org/bluez/input/pointing0
[COLOR="Red"]input[8024]: Failed to listen on control channel[/COLOR]
hcid[8023]: /usr/lib/bluetooth/bluetoothd-service-audio executed with PID 8025
audio[8025]: Can't bind unix socket: Address already in use (98)
audio[8025]: Unable to setup unix socket
hcid[8023]: Child PID 8024 got the unique bus name :1.210
hcid[8023]: name_listener_add(:1.210)
hcid[8023]: Sending GetConnectionUnixProcessID failed: Could not get PID of name ':1.211': no such name
hcid[8023]: Could not get PID of :1.211
hcid[8023]: Got NameOwnerChanged signal for :1.211 which has no listeners
hcid[8023]: Audio service (audio) exited with status 1

---

