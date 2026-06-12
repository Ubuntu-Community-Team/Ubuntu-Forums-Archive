---
title: "Bluetooth confusing menu selections"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GeorgeVita on 2009-08-26
Hi, I am testing bluetooth on EeePC 1000H with a GSM phone Sony Ericsson K750i which generally works great (transfers and remote desktop control tested, not teethering as modem).
'Playing' with the various selections (from the bluetooth icon) menus are changing in a confusing manner:

- Boot, checked via Bios setup (F2) that all onboard peripherals are enabled
- Boot 9.10
- Click on Bluetooth icon shows all selections black (can be used) and only the first one gray ('Bluetooth on' as it is already on) > OK
- Click to turn it OFF
- Clicking again to icon shows different selections than initial, and there is no 'turn on' selection. You can get it from 'Preferences'
- From now, as menu shows new selections you cannot turn it off (neither via preferences)

My system is updated dist-upgraded till today. Searching this forum I did not found any  similar note.


Please verify above and provide any idea to check if using wrong versions of Bluetooth manager.

Thanks in advance,
George

---

### Post by meeples on 2009-08-26
i use Blueman much better than gnomebluetooth :D

---

### Post by GeorgeVita on 2009-08-26
Hi **meeples**, thanks for answering!

Main idea when 'testing' is to find what a user of the final release may NOT find. So the question remains:
Do we feel confused using bluetooth manager (default) as menus change completely after first disable of the device?
How can we do an OFF-ON-OFF cycle on the bluetooth peripheral?

G

---

### Post by GeorgeVita on 2009-08-28
This is more a 'malfunction' than a 'bug'.

Reported to: [https://bugs.launchpad.net/bugs/420456](https://bugs.launchpad.net/bugs/420456)

Please follow above link if you can test it and 'affects you'.

Regards,
George

---

### Post by GeorgeVita on 2009-10-07
Solved now! >>> [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/428151](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/428151)

gnome-bluetooth 2.28.1-0ubuntu1
tested on: EeePC 1000H, Sony Ericsson K750 (phone), Sony CMT-HXBT (HiFi)

Menus are OK now.
Bluetooth ON/OFF works as expected.
Connected to: phone only, phone and HiFi, doing single or multi bluetooth tasks

Tasks tested: bluetooth on/off, scan new bluetooth devices (via setup new device), connected to phone, browse/copy from phone to PC, bluetooth 'remote mouse' started, worked from phones joystick, HiFi connected, music playing from PC to HiFi

Also working ALL together: using phone's joystick as mouse to browse phone's directory (from PC screen), starting download, and at the same time listening via bluetooth music playing from PC to HiFi.

G

---

