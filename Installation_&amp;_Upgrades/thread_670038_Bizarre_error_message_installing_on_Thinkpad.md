---
title: "Bizarre error message installing on Thinkpad"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by 11010001 on 2008-01-17
I am getting a bizarre error message while trying to install Ubuntu on a Thinkpad T21 (older machine).  I have installed it before on  a Compaq laptop with no problem, but for some reason this IBM is a stinker.

I put in the LiveCD and turned on the machine, then went to boot from the CD, part way through I get this message

* Loading harware drivers...
[238.764000] piix4_smbus 0000:00:07.3: IBM system detected; this module may corrupt your serial eeprom ! Refusing to load module !

Then the boot up seems to finish, but instead of getting the Ubuntu desktop, the screen is blank. 

:confused:

---

### Post by fwojciec on 2008-01-17
I doubt this message is in any way related to the ultimate problem (blank screen) -- most likely that problem has to do with video driver and xorg configuration.  Can you switch to text consoles when you get that blank screen?  (try pressing Ctrl-Alt-F1m Ctrl-Alt-F2 and so on).

---

### Post by 11010001 on 2008-01-17
I think you are right about that. before I saw your post I tried booting in safe grphics mode and that seemed to work. 

But there is definetly something else going wrong. I get all the way into the desktop now but the install program hangs and the CDROM just churns and churns and never gets past the first panel.

I am also seeing some messages like this:

cat: /var/lib/acpi-support/system-manufacturer: no such file or directory
cat: /var/lib/acpi-support/system-product-name: no such file or directory
cat: /var/lib/acpi-support/bios-version: no such file or directory
cat: /var/lib/acpi-support/system-version: no such file or directory

Not sure what is going on, I am about to give up for the evening (late here in Seattle)

Thanks for the help !

---

### Post by Thanoulis on 2008-01-17
Try do disable ACPI support (there must be a BIOS option like Plug'n'play BIOS or something), and try again. I'm not sure it will word, though. But for your information, i had installed Ubuntu 7.04 on a T23 last year...Good luck!

---

### Post by 11010001 on 2008-01-17
Thanks, that sounds like it worth a try. Good to know someone got it to work on a similar maching.

---

