---
title: "Installing 12.04 from ISO on USB Thumb Drive. Sony VAIO will not boot from thumbdrive"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by graysunlight on 2013-05-12
Pretty new to Linux. Just bought a used Sony Vaio. Dual Core E-450 APU AMD Processor 1.65 ghz, I am unable to find the motherboard or BIOS specs.  I have the Ubuntu 12.04 ISO copied onto a thumb drive and when I attempt to boot to an external device, I get the message "remove disks or other media/press any key to restart" and it boots right back to windows. I have gone into the BIOS and changed the boot order (there are three options: external device, harddrive, and network) so that the external device is the priority. I have also enabled external device boot in the BIOS. On a Sony forum, it said to tap f11 repeatedly during boot to boot to a USB device, which I did with the same message "remove disks or other media/press any key to restart"

Do I need a new version of bios? Any suggestions?

Thanks!

---

### Post by oldfred on 2013-05-13
How old is system? If more than 6 or 7 years it may not boot from a flash drive.
How much RAM? Full Ubuntu needs more RAM and decent video. Older systems work better with Xubuntu or Lubuntu.

Did you install to Flash drive or just copy to flash? You cannot just copy an ISO to a flash drive. Also to verify that download was correct you should do the md5sum.
       
Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

