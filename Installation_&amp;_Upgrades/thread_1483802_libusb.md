---
title: "libusb"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by sumfarty1 on 2010-05-15
I am having trouble installing a program onto my atmega128 microcontroller using a usbtinyisp. It seems that the problem might be with my linux usb support. when I try to make install, an error pops up saying no usb sopport found, reinstall with libusb installed. I have tried to install libusb up to version 0.1.12 and I am pretty sure it did not install properly, and when I think its installed, the error remains, why is it giving me this error?

I am a novice linux user and anything will help...

HER IS THE ERROR


make install
sudo avrdude -p m128 -c usbtiny -V -E noreset -Uflash:w:adc_test.hex
avrdude: WARNING: -E option not supported by this programmer type
avrdude: error: no usb support. Please compile again with libusb installed.
avrdude: programmer operation not supported

avrdude done.  Thank you.

---

