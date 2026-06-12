---
title: "Dual booting Ubuntu/Windows. Seperate hard drives?"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by casacerian on 2010-08-02
I can not choose whice OS to boot at system startup. Windows 7 was installed 1st and Ubuntu 10.04 was installed 2nd on a seperate hard drive.

I have tried holding SHIFT when the system starts to open up GRUB and have gotten nothing. My computer boots strait into windows.

Can someone spoon-feed me how to sort this, or point me to a proper post about it. I have tried several different thingsto get grub to start, and have not been successful.

---

### Post by lechien73 on 2010-08-02
Where was Grub installed when you were installing Ubuntu?

Please could you try booting from a Live CD. Then download the Boot Info Script from: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Follow the instructions there to create a results file, and then post the results here. When you post the results, select the results text with your mouse, and then click the "#" button on the toolbar to wrap CODE tags around it.

---

### Post by casacerian on 2010-08-02
Sorted.

I changed the boot order in the BIOS; placed the drive that runs Ubuntu as the 1st in the boot priority and now it takes me right into GRUB.

Thanks for the reply, though. :)

---

