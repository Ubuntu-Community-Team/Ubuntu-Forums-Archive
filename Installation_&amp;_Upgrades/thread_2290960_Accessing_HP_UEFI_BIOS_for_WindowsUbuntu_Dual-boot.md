---
title: "Accessing HP UEFI BIOS for Windows/Ubuntu Dual-boot."
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by th1bill on 2015-08-16
Okay, I'm stupid, I admit it, a 70 year computer nerd with zero brains devoted to reasoning.  My wife bought me an HP Slim Line 400-224 with a Foxconn Mulberry Mainboard, sporting an AMD A4-5000 1.5g Quad Core with six gig of RAM.  Not what I would have built and not what I would have bought but I ask, are you gonna rebuke my 5'11" wife?

It came with windoze 8.1 in a UEFI envioroment and dual booted 14.04.4 nicely but I wanted to see if the stupids had let go of MS and knowing the manure they are famous for, having, in the past, tested for them, removed Ubuntu to prepare for the update.

As Gomer Pyle would say surprise, surprise, surprise, I can no longer hit the ESC Key to get into any menu to set anything up.  I have my partition ready but cannot boot from the DVD Drive.  I can't even crash the system and reload Ubuntu.  Does anyone know a way around this?  I asked at HP but to no avail.

Thank you for just reading this.

---

### Post by oldfred on 2015-08-16
UEFI seems to have a fast boot which is different than the fast startup or hibernation in Windows.
Fast boot in UEFI skips all the hardware type checks that BIOS would do to see if you have new or changed hardware or test memory. That makes for a very fast boot, but then do not have time to press a key.
Of course they designed it that you can always get into UEFI from Windows. But seem to have forgotten that Windows does not always work. And then you need to get into UEFI to boot a Windows repair flash drive.

Some systems will give a normal UEFI boot which just gives you time to press correct keys to get into UEFI, if you do a full power down or cold reboot. Turn off power, unplug system, if laptop remove battery. Hold power switch for 10 sec or so to drain all power. Then boot and see if you can get into UEFI.
Some laptops have a tiny reset access hole in bottom of case. Other system require you to jumper pins on motherboard to have a total reset.

       HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[URL="http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079"]http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079
[/URL]
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[URL="http://ubuntuforums.org/showthread.php?t=2218154"]http://ubuntuforums.org/showthread.php?t=2218154
      [/URL]
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

    [URL="http://ubuntuforums.org/showthread.php?t=2218154"]
[/URL]

[URL="http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079"]
[/URL]

---

### Post by th1bill on 2015-08-17
Thanks a lot OldFred, I'll print this out and give it a wail.  I've been playing, off and on since the VIC 20 and when this unit landed here I was impressed with the number of partitions available but this change from the access point in 8.1 to 10 threw me.  I upgraded my T400 laptop after the desktop and left it in dual boot and there it remained, who knew MicroSoft had the brains to allow such a thing.  I'm a Viet Vet in the last stage of Orange induced Multiple Sclerosis but I'll get on this in the morning to see if I can mark this solved.

Thanks from one old Killer Spade, tail number 67806.

---

### Post by th1bill on 2015-08-17
I couldn't wait and that got me into the system board, now I'll need to piddle to get the DVD to boot and reinstall my Ubuntu, thank you sir.

---

### Post by th1bill on 2015-08-17
Thanks Fred.

---

### Post by coffeecat on 2015-08-17
Support, not chat.

*Thread moved to **Installation & Upgrades**.*

And thread renamed to help others with a similar problem and who need the fix to find it.

---

