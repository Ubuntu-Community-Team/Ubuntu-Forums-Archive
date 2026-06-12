---
title: "Trying to install KUBUNTU 16.04 LTS on HP Pavilion 15"
date: 2018-02-28
forum: Installation &amp; Upgrades
---

### Post by SimpsonTruckDriver on 2018-02-28
I downloaded the ISO for KUBUNTU 16.04 LTS, through Windows 10. This is a brand new system, model 15-cd075nr (touch screen), with 8Gb RAM and AMD A12 processor and AMD graphics. Once I downloaded it, sent to USB, I changed the UEFI Boot to use the USB as first boot, and enabled Virtualization. It boots into the USB card, but gives the error **casper/vmlinuz.efi** not found, then after hitting ENTER, boots fine into Windows 10.

Anything I am missing? I am planning on dual-boot, since I need Windows for possible hardware diagnostics.

Thanks
TS

---

### Post by vasa1 on 2018-02-28
> **SimpsonTruckDriver said:**
> ... Once I downloaded it, sent to USB, ...
What did you do here? Did you follow the procedure described in [Create a bootable USB stick on Windows]("https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.203476818.376786565.1519869275-1846082978.1519869275#0")?

---

### Post by SimpsonTruckDriver on 2018-02-28
Yes, I used RUFUS to create the USB disk, my apologies for not mentioning that part. It was created, I booted from it (UEFI, not Legacy, not sure if that makes a difference), and got that error message.

TS

---

### Post by SimpsonTruckDriver on 2018-03-01
I even tried booting in Legacy (not UEFI) Mode, same error. Even tried with Virtualization disabled, still the same error. I see online that this is a "bug" reported to AskUbuntu, but it was in Ubuntu 12.04, so I don't know if those are outdated, or if Canonical simply left the bug in place 6 years later.

TS

---

### Post by vasa1 on 2018-03-01
> **SimpsonTruckDriver said:**
> I even tried booting in Legacy (not UEFI) Mode, same error. Even tried with Virtualization disabled, still the same error. I see online that this is a "bug" reported to AskUbuntu, but it was in Ubuntu 12.04, so I don't know if those are outdated, or if Canonical simply left the bug in place 6 years later.

TS
Please provide the AsUbuntu link.

If you have another Linux machine, try installing the *mkusb* ppa and then use *mkusb* to make the iso.

---

### Post by SimpsonTruckDriver on 2018-03-01
Actually, I looked and found out it was a bad USB install. I was able to get into the LIVEUSB. I will try it later tomorrow to see if I can get it installed. At least video, WiFi, and touchscreen works. Sound didn't work, possibly because the LIVEUSB doesn't have drivers. Not a big deal for now.

TS

---

### Post by vasa1 on 2018-03-01
> **SimpsonTruckDriver said:**
> Actually, I looked and found out it was a bad USB install. I was able to get into the LIVEUSB. I will try it later tomorrow to see if I can get it installed. At least video, WiFi, and touchscreen works. Sound didn't work, possibly because the LIVEUSB doesn't have drivers. Not a big deal for now.

TS
Sound should work, even with a Live USB.

For which applications doesn't sound work?

---

### Post by SimpsonTruckDriver on 2018-03-02
Just trying to play a generic audio file that came with the KUbuntu install. Windows10 Device Manager shows both AMD HD Audio Device and Realtek HD Audio, same with the playback section of Device Manager (sound works fine in Win10).

TS

---

### Post by SeijiSensei on 2018-03-02
If the machine has multiple audio outputs, you may not have selected the right one.  Go to System Settings > Multimedia and look at how your audio devices are configured.  Make sure you've chosen the correct input and output channels, and that the output stream isn't muted.

---

### Post by SimpsonTruckDriver on 2018-03-11
I was able to get sound going, Wi-Fi and everything works right out of the box. Now to tweak it to the way I want it :)

TS

---

