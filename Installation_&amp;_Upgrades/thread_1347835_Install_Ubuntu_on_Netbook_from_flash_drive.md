---
title: "Install Ubuntu on Netbook from flash drive???"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by PepeLapiu on 2009-12-06
OK all, I have an Acer Aspire One AS1410 with a windoze 7 installed:
[http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=63750&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=447&ctx1.att21k=1&CRC=1346651341](http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=63750&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=447&ctx1.att21k=1&CRC=1346651341)

I have already downloaded the Ubuntu Netbook Remix ISO from here:
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

I also just bought two 8Gb USB sticks but the instructions are just too confusing to me. Can anyone here explain in simple terms and step-by-step what I should me doing next to install Ubuntu Netbook Remix on my machine from a USB stick ???

Thanx,
PepeLapiu :)

---

### Post by darkod on 2009-12-06
Here are screenshots of the process:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

You can use software called unetbootin in windows to create the usb stick. Google it, it's free. Download it and run it. Select Image and the ISO and at the bottom select your stick letter. Press OK and let it finish. Ignore the ask to reboot, just close the program.

To get rid of the unetbooin menu and enable the standard ubuntu menu open the stick and do this:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That will enable the ubuntu menu. Boot with the stick (you might need to select USB as boot device in BIOS), it's better first to select Try Ubuntu option to see how it will run from the stick. You can test if internet is working, audio, video, etc. If drivers are missing they would be missing when you install, keep that in mind.
After that boot again but select Install Ubuntu option and the above tutorial should help.

---

### Post by PepeLapiu on 2009-12-06
Thanx a whole lot Darko :)
It worked almost flawlessly, I now have wind-dose 7 AND Ubuntu on the machine.

The look of Ubuntu has really changed since I briefly tried it a couple of years ago, looks more user friendly now.

All that is left to do is to learn how Ubuntu works.
Any specific tutorial(s) you would recommend?

Cheers and THANX A MILLION,
PepeLapiu :D

---

### Post by spcwingo on 2009-12-06
Psychocats has some great tutorials.  Here's the link:

[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by pifactory on 2009-12-06
I have a similar problem, except I'm trying to do it from within Ubunto.

I've upgraded my machine from Hardy and all appears to have gone well (how do I check that I'm now running 9.10?)

But I can't find usb-creator anywhere within my system to create a usb stick with Netbook Remix set up as a boot.

I've downloaded Netbook Remix ok.

I'm using an Asus Eeepc with an atom processor. I also have an Asus with a celeron, which is my ultimate to get that machine running. Hence my need to create a stick.

Any ideas?

Thanks.

---

