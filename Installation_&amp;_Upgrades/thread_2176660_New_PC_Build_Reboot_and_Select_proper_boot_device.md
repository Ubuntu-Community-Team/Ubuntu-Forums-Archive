---
title: "New PC Build Reboot and Select proper boot device"
date: 2013-09-25
forum: Installation &amp; Upgrades
---

### Post by don14 on 2013-09-25
Hello. i've googled this to death but I just built my first pc, biostar ta970 AMD  mother board, seagate 1 tb hard hard drive, samsung dvd drive, 8 gigs memory, 600watt power supply. I finally have it powering up and have tried all the solutions I've read online, making sure the dvd drive boots first, making sure cables are connected, drive spins, burned 2 copies of ubuntu, 1 - 12 and 1- 13. Still getting the error "Reboot and select the proper boot device."  The hard drive is brand new, no os installed. Wanted to avoid buying windows (I'm a mac guy, this is for my son).  

I see the hard drive and dvd drive in the bios, I assume that they must be working, I know they may be faulty, both are brand new. Dvd spins and just get the same error over, and over. Been at this for hours.  Even downloaded ubuntu to a flash drive but it seems that I would need some kind of installer, I'm new at this so I'm not familiar with all the lingo.

Any suggestions on something I might be missing?  

Thank you in advance :)

---

### Post by Pedro_Matias on 2013-09-25
Try to install using an USB stick. Like you said you are mac guy here you have step by step what you have to do to create a bootable usb stick [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

---

### Post by Pedro_Matias on 2013-09-25
After that boot from the USB and you should be able to install Ubuntu with no problems ;)

---

### Post by oldfred on 2013-09-25
Is this now a UEFI system? You may need to change some settings in UEFI/BIOS.
Do you want to install in UEFI mode or BIOS mode.
See the lot of links on UEFI in the link in my signature.

Default boot may still be hard drive. You need to select DVD or Flash drive. 
Then is downloaded ISO good 64 bit version? Must be 64 bit for new UEFI type systems.
And correctly installed to flash drive or DVD?

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by don14 on 2013-09-25
Holy BLEEP! That was easier than I thought. Pedro, you rock! Installing Ubuntu now. I wish I would have came here yesterday.

---

