---
title: "Black Screen after GRUB selection"
date: 2017-03-17
forum: Installation &amp; Upgrades
---

### Post by sampj on 2017-03-17
Hi all!, i'm trying to install ubuntu 16.04 (UEFI mode), the problem is that when i reach the GRUB whichever thing i select (Try ubuntu without install, Install ubuntu ...) the screen of my monitor becomes black, because the computer stop sending any signal to it (Monitor in sleep mode). 

- Installing from live usb
- Main operating System: W10 installed (UEFI) on SSD + another HDD for storage
- Trying to install ubuntu on a different SSD
- MOBO: MSI Z97-G45 GAMING

I have tried with Secure Boot both on/off, fast boot was always off.

(i have checked for post regarding that issue, nothing worked)

---

### Post by Bashing-om on 2017-03-17
sampj; Hello; welcome to the forum :)

Boot the liveUSB;
As soon as the EFI splash screen clears spam the escape key to get the boot loader's attention ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s); space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time;
enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.
If this works in the liveUSB, we know what to do for the install .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by sampj on 2017-03-20
Man, you saved my life :)

---

### Post by Bashing-om on 2017-03-20
sampj; Hey !

See, no big deal . All in knowing how .

Let us know how the install goes .

[INDENT][INDENT]we are here to guide assist and render aid
[/INDENT][/INDENT]

---

### Post by RobGoss on 2017-03-20
If you have resolved this issue you can mark this thread as solved. please use the **Thread tool** tab at the top of this post

---

### Post by miquael on 2017-03-20
> **Bashing-om said:**
> sampj; Hello; welcome to the forum :)

Boot the liveUSB;
As soon as the EFI splash screen clears spam the escape key to get the boot loader's attention ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s); space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time;
enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.
If this works in the liveUSB, we know what to do for the install .
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


Hi, I have exact same issue, but this did not work for me.  Any insights?  I posted my issue here: [https://ubuntuforums.org/showthread.php?t=2356205&p=13623096#post13623096](https://ubuntuforums.org/showthread.php?t=2356205&p=13623096#post13623096)

---

