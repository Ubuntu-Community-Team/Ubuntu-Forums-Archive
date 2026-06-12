---
title: "Installing Hang"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by pjmia96 on 2012-02-05
Hello, I am using a 1998 Micron Transport Trek. It does not have A CD Rom drive. It does not have USB Boot Support in bios. I am trying to install from USB. So I put "Plop Boot Manager" on a floppy disk. I boot from the Floppy disk and the Plop Menu comes up, and I Hold down the "Shift" Key and select USB. I need to press the "Shift Key" twice to get to the main Ubuntu Screen where I can select, "Install To Hardrive". When I press it it Freezes there and I shut Down the Computer.

Has anyone ever solved this Problem?

I want to install Ubuntu but I am New. The ISO is not damaged I try ed it on 2 different Downloaded Files.

Please Help, Im New, and a Beginner to Ubuntu.:confused:

Matt

---

### Post by searchfgold6789 on 2012-02-05
This will not be able to run Ubuntu.
Try another (much more lightweight) version of Linux, such as TinyCore.

---

### Post by varunendra on 2012-02-06
> **searchfgold6789 said:**
> This will not be able to run Ubuntu.
Try another (much more lightweight) version of Linux, such as TinyCore.
+1
A few others include [DSL]("http://www.damnsmalllinux.org/") (Min. 16MB RAM) and [SliTaz]("http://www.slitaz.org/en/about/") ([16MB]("http://www.slitaz.org/en/doc/releases/3.0/relnotes.en.html#hardware") min., better GUI).

---

### Post by Mosome on 2012-02-06
It depends on your hard drive and memory capabilities too.  Newer versions use a lot of power and old machines will probably hang for awhile simply because of loading massive resources.

---

### Post by pjmia96 on 2012-02-06
That Doesn't work Either. The computer should be able to handle Ubuntu. Its something with Plop boot manager working with the computer. I did this to me on 3 Different Linux versions and windows xp. I need to hold down shift for every different window that opens. I'm lucky if I get to the install screen, no matter what button I push that requires information from the USB Drive It Hangs.

---

### Post by varunendra on 2012-02-06
> **pjmia96 said:**
> no matter what button I push that requires information from the USB Drive It Hangs.
.. Ah, I missed the fact that such an old computer must have USB1 or 1.1 with only a speed of 12Mbps (1.5MBps). So it must be an issue of speed/timeout. As such, I can think of three possibilities:

1)
Your best bet in this case is to pull-out the hard disk from the laptop, connect it to a faster computer via a USB enclosure, then install the desired OS on it (must be light and small..), and reinstall the drive in the lappy.


2)
If you don't have that option, I'm afraid you have no choice but to install an OS the same way it was done those days - using multiple floppies. Both DSL and SliTaz can be installed that way:
[Boot DSL from floppy]("http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies") (similar to Plop; would eventually boot from a CD/USB),
[SliTaz on floppy]("http://mirror.slitaz.org/floppies/") (the whole OS can be installed using only floppies).


3)
Another way might be:

[LIST]
[*]Install the desired OS in a virtual machine on a different computer,
[*]Create its image using clonezilla
[*]Setup the VM as a [Clonezilla PXE server]("http://clonezilla.org/livepxe.php")
[*]Boot the laptop with PXE support using Plop or any similar utility.
[*]Install (restore) the OS image from the virtual machine via PXE.
[/LIST]
In this method, although I'm assuming your network interface must also be the slow one (10Mbps), but hope it may succeed since network protocols used in these methods have less data overhead than USB, and are more tolerant to delays.


Let's hope someone can suggest a better way..

---

