---
title: "New system install"
date: 2023-08-22
forum: Installation &amp; Upgrades
---

### Post by gymbo2 on 2023-08-22
I have an old Windows PC that has 1 drive bay, I'm replacing the HDD with an SSD. How do I get Ubuntu onto this drive?

---

### Post by oldfred on 2023-08-22
How old?
What brand/model? What video card/chip?

If over 10 years old or a lightweight system with limited RAM memory, you probably need a BIOS install using a lightweight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

If after Windows 8 released in 2012, hardware will be UEFI as Microsoft required UEFI boot with gpt partitioning.
Note that many vendors even now, call UEFI as BIOS. Those systems can be installed in UEFI or old BIOS/Legacy/CSM boot mode.
How you choose to boot install media/flash drive, is then how it installs. Boot menu should have two options one clearly UEFI:xxx and one xxx which is the BIOS mode.

Systems starting in 2020 may be UEFI only. 

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Typical screens you see during install from USB flash to to your hard drive.
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

See link in my signature below, but it also includes a lot of additional technical info, you probably do not need.

---

### Post by gymbo2 on 2023-08-22
The system is only 5 years old.

I guess what you are saying is to run Ubuntu from a flash drive, then install it on to the new hard drive, sounds easy enough.

Is that correct?

---

### Post by ne29914 on 2023-08-22
> **gymbo2 said:**
> The system is only 5 years old.

I guess what you are saying is to run Ubuntu from a flash drive, then install it on to the new hard drive, sounds easy enough.

Is that correct?

Almost. You need to _boot_ Ubuntu from a USB drive, not just run it.

---

### Post by gymbo2 on 2023-08-22
Yep, it worked like a charm.

---

