---
title: "can't finish install"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by suspectjake on 2008-03-26
when my installation get to the part where it says select software or something like that it stops at 6% and goes to the boot loaders, which it cant install either, help please.

---

### Post by rectec794613 on 2008-03-26
On the live CD? Because I have this problem whenever I try to reinstall Ubuntu from the Live CD; the partitioner gets to 46% and freezes. I've learned how to solve the problem by removing my iPod

---

### Post by suspectjake on 2008-03-26
i dont have anything plugged in, but no the live cd won't even go past the first selection screen upon boot up, i am having this problem with the text based installer(alternate cd)

---

### Post by Pumalite on 2008-03-26
Post your specs. You might need a lighter Desktop. OTOH, you might need to burn a new CD after doing md5sum on the iso, Burn at 4x or less on CD-R, check CD integrity after burn and before install.Clean the lens in your burner just in case.

---

### Post by suspectjake on 2008-03-26
i have:
(desktop)
dell demension
cd-r
760mb ram
celeron processor
160 samsung hdd(with nothing on it!)

would slower speeds help at all?

---

### Post by Pumalite on 2008-03-26
Graphics?

---

### Post by suspectjake on 2008-03-26
intel graphics controller

the text based installer registers errors and the live cd doesn't respond after pressing enter or waiting 30sec.

---

### Post by Pumalite on 2008-03-26
Here are some boot parameters to try:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791
Alone or in different combinations.

---

### Post by suspectjake on 2008-03-26
i am new to ubuntu and the install proces, where would i enter the params?

---

### Post by Pumalite on 2008-03-26
Here is a guide:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by suspectjake on 2008-03-26
i will give that a try...hold on

---

### Post by suspectjake on 2008-03-26
just to clearify.. these parameters are for the live cd right? when i enter the params it says loading for a while.( i still haven't been able to even start it from the live disc.

---

### Post by Pumalite on 2008-03-26
'One last point: When installing Ubuntu, the very first screen you get to when booting with the install CD has an option to set boot parameters for your system. If you know ahead of time of boot parameters that need to be set to make your graphics card work, for example, then setting them here will not only make your installation much smoother, but they will also get added as default options, as in (2.2) above.'

---

### Post by suspectjake on 2008-03-26
im not sure i get you.. the main screen shown [[COLOR="Lime"]here[/COLOR]]("http://images.google.com/imgres?imgurl=http://linux.hostcurry.com/wp-content/uploads/2007/10/installfeistyfawn-large_001.png&imgrefurl=http://linux.hostcurry.com/%3Fcat%3D3&h=480&w=640&sz=23&hl=en&start=18&tbnid=fnO88ke9WSHdHM:&tbnh=103&tbnw=137&prev=/images%3Fq%3Dubuntu%2Binstall%2Bscreen%26gbv%3D2%26hl%3Den%26sa%3DG") is the one i see and when i either enter the parameters or i press enter, i can hear the disc begin to spin then slow and not load. i waited almost 30 mins last night to see if it would load but it never did.

---

### Post by Pumalite on 2008-03-26
At that screen, you have to hit F6, which will lead you to another menu, from there follow the instructions in the guide.

---

### Post by Pumalite on 2008-03-26
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)

---

### Post by suspectjake on 2008-03-26
i just tried that and it didn't work, the disc began to spin then stopped and froze my screen

---

### Post by Pumalite on 2008-03-26
Check all your hardware. Start with a memtest.

---

### Post by suspectjake on 2008-03-26
now when i tried to install with the text based, during the select and install loading screen it stopped and gave an error.
i have tried most everything and now i think i will redownload and try at a lower write speed.

---

### Post by suspectjake on 2008-03-27
is there any way to write the contents of the disc to a flash drive to boot from (im out of discs)

---

