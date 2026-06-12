---
title: "Linux installation from USB"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by arun_a on 2010-07-19
I am new to Linux. I want to install Kubuntu 10.04 LTS(kubuntu-10.04-dvd-i386.iso) on my Laptop hard disk. My internal DVD drive is not working. The external DVD drive is not supported by BIOS and I am not able to boot from it. I can boot from USB stick. I am able to load Ububtu 9.04(CD version) and other previous versions from it(using unetbootin).After booting, Linux is able to recognize the external DVD drive. My USB stick capacity is 2 GB. The current ISO file is 3.6 GB and wont fit on my USB pen drive.**Is there a way by which I can boot from USB stick and continue Linux installation from External USB DVD drive? **Kindly help.......

---

### Post by oldfred on 2010-07-19
The standard installs are all about 700MB so they fit on CDs. Do you have a DVD install?

[http://www.ubuntu.com/](http://www.ubuntu.com/)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by gansvv on 2010-07-19
Kubuntu has both CD and DVD installation options. Get the 700MB (approx) sized CD installation from here:

[URL="http://www.kubuntu.org/getkubuntu/download"]http://www.kubuntu.org/getkubuntu/download
[/URL]

After installation, you can continue installing other packages (or upgrade) from the web, external DVD drive, HDD, etc.


> **arun_a said:**
> I am new to Linux. I want to install Kubuntu 10.04 LTS(kubuntu-10.04-dvd-i386.iso) on my Laptop hard disk. My internal DVD drive is not working. The external DVD drive is not supported by BIOS and I am not able to boot from it. I can boot from USB stick. I am able to load Ububtu 9.04(CD version) and other previous versions from it(using unetbootin).After booting, Linux is able to recognize the external DVD drive. My USB stick capacity is 2 GB. The current ISO file is 3.6 GB and wont fit on my USB pen drive.**Is there a way by which I can boot from USB stick and continue Linux installation from External USB DVD drive? **Kindly help.......

---

### Post by C.S.Cameron on 2010-07-19
If you had a 4GB USB flash drive you could do a full install to it then boot from it and reinstall grub with the USB hard drive plugged in.
This will give you the option to select either when booting the flash drive.

or you can do a MultiBootUSB install, 
( [http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273) )
and then add your USB hard drive to grub.cfg

This will also give you the option to boot the hard drive.

Edit:
Downloading the 700MB file is probably less hassle.

---

### Post by arun_a on 2010-07-23
Hi .....
 
 
 I downloaded **Gujin boot loader** and with its help I installed Kubuntu 10.04 from external DVD drive.

---

