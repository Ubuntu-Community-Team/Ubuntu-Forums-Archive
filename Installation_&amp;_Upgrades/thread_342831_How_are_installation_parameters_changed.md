---
title: "How are installation parameters changed?"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by ecterg42 on 2007-01-20
Hello all,):P 

I am a noob to Linux and have problems trying to install Edgy on a HP Pavillion with AMD Athlon 64 X2 DualCore 5000+, 2 GB RAM, NVIDIA GeForce 6150 LE, SATA drive. I also have a flat panel widescreen monitor. 

After selecting an option from the Ubuntu installation menu, the install freezes after a line about the PS2 mouse.  It is a standard wheel mouse using the mouse port.

I have see potential solutions in other posts about using parameters like "ide=nodma" and others.  Please tell me what I need to do to utilize these parameters. Where exactly do I type "ide=nodma"? How do I get to that 'place' in the installation?:confused:

HP Media Center m7640n
AMD Athlon 64 X2 DualCore 5000+
2 GB RAM
NVIDIA GeForce 6150 LE
TSSTCorp SuperMulti DVD Burner

Thanks, Ecterg.

---

### Post by Stephen Howard on 2007-01-20
Using the installation disk, the way to edit the boot parameters is to highlight "Start or Install Ubuntu", then press F6 - "Other Options".  A cursor should appear at the end of a string of boot options. Use the left/right arrows, backspace and delete keys to delete 'quiet splash' (deleting it gives you some more error messages which is useful when debugging). Type in its place any of the boot parameter options you want.  

[Click here for a list of the possible boot parameters and their meanings.]("http://redsymbol.net/linux_boot_parameters/")

Good luck.

---

