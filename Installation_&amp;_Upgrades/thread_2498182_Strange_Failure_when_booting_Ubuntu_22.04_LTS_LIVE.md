---
title: "Strange Failure when booting Ubuntu 22.04 LTS LIVE DVD"
date: 2024-06-03
forum: Installation &amp; Upgrades
---

### Post by cparke on 2024-06-03
Want to install 22.04 LTS [Jammy Jellyfish] Desktop, but of course that normally requires booting the Live DVD to access the installer.

The error I am getting in the log output during boot after about 5 minutes is quite odd:[INDENT]**[FAILED] Failed to start Ubuntu Live CD installer.workd.ally.nel crash signatures....**[/INDENT]

I've gotten this several times, using actual DVD, USB Flash, different DVD drive, etc.  It happened both using UEFI boot of DVD as well as Legacy Mode.  It is only happening on one of my computers; the exact same media is booting into Ubuntu Live just fine on another computer and I've checked the SHA256 of the .ISO as well as the MD5SUMS of the individual files on the DVD/ISO image.

Looking for some clues what the error message is talking about, what I could change in the boot parameters, etc. to get around this issue, or last resort how to boot to console instead and run the Ubuntu installer from the command line?

---

### Post by Rubi1200 on 2024-06-03
What is the make/model of the computer and what are the specifications?

Have you tried starting in safe graphics mode?

If you are trying to install as a dual-boot with Windows, try disabling Fast Start, Secure Boot, TPM etc. in BIOS to see if one of those settings is affecting this.

Do you have Bitlocker enabled on Windows (if relevant)?

---

### Post by cparke on 2024-06-03
> **Rubi1200 said:**
> What is the make/model of the computer and what are the specifications?

Have you tried starting in safe graphics mode?

If you are trying to install as a dual-boot with Windows, try disabling Fast Start, Secure Boot, TPM etc. in BIOS to see if one of those settings is affecting this.

Do you have Bitlocker enabled on Windows (if relevant)?


It is a CyberPower PC with:[INDENT]INTEL CORE PROCESSOR I7-12700K 8P/16 + 4E 3.60GHZ 
ASUS UEFI BIOS
1TB SSD, 2TB HDD
16GB DDR4-3200
NVIDIA GEFORCE RTX 3070
WINDOWS 11
[/INDENT]

Secure Boot is disabled, also no BitLocker.  Have not seen this problem with other distos, including Ubuntu 22.04-based Linux Mint 21.

I have not tried 'nomodeset' or what other boot parameters do you suggest to constitute 'Safe Graphics' to try?

---

### Post by currentshaft on 2024-06-03
Does it happen with Secure Boot enabled?

---

### Post by oldfred on 2024-06-03
Standard Ubuntu is too large for DVD. You would not be able to fully write it.
Ubuntu has been flash drive install based for several LTS versions.

Since you have nVidia, you need safe boot. It should be an option on install menu. Or you can use nomodeset.
But you also need to check or include the install of optional restricted drivers, so nVidia driver is installed as part of install.
After install you could boot recovery mode to terminal & install driver there, but more difficult.

[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview) & 
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by ActionParsnip on 2024-06-03
using USB rather than optical media will be quicker and allow you to write the entire ISO to the storage.

---

### Post by cparke on 2024-06-03
> **oldfred said:**
> Standard Ubuntu is too large for DVD. You would not be able to fully write it.
Ubuntu has been flash drive install based for several LTS versions.

Since you have nVidia, you need safe boot. It should be an option on install menu. Or you can use nomodeset.
Ubuntu desktop still fits on a dual-layer DVD, but given that the ISO  image has increased by 1GB (to 6GB) between 22.04 LTS and 24.04 LTS,  those days may be ending in the next few years.  USB boot  (which uses the USB controller and a generic interface) is not exactly the same as Optical drive boot (which uses the specialized SATA storage controller), it is more like a retrofit.

Why did you say that Nvidia video card mandates use of safe boot?  

I'm  told the boot did finally work with '**nomodetest**' added, but the error  message without it was quite cryptic and it did not look like a graphics card  caused it. So that's apparently the simple resolution here.

---

