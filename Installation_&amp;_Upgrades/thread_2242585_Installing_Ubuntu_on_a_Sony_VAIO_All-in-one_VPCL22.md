---
title: "Installing Ubuntu on a Sony VAIO All-in-one VPCL22 computer"
date: 2014-09-02
forum: Installation &amp; Upgrades
---

### Post by machine-claudius on 2014-09-02
I am currently using Windows 7. I would prefer to run Ubuntu on this computer. I have just searched the Web for any experience in installing Ubuntu on this Sony VAIO All-in-one VPCL22 device. I get no hits at all. Has anyone had any experience intalling Ubuntu on this device?

Feedback would be appreciated.

---

### Post by Dennis N on 2014-09-02
Trying a live media version of Ubuntu before installing should give you a good idea of what to expect.

---

### Post by rtb on 2014-12-25
I successfully installed 64 bit Xubuntu 14.04.1 on an older Sony Vaio all-in-one I recently inherited.  This is the thread Google offers when I search "sony vaio all-in-one ubuntu."  It is relatively recent; I'll drop a note here even if it does not help the original poster much.

In my case, the secret was to install from DVD not USB.  The BIOS acted like it would boot from USB, but it never succeeded.  It took far too long for me to fiigure out the obvious solution was to do it the old fashioned way.  (The error message with USB was along these lines: "isolinux.bin missing or corrupt; operating system not found".  The bootable USB worked fine elsewhere.  This may just be due to the age of the machine.)

Everything I cared about came up working: display, keyboard, mouse, sound, network.  I did have to flip a "WLAN" switch in the back before network worked.  For some strange reason it worked in Windows Vista with the switch off; I have no idea why.  The machine appears to have a camera attached.  That doesn't work, but I didn't spend any time with it because I don't need it.

The model was labeled PCG-252L on the sticker.  The BIOS called it VGC-LS25E, though, and that is the model number Sony's website recognized when I searched for BIOS upgrades and manuals.  The specs are what you would expect from an older machine: Core 2 Duo, 2 GB RAM, 250 GB hard drive.  Performance is better than my five-year old netbook and not as good as my Acer C720 Chromebook running Xubuntu 14.10.  That assessment is based on a brief visit to Youtube.

---

