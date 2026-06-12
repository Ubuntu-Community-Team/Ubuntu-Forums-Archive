---
title: "Restarting Problem (Desperate)"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by Cybermagellan on 2005-03-15
So I have tried the Hoary preview (as well as other distro's of Live -> HD installing CD's) and each time I install a linux build after awhile (aprox 20-40) minutes my computer will beep and hang for a second....do two or more processes (Close windows open windows) and then shutdown. The error message I seem to have been getting is.

Critical Temperature reached 129~ restarting now

however my motherboard doesn't have any Temperature monitoring software or capabilities at all (I HAVE CHECKED THE BIOS). I have passed pci=noacpi to the kernel and still no changes? I have even tried to uninstall acpi using apt-get remove acpi and it uninstalls and still restarts the computer. However my windows drive will load perfectly fine and stay up for days at a time. Any ideas?

Shawn

---

### Post by eternity on 2005-03-15
Uninstalling the acpi package is AFAIK only a program to display acpi, uninstalling this should therefor make no difference. Try booting with "acpi=off apm=off". If that doesn't help I would compile my own kernel and disable all powermanagement options.

If you have never compiled a kernel before there are alot of guides out there...

---

### Post by Cybermagellan on 2005-03-16
[QUOTE=eternity]Uninstalling the acpi package is AFAIK only a program to display acpi, uninstalling this should therefor make no difference. Try booting with "acpi=off apm=off". If that doesn't help I would compile my own kernel and disable all powermanagement options.

If you have never compiled a kernel before there are alot of guides out there...[/QUOTE]
 OK, after spending countless HOURS and days trying to figure out what the problem is I said the heck with it I was going back to Windows.....well now Windows wont work.....so I said the heck with it and installed ubuntu on my primary drive....now there are no issues....except this one...

NVIDIA ( I swear they have it out for Linux ) I have a PNY GeForce 4400 ( I think is the model ) and xorg says it can't startx. But it can on my intergrated chip which is an intel board. 

Any Ideas?

---

