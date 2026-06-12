---
title: "need help installing Ubuntu 7.10 live cd"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Charbs152 on 2008-01-25
i get this message
bios age (1997) fails cutoff , acpi = force is required to enable acpi

then it goes to the scrolling ubuntu screen then a black screen that says type help for a list of commands

then a whole bunch of numbers come up and other code

---

### Post by bwtranch on 2008-01-25
Make sure you burned an iso image and just did not copy the files.

---

### Post by Charbs152 on 2008-01-25
no i burned the image using power iso

i am very familiar  with burning iso files

what could be wrong

---

### Post by bwtranch on 2008-01-25
Okay, kinda weird. We're gonna need some info. Your machine, what else you have installed. Dual boot?, etc. I guess you can't post any output, but anything would be useful. At this point, kinda shootin' in the dark.

---

### Post by Charbs152 on 2008-01-25
my machine is 

socket A athlon 1.2 Ghz

pc chips m810L motherboard 32MB onboard video

384MB pc133 ram

320GB western digital HD

wireless pci internet

---

### Post by Pumalite on 2008-01-25
Try the Alternate CD.

---

### Post by Charbs152 on 2008-01-25
i cant do that right now because i would have to go to my dads PC downstairs (my burner doesnot work) and its a pain because i had knee surgery last week

---

### Post by Pumalite on 2008-01-25
I'm afraid your machine might not be able to boot a Live CD. Or install it for that matter.

---

### Post by scorp123 on 2008-01-25
> **Charbs152 said:**
>  bios age (1997) fails cutoff , acpi = force is required to enable acpi Perfectly normal. Your BIOS seems to be pre-2000 and ACPI as a standard simply did not yet exist back then. Hence the message. Pre-2000 machines most likely simply don't support ACPI. You can force it though ... exactly as the message says.

> **Charbs152 said:**
>  ...  then a black screen that says type help for a list of commands  Sounds like the booting gets interrupted and you're being thrown into "busybox", a total minimalist shell that comes up when booting fails.

> **Charbs152 said:**
>  then a whole bunch of numbers come up and other code  Does it say "Kernel panic" anywhere? It sounds like you have hardware issues. Could you give more details about the errors you see?

---

### Post by bwtranch on 2008-01-25
I really don't see a problem with your hardware, if everything is working. Probably something simple, like the media. I've done numerous installs and re-installs and never had this. Did you do a checksum and verify the data? I'm just thinking there is something wrong with that CD.

---

### Post by Charbs152 on 2008-01-25
why not?
ive seen many people with older machines install it with no problems

---

### Post by Charbs152 on 2008-01-25
nothing is wrong with the cd 

i got a live boot on my dads PC

---

### Post by scorp123 on 2008-01-25
> **Charbs152 said:**
> nothing is wrong with the cd , i got a live boot on my dads PC OK, so we know the CD works tip top. So when it does not work in your PC and instead of booting crashes there must be hardware related issues somehow; maybe the kernel the way it is configured won't properly boot on your machine and instead the whole thing crashes. I've had that too in the past. But in order to be able to suggest any potential workarounds we'd need to know more about the exact error messages you get ...

---

### Post by Charbs152 on 2008-01-25
there are a ton of them its  a whole screen of them

---

### Post by Charbs152 on 2008-01-25
here is a pic

---

### Post by Charbs152 on 2008-01-25
bump

---

### Post by scorp123 on 2008-01-25
> **Charbs152 said:**
> here is a pic Yeap, looks like the Ubuntu Live CD doesn't like your ATA disk controller (the error message says stuff about **"ata1.00"** and **"Exception"** ... so yes, that's a hardware issue somewhere somehow)

Try this: When you boot the live CD's boot menu shows up, e.g. this screen:

[IMG]http://ubuntumasfacil.blogsome.com/wp-admin/images/gfxboot-big.png[/IMG]

Select **F6** for "Other options". You should get a screen that looks something (not exactly though; remember this is a screenshot I found via Google so things might look a slight bit different!):

[IMG]http://www.profi-admin.eu/img/ubuntu_cd_eng.jpg[/IMG]

You should be on that line where all the various boot parameters are listed (similar to the screenshot). When you're there ***add*** (do not remove the other stuff there!) this additional parameter ***exactly*** as I write it here:

**all_generic_ide**

Then hit enter .... and *maybe* it will work now. This parameter causes the Linux kernel to load and try out all the IDE modules ("drivers") it has, even ancient ones that are probably no longer used these days. This fixed the problem for some of my machines, but not for all of them.

Maybe this will work in your case .... It's at least worth trying out IMHO.

---

### Post by Charbs152 on 2008-01-25
thanks ill try it

---

### Post by Charbs152 on 2008-01-25
IT WORKED 







thanks

---

### Post by scorp123 on 2008-01-26
> **Charbs152 said:**
> IT WORKED thanks You're welcome. :)

---

