---
title: "logitec 5000 web cam not found after Hardy update"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by myotis on 2008-06-22
Skype and camera plus sound working with Gutsy before update.

The sound (mic built into the camera is working fine)

When I now test the webcam with Skype, Skype simply shuts down.

I have updated to latest version of Skype but it hasn't helped.

The address of the camera in Skype is 

uvc Camera (046d:08ce)(/dev/video0)

Opening camorama give me an error:

Could not connect video device (/dev/video0) please check connection

var/log/messages gives me this

Jun 22 12:11:02 Antec-Linux kernel: [13353.973081] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Jun 22 12:27:42 Antec-Linux kernel: [14352.245230] usb 5-1: USB disconnect, address 2
Jun 22 12:27:49 Antec-Linux kernel: [14359.023933] usb 5-1: new high speed USB device using ehci_hcd and address 6
Jun 22 12:27:49 Antec-Linux kernel: [14359.288532] usb 5-1: configuration #1 chosen from 1 choice
Jun 22 12:27:49 Antec-Linux kernel: [14359.288730] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)
Jun 22 12:27:50 Antec-Linux pulseaudio[6419]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
Jun 22 12:27:50 Antec-Linux pulseaudio[6419]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.

Any one any suggestions where I start with this.

Many thanks.

Graham

---

