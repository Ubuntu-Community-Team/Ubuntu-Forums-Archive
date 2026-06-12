---
title: "cant get ubuntu to work on my hp pavilion a450n"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by CosmicChan on 2011-09-17
hello ubuntu community, i have been trying my hardest to get ubuntu to work on my hp pavillion a450n tower. when i use the wubi installer i get the error no cd in drive meassage, and when i use a flash drive (well technacly its a microsd card in a reader) it gets to the purple ubuntu splash screen and then just stays there. for the usb ive tried it on multiple computers and the same thing happens on all of them. i am looking to either get ubuntu to run alongside windows or if possible replace windows on my tower. thanks in advance

- i believe i forgot to mention im running xp on the tower atm

---

### Post by varunendra on 2011-09-18
Hello Chan, and welcome to the forums!

Have you tried booting from a CD? Also, if multiple computers give the same result with the USB flash drive, then I doubt the integrity of the iso you downloaded. Accordingly, I suggest to follow this:
> **varunendra said:**
> Please post your systems' specs, especially, the amount of RAM. At least  1 GB RAM is recommended for Ubuntu 11.04 with Unity. If you have less  than this amount of RAM, try [Xubuntu]("http://www.xubuntu.org/getubuntu") or [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") instead (for newer kernel), or just stick with 10.04.

<snip>

If you are really keen to use natty, try this:

[LIST]
[*]First of all, please verify that your downloaded iso is not corrupt itself: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[*]After the integrity of the downloaded image is verified, do the following:
[*]while booting, press any key. This should bring up advance boot menu.
[*]In the advance menu, after selecting language, press F6. This will pop up "Other options" menu.
[*]In  this menu, select (by highlighting with arrow keys and pressing  "spacebar"): acpi=off and nomodeset. Then press escape key, and  selecting "Try without installing..", press 'Enter'.
[*]If this does not help to boot normally, retry by also selecting noapic, nolapic and nodmraid this time.
[/LIST]
 For a detailed info on customized booting, follow this (thanks to drs305 for the link): [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions).

As a side note, I suggest not to make any changes to your current installation (of xp) until the compatibility of your hardware with ubuntu is verified successfully. Or, you can make a backup image of the installation, then proceed as you wish. Just to be safe.

---

