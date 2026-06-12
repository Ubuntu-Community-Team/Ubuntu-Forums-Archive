---
title: "Installing Ubuntu 10.04 NEC P520"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by QuintS on 2010-05-28
I tried installing Ubuntu 10.04 on my old NEC P520. Had the previous two on it and worked like a charm. Came 10.04 as upgrade and no succes. After installing wants get to start GRUB and then freezes. Needs hard boot to do anything. I then tried to reinstall 10.04 from an image cd, but it froze trying to run from the cd. Now I'm back to 9.10. Have no clue how to fix this.

---

### Post by davidmohammed on 2010-05-28
could be a graphics issue - since its working in 9.10 - can you dump the contents of 

lspci

from a terminal here.

Its probably that you need to boot with

nomodeset

or

i915.modeset=1

or 

i915.modeset=0

in your grub  (press e on grub and add the above before "quiet splash")

---

### Post by QuintS on 2010-05-28
Installed Ubuntu 10.04 again and ran into same problem. Ran i915.modeset=0 and this is lspci output


00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
02:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
02:09.0 Ethernet controller: Intel Corporation 82541EI Gigabit Ethernet Controller

---

### Post by davidmohammed on 2010-05-29
hi there - you've got a 855GM intel graphics.  On my laptop I use
i915.modeset=1

Hopefully that will work for you.

---

### Post by QuintS on 2010-05-29
Sorry I was confused. I only get to do something with my laptop when I run grub with the command nomodeset. Then I get into terminal and then I can run lspci to get the output above. When running with i915.modeset=0 or =1 then I get an ubuntu splash screen but it does not look like the splash screen I had with 9.10. It just says ubuntu 10.04 in a "terminal like" font with four dots in the bottom indicating something is loading, but this takes forever. So still no succes.

---

### Post by davidmohammed on 2010-05-29
have you tried some of these [suggestions]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")?

---

### Post by davidmohammed on 2010-05-29
> **QuintS said:**
>  It just says ubuntu 10.04 in a "terminal like" font with four dots in the bottom indicating something is loading, but this takes forever. So still no succes.

I presume also you meant i915.modeset=1?

If you remove quiet splash but have i915.modeset=1 it should boot with messages displayed.  What messages take a long time to appear?

Can I suggest also you use combinations of
i915.modeset=1 with noapic, nolapic, acpi=off

e.g.
i915.modeset=1 noapic

does this make a difference?

---

### Post by QuintS on 2010-05-29
Done some of the suggestions but after a while my pc did not want to get out of some hardware check. Said something like "checking battery... [OK]" and hung. Decided to burn a new Ubuntu image cd. This time using the i915.modeset=1 command got me trough installing allmost all. Then at the end a window popped up saying:

"Ubuntu is running in low graphics mode

Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."

with the option:

"what would you like to do?
- Run Ubuntu in low graphics mode for just one session
- Reconfigure graphics
- troubleshoot the error
- exit to console login
- Restart X"

The first option loads ubuntu from cd.
The second gives me three options:
- use default (generic) configuration
- Create new configuration for this hardware
- Use your backed-up configuration
Use generic obviously does not work. Create new just loops me back to these three options and use back-up I don't have. This does not work either.

Troubleshoot error gives me four options.
- Review the xserver log file
- Review the startup errors
- Edtit configuration file
- Archive configuration
Review xserver log gives a list of all drivers not working. Duh!! And then gives fatal server error: please consult the x.org foundation support. May be last resort. Second option is same as first. Third option loops me back and archive conf saves the log somewhere I can't get to.

Exit to console login lets me play around with ubuntu loaded terminal like but is loaded from cd. In the suggestions a workaround was given to execute:
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u
But this obviously does not work because its loaded vis the cd. So no go.

Restart X does som strange things to my screen (guess its trying to load graphics drivers, but these do not work) and then just halts after checking battery state. Ctrl+Alt+Del to restart.

Restarting the pc gets me past the bios screen. Then I would expect loading GRUB, but just gives me a blank screen with a cursor blinking at the top left. So it does not go further. Ctrl+Alt+del just delivers same result again.

Then loading the cd again to reinstall ubuntu shows me I already have it installed. Installing it again with the modeset=1 gets me back to the window telling me to configure graphics myself again. Endless loop....

---

### Post by davidmohammed on 2010-05-30
... if you've managed to get it to install then you'll need to add i915.modeset=1 to grub.

To get to the desktop, first boot, press shift to display grub and then e to edit.  Add i915.modeset=1 on the line containing quiet splash (add it before quiet splash)

when asked, run the desktop in low graphics mode.  I would follow the suggestion in the linke to create a xorg.conf with a "uxa" configuration.  Reboot, hopefully your desktop will appear correctly.

---

### Post by QuintS on 2010-05-30
No, it doesn't. What I get now is the blank screen with the cursor blinking. So it does not load grub, for me to edit in the first place. I've read somewhere some package called lilo could fix this, but this was for when you had a dual boot system and the ubuntu install messed u your mbr. But tried it anyway. Could not get it to fix the problem. It only made it worse. The system tried booting through the net. So I reinstalled Ubuntu again (for the zilliont time) and got back to the Black Screen of Death. Put my laptop aside for a moment now. Somewhat gave up on it. Will probably install 9.10 sometime in the future. But thanks a lot for your help anyway. Wouldn't have gotten this far without it.

---

### Post by davidmohammed on 2010-05-30
... the blank screen with blinking cursor is after the grub.  You have to be quick - recommend when booting (i.e. when your laptop "bios/pc logo is displayed") to hold down shift.  You'll then see grub appear briefly.  At that point press e to edit.

---

### Post by QuintS on 2010-06-04
This is not true. Passed the bios, but grub doesn't start at all. So there must be something wrong with the installation. Maybe more wrong then just the graphics issue. Went back to 9.10.

---

### Post by alaw005 on 2010-07-29
I had same problem NEC Versa E2000. I found that selecting advanced (F6) and adding "i915.modeset=1" in the settings worked

---

### Post by Jovaro on 2010-08-10
I have a NEC Versa P520 as well and ran into the same problem. I "solved" it by creating a standard xorg.conf and then changing the driver to fbdev instead of intel.
Maybe that works for you as well...

---

### Post by QuintS on 2012-06-08
Solved... Laptop died last year. RIP

---

