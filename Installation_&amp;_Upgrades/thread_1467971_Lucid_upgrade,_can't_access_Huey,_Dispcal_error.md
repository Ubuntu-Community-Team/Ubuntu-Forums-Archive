---
title: "Lucid upgrade, can't access Huey, Dispcal error"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by msknight on 2010-05-01
Hi Folks,

Upgraded a 9.10 installation to 10.04 and now, on trying to execute Dispcal I get...
dispcal: Error - new_disprd() failed with 'Instrument Access Failed'


The lights on the Huey flash as if calibration is about to start, but then I get the error.

The Huey is connected as it always has been, via a USB hub. No change there. I have also re-installed the Argyll package. 

A disconnect and reconnect of the Huey prompts this...
May  1 10:37:19 michelle-desktop kernel: [48400.442788] usb 1-4.4.4: USB disconnect, address 6
May  1 10:37:29 michelle-desktop kernel: [48410.220390] usb 1-4.4.4: new low speed USB device using ehci_hcd and address 7
May  1 10:37:29 michelle-desktop kernel: [48410.333312] usb 1-4.4.4: configuration #1 chosen from 1 choice

Reconnecting direct to a USB port on the computer gives this...
May  1 10:38:17 michelle-desktop kernel: [48458.445037] usb 1-4.4.4: USB disconnect, address 7
May  1 10:38:27 michelle-desktop kernel: [48468.401321] usb 6-1: new low speed USB device using ohci_hcd and address 2
May  1 10:38:27 michelle-desktop kernel: [48468.587629] usb 6-1: configuration #1 chosen from 1 choice

... but still the same error.

Any ideas please?

---

### Post by msknight on 2010-05-01
Solved. The -p option has been changed to -P - using the capital P, it works.

---

