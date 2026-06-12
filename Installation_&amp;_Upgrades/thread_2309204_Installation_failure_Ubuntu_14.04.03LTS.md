---
title: "Installation failure Ubuntu 14.04.03LTS"
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by dom.b.mann on 2016-01-08
Hello everyone.


I recently bought an ASUS X555UB (Inter Core i5 6200U , Nvidia Gforce 940m , 256GB SSD , Win10 , 8GB RAM).
What I want is a clear installation of Ubuntu 14.04.03..
So downloaded the ISO and burned it to a DVD (tried it with USB to).
This might sound strange but I formatted the SSD with the Windows installer , since it is the only way to get far enough to perform a disk operation.
I can get to Live Mode when booting the DVD in Live Mode but an Error pops up everytime telling me that "This Computer only has 0 bytes left" .
After that Error installing Ubuntu in not possible.
I disabled Secure Boot and Fast Boot and enabeld CSM (Aptio Setup Utility Version 2.17.1249) 

Still nothing changed and the Installer crashes and tells me ubi-partman/timezone/console-setup (all of those) crashed with exit code 10 /1/1.
After clicking "continue anyway" the Installer continues up to the point of the "Who Are you " screen . After choosing a name the "your computers  name" field is auto filled with "NAME- SMBIOS-implementations-newer-that-version-2-8-are-not-fully-supported-by-this-version-of-dmidecode-X555UB"
Now it is Installing to the point of the "setting timezone" screen ,at wich the installer crashes and i have to reboot.

Is there anymore information that I have to provide ? 

Greetings Dominik.

p.s. sorry for my bad english - not my mothertongue
i tried severall different version s of ubuntu and some different distros - nothing works

update:
I managed to install ubuntu 15.10 with boot parameter "pci=nomsi".
After reboot I can see the ubuntu logo for a moment and then the screens turns black and stays like that

update2:
I disabled csm , booted in uefi and added the params "pci=nomsi" and  "i915.preliminary_hw_support=1" .
After installation was completed i added those params again when grub asked me what to boot.
Ubuntu 15.10 now boots without errors . And i chnaged in /etc/default/grub GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="pci=nomsi quiet splash" saved and updated grub .
Working ootb : Touchpad (although 2 finger scrolling is supposed to work only after installing 4.3 kernel) , sound , webcam , wifi , lan . (atleast thats whats checked by me)

---

### Post by STrRedWolf on 2016-03-03
I can confirm booting with the "pci=nomsi" flag passed to the kernel stabilizes the ASUS X555UB but also the E451LD/PU451LD.

---

