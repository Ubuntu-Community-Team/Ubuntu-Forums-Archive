---
title: "Having trouble booting Ubuntu on SSD"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Wallysauce on 2011-01-21
Hi Everyone.

I am a noob but i have installed Ubuntu several times and never had a problem until lately. I am using a brand new intel D525MW motherboard with a usb SSD ( [http://www.cpusolutions.com/store/pc/viewPrd.asp?idproduct=1241&idcategory=217#details](http://www.cpusolutions.com/store/pc/viewPrd.asp?idproduct=1241&idcategory=217#details)). I am installing from a usb pen drive.

I have changed the BIOS settings and it does recognize the SSD as a drive and it is in the boot order. I booted to the pen drive (which worked great) and installed as usual to the detected SSD. Then when i reboot to the SSD I just get a flashing cursor. If i hold shift, I just get a message, "GRUB Loading" and then a flashing cursor underneath. I have tried reformatting the SSD and reinstalling at least 5 times.

Does anyone have any ideas on what my next step should be. I read that i should try installing from a CD, but the board does not have an IDE header and i do not have a sata optical drive.

---

### Post by ajgreeny on 2011-01-21
Using you live USB pen drive install and run the Boot-info-script shown in my signature, then copy back here the RESULTS.txt file between code marks (the # in the toolbar of the reply box)

---

### Post by Wallysauce on 2011-01-21
thanks so much for the reply. i will post the output as soon as i get home.

---

### Post by Wallysauce on 2011-02-07
ajgreeny, Thanks for your help. Sorry about the ridiculously long time to reply. I tried using the boot script but i kept getting errors. I was able to solve my problem though for anyone else that is not able to boot linux from a usb ssd. For some reason installing it from a pen drive would not work, but the first time I installed it from a CD it worked like a champ. Now i just need to figure out how to fix my screen resolution.

---

