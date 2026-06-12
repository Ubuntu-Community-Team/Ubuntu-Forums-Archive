---
title: "Trying to install Ubuntu for the first time on this PC / Boot disk problem"
date: 2023-12-27
forum: Installation &amp; Upgrades
---

### Post by zaphanathpaneah on 2023-12-27
Hi team,

I am trying to install Ubuntu on the machine for the first time and it fails right after the prompt “try or install Ubuntu”. The error is “ 1.061670] hub 8-0:1.0: config failed, hub doesn't have any ports! (err -19)” I have secure boot enabled but tryed it with it off, still no dice.l i have attempted to make one from myother Ubuntu machine but Ubuntu cannot get the package. I have tried different ways in ubuntu but all is failing. The boot disk was made with Rufus. I have tried several other apps but they are all full of malware. Any suggestion? Motherboard MSI Tommahawk B650, 32gb Ram, 1tb SSD, windows 11 installed on one partition, AMD Ryzen 5 5600, Nvidia 3060. Nothing too igh end.

wondering if the boot disk does not have the right keys for secure boot, or Ubuntu is not supported on MSI boards. So wondering if Mint Linux would be better?

---

### Post by MAFoElffen on 2023-12-27
I have an MSI MPG Z790 Wifi w/ 13th gen Intel... Ubuntu supports, boots and runs on MSI. Whether SecureBoot is enabled or not. It installed better than Windows 11, as for it I had to download and install MSI's Windows drivers for it to recognize the newer hardware... Something I didn't have to do with Ubuntu.

Let's be clear that we are talking about Ubuntu Desktop 22.04.3 LTS. (The latest point release.) And that you have verified the sha256checksum on it, right?

Next, because you have NVidia 3060 graphics, when it goes to the Grub2 boot menu, start with the second boot menu option > "Try with Safe Graphics Mode"... That will add a "nomodeset" option to the kernel boot parameters and allow the graphics to come up... Also (tip), when the "Ubuntu" Splash screen comes up, press the <Arrow-Down> key to toggle to the boot massages and note any errors with those... may help later if there are.

Important that during the install, that you check the "Download and Install Third Party Drivers" checkbox, so that it installs your NVidia Graphics driver during the install. You could do that later, but would require your to do some tricks to boot it on the first reboot, to be able to install it then. Just a thing... Having NVidia, eventually you are going to need to learn those tricks...

I'll explain those later, or read the first three posts of the Graphics Resolution Sticky in my Signature Line... Being an Nvidia owner (like me), it takes some care and feeding to keep it maintained and running well.

---

### Post by oldfred on 2023-12-27
> &#8220; 1.061670] hub 8-0:1.0: config failed, hub doesn't have any ports! (err -19)"

Is USB live installer plugged into system or external hub with ports?

Some AMD systems have needed UEFI firmware & if SSD firmware updates.
Some older AMD systems also needed IOMMU setting in UEFI changed to see ports correctly.
Issues often common by chipsets as well as vendor's implementation.
Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)
Asus Rog Strix B550 Disable IOMMU
[https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397](https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397)

---

