---
title: "Acer Aspire with Ubuntu 8.04/8.10 acpi problem... temp fixed, need permanent fix"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by nkei0 on 2008-10-25
Okay, I've got an Acer Aspire 1680 laptop.  I had originally installed 8.04 alongside a messed up windows install.  I've since gotten rid of the windows partition.  However, installing was a pain for a newbie like myself.  I had to figure out how to edit the menu.lst to show the kernel options of acpi=off noapic nolapic and edd=on before I could boot without freezing.  However, from reading the posts and personal experience I've noticed I have no battery indicator, I can't suspend, and playing any 3d accelerated games is out of the question.  Someone said somewhere that I should go into my xorg.conf and change my driver back to VESA.  The only problem with that is that this is my output for xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Also, I've removed the quiet and splash tags from the kernel boot line so that I could see what was going on.  It shows tons of problems with ACPI (when I don't have the acpi stuff disabled), I would show you the output but I'm not sure how to access it and it's rather long.  Any help on this situation would be great.

Thanks,
nkei0

P.S. This problem started in 8.04 but I went ahead and clean installed 8.10 hoping it would fix this problem.  So, here I am.

---

