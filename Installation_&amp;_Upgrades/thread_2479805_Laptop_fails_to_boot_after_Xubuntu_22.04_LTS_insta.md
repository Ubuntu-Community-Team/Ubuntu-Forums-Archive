---
title: "Laptop fails to boot after Xubuntu 22.04 LTS install"
date: 2022-10-08
forum: Installation &amp; Upgrades
---

### Post by peterg84 on 2022-10-08
I have an older HP zbook 15 g2 laptop, with 1TB SSD. I used to have xubuntu 20.04 and Windows 10 dual boot, which worked OK.

I tried to do a clean install of xubuntu 22.04, overwriting my old 20.04 install.

The installation completed, but after a restart I now get the error message that no OS is installed to the hard drive.

The BIOS is EFI compatible, but years ago, I went for the legacy approach.
Once the install broke, I booted into the installer USB stick and installed Boot-Repair and created this report: [https://paste.ubuntu.com/p/rqFR286whX/](https://paste.ubuntu.com/p/rqFR286whX/)

To me this looks good - but my laptop no longer boot, I do not even see GRUB menu starting, I get the error message from the BIOS that there is no OS installed.

Can someone please help?

---

### Post by tea for one on 2022-10-08
Is there a compelling reason to continue with Legacy mode?
Dual booting is easier to manage with UEFI and GPT

Nevertheless, you can see from line 52 in the report that Xubuntu has created an ESP (Efi System Partition), which has probably confused Grub?

You could try to re-install Xubuntu without the ESP.
Make sure that you have data backups (both Windows and Xubuntu)
Boot the 22.04 USB in Legacy mode
Try Ubuntu
Open Gparted
Delete sda6 and sda7
Create _one_ Ext4 partition only
Install the system to this one partition
Install Grub to sda.

A better solution is to install Windows 10 and Xubuntu in UEFI mode with GPT.

---

