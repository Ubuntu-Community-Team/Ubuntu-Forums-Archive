---
title: "this **** is so frustrating :("
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by makuab on 2010-06-04
I've been at this for the last 48 hours.. trying to get this installation/HDD to work.

My first problem, ubuntu doesnt recognize any partitions/hard disks
when i open gparted it says "no devices detected". So i look in bios, i cant seem to find my hard drive (i have 2 IDE OPTICAL drives and 1 SATA HARD drive), it shows the two optical drives as master and slave. When i turn the computer on i can feel the hard disk but after that it doesnt do much.

My second problem, Ubuntu now wont load to step 4 (the page where you select a partition or w/e, the page that i didnt see anything on.)

I have both SATA and IDE connectors


MOTHERBOARD: MSI 915GLM-V
SYSTEM: MED MT 347G

---

### Post by madverb on 2010-06-04
Reset the BIOS to optimised defaults. Also, make sure that SATA is enabled in BIOS.

---

### Post by makuab on 2010-06-04
> **madverb said:**
> Reset the BIOS to optimised defaults. Also, make sure that SATA is enabled in BIOS.
im pretty sure it is... but if not how can i activate it?

---

### Post by darkod on 2010-06-05
> **makuab said:**
> im pretty sure it is... but if not how can i activate it?

You need to look in your BIOS more carefully. We can't know how it looks like.

There might be option whether the SATA controller to be Enabled or Disabled. Maybe it's disabled right now. Just change to Enabled, usually with PageUp, PageDown buttons, save the settings and exit.

And just to clarify, since you already noticed the hdd is not recognized in BIOS, it's not fair to say ubuntu doesn't recognize it. In fact your BIOS doesn't recognize it and that's the same like it's not there. No OS will be able to recognize it.

---

### Post by wojox on 2010-06-05
Do you have a RAID set up?

---

### Post by makuab on 2010-06-05
ONE ****ing HDD NO raid. I already set it back to optimized defaults and NOTHING happened.
and i am sure the sata controller is not disabled, i've tried changing the modes (enhanced, combined, SATA only)

---

### Post by makuab on 2010-06-05
I think the hard drive is dead

---

### Post by wojox on 2010-06-05
Oh sorry for the confusion.

---

### Post by wojox on 2010-06-05
> **makuab said:**
> I think the hard drive is dead

Yeah if G-parted can't recognize it and you can't install anything on it, it's more than likely DEAD.

---

### Post by spareme on 2010-12-20
well, after a couple of months of searching, experimenting, going though every possible forum and blog related to this issue, i had almost given up ubuntu, however something clicked and i finally got ubuntu to work on this msi 915glm motherboard. Hope this help you guys too.

[LIST=1]
[*]Go to Bios settings
[*]Look for Integrated Peripherals
[*]Under Integrated Peripherals, look for Sata Devices Configuration
[*]Change Sata Devices Configuration to Enhanced Mode
[*]Press F10, save and quit
[/LIST]

Put in the live or alternate cd and install ubuntu normally.

Just making this minor change in bios settings worked for me, hope it works for you too.

All the best :D

---

