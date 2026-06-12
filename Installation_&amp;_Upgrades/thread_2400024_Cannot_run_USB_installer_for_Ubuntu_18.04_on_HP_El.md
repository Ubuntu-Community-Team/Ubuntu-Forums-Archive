---
title: "Cannot run USB installer for Ubuntu 18.04 on HP Elitebook 1050 G1"
date: 2018-09-01
forum: Installation &amp; Upgrades
---

### Post by buzzcook on 2018-09-01
Hello everyone

I can run the Ubuntu 17.10 installer but I can't get the Ubuntu 18.04 installer (AMD 64 desktop image) to run on my new HP Elitebook 1050 G1. I want to set up a dual boot (Windows 10 / Ubuntu).

I created the live Ubuntu USB installer both with Rufus and Unetbootin but the error is the same.

I presume it's something to do with the BIOS / UEFI settings for secure boot, which are mentioned in so many other threads. 

The initial problem was that I couldn't even boot from the USB stick so I changed the following 2 BIOS / UEFI settings:

1) Advanced -> Boot Options -> Fast Boot: OFF (was ON by default)
[ATTACH=CONFIG]280939[/ATTACH]

2) Advanced &#8594; Secure Boot Configuration &#8594; Configure Legacy Support and Secure Boot: Legacy Support Disable and Secure Boot Disable (was "Legacy Support Disable and Secure Boot Enable" by default):
[ATTACH=CONFIG]280940[/ATTACH]

Now it starts booting from the USB installer but then just stops with a blinking cursor at the bottom of the screen:
[ATTACH=CONFIG]280941[/ATTACH]

I haven't changed BIOS Sure Start yet because I don't know what to do, but it might be a possibility:
[ATTACH=CONFIG]280942[/ATTACH]

Any ideas how I can get this installation running? Thanks!

**Update 2nd Sept after I updated the BIOS**:
New message with lots of ACPI errors, starting with "ACPI error ... Namespace lookup failure":
[ATTACH=CONFIG]280945[/ATTACH]

---

### Post by buzzcook on 2018-09-02
This is the fix that helped me to get the installer running with Ubuntu 18.04, editing the line starting "**linux /casper/vmlinuz*****" to add "nomodeset" after "... splash":
[https://www.dell.com/support/article/us/en/19/sln306327/manual-nomodeset-kernal-boot-line-option-for-linux-booting?lang=en](https://www.dell.com/support/article/us/en/19/sln306327/manual-nomodeset-kernal-boot-line-option-for-linux-booting?lang=en)

---

