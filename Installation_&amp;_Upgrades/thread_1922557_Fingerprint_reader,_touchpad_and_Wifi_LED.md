---
title: "Fingerprint reader, touchpad and Wifi LED"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by martin11ph on 2012-02-09
These are the only things that are stopping me from using Ubuntu permanently. Anyone have any idea how to resolve these things?

Laptop: HP dv7-4190us
OS: Dual boot Windows 7/Ubuntu 11.10 64-bit

1. Fingerprint reader - My laptop uses the HP SimplePass software. I want it to store passwords and auto-login using scanning.

2. Touchpad - I can't turn off the touchpad by double-tapping the LED at the upper left corner of the touchpad.

3. Wifi LED - Doesn't show if it is on(white) or off(red). Its stuck at off.

Hope someone has had similar experience with this. My main concern is the touchpad as I keep brushing it when I am typing. I have disabled clicking on the Mouse and Touchpad menu but it can still move accidentally while typing.

---

### Post by Firezap on 2012-02-09
A good place to start would be to type```
lsusb
``` in terminal. This will tell us your detected input devices. You can use this to see if your fingerprint reader is detected.:)
Hopefully it is.

---

### Post by martin11ph on 2012-02-09
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 1b1a:0000  
Bus 002 Device 004: ID 138a:0005 Validity Sensors, Inc. VFS301 Fingerprint Reader
Bus 002 Device 005: ID 0408:03b2 Quanta Computer, Inc. HP Webcam

I totally forgot about the webcam. Anyway, I rarely use it. Nice, it found the fingerprint reader.

---

### Post by raja.genupula on 2012-02-09
[http://www.thinkwiki.org/wiki/How_to_enable_the_integrated_fingerprint_reader](http://www.thinkwiki.org/wiki/How_to_enable_the_integrated_fingerprint_reader)

---

### Post by martin11ph on 2012-02-13
Thank you. I will give it a try and update later.

---

### Post by raja.genupula on 2012-02-13
> **warii said:**
> <snip>

didnt get your message , could you explain it please .

---

### Post by martin11ph on 2012-02-13
That is a portion of my second reply. I don't know why he copied it.

---

### Post by raja.genupula on 2012-02-13
> **martin11ph said:**
> That is a portion of my second reply. I don't know why he copied it.

hmmm ok i got , i will do the remaining job .

what about your issue ?

---

### Post by coffeecat on 2012-02-13
> **raja.genupula said:**
> didnt get your message , could you explain it please .

> **martin11ph said:**
> That is a portion of my second reply. I don't know why he copied it.

It was a spam post with a hidden link. It has been dealt with.

---

### Post by martin11ph on 2012-02-14
@coffeecat, Ok cool.

@raja.genupula, Since the two others don't seem to be updated, my only choice was Fingerprint GUI. 

My device is 138a:0005 and the supported one is 138a:0001. In any case, I tried installing it. I successfully installed the program but it cannot detect my fingerprint reader. :(

Edit: Used this for the touchpad, [http://www.alonon.net/how-to-disable-enable-touchpad-in-ubuntu-11-10](http://www.alonon.net/how-to-disable-enable-touchpad-in-ubuntu-11-10) 
All that's left is the fingerprint and WiFi LED.

---

### Post by martin11ph on 2012-02-23
Bump. Hope someone can help.

---

