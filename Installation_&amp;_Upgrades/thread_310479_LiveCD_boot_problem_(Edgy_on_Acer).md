---
title: "LiveCD boot problem (Edgy on Acer)"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by Leed on 2006-12-01
Strange enough I had this already running, but I can't figure out what was different at the time...

I'm setting up Ubuntu for a younger brother of mine, originally I could boot from the edgy liveCD, but not install, because it doesn't recognise SATA disks. In the end I added a IDE Disk into the pc and set up Dapper there, then upgraded to Eft. Unfortunatly this compromised the dual boot with Windows on the SATA. 

I've found out I can boot with SATA by adding "acpi=force irqpoll" into the boot options of the CD. My plan is now to remove the ide disk and have all systems running on the faster and quiter sata disk. I remember managing to boot previously with dapper on that system using irqpoll and seeing the sata disk. However now it doesn't work any more. 

Dapper still works, but can't handle the sata disk, the edgy disk work a day ago when installing it on my other brothers system, so I doubt it is corrupt. 

the booting now hangs with the following
```

[17179586.192000] hda : cdrom_decode_status: error=0x40 { LastFailedSense=0x04
[17179586.192000] ide : failed opcode was : unknown
[17179586.192000] hda : DMA disabled

```

Somethings must be wrong with the CDROM drive, I tried switching from Cable-Select to Master and back, no difference... I can't figure out what's wrong....

please help, that would get the number of Ubuntu systems I've installed up to 4.... and more to come ;) 

Dave

---

