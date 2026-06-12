---
title: "RAID config options - what do you think is best?"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by RandomJoe on 2006-12-19
I am about to rearrange my server storage, and have several options on just how to do it.  I would like to know if anyone has thoughts or suggestions on what would be best!

I currently have four 300GB drives on a SATAII 150 TX4 PCI controller card.  I'm using software RAID5 on them, been working wonderfully!  (So why am I messing with it...?!? ;) )

I just assembled a new desktop that uses an ASUS P5N32-SLI SE Deluxe motherboard, and it's an absolute screamer compared to the machine the RAID is currently in.  I intend to move the RAID to this machine.  The motherboard has five SATA connections on the mobo (six, actually, but one is on the back panel) - four are part of the nVidia chipset, the other is a Silicon Image SiI 3132 controller.  I want to have a non-RAID (or, at least separate from THIS set) system drive.  So this gives me four options:

[LIST]
[*]The system wants to boot off the nVidia SATA, so I could put the system disk as the first drive there, then three of the RAID drives, with the fourth on the SiI controller.
[*]I could use a PATA system drive, and hang the whole array off the nVidia chipset.
[*]Leave the RAID array on the PCI card, installing the card into this machine as well (for a total of THREE SATA controllers!)
[*]I suppose I could also hang a SATA system drive off the PCI controller, and put the RAID on the nVidia chipset.  (I don't think I can boot from the onboard SiI chipset - need to check though.)
[/LIST]
Any thoughts on what might be better?

I'm not keen on using a PATA system drive, although I don't really know just how much of a speed increase the SATA gives me there.  I assume it isn't insignificant.  My inclination is just to hang everything off the motherboard ports, and one of the four RAID drives will be on the SiI chipset.  I'm sure it would work fine, I'm just wondering about performance.  And I am also assuming the PCI card would be slower than the onboard controllers as well.  (Although the drives are probably the biggest bottleneck...)

Edit:  NOW I read the detailed forum description...  Perhaps this should be in "Hardware" or maybe "General"?!?  Oops!...

---

