---
title: "Bluetooth problems after upgrade"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by Grizzlitiger on 2007-01-13
Hello everyone!

I've got a very serious problem with my bluetooth after upgrading to edgy (I'm studying in a country other than my home country and use my computer to call home) which I need to solve asap.

Before upgrading my bluetooth using bluez-utils and btsco worked perfectly (apart from the problems that windows causes). After upgrading however I can't connect my to my bt headset anymore. The message I get is 

btsco v0.42
Device is 1:0
Error: Failed to connect to SDP server: No route to host
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Host is down


when I try to do a restart of the bluez-utils I get

sudo: /etc/init.d/bluez-utils: command not found

obviously the folder and program names have changed as 

sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services...                                      [ ok ] 

works. However even after restarting the service it doesn't work. 

Maybe some configs have been over-written, I don't. Can anyone help me please?

Cheers

---

