---
title: "Screwed up the DualBoot (or never had it), only ubuntu loads (no win7 on the list)"
date: 2015-03-31
forum: Installation &amp; Upgrades
---

### Post by oleshkin on 2015-03-31
Hello world! 
I just installed a fresh 14.04 on my Asus 1215B laptop, which had a fresh installation of Win7 HP x64. 
Now after completing the installation, the system booted automatically into Ubuntu. Since I am new to linux, I decided, that this is my journey and I started researching.

Step 1. 
Someone recommended to edit the grub file and change the value of TIMEOUT to XX sec (90 was my choice) and make a ```
sudo apt-update
``` if I am not mistaken. After reboot, I got a black screen, which after a pause gave me the following line:

> Reboot and Select Proper boot Device
After research, I have done the 

Step 2.
booted from live usb, installed ```
boot-info
``` and run it, results were here:
[http://paste.ubuntu.com/10712975/](http://paste.ubuntu.com/10712975/)

I have also done Step 3 and ran the boot-repair, which now gives me a proper OS SELECTION page on boot, but there is only ubuntu on the list.
[http://paste.ubuntu.com/10713036/](http://paste.ubuntu.com/10713036/)

Can anyone please refer me to the proper actions needed to make win7 also appear on the list of GRUB.

---

### Post by yancek on 2015-03-31
The bootinfo output you posted shows windows 7 on the first partition and all the boot files seem to be present so the first thing I would suggest would be to boot Ubuntu, open a terminal and enter the following command: 

>  sudo update-grub


Watch the output to see if there is any mention of windows being found, if so reboot and give it a try.

---

### Post by oldfred on 2015-03-31
You have both Windows & Ubuntu installed in BIOS boot mode on a MBR partitioned drive.
But you also show an efi partition.
And you booted Boot-Repair in UEFI boot mode as it shows efibootmgr -v output.

Best to only boot in BIOS boot mode. You must make sure secure boot is off, and that UEFI mode is off or that CSM/BIOS mode is on.
Often if in UEFI mode with secure boot on, it will not let you boot anything other than a secure boot install. And CSM mode is not a secure boot install.

---

### Post by oldos2er on 2015-03-31
Thread moved to Installation & Upgrades.

---

