---
title: "Error in Install"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by unconquerable on 2006-06-11
When I go to install Xubuntu 6.06 on an older system (HP 3266).  During the intial setup it errors out with the following in the screen:

> Uncompressing Linux... Ok. booting the kernel
[4294667.296000] ACPI: Unable to locate RSDP

Any suggestions?

---

### Post by bobby.hawk on 2006-06-12
Similar situation:

I am trying to install xubuntu 6.06 desktop on my IBM Thinkpad 380ed, P166, 81m RAM and a 3 gig hd. I have run RH9, Slackware, and VictorLinux on it just fine. 

The Xubuntu ISO cd boots just fine but yeilds the following error... ACPI: Unable to locate RSDP

Then Xubuntu seems to bypass the error and continues loading the essential files/drivers but then stops again with the following final message:

Uncompressing Linux... Ok, booting the kernel.
[4294667.296000] ACPI: Unable to locate RSDP

Any ideas what's going on?

Bob

---

### Post by Jemod on 2006-06-12
I got the same error message, but my install continued successfully.  When I boot my machine I get that error but it keeps going and boots.

---

### Post by unconquerable on 2006-06-12
[QUOTE=bobby.hawk]Similar situation:

I am trying to install xubuntu 6.06 desktop on my IBM Thinkpad 380ed, P166, 81m RAM and a 3 gig hd. I have run RH9, Slackware, and VictorLinux on it just fine. 

The Xubuntu ISO cd boots just fine but yeilds the following error... ACPI: Unable to locate RSDP

Then Xubuntu seems to bypass the error and continues loading the essential files/drivers but then stops again with the following final message:

Uncompressing Linux... Ok, booting the kernel.
[4294667.296000] ACPI: Unable to locate RSDP

Any ideas what's going on?

Bob[/QUOTE]

THAT is exactly what happens with me, it seems to bypass and then yields the error again and stops.  :confused:

---

### Post by bobby.hawk on 2006-06-12
I have tried pressing F6 while the Xubuntu CD is loading and adding other boot parameters:

xubuntu noacpi
or
linux noacpi
or 
noacpi
or
acpi=off

None of this options seemed to have helped.

---

### Post by elbryan on 2006-06-12
That error could appears for old machine ..

Try to look at this:
There is a setting under Power Mangement called "ACPI BIOS mode" (in the BIOS setup).

If you have that setting, try to enable it and reboot

---

### Post by unconquerable on 2006-06-12
I do not see a setting of that sort... hummm.

---

### Post by bobby.hawk on 2006-06-12
On my Thinkpad 380ed I went into the bios but I didn't see where I had access to a setting for "ACPI BIOS mode".  That's why I think on older pc's we should be able to pass a startup command like:

xubuntu noacpi
or
linux noacpi
or 
noacpi
or
acpi=off

Do you know the right syntax?

---

### Post by bobby.hawk on 2006-06-16
I found this thread... when booting I pressed F6 and added apci=off to the initialization string.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/14475](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/14475)

---

### Post by bobby.hawk on 2006-06-17
Setting acpi=off didn't work... I was able to bypass the problem with ACPI: Unable to locate RSDP but my machine just sat there at the uncompressing the linux kernal ... hours... I powered it off.

back to square 1

---

