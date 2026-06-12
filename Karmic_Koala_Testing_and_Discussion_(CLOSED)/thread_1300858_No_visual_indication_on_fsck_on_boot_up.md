---
title: "No visual indication on fsck on boot up"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nvshaji on 2009-10-25
I have upgraded my jaunty to Karmic. One problem I have noticed on boot up is lack of any kind of message to the user upon disk check being performed at boot up. Has anyone else seen this issue? I can see the hard disk spinning and this happens only once in a while. This from dmesg:

[   17.565912] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   17.566019] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input9
[  270.485559] EXT3 FS on sda2, internal journal
[  271.409663]   alloc irq_desc for 27 on node -1
[  271.409669]   alloc kstat_irqs on node -1

---

