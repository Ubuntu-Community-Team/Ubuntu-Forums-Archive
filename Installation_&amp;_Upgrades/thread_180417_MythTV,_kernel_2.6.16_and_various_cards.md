---
title: "MythTV, kernel 2.6.16 and various cards"
date: 2006-05-22
forum: Installation &amp; Upgrades
---

### Post by the_plumber on 2006-05-22
I have a P4 3.02 Ghz Procesor, with 512 Gb ram. I bought this system as a bundle with a Hauppauge HVR-1100 and XP Media Centre.

I set up dual-boot with Breezy, which couldn't recognise the card. I used the howto on these pages to upgrade to 2.6.16, and the card was detected, and I could run MythTV if I booted into Linux, or Media Centre if I booted into XP (sorry!)

Next, I installed a Hauppauge Nova-T DVB-T card, in the slot next to the HVR-1100. 

This is where things got a bit weird. The original HVR-1100 is now recognised and works fine with XP/Media Centre, but the Nova-T, while recognised by the kernel, delivers no signal, and during a scan, picks up no services. 

Now boot into linux 2.6.16 (that's FAST! with the performance patch!) and the Nova-T works according to plan, but the HVR-1100 doesn't pick up services in a scan, and delivers no signal.

This is repeatable, the same card works with the same OS on each re-boot. There are no obvious errors showing in the logs....

I *guess* that this may be interference between cards, since they both work OK on their own. The PCI detection in BIOS is all set to auto....


Any Ideas?](*,) 

The Plumber

---

### Post by indulis on 2006-05-24
Check /var/log/messages to see if there is anything that looks out of place (or errors that happen as you start your scan or open the card from mythtv/xine etc).

To keep the messages scrolling try
tail -f /var/log/messages

Cheers,

Indulis

---

### Post by the_plumber on 2006-06-03
Whoa! Hold on....found the problem....cables that meter out (DC) fine, but under RF conditions go bad intermittently! Made new cables from the booster/splitter, and both cards work as expected.

Thanks

---

### Post by miobrad on 2006-06-09
I have got a WinTV-HVR-900 USB card. I have not yet managed to get it working. 

Does anyone know of support for this card? Has anyone tried it? Got it working? Failed? ..

It is a DVB-T card but also supports Analog TV. 

I am searching the web and trying to configure it since a couple of hours with no luck so far. Will update if I find a solution myself, otherwise thanks for any help!

Miki

---

