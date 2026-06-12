---
title: "eMMC Boot - Installation &amp; Compatibility"
date: 2017-02-04
forum: Installation &amp; Upgrades
---

### Post by schyken on 2017-02-04
I have a laptop (Dell - Inspiron 14 3000 Series) that came with Windows 10 installed. I want to install Ubuntu to the system, but there's a small (or maybe large) issue with that. The laptop storage drive is a 32GB eMMC Flash Drive. From what I can see, the BIOS/UEFI doesn't support booting from this device. This absolutely baffles me, considering it boots up into Windows from that drive, yet there's no option to select it in the menu. Even more disconcerting is that when I install Ubuntu onto the drive, I turn on the machine and it instantly runs hardware recovery because it can't find a bootable OS. Is there some way I'd need to install Ubuntu to the device for it to run properly? Steps I'd need to take for the system to install and run from the eMMC drive? (Also, I know 32GB isn't a lot, but I can do a lot more with it in Ubuntu than I can with Windows 10 where it's likely to become so cluttered that I'd need to refresh the machine every three months.) Any help with this would be fantastic. Thanks in advance.

(Other specs include Celeron N3050, 4GB DDR3, 768p 14" display.)

EDIT: SOLVED: [https://ubuntuforums.org/showthread.php?t=1543006&page=170&p=13603417#post13603417](https://ubuntuforums.org/showthread.php?t=1543006&page=170&p=13603417#post13603417)

---

### Post by schyken on 2017-02-04
Help?

---

### Post by wildmanne39 on 2017-02-04
You can bump the thread once every twelve hours,please be patient we are volunteers from all over the world so it is possible the person that can help you has not been on yet.

---

### Post by Bucky Ball on 2017-02-05
When you are looking in the BIOS for this device, what exactly are you looking for? It will not appear as a regular drive might. It should look quite unfamiliar actually with different lettering (I think they start with 'mcl' or something ... not near mine at the moment so can't confirm).

The other thing: how did you create the installer on the eMMC card? More details about how exactly you are installing to the eMMC, please. ;)

And one last suggestion. Boot the machine with the eMMC in and hit F12 to get to a boot device menu. Does it appear there? If you have the eMMC attached to a USB via an adapater then into a USB slot, it will be the USB that is showing in the boot device options. If you have it in an adapter to USB, you are looking for the USB, NOT the eMMC.

---

### Post by schyken on 2017-02-05
> **Bucky Ball said:**
> When you are looking in the BIOS for this device, what exactly are you looking for? It will not appear as a regular drive might. It should look quite unfamiliar actually with different lettering (I think they start with 'mcl' or something ... not near mine at the moment so can't confirm).

The other thing: how did you create the installer on the eMMC card? 

And one last suggestion. Boot the machine with the eMMC in and hit F12 to get to a boot device menu. Does it appear there? If you have the eMMC attached to a USB via an adapater then into a USB slot, it will be the USB that is showing in the boot device options. If you have it in an adapter to USB, you are looking for the USB, NOT the eMMC.

I can't access the BIOS *unless* there's SOME device plugged in, otherwise I get sent to hardware recovery which just ends saying all hardware is functioning properly. In the BIOS, the only options are *LEGACY*:USB Storage Device, *UEFI*: USB1, Diagnostics, Setup, BIOS Flash Update, and Change Boot Mode. There's an unselectable option for Peripgeral Device Setting (OPROM Setting)

I'm not sure what to do with this. Under the BIOS setup menu, I can see under boot priority USB, CD, HDD, Diskette, and Network respectively. I've tried changing the orders, changing between BIOS and UEFI boot types, disabling and enabling secure boot. I hope these details help a little. Any input?

---

### Post by Bucky Ball on 2017-02-05
You've marked this thread as solved. Is it? If so, please share. That's the norm around here. ;)

---

### Post by schyken on 2017-02-05
Share? What do you mean by that?

---

### Post by Bucky Ball on 2017-02-05
Share the solution to your problem with the rest of the community! You have marked this thread as solved. If you have solved your problem, please share the solution. As straightforward as that. Thanks. ;)

---

### Post by schyken on 2017-02-05
I did. The post has been edited to include the information. More (simplified) detail can be found here: [https://ubuntuforums.org/showthread.php?t=1543006&page=170&p=13603417#post13603417](https://ubuntuforums.org/showthread.php?t=1543006&page=170&p=13603417#post13603417) . 
> **schyken said:**
> -Using Ubuntu 16.04.1 LTS
-Dell Inspiron 14 3452 (Intel Celeron N3050, 4GB DDR3L, 32GB eMMC Flash Storage, UEFI)
--In order for the system to recognized the installed OS, you must ensure the system is using UEFI boot mode as well as enabling Firmware TPM BEFORE installation. Secure boot MUST be off for installation and after installation. Legacy Option ROM should be disabled. After install, the system will recognize the OS and boot properly after the TPM check which will only occur at the very first bootup and never occur again.

---

