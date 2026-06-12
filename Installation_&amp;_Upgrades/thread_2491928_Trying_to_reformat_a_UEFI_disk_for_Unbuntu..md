---
title: "Trying to reformat a UEFI disk for Unbuntu."
date: 2023-10-25
forum: Installation &amp; Upgrades
---

### Post by rick-price on 2023-10-25
In trying to take my daughter's laptop from Win11 to Ubuntu, the UEFI apparently got clobbered.  Now we get the no drive found message.

My goal is Ubuntu only on the laptop.  I would prefer not having to deal with UEFI unless I have to.  We don't have a bit locker key and Microsoft says they don't have it either.  There is nothingon the drive we need to save.

Any help appreciated.

---

### Post by ubfan1 on 2023-10-25
Just run the Ubuntu installer and select "Erase and use whole drive".  UEFI has been the default for over 10 years, there is no sense in trying to avoid it.

---

### Post by guiverc on 2023-10-25
You download the Ubuntu product/release you want, write or burn to USB or bootable media; boot it (*if written correctly it will boot*) & just install over whatever was tehre before hand as per @ubfan1's instruction.

Links that maybe helpful

- [https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop](https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop)
(*if you're wanting Server, or another Ubuntu product, other links are available too*)

- [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)
- [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)
- [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

If a modern Ubuntu ISO is written correctly to media; it'll install on old *legacy/BIOS* boxes; uEFI or modern Secure-uEFI correctly too, so you can go into your machine *firmware* and change settings, but I agree with ubfan1 I'd just whatever you were using (*at most you may get benefit from disabling Secure-uEFI as some third party packages are easier with Secure.Boot disabled; but you can change between uEFI & Secure-uEFI anytime*)

---

### Post by yancek on 2023-10-26
If this laptop had windows 11 preinstalled, it is likely a UEFI install on a GPT drive.  As pointed out above, UEFI is here to stay and is actually better in most ways although it is always problematic to get used to changes.  Did you go through the process of installing Ubuntu from a USB?  Did it appear to succeed or were there  warning/error messages in the install process?  How do you get the no drive found message?  Have you gone into the BIOS after installing Ubuntu and reset the boot order to boot the internal drive where you installed Ubuntu?  Are you able to boot the USB device you used to install Ubuntu?  If you can do that, select the Try Ubuntu option and when you get to the Desktop, open a terminal and type the following command:

```
sudo parted -l
```

That should list the drives/partitions.  Post that output here. 
The suggestion in post 2 to Erase and install Ubuntu should resolve the problem.   Bitlocker key won't be relevant.

---

### Post by tea for one on 2023-10-26
> **rick-price said:**
> the UEFI apparently got clobbered.
Can you access the UEFI settings?
> **rick-price said:**
> Now we get the no drive found message
Open UEFI settings and check that the disk is visible and activated.
(Some UEFI settings allow disks, ports, devices to be de-activated i.e. unavailable)
Is the disk attached to the motherboard i.e. not loose?

---

