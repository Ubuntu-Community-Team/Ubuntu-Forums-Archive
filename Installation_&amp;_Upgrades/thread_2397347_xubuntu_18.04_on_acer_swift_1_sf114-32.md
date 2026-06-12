---
title: "xubuntu 18.04 on acer swift 1 sf114-32"
date: 2018-07-28
forum: Installation &amp; Upgrades
---

### Post by maclenin on 2018-07-28
A quick **How-to** install xubuntu 18.04 as the only OS on the lovely acer swift 1 sf114-32

1. Download the .iso
```
[xubuntu-18.04-desktop-amd64.iso]("https://xubuntu.org/")
```
2. Create a bootable usb drive (using mkusb)
```
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
```
3. Insert bootable usb drive into laptop usb port
4. Power on the laptop
5. Laptop should boot straight to xubuntu trial version after a brief pause at the Grub menu
6. Install xubuntu (as the only OS, replacing Windows)
7. Restart the laptop

**Errata:**

*(i) bootable usb drive does not boot*
a. usb drive could be faulty
b. return to step 2. with a different usb drive

*(ii) touchpad freezes after installation*
a. Press ctrl+alt+t to open a termainal via the keyboard
b. Shutdown laptop via the terminal
```
sudo shutdown -h +0
```
c. Power on laptop and press F2 before "acer" appears, to enter the BIOS
d. Navigate to "Main" and toggle the Touchpad from "Advanced" to "Basic"
e. Save and exit the BIOS

Good luck!

---

### Post by demontager on 2019-02-25
I had an issue with touch-pad freezes and disabling advanced touchpad function solved this problem. Thank you. 
I got questing regarding keyboard backlit. Did you try to extend its enabled duration ? For me it is bit irritating seeing like backlit on and off constantly while i do typing. At least i want to keep backlit always on when on AC power.

---

