---
title: "Removing Ubuntu without killing Vista"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by nLinked on 2008-04-26
I installed Ubuntu 8.04 LTS to give it a try. I'm impressed! I now will be installing Ubuntu on a laptop but want to remove it from this desktop system for now.

This is how it's installed at the moment on my PC:

- Ubuntu on its own HDD
- Vista on its own HDD

I had Vista installed first, then installed Ubuntu. GRUB has taken priority as the boot loader even though I am booting up with my Vista HDD as the first boot device.

If I disconnect the Ubuntu HDD, I assume GRUB will still show up. How do I then remove GRUB so my Vista boot loader shows up again by default (ie: remove Ubuntu/GRUB completely)?

---

### Post by Linja on 2008-04-26
If you remove GRUB, there won't be anything left at all. If you remove only Ubuntu, GRUB will still be there but it won't work anymore. The best solution is get a vista install cd to restore your MBR (fixmbr command). Back in the XP days, you could also restore from a floppy that you could download but I don't know whether that is still valid. Ask your friend google. :D

---

### Post by the8thstar on 2008-04-26
You can also run fixmbr from the command prompt. Do it with administrator privileges.

As far as wiping off the Ubuntu partition, go to the disk tools (somewhere in control panel sub-options, can't remember where exactly). A GUI will come up, select the Ubuntu partition and right-click delete.

---

### Post by obidose on 2008-04-26
I have just uninstalled the way you want to. It can be done with no command promt or terminal fiddling.

It is very easy.

1)Boot into vista
2)[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)  Install easyBCD and run it
[INDENT]a)click the manage bootlaoder tab
b) Reinstall the vista bootloader
c) grub should be done away with now and you will auto boot into vista as if ubuntu had never been there. I recommend you test this before going further though[/INDENT]

3)Delete the ubuntu partitions or if there is nothing else on the ubuntu disk completely format it. (partition deletion can be done using the ubuntu live-cd partition manager (Gparted)

4) Your system should be as if ubuntu was never there

---

### Post by nLinked on 2008-04-26
> **obidose said:**
> I have just uninstalled the way you want to. It can be done with no command promt or terminal fiddling.

It is very easy.

1)Boot into vista
2)[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)  Install easyBCD and run it
[INDENT]a)click the manage bootlaoder tab
b) Reinstall the vista bootloader
c) grub should be done away with now and you will auto boot into vista as if ubuntu had never been there. I recommend you test this before going further though[/INDENT]

3)Delete the ubuntu partitions or if there is nothing else on the ubuntu disk completely format it. (partition deletion can be done using the ubuntu live-cd partition manager (Gparted)

4) Your system should be as if ubuntu was never there

Thank you all for your help. I will give these a try.

---

