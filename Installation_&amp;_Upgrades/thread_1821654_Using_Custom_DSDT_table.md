---
title: "Using Custom DSDT table"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by alokhan on 2011-08-09
Hi,

I followed this guide [http://ubuntuforums.org/showthread.php?t=1341580](http://ubuntuforums.org/showthread.php?t=1341580) and everything went smooth but unfortunatly linux is not loading the custom DSDT table here is what i get from the dsmeg :

> [    0.000000] ACPI: Override [DSDT-CALISTGA], this is unsafe: tainting kernel
[    0.000000] ACPI: DSDT @ 0x000000007fe95a6e Table override, replaced with:
[    0.000000] ACPI: DSDT ffffffff81a5cf80 0523C (v01  INTEL CALISTGA 06040000 INTL 20100528)
[    0.351538] ACPI: EC: Look up EC in DSDT

Anyone have any idea how to solve this issues ? 


PS : my laptop is a Area-51® m5550.

Regards 

Alokhan

---

### Post by dino99 on 2011-08-09
> **alokhan said:**
> Hi,

I followed this guide [http://ubuntuforums.org/showthread.php?t=1341580](http://ubuntuforums.org/showthread.php?t=1341580) and everything went smooth but unfortunatly linux is not loading the custom DSDT table here is what i get from the dsmeg :



Anyone have any idea how to solve this issues ? 


PS : my laptop is a Area-51® m5550.

Regards 

Alokhan


seems to be loaded: the 2d line says "Table override, replaced with:", so its the new table, be happy ;)

but you can still fight against error(s) using: 

fwts
This is a firmware test suite that performs sanity checks on Intel/AMD
PC firmware. It is intended to identify BIOS and ACPI errors and
if appropriate it will try to explain the errors and give advice to
help workaround or fix firmware bugs.  It is primarily intended to
be a Linux-centric firmware troubleshooting tool.

sudo apt-get install fwts

and last comment:
instead of tweaking your own DSDT table, you should report this DSDT issue with your hardware against linux, into a terminal:

ubuntu-bug linux
(you will be asked to create an account on launchpad, like all ubuntu lovers have :))
that way everyone will get a fixed future kernel

---

### Post by alokhan on 2011-08-09
> **dino99 said:**
> seems to be loaded: the 2d line says "Table override, replaced with:", so its the new table, be happy ;)

but you can still fight against error(s) using: 

fwts
This is a firmware test suite that performs sanity checks on Intel/AMD
PC firmware. It is intended to identify BIOS and ACPI errors and
if appropriate it will try to explain the errors and give advice to
help workaround or fix firmware bugs.  It is primarily intended to
be a Linux-centric firmware troubleshooting tool.

sudo apt-get install fwts

and last comment:
instead of tweaking your own DSDT table, you should report this DSDT issue with your hardware against linux, into a terminal:

ubuntu-bug linux
(you will be asked to create an account on launchpad, like all ubuntu lovers have :))
that way everyone will get a fixed future kernel

Oki thanks a lot the issues is i still have the 18 second delay during the boot but i think i found the solution :

for the 18sec delay:
open in a text editor your dsdt.dsl and search the function called "Sleep" in the section "Device (EC0)":
Sleep (0x2710) change the value to (0x3E8)
Sleep (0x1F40) change the value to (0x3E8)

I will post the result :)

there is also another strange thing happening , i removed the quiet and splash grub paramater to see the boot log but the logs are not readable, it's like a resolution bug or something.

---

### Post by alokhan on 2011-08-09
all right no more 18 second boot delay yepa ! :)

---

