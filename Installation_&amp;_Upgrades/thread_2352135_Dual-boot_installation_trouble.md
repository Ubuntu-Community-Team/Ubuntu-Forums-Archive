---
title: "Dual-boot installation trouble"
date: 2017-02-09
forum: Installation &amp; Upgrades
---

### Post by stephenspicer on 2017-02-09
I am trying to dual-boot Ubuntu with Windows. I am going through the installation process and got to the section asking either to dual boot, erase, or do something else. It will not let me click continue as the button is faded. Thus I can't go forward and install.  On the previous slide I chose to do updates as it installs but didn't choose the third party thing. (Don't know if relevant) My laptop is a couple year old HP and I have Windows 10. Please help :(

---

### Post by oldfred on 2017-02-09
Is Windows 10 hibernation still on?
What model HP & what video card/chip?

Is system UEFI or bit older BIOS?

See link in my signature below for more UEFI info.

---

### Post by stephenspicer on 2017-02-09
The laptop is HP Envy (forgotten the specific number) Video card is GT635M. Hibernating is off. I just checked and it is on EFI.

---

### Post by oldfred on 2017-02-09
You need to boot in UEFI mode.
You may need nomodeset.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

And follow install steps from link in my signature.

But after install, you will need to do a work around.
HP violates UEFI spec and uses description as part of boot. 
And of course only valid description is "Windows Boot Manager".

But many work arounds, several listed in link in my thread below.

But after install run Boot-Repair and post link to its summary report.
       
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by yoshii on 2017-02-23
I have been reading about this type of thing this evening, and some HP computers have firmware issues with dual booting, unless it is "tricked".  Others here can explain better than me though.

---

