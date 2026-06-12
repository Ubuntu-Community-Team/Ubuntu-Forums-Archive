---
title: "Installer finds harddisk but BIOS doesn't detect"
date: 2017-02-22
forum: Installation &amp; Upgrades
---

### Post by hvn2 on 2017-02-22
Hi,

I replaced a 320 GB laptop harddisk, didn't check for BIOS and just went on to install Lubuntu which went fine. After this, I reboot and the laptop asks for bootable medium. I check the BIOS which shows no harddisk. Back to Lubuntu installation, check for harddisk: shows /dev/sda 320 GB is installed with Lubuntu 14.04. Reboot again, same story: asks for bootable medium, BIOS shows no harddisk. Anyone a clue what's going on? Thanks.

hvn

---

### Post by oldfred on 2017-02-22
BIOS/UEFI may have two places/tabs.
One is the list of drives, and another is list of bootable devices.

You could not install if list of drives shows no drive. As UEFI/BIOS copies hardware system configuration to hard drive for operating system to use. And then operating system can only see drives UEFI/BIOS sees.

What brand/model system? And what video card/chip?

Is install UEFI or BIOS?

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Bucky Ball on 2017-02-22
Any reason you went for 14.04 LTS, supported until the middle of this year, rather than Lubuntu 16.04 LTS, supported til 2019? Anyhow, try with Boot Repair. There is a link at the bottom of this post (in signature, first line, last link in red). Don't go the 'Recommended Repair'. Go to I think Advanced and install grub to sda. NOT sda1 or any other number; just sda. 

Reboot. If you've only just installed, perhaps you could just reinstall instead and have a closer inspection during the process this time to see what might have happened.

Good luck. ;)

---

### Post by hvn2 on 2017-02-22
It is a 5 year old laptop, BIOS only. When the old harddisk is installed, it is detected. It's a custom-built laptop which has run fine, until the old harddisk started showing serious read errors. Not sure about the video card (it's on a different location).

---

### Post by hvn2 on 2017-02-22
I went for 14.04 since any boot medium (USB stick/CD) with 16.06 refused to boot. And 14.04 is easily upgraded to 16.04. Thank you for the link.

---

