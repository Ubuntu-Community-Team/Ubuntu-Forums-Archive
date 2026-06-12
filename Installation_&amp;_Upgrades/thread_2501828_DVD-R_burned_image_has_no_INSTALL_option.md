---
title: "DVD-R burned image has no INSTALL option"
date: 2024-10-22
forum: Installation &amp; Upgrades
---

### Post by eegmanz on 2024-10-22
Trying to install 24.04.1 from a DVD. Is there a way to start installation without booting into painfully slow and DVD intense "try before install" live desktop? 
This is an older Dell with disabled Secure boot, booting into legacy mode. No dual OS booting. I want to start installation right away without enduring half an hour of DVD carnage.

PS I am aware of USB boot option, I am looking for a way to have the same installation routine from a DVD.

Thanks
eeg

---

### Post by yancek on 2024-10-22
How old is this computer?   If your hardware is 10+ years old, you might be better off using a lighter version of Ubuntu or Linux.  Ubuntu derivatives like Lubuntu, Xubuntu or Bodhi come to mind but there are others and other Linux systems which might be better.

System requirements are listed at the Ubuntu site at the link below.

[https://ubuntu.com/download/desktop#system-requirements-NobleNumbat](https://ubuntu.com/download/desktop#system-requirements-NobleNumbat)

---

### Post by eegmanz on 2024-10-22
The PC is well within reqs, that's not the problem. i7, 16G ram, 1TB SSD, etc.

---

### Post by grahammechanical on 2024-10-22
I am surprised that you had a DVD-ROM large enough to hold the present Ubuntu ISO Image (24.04.1)

In the past the ISO image would load into system memory and run from there. We got a TRY/INSTALL option early on. I think that today the ISO image is too large to run in system memory. My machine has 16 GB system memory. During a recent install of 24.04 on to an eternal SATA drive almost 4 GB of system memory was being used as cache memory. The installer was running from USB memory and transferring data into cache memory as it uploaded data from the internet and then transferred it on to the SATA drive. The install took a long time. Imagine the difficulty if system memory was only 4 GB RAM. 

Not only does Ubuntu have a different installer compared to the past but it examines the hardware before we get the TRY/INSTALL screen. If we select TRY we get a working Ubuntu live session. In the old days the examination of hardware was still going on as we made the selection.

This is the experience even if we only want to install the default selection of just the essentials. So, the answer to your questions is NO.

There is also a new option aimed at corporate users. Automated Installation - for advanced users who have an autoinstall yaml for constant and repeatable system setups. This may also have a part in why changes to the installation process have been made. Such an autoinstall method would load the system setup from a computer on the corporate network and not only from the Ubuntu ISO image.

Regards

---

### Post by yancek on 2024-10-22
>  The PC is well within reqs, that's not the problem. i7, 16G ram, 1TB SSD, etc. 				

And in your initial post you referred to it as "an older Dell" which of course is very vague.

If you had a Linux OS on the computer with the Grub bootloader, you would not need a USB or a DVD, you could just boot the installed iso.  A DVD will be slower than a USB and slower still than running from a HD.  Good luck with the DVD

---

### Post by ne29914 on 2024-10-22
How on earth did you get a 5.8 GB install image onto a 4.7 GB DVD?
And no, there's no way around spending 45 min. installing from the DVD (except USB-stick, which will take around 15 min.).

---

### Post by yancek on 2024-10-23
>  How on earth did you get a 5.8 GB install image onto a 4.7 GB DVD?

Dual layer DVD's are 8.5GB but booting from a USB or HD is a much better option.

[https://www.bandcds.co.uk/faqs/dual-layer-dvds/](https://www.bandcds.co.uk/faqs/dual-layer-dvds/)

---

### Post by eegmanz on 2024-10-23
Dual layer DVD-R is 8.5G, no problem fitting on full ISO. 16GB ram should be enough to cache whatever installer needs to get running without booting into the full system (about 30 minutes later) just to present INSTALL NOW option (now that memory is already loaded with the entire system). 

24.04.1 installs fine from USB, just wondering why is there no option to do so straight from DVDR (it's the very same ISO image burned to DVDR instead of unpacked to USB drive) considering that most tutorials are showing INSTALL UBUNTU option. 

Here is tutorial showing this option

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#2-boot-from-dvd](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#2-boot-from-dvd)

[IMG]https://ubuntucommunity.s3.us-east-2.amazonaws.com/original/2X/5/5be2cc3620044ff4f6b1f88279accee82efff83d.png[/IMG]

---

### Post by eegmanz on 2024-10-23
It is an older Dell manufactured in 2012. The problem is not slow DVD (yeah it is pain in ass)  but lack of INSTALL UBUNTU without booting into the desktop

This is from Ubutnu page

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#2-boot-from-dvd](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#2-boot-from-dvd)

[IMG]https://ubuntucommunity.s3.us-east-2.amazonaws.com/original/2X/5/5be2cc3620044ff4f6b1f88279accee82efff83d.png[/IMG]



> **yancek said:**
> And in your initial post you referred to it as "an older Dell" which of course is very vague.

If you had a Linux OS on the computer with the Grub bootloader, you would not need a USB or a DVD, you could just boot the installed iso.  A DVD will be slower than a USB and slower still than running from a HD.  Good luck with the DVD

---

### Post by eegmanz on 2024-10-23
> **ne29914 said:**
> How on earth did you get a 5.8 GB install image onto a 4.7 GB DVD?
And no, there's no way around spending 45 min. installing from the DVD (except USB-stick, which will take around 15 min.).

You are missing the point, the problem is not 45minutes install, but 45 minutes booting into full desktop THEN followed by another 45 minutes of installing. 

This is what you are supposed to see (but not) when booting from DVD. 

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#2-boot-from-dvd](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#2-boot-from-dvd)

---

### Post by grahammechanical on 2024-10-23
You are showing images from the old days when Ubuntu was installed from a DVD-ROM. Ubuntu has changed. The install process has changed. The install guide has been re-written.

> Once the installer has initialised you will be invited to choose your language
That initialisation takes place while the message "preparing Ubuntu" is on the screen.

There are different images in the up to date install guide.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive](https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive)

You will not see the images that you have placed in this thread unless you are installing a version of Ubuntu that is many years out of life.

Regards

---

