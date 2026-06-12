---
title: "Problem Installing Ubuntu"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by bfr on 2007-01-03
When I would start Ubuntu in "safe graphics mode" and then run the Install program, when installing, it would always freeze in the "Copying Files..." part (First it froze at 33%, then 31%, then 23%).  I also would get the errors:

hda: ide_intr: huh? expected NULL handler on exit 

Buffer I/O error on device hda, logical block 357566 

...before the Ubuntu desktop, icons, etc. appeared (but after I selected to start Ubuntu in "safe graphics mode.")

I was told:

AHA! If its a SATA harddrive (connected with a small, usb-sized cable rather than a huge, 40 wire ribbon cable), make absolutely sure to tell ubuntu that it is installing to the drive /dev/sda NOT /dev/hda

How would I do that?

---

### Post by raul_ on 2007-01-03
I think that would be in the step where you chose the partitions but i don't think that the installer would make that mistake

---

### Post by flir48 on 2007-01-03
I have a SATA device also,...and it installed correctly for me as well...

---

### Post by bfr on 2007-01-03
I got it working now, anyway.  :)

I added the following to the boot paramters:

noacpi noapm noapic pci=noacpi

---

