---
title: "Ubuntu Installation on Dell R510"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by Jordan_Cook on 2016-05-16
Hello,

I'm trying to install Ubuntu Server on a Dell R510. So far i've tried 14.04.4 and 16.04 and got the same problem each time.

Everything seems to be working fine up until installing GRUB. This is what I see on the screen

Running "grub-install dummy" 
Installing the 'grub2' package
Looking for other operating systems
Running "grub-install dummy" 

It then comes up with a screen that says "Choose the next step in the install process" and whatever I choose it just repeats the above.

Looking at the messages I see the following:

main-menu[922]: (process:6684): ERROR: pdc: reading /dev/sda[Input/output error]
main-menu[922]: INFO: Menu item 'grub-installer' succeeded but requested to be left unconfigured.

I've tried in both BIOS and UEFI modes and have the same issue.

Any ideas?

---

