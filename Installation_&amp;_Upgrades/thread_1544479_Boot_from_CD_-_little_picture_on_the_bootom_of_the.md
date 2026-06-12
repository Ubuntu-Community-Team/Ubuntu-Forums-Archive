---
title: "Boot from CD - little picture on the bootom of the screen?"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by Grebox on 2010-08-02
Hello there!

I created bootable CD and now trying to install Ubuntu on the IBM TP. Boot sequence is starting, CD is spinning, HDD is blinking but after few seconds little picture appears on the bottom of the screen with "a keyboard key = person in a circle" ?? And it is standing there many hours w/o any action on the screen.

:confused: what is this and how to continue with installation ? 

Thank you.

---

### Post by Grebox on 2010-08-03
anyone please ?

I see that similar problem is asked to be resolved several times but up to now no answer.

Doe's it means I can't use Ubuntu on my TP? :(

---

### Post by DrMelon on 2010-08-03
Actually, that little symbol should be showing "a keyboard key = person in a circle". Push that key if you need help for a disability, such as poor sight. Since you say nothing else appears, I imagine there's a problem with the graphics output. What graphics chipset do you have, and can your monitor support the low resolution of the installer?

---

### Post by Grebox on 2010-08-03
ThinkPad T42, 2373-CW9 
PM 735(1.7GHz), 1GB RAM, 60GB 5400rpm HDD, 14.1in 1400x1050 LCD,
 64MB ATI Radeon 9600, CDRW/DVD, Intel 802.11bg wireless(MPCI),
 1Gb Ethernet(LOM), UltraNav, Secure Chip

Only key which responds is ESC key and than I can select several options. However, after I select "install" again nothing happens. TP LCD screen is still blank and CD is running w/o any further response on the screen.

I'm installing from a bootable CD.

---

### Post by Grebox on 2010-08-05
anyone please?:popcorn:

---

### Post by oldfred on 2010-08-05
Push f6 and try nomodeset.

For other video cards:

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

if you've got an i8xx Intel chipset, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

