---
title: "BIOS Error on bootup - Ubuntu 22.04"
date: 2022-09-04
forum: Installation &amp; Upgrades
---

### Post by Malcolm_Brown on 2022-09-04
I recently upgraded from Ubuntu 20.04 to Ubuntu 22.04 on a Toshiba laptop

I have the following error which appears for a few seconds on screen during bootup:-

[    0.311867] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.X
HC.RHUB.SS04._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.311874] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (202107
30/psobject-220)

There are several more error lines following this which are similar.
The operating system then starts normally.

I am curious as to what is causing this and how it can be fixed.  Thanks.

Malcolm

---

### Post by MAFoElffen on 2022-09-04
Mine has some BIOS firmware messages on my 12 year old ThinkPad now that I ignore... These are usually harmless, noting that the user should update the BIOS firmware. My laptop is 12 years old and has no recent BIOS updates.

I wrote the Forum's UbuntuForums 'system-info' script, where part of my script looks up BIOS values, so I understand this subject a bit...

This is what I did... I checked with the bug reports of kernel.org. My error message was there. but they aren't going to change anything for mine in the current kernel. When the kernel starts, it parses the Machine's BIOS and copies values into /sys, /proc and /run. Years ago there was no compliance to a common standard with BIOS vendors. 

Then came the Desktop Management Interface (DMI) and the System Management BIOS (SMBIOS) standard. These came about to get a common compliance baseline standard, for operating systems and management software to be able to access easier.

[COLOR=#ff0000]Your error message is a bit different.[/COLOR] It is saying that when the kernel is looking a for power settings (acpi), it is already created and looked up, but is trying to create it again new, instead of updating the existing object, and the code there has a conflict somewhere...This should be reported to Ubuntu launchpad on 'Kernel' or kernel.org so they correct that code... That is probably already updated for later kernels, but needs a patch to backport the 'currently used' kernels...

---

