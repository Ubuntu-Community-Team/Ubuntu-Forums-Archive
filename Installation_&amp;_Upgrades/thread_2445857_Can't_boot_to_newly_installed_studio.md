---
title: "Can't boot to newly installed studio"
date: 2020-06-20
forum: Installation &amp; Upgrades
---

### Post by ozstar on 2020-06-20
Hi,

I have a Win 10 PC and have been using a USB stick install of studio but now wanted a full blown studio on an SSD to boot from in a dual boot.

I installed studio on the SSD from the USB stick and it showed it installed correctly but after the reboot it does not boot to it.  I have tried with and without the Win 10 primary os disk attached but still no boot to SSD.

I have this image of what is going on and I am not sure why but it shows a drive letter and /target which is where Linux looks to be.

Any ideas what has happened in the install and how to get it back to a good bootable studio, even if I have to do it again.

I see that Win 10 says one can install Linux inside it but not too sure about it, so will go with the separate disk and do a dual boo eventually.

Thanks

---

### Post by oldfred on 2020-06-20
What brand/model system?

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sudodus on 2020-06-21
1. Please provide the details that oldfred asks for.

2. Then tell us (here in this thread) about the hardware: brand name and model of your

- computer
- graphics chip/card
- USB to SATA adapter (or USB to NVME adapter)
- SSD

3. Then I suggest that you test that your computer really can boot from the external USB. Use [mkusb](https://help.ubuntu.com/community/mkusb) to **clone** from the Ubuntu Studio iso file to the external USB drive. The cloning process is very robust, and you know that the computer can boot from your USB stick. So with a cloned system on the SSD, the problem is not the software on the SSD.

4. You can modify and test

- booting in another computer (to check that the SSD can be booted from
- different USB ports
- remove other USB devices, that might confuse the system
- settings in the UEFI/BIOS menu system
- ... there are many more tips in the following links
. [Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB)
. [Flow chart for trouble-shooting](https://askubuntu.com/questions/1190764/why-doesnt-a-bootable-usb-boot/)

5. When you have managed to make that drive boot, it will probably also boot from a persistent live or installed system in the same drive. So now it is time to install the system you want into the SSD.

---

