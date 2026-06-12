---
title: "grub2 change boot options"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by dominik.l on 2010-11-03
i've been using arch linux for a while, but have decided to install ubuntu again, for a change... so it's the first time i use grub2 and have my problems with it...

my toshiba laptop has had a problem with linux since i got it... it can't seem to get the cpu fan to work properly.

i have found two solutions for this, which i have been using for over a year now. either i can suspend linux after bootup; when i turn it back on, the fan runs all the time, don't ask me why... 

the other thing i found online was to add acpi.power_nocheck=1 to the kernel line in grub, which was easy in the old grub. i have searched the web all day, but can't seem to find what i am looking for. i could just add it to the grub.cfg file, but as i understand, one shouldn't mess with this file, as it is automatically generated.
anyone know where i can add this?

thanks in advance!

cheers,
dominik

---

### Post by Rubi1200 on 2010-11-03
Hi and welcome to the forums :-)

To change the boot options:

```
sudo gedit /etc/default/grub
```Find this line:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"and change it to this:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi.power_nocheck=1"Save and then run ```
sudo update-grub
```Let us know if this works for you please.

---

### Post by dominik.l on 2010-11-03
thanks for the reply...worked like a charm! :)

---

### Post by Rubi1200 on 2010-11-03
You are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

