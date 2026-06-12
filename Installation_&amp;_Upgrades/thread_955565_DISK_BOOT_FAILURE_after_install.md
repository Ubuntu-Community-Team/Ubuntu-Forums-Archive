---
title: "DISK BOOT FAILURE after install"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by jarthurs on 2008-10-22
I've just upgraded my PC to a 160Gb WD drive and thought it would be a good time to change from XP to Ubuntu. 

The install process went fine, but after rebooting it attempts to boot from LAN (Intel PXE) and if I cancel this I get DISK BOOT FAILURE. I rebooted with the CD and tried to install grub which appeared to work but it still boots to the LAN.

I can however boot into Ubuntu if I insert the CD (alternate install) and choose 'boot from first hard drive' I get a grub screen and then it boots into Ubuntu. 

Gparted states /dev/sda1 is set to bootable but I can't figure out why it isn't booting.

Any suggestions gratefully received.

Regards,
Jason.

---

### Post by cariboo on 2008-10-22
Did you install grub on the mbr. You might solve the problem, once you have booted to the desktop, by typing in a terminal:

```
sudo grub install
```

Jim

---

### Post by prshah on 2008-10-22
> **jarthurs said:**
> 
this I get DISK BOOT FAILURE. I can however boot into Ubuntu if I insert the CD and choose 'boot from first hard drive'

Check your CMOS settings for boot order; possibly your HDD has been eliminated from the list altogether. Remember, if you're using SATA, it is not necessary that IDE0 is your HDD. Also, if you have the option "Try other boot devices", enable it.

---

### Post by jarthurs on 2008-10-23
The disk in question is an IDE drive so I wasn't expecting any problems from the BIOS. I have now reinstalled GRUB and even blanked the drive and reinstalled Ubuntu from scratch, but I get the same problem. 

The partition is set to active and bootable but it just won't boot!

---

### Post by prshah on 2008-10-23
> **jarthurs said:**
> The disk in question is an IDE drive so I wasn't expecting any problems from the BIOS. 

What is the boot order setting in the BIOS / CMOS Setup? Eg., 1st Boot Device, 2nd Boot Device, etc etc.

If you're having difficulty in figuring it out, take a photo of the CMOS setup screen with a digital camera and post it here.

---

### Post by jarthurs on 2008-10-25
First boot device is CD-ROM, 2nd HDD-0, 3rd USB-HDD (there are no USB devices plugged in aside from the mouse). The NIC is an Intel PRO 10/100 card so there is no specific boot setting for the network card, other than if I set 'Try other boot devices' to enabled it will try to boot from the LAN a second time after the first boot fails.

I'm beginning to wonder if the sectors on the hard drive where the MBR is stored are faulty in some way. I will trying running a Windows install and see if it manages to boot up OK. The drive is detected in the BIOS and the size is reported correctly, but still no boot.

Regards,
Jason.

---

### Post by bulldog on 2008-10-25
Look in your BIOS for an option "boot from LAN"or something similar.
Set this option to OFF.
This option should be there somewhere,but I can't tell you where to search.
Maybe the manual can help you out.

---

### Post by prshah on 2008-10-27
> **jarthurs said:**
> First boot device is CD-ROM, 2nd HDD-0, 3rd USB-HDD 


Try setting 1st to HDD0, 2nd to HDD1, third to HDD2 and so on; if it does not work, you can always go back to what it was.

---

