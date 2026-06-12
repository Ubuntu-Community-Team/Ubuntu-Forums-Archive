---
title: "Got no sound or usb is this virtualbox or intrepid"
date: 2008-06-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-06-10
Got the Guest additions installed correctly, got normal screen res.

Volume control got a red x.

open Vol Control gives.
No volume control GStreamer plugins and/or devices found

---

### Post by forestpixie on 2008-06-10
Have you got audio enabled in settings - I use pulseaudio and it works ok

---

### Post by philinux on 2008-06-10
lsusb reports nothing
lspci does not show sound card.

Must be virtualbox

---

### Post by forestpixie on 2008-06-10
You have to enable it in vbox before you start the guest. If you have - then I'm not sure without digging, I have never had a problem with sound in it.

---

### Post by philinux on 2008-06-10
Thanks now got audio. Learning some new stuff today.

Usb says unkown device.

I've deleted the guest and gonna wait till Thursday for the alpha then try again.

---

### Post by zorkerz on 2008-09-29
What did you do to fix it?

---

### Post by zorkerz on 2008-09-29
I have been able to get some sound improvements through the guest machine settings in virtualbox. In the audio section I have changed the Host Audio Driver to anything except Null Audio Driver. This allows the starting sound to play nicely but sound in videos is horrendous. It does not seem to change no matter which host Audio Driver I select other than Null and none of the sound settings within the guest machine have made much of a difference either.

---

