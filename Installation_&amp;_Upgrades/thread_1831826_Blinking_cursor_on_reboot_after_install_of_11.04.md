---
title: "Blinking cursor on reboot after install of 11.04"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by nathanielw on 2011-08-23
After rebooting from a fresh install of 11.04 on my Gateway ML310 all I get is a blinking cursor from a normal boot. Booting into recovery mode also hangs. CTRL+ATL+DEL, CTRL+ATL+F1, CTRL+ALT+F2 all do nothing, I have to hold the power button down to turn off. 

When I edit the GRUB script of the normal boot by replacing ```
quiet splash vt.handoff=7
``` to ```
nosplash --verbose text
``` the boot gets as far as the following line and then hangs with a blinking cursor. 
[     1.620347] scsi 0 :0 :1 :0 CD-ROM         HL-DT-ST RW/DVD GCC-T10N GW00 PQ : ANSI : 5

Booting in recovery mode gets as far as:
[     1.653667] sd 0 :0 :0 :0 : [sda] Attaced SCSI disk


It took me a while to get 11.04 installed on my Gateway ML3109 in the first place - I had  to add "irqpoll nolapic noapic acpi = off" to the install script. otherwise I got similar hang ups where the CD-ROM drivers were being loaded. 

Please help, I have been at this for a whole day and I am beating my head against the wall!

---

### Post by Hakunka-Matata on 2011-08-23
try this line modification:
```

quiet splash nomodeset
``` if that doesn't work, search this forum for 'nomodeset'

---

### Post by nathanielw on 2011-08-23
Adding nomodeset gives the hang same blinking cursor. HOWEVER, I got it to boot just fine by changing```
quiet splash vt.handoff=7
``` to ```
quiet splash vt.handoff=7 irqpoll nolapic noapic acpi=off
```NEW PROBLEM: Now the computer has no information on the battery. Their is no battery icon in the toolbar when the AC Adapter is unplugged, and the Power Management application has no tab for "On Battery Power" like my other 11.04 laptop.  Is this because I disabled all the power management tools?

---

### Post by Hakunka-Matata on 2011-08-23
Glad you got the graphics working.  Have you checked for "Additional Drivers"?  **System > Administration > Additional Drivers**

I don't know about the missing battery Icon, no laptops here

---

### Post by nathanielw on 2011-08-24
No there are no additional drivers, but I have discovered another sympton of my work around. The computer can no longer shut itself off when I shutdown. I again think this is because I disabled all the power management tools like acpi (Advanced Configuration and Power Interface). Any suggestions?

---

### Post by nathanielw on 2011-08-24
I have moved this thread to here:
[http://ubuntuforums.org/showthread.php?p=11183214#post11183214]("http://ubuntuforums.org/showthread.php?p=11183214#post11183214")

---

