---
title: "Problems installing Ubuntu 18.04 on a Dell Inspiron 15 Gaming notebook"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by rogerioces on 2018-04-28
Good afternoon

I need help because I have a situation that is happening to me (and I believe) with other people as well. Since Canonical killed Unity and decided to use gnome, I can no longer install a new version of ubuntu. I  am using version 16.04.4 so far, and when I try to install the latest  version 18.04, soon in the installation ubuntu ja freezes, it even  crashes. This has been since 17.10, and I do not know what to do, because my research has not come to anything. The notebook I use is a 15-inch gamer notebook, even popular: the Dell Inspiron 15 Gaming Notebook i15-7567-A20P. The setting I am using is:
7th Generation Intel® Core ™ i7-7700HQ Processor (4 cores, 2.8 GHz expandable up to 3.8 GHz, 6 MB cache)
8GB Memory, DDR4, 2400 MHz
1TB Hybrid Hard Disk (5400 RPM) 8GB Cache (I also added a 256GB SSD .M2, which is where ubuntu is installed)
NVIDIA® GeForce® GTX 1050Ti Video Card with 4GB GDDR5
Dell Wireless ™ 802.11ac + Bluetooth 4.0 Network Card, Dual Band (2.4 GHz / 5 GHz, 2x2)
74 Wh 6 cell battery (integrated)

I really need some help because I want to be able to use the new ubuntu with gnome, but these crashes are not leaving me. The same installation pendrive that I tried to use on this computer and  could not, I put it on another computer and it did install ubuntu 18.04  without problems.
If anyone can help me, I will be very grateful.

---

### Post by oldfred on 2018-04-28
That is UEFI system, so are you installing in UEFI boot mode.
You also have nVidia, have you added nomodeset boot option?
If Windows installed anywhere make sure fast startup is off.

See link in my signature for more details. Of which backup is most important.

---

### Post by uzkha on 2018-06-03
Hi guys!

Any update in this case? I have a same issue. I tried a lot of times and nothing works.

---

### Post by oldos2er on 2018-06-03
rogerioces hasn't returned to the forum since they posted; best to start your own thread if you need help.

---

### Post by thedesertsong on 2018-06-09
Hi there!
I've had issues installing Ubuntu and various distros on my Inspiron 15 7559 due to some weird DSDT bugs in the BIOS/firmware. The work around is to boot with the kernel option "acpi_osi=" which forces the laptop to boot with "safe" DSDT options.
That fixed all of my freezing issues! =D

To make the option permanent, edit your /etc/default/grub file and make sure GRUB_CMDLINE_LINUX="acpi_osi=" is in there.
After making the edit, run update-grub.

Hope that helps!
-Reed

---

