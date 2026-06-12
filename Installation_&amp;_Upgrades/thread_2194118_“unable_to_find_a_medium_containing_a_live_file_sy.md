---
title: "“unable to find a medium containing a live file system” error"
date: 2013-12-16
forum: Installation &amp; Upgrades
---

### Post by yaru22 on 2013-12-16
I'm currently using Ubuntu 12.04 32bit but since I increased my RAM, I wanted to upgrade it to 64bit.

I downloaded Ubuntu 12.04 64bit iso (**ubuntu-13.04-desktop-amd64.iso**) file and created a bootable USB. **I checked that md5 checksum is correct.**

While it boots up from USB (**I put it in usb 2.0 socket**), it spits out an error message saying "unable to find a medium containing a live file system" and dropped to busybox.

My computer spec is as follows:

- Intel Core 2 Quad Q6600 2.4ghz (supports 64 bit)
- ASUS p5kpl-vm motherboard
- Western Digital WD Black WD1002FAEX 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5
- NVIDIA GeForce GT 520
- 2 x Mushkin Enhanced 4GB (2 x 2GB) 240-Pin DDR2 SDRAM = 8gb RAM (this is the reason I'd like to upgrade from 32 bit Ubuntu to 64 bit)

I tried putting the usb stick to different sockets and upgrading the BIOS to the most recent version.

I tried to check my BIOS setting to see if my SATA type is ACHI as opposed to IDE. However, I didn't see any option in my BIOS. The closest thing I came across in my BIOS setting is:

Main -> IDE Configuration:
ATA/IDE Configuration = [Enhanced]
  Enhanced Mode Support On [S-ATA]

Not sure what else to check for.

If anyone has an insight on this issue, please help. Thanks!

---

### Post by sudodus on 2013-12-16
Some tips:

1. How did you install the current Ubuntu system? Try the same method :-)

2. Check if the USB device (stick, pendrive) is bootable in another computer

3. Try another USB device

4. Try another method to transfer the system from the iso file to the pendrive. ***Unetbootin*** and ***mkusb*** (cloning) have high rates of success.

Find more tips at this link [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by yaru22 on 2013-12-16
1. How did you install the current Ubuntu system? Try the same method 

  **Of course I tried the same method. =) That's why I'm puzzled. 32 bit OS installs fine whereas 64 bit OS doesn't.**

2. Check if the USB device (stick, pendrive) is bootable in another computer

  **The USB device is bootable in my other desktop.**

3. Try another USB device

  **I tried with two other USB devices.**

4. Try another method to transfer the system from the iso file to the pendrive. Unetbootin and mkusb (cloning) have high rates of success.

  **I used Ubuntu's startup disk creator as well as unetbootin**

Any other suggestions?

---

### Post by sudodus on 2013-12-17
> **yaru22 said:**
> I'm currently using Ubuntu 12.04 32bit but since I increased my RAM, I wanted to upgrade it to 64bit.

I downloaded Ubuntu 12.04 64bit iso (**ubuntu-13.04-desktop-amd64.iso**) file and created a bootable USB. **I checked that md5 checksum is correct.**

While it boots up from USB (**I put it in usb 2.0 socket**), it spits out an error message saying "unable to find a medium containing a live file system" and dropped to busybox.

Which versions (with 64-bits) did you try? These are available

- ***12.04.3 LTS*** (end of life April 2017)
- 13.04 (end of life soon, January 2014)
- ***13.10*** (end of life July 2014)

I would recommend 12.04.3 LTS and 13.10. The kernel and hardware drivers are different, so it is worth trying both of them.
> 
My computer spec is as follows:

- Intel Core 2 Quad Q6600 2.4ghz (supports 64 bit)
- ASUS p5kpl-vm motherboard
- Western Digital WD Black WD1002FAEX 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5
- NVIDIA GeForce GT 520
- 2 x Mushkin Enhanced 4GB (2 x 2GB) 240-Pin DDR2 SDRAM = 8gb RAM (this is the reason I'd like to upgrade from 32 bit Ubuntu to 64 bit)

I tried putting the usb stick to different sockets and upgrading the BIOS to the most recent version.

I tried to check my BIOS setting to see if my SATA type is ACHI as opposed to IDE. However, I didn't see any option in my BIOS. The closest thing I came across in my BIOS setting is:

Main -> IDE Configuration:
ATA/IDE Configuration = [Enhanced]
  Enhanced Mode Support On [S-ATA]

Not sure what else to check for.

If anyone has an insight on this issue, please help. Thanks!

> **yaru22 said:**
> 1. How did you install the current Ubuntu system? Try the same method 

  **Of course I tried the same method. =) That's why I'm puzzled. 32 bit OS installs fine whereas 64 bit OS doesn't.**

2. Check if the USB device (stick, pendrive) is bootable in another computer

  **The USB device is bootable in my other desktop.**

3. Try another USB device

  **I tried with two other USB devices.**

4. Try another method to transfer the system from the iso file to the pendrive. Unetbootin and mkusb (cloning) have high rates of success.

  **I used Ubuntu's startup disk creator as well as unetbootin**

Any other suggestions?

You have done a good job so far, sorting out a lot of alternatives.

Maybe your nvidia card needs a boot option with the 64-bit version to work. Start with ***nomodeset*** and then install a proprietary driver. See this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

