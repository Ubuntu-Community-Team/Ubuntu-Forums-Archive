---
title: "Trying to install Ubunto on Lenovo Flex3 1580"
date: 2018-09-20
forum: Installation &amp; Upgrades
---

### Post by heroquestelf on 2018-09-20
Guys, I am trying to install Ubuntu on a Lenovo Flex3 1580 and the main problem I'm having is that this is the first time I've ever tried to do an install with a flash drive. The laptop does not have a CD-Rom drive and I can't get it to boot from the Flash Drive.

I don't know if the BIOS is set up wrong or what. It took me the longest time to figure out how to even access the BIOS (there is a recessed button beside the power button that you have to press). Once I got the startup menu to launch I originally chose to switch the bootup order so that it would boot to the flash drive (and I'm about 85% certain that I did that correctly). However, I tried it twice and both times the screen would go blank and the flash drive would flash for a few seconds, and then it would boot from the hard drive. 

I honestly don't know what I'm doing wrong.

---

### Post by westie457 on 2018-09-20
.Firstly, within Windows burn the ISO to your USB with either rufus [http://rufus.akeo.ie/](http://rufus.akeo.ie/) or etcher [https://etcher.io/](https://etcher.io/)
While that is processing open Control Panel > Power Options > Change what the power button does > Change settings currently unavailable > un-tick the Fast Start up box > also empty the Allow Hibernation box > Apply. Close the Control Panel.

Has the ISO burn finished yet?
Leave the USB plugged in.
Restart the machine and start tapping the F2 button (unless Lenovo have set a different one) to get into the BIOS/UEFI pages.
On the Security Tab disable SECURE BOOT. Go to the Boot tab, in here you want (cannot remember the order on the page) UEFI first, USB boot enabled, Default Boot - Other OS. Save the changes. When you see the Lenovo Splash screen start tapping the F12 key, select the USB UEFI line.
After these changes there will be no need to start the machine from the NOVO button.

ps After you have changed any partition on the hard drive the Lenovo recovery software will not work at all. If you ever want/need to do a factory reset make a back up of the Windows partition first or buy a install usb stick from Lenovo.

pps The above instructions work on my Flex2 and my G50-30.

---

### Post by heroquestelf on 2018-09-20
Thank you **SIR**.

I'm up and running.

(it was actually funny. I did everything you told me and it still didn't work. It turned out that at least one of my problems was that my USB stick was corrupted.)

---

