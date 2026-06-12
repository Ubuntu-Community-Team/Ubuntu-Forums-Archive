---
title: "Installation on a G4 Powerbook"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by deanm on 2006-03-10
Ok, so I may be a bit retarded!  When trying to install, things go fairly well until I get a message stating that it can't find the CD-Rom drive!  If I started the install on the CD-Rom drive to begin with, how could it have forgotten already?  I can't get past this hiccup.  Any ideas???   (or is it worth the bother in the first place since OS-X works as advertised?):???:

---

### Post by stuporglue on 2006-03-10
Do you happen to have two optical drives? Try using the other drive.

---

### Post by anders_gud on 2006-03-10
[QUOTE=deanm]Ok, so I may be a bit retarded!  When trying to install, things go fairly well until I get a message stating that it can't find the CD-Rom drive!  If I started the install on the CD-Rom drive to begin with, how could it have forgotten already?  I can't get past this hiccup.  Any ideas???   (or is it worth the bother in the first place since OS-X works as advertised?):???:[/QUOTE]

Try enabling/disabling DMA on the cdrom.
switch to console ctrl+alt+F1:

Look for settings on CD

hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

returns current settings.

hdparm -d1 /dev/hdc (on)
hdparm -d0 /dev/hda (off)

switch back to install and try again...

---

### Post by deanm on 2006-03-10
[QUOTE=anders_gud]Try enabling/disabling DMA on the cdrom.
switch to console ctrl+alt+F1:

Look for settings on CD

hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

returns current settings.

hdparm -d1 /dev/hdc (on)
hdparm -d0 /dev/hda (off)

switch back to install and try again...[/QUOTE]

Is there a different key-combination to use?  On my powerbook using the sequence of CTRL / Alt / F1 changes the brightness of my display.

---

### Post by deanm on 2006-03-10
[QUOTE=stuporglue]Do you happen to have two optical drives? Try using the other drive.[/QUOTE]

Just one drive... that came with the powerbook...

---

