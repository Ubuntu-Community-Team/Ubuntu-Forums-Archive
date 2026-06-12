---
title: "Getting a black screen when installing or Live booting Ubuntu (any version) in my lap"
date: 2015-12-07
forum: Installation &amp; Upgrades
---

### Post by Ajith_Kumar on 2015-12-07
I have an ACER Aspire laptop. Model number is E5-573G-56RG. I bought it only 15 days back. I have tried various versions of Ubuntu- 14.04.2, 14.04.3, 15.10, 12.04.5. Tried disabling secure boot, fast startup. I current have Windows 10 Home and Windows 10 PRO (not-activated) installed with GPT partition in UEFI bios. I actually want only the Home edition and Ubuntu 14.04.3 (preferably because of LTS) or 15.10. If I need to give more information, kindly ask me. Please help me! Please! :(


I tried installing through Wuabi, when booting if I choose Ubuntu it automatically restarts and goes into Windows 10 Home! (I didn't have Windows 10 PRO at that time)


ONLY BECAUSE NONE OF THE SOLUTIONS I REFERRED HELPED ME, I AM ASKING THE QUESTION. I REQUEST NOT TO FLAG OFF MY QUESTION.





**P.S: **I know  that the question has been already asked. I have spent 5 days (literally at least 20 hours reading all of them and trying out all kinds of editing in the grub command line- removing quiet splash, adding and replacing with nomodeset, no splash, acpi_osi=off, acpi_osi=Linux, acpi_backlight=vendor,  acpi_backlight=legacy, noveau.modeset=0, i915.i915_enable_rc6=1 and such things! But I was not able to succeed installing which is why I doubt if there is some more thing to be done or know exactly what has to be done.

---

### Post by yancek on 2015-12-07
Did you just try installing on windows using the wubi software?  If so, you apparently didn't come across the official Wubi Guide at the link below which explains why it won't work with windows 8 or newer.  It also hasn't been in development or supported for several versions of Ubuntu.  So, unless you want to spend many more probably fruitless hours on this, give it up.  

If you have also tried to install Ubuntu to its own partition on a hard drive, could you post more specifics on exactly what happens when you boot the Ubuntu installation medium?  Also, are you using a DVD or a flash drive?  In either case, can you test the medium on another computer to see if it boots to eliminate that as a problem.  If you are using a usb, what software did you use to create it?
 
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

