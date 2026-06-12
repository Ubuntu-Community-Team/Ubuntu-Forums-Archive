---
title: "Ubuntu not starting up on windows 8 with LiveUSB"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by arturo6 on 2014-02-02
Hi.

I recently bought a new laptop, an HP Pavilion 15 sleekbook, model 15-b119wm, with Windows 8 pre-installed. I created a LiveUSB, put ubuntu 12.04.2 on it, disabled secure boot, and attempted to start up the computer through the usb. Nothing shows up - a black screen flashes for a few seconds, then nothing. 

I have ubuntu on another pc alongside win7, so I'm somewhat familiar with this stuff. I had no idea that windows 8 would be so damned frustrating, and I have absolutely no idea where to go from here.

---

### Post by Bucky Ball on 2014-02-02
Boot to Windows and switch off Faststart (or whatever it's called) in the software. They don't make it easy.

This:

[http://www.pcmag.com/article2/0,2817,2417361,00.asp](http://www.pcmag.com/article2/0,2817,2417361,00.asp)

... gives you some clues. It equates to Win* hibernating which will prevent ANYTHING else from functioning. ...

And BTW, welcome to the forums! ;)

---

### Post by arturo6 on 2014-02-02
thanks - I'm glad to be here :)

well, I did what that guide told me, and still a blank screen, except now in the bottom-left corner it says "ESC...Pause Startup"

---

### Post by arturo6 on 2014-02-02
HOWEVER... under System Configuration, the platform key says "Not Enrolled". Not sure if that has anything to do with it.

Basically everything else is done - faststart/secureboot off, legacy support enabled.

---

### Post by Under Tree on 2014-02-02
Faststart?

---

### Post by arturo6 on 2014-02-02
I used the ubuntu-12.04.3-desktop-amd64 iso file, and used Universal USB Installer to create my LiveUSB

EDIT: now the damned thing says "Press the ESC key for Startup Menu". Pressing ESC does nothing. Ready to start smashing things

---

### Post by arturo6 on 2014-02-02
ahhh, it says "The selected boot device has failed"

---

### Post by Bucky Ball on 2014-02-02
Try UNetbootin.

---

### Post by arturo6 on 2014-02-02
oki-doke, am trying that, will return with results.

EDIT: process paused at step 2, at 666 mb. the future does not look bright for me.

---

### Post by arturo6 on 2014-02-02
Did not work. Same mistake as before.

---

### Post by oldfred on 2014-02-02
You probably need to turn fast boot off, and secure boot off. Then depending on which video chip you have you may need other boot parameters like nomodeset. But if Intel it is others.

With very new UEFI systems, usually better to use 13.10 or wait for the new 12.04.4 that will be out in a couple of weeks.
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

HP's seem not to be the easiest to get working.
       HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

            acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by arturo6 on 2014-02-02
thing is, I can't even to the part where I live boot the damn thing first. I get as far as turning off secureboot and fastboot in the BIOS, prioritizing USB boot, rebooting the computer with USB stick in, then nothing.

---

### Post by oldfred on 2014-02-02
Are you adding nomodeset or other boot parameters if Intel?

And the procedure to add them is different with BIOS or UEFI. 
With BIOS hit any key immediately when accessiblity (tiny) icons are at bottom & then f6
With UEFI it is like first boot after install and you have to manually edit boot stanza. Use e for edit, scroll to linux line and replace quiet splash with nomodeset.

Some can only install in BIOS mode and then you have to use Boot-Repair to convert to UEFI. A few only work in BIOS mode and you then can only dual boot from UEFI menu or one time boot key.

---

### Post by arturo6 on 2014-02-02
SOLUTION! FINALLY!

I will post a detailed description of each step I took, as well as model, specs, etc. of my laptop. Thank you so much for your help, all of you - just give a sec while I finish installing it.

---

### Post by arturo6 on 2014-02-02
Well, I completely wiped Windows 8 (thank god), so I already forgot the specific steps needed to fix my problem.

---

