---
title: "mouse bluetooth  intrepid ibex on my laptop"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ^[H3ad-Tr1p]^ on 2008-10-26
hi friends

I had installed intrepid ibex on my laptop and now I have to use my mouse bluetooth 

the strange thing is that the first time I have booted up my intrepid,only with the service icon bluetooth next to the time applet,I had connected my mouse,then I have upgrading my distribution and now I don't get to connect my mouse anymore

so I have followed this guide [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

I have found my mice device with hcitool scan

then I have to connect it but when I type 

  sudo hidd --connect aa:bb:cc:dd:ee:ff

I get thet hidd not found


then I had saw thet in this guide tell us thet if you want have devices connected at start up we must to edit /etc/default/bluetooth and look some line like  HIDD_ENABLED=0

but in my configuration file I can see thet this voice isn't exist

in my /etc/default/bluetooth I can find:

HID2HCI_ENABLED=1
HID2HCI_UNDO=1

so I think that in intrepid something was changed

how can I connect the mouse?

thanks a lot and sorry for my bad English

---

### Post by NilsE on 2008-10-26
It actually changed in Hardy but the way to associate and activate the mouse is to either single click the BT icon and select add a new device and go through those steps or right click and select preferences and use the + button on the first panel.  You may have to turn the mouse on and off a couple of times or hit the reset/connect button on the mouse to get BT to find it.

---

