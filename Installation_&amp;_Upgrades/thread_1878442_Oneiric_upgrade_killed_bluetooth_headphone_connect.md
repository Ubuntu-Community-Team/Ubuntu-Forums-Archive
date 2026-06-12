---
title: "Oneiric upgrade killed bluetooth headphone connection"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by DrJohn999 on 2011-11-09
Nokia BH-905i bluetooth phones used to connect and work with Asus 1215-n & IOGear GBU-421 USB Bluetooth adapter. Now after otherwise successful upgrade to 11.10, the headphone connection won't stick.

The phones work corded; the BT adapter works fine with my mouse. The device profiles carried over from 11.04, so I deleted them and started over. BT will detect and pair with the headphones, sort of, but then just drops and/or the phones don't show up in Sound Settings. Anyone else seen this? Any suggestions / solutions?

---

### Post by DrJohn999 on 2011-11-09
No sooner spoken... While writing the original post, I removed the bluetooth adapter to get the model number. Plugged it back in, and then 10 mins later decided to just try connecting to the phones again. What do you know, now they work... So, solved I guess, but I don't really know what went wrong.

FWIW, the sound is better when jacked into the laptop directly. Yes, I'm running the A2DP profile, and yes, it's really really bad using the default telephony profile. Used to be the sound quality on BT was about the same as with a wire, so something is different.

---

### Post by TheGermanBaron on 2012-03-30
I have the same problem, removing and re-adding does not solve the problem.  After some - seemingly random - amount of time, the connection just drops out, in dmesg there are many lines such as these:


[110263.116223] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[110263.116226] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[110263.116229] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1536
[110263.116232] hci_scodata_packet: hci0 SCO packet for unknown connection handle 48
[110263.116235] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0

and 

[111692.323868] btusb_bulk_complete: hci0 corrupted ACL packet
[111692.323886] hci_acldata_packet: hci0 ACL packet for unknown connection handle 0
[111694.112177] hci_cmd_timer: hci0 command tx timeout
[111695.112428] hci_cmd_timer: hci0 command tx timeout
[111696.116031] hci_cmd_timer: hci0 command tx timeout
[111697.116060] hci_cmd_timer: hci0 command tx timeout
[111697.880584] usb 5-1: USB disconnect, device number 21
[111697.880951] btusb_intr_complete: hci0 urb eece8280 failed to resubmit (19)
[111697.880969] btusb_bulk_complete: hci0 urb eece8500 failed to resubmit (19)
[111697.881961] btusb_bulk_complete: hci0 urb eece8a80 failed to resubmit (19)
[111697.882045] btusb_send_frame: hci0 urb c7e57e80 submission failed
[111697.887079] __set_isoc_interface: hci0 setting interface failed (19)
[111698.376440] usb 5-1: new full speed USB device number 22 using uhci_hcd



When it drops out, in blueman the green column goes away.  Disconnecting, sometimes twice, then reconnecting reestablishes the link.

It appears that the connection drops out due to unhandled data.

Any help or suggestions on how to triage the problem better is much appreciated.

---

