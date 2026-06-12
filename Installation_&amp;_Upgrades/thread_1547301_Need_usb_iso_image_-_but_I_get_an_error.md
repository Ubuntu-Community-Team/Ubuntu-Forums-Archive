---
title: "Need usb iso image - but I get an error"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by dorien on 2010-08-06
Hi,

I need an installation USB for Ubuntu.

I downloaded the ISO.

I only have OpenSuse systems available to create the USB and a 1G stick. 

So: I used 

```
isohybrid /pathtoiso/ubuntusomething.iso
```which gives me the following error:

```
ubuntu-10.04-desktop-i386.iso: bootloader does not have a isolinux.bin hybrid signature.Note that isolinux-debug.bin does not support hybrid booting.
```
I have used this command before successfully with other isos.

I decided to skip the step and dd this to a usb, which of course, was not bootable.

Right now, I am redownloading the iso, perhaps it was a download error. 

Any other suggestions? I don't have any of the suggested os's at my disposal (win, mac, ub)

---

### Post by snowpine on 2010-08-06
I would suggest reading through the documentation as there are several supported methods: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I believe that [Unetbootin]("http://unetbootin.sourceforge.net") is distro-agnostic (i.e. it can be used in OpenSUSE to create an Ubuntu Live USB) and it is also very user-friendly. :)

---

### Post by dorien on 2010-08-06
I tried Unetbootin, but it won't start up. I'll give it another try as soon as the download finishes.

Thanks

---

