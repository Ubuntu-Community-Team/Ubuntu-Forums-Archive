---
title: "Ubuntu installation problem in Asus K55A"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by jakanfinne on 2013-03-29
Hi all,im trying to install Ubuntu via the instructions given here

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I have done everything stated on that page bios settings,checked the image etc, formatted USB stick again, copied the files from .ISO using Unetbooting etc.

When booting from USB,it stated UEFI: Ubuntu etc, and boots to the menu,where i can select Try Ubuntu, Install Ubuntu etc.
When selecting either of the options,computer just goes blanck.

I have tried to add nomodeset,acpi = off etc in to the boot parameters, but still no avail.

Is there anything else i can try?

---

### Post by dino99 on 2013-03-29
same hardware: [http://ubuntuforums.org/showthread.php?t=2070941](http://ubuntuforums.org/showthread.php?t=2070941)

---

### Post by jakanfinne on 2013-03-29
> **dino99 said:**
> same hardware: [http://ubuntuforums.org/showthread.php?t=2070941](http://ubuntuforums.org/showthread.php?t=2070941)


Thanks, browsed that quickly, and didnt get any wiser :)

Also burned  the image to dvd, cant even get the Dvd drive visible in boot options..Under Bios it is detected,but when trying to hit esc during the boot, dvd drive is not there.

So at this point i think im giving up and following if there is any solution available for this.

Thanks

---

### Post by oldfred on 2013-03-29
A couple of more Asus:
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)

Have you turned off fast boot, secure boot and reviewed settings in UEFI/BIOS?

---

### Post by jakanfinne on 2013-03-31
yeah, i have tried all that, all the combinations etc,but still no success. As told when booting from USB i can select Try/Install etc, after that computer just freezes, no error messages etc.
Burned the image to DVD, i cant even see the DVD in boot options, its visible in BIOS though.

At this point im starting to think that there is something wrong with this laptop :mad:

---

### Post by oldfred on 2013-03-31
Do you have a good download and have you written it correctly to flash or DVD. It has to be an extracted bootable version, not just a copy of the ISO.

 Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by jakanfinne on 2013-03-31
yes,i am well aware how to burn ISO files :)

---

### Post by jakanfinne on 2013-04-04
I was able to install Ubuntu to dualboot with Windows 8 using the rEFInd Boot Manager. Installed it manually, and after that i was able to start the Ubuntu installation from USB live image using rEFInd bootloader.

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

