---
title: "install of 6.06 hangs on Acer TravelMate 521TXV"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by sugar_chihuahua on 2006-12-24
I am trying to install Ubuntu 6.06 on a Acer TravelMate 521TXV- I can start the installation CD but after the first 30 secs of installation it seems to freeze and eventually goes to a command prompt style mode with msgs relating to IRQ 15... from this point I have to restart the machine... any suggestions? I am desperate to get Ubuntu onto this laptop and Windows XP off!

Pentium III 412 Mhz
256 MB RAM

---

### Post by 5-HT on 2006-12-25
What about passing 'irqpoll' as a boot option during installation?

---

### Post by sugar_chihuahua on 2006-12-25
Hi 5-HT, 

I am a bit of a newbie doing this- how do you pass the "irqpoll" during installation?

---

### Post by Stephen Howard on 2006-12-26
I've been trying to get 6.06 running on my 529TXV - no luck yet using a whole bunch of options including irqpoll, noapic, nolapic, acpi=off among others.

PS:  To answer your question about how you add a kernel option, you have to press F6 at the first screen.  A string of commands will appear near the bottom of the screen, just insert the option you want into that string (ie insert irqpoll), and/or delete the options you don't want (ie quiet), then press enter.

But as I said, no luck at all, though I do recall having better luck with Ubuntu Badger.

Please tell us if you find a working combination of boot options.

---

### Post by 5-HT on 2006-12-26
Hi sugar_chihuahua, hope that Stephen Howard's post answered your question about boot options. Please post back if not.

[quote= Stephen Howard]I've been trying to get 6.06 running on my 529TXV - no luck yet using a whole bunch of options including irqpoll, noapic, nolapic, acpi=off among others. [/quote]

Are you getting any error messages or just a lock up?

What about trying: *pci=noacpi*? That worked for me on a very similar Acer.

---

### Post by sugar_chihuahua on 2006-12-26
Hi Guys,

Thanks for your suggestions but I am still having no joy... when I bring up F6 and enter the commands (i'm still a little unsure of whether I' m typing the right thing, ie, typed, pci=noapic, then enter) I end of with the following:

VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

This has happened each time I have tried the various boot commands using F6... do you know what this means? Any help would be greatly appreciated!!

---

### Post by sugar_chihuahua on 2006-12-26
PS - I also have a copy now of the 6.10 alternate CD that I've been trying this with also to no avail

---

### Post by Stephen Howard on 2006-12-27
The way to edit the boot parameters is to highlight "Start or Install Ubuntu", then press F6  - "Other Options" and a cursor should appear at the end of a string of boot options.  Use the left/right arrows, backspace and delete keys to delete 'quiet splash' (deleting it gives you some more error messages which is useful when debugging).  Type in its place any of the boot parameter options you want ([click here for a list with descriptions]("http://redsymbol.net/linux_boot_parameters/")).

The most common for laptop problems are:

[FONT="System"]> irqpoll
acpi=off
noapic
nolapic
pci=noacpi
pci=biosirq[/FONT]
(don't put an spaces around the '=')

I just finished installing Debian Etch on the Travelmate 529TXV, and it is working happily after I added 'pci=noacpi' to my boot parameters.  I tried the same on Edgy but it still fails.  However, I did get a terminal to work and spotted an error message:

> ACPI Exception (evxface_0545):  AE_BAD_PARAMETER, Removing notify handler

The terminal soon stopped responding, so I didn't get much further.  I did some googling on the ACPI error message and it looks like some laptops have a malformatted ACPI-table.  I gather its reasonably easy to check and fix, but it requires recompiling the table and then the kernel which I'm not motivated to do now that Etch is running happily.

---

### Post by sugar_chihuahua on 2006-12-27
Hi Stephen- some good news! followed your instructions using pci=noacpi and I am underway with an install of 6.10 using an alternate CD... the install is taking its time but seems to be slowly moving forward- will report back to let you know if it all works!

---

### Post by sugar_chihuahua on 2006-12-27
Ubuntu 6.10 has been successfully installed! Thanks for the tips and all of your help!

---

### Post by Stephen Howard on 2006-12-27
That's great Sugar.  Ironically, its not working on my 529!  But at least Debian Etch installed okay with that option.

Regards, S.

---

