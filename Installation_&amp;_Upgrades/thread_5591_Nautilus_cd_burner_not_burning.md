---
title: "Nautilus cd burner not burning"
date: 2004-11-20
forum: Installation &amp; Upgrades
---

### Post by mal on 2004-11-20
After fiddling around to get scsi emulation working on Warty, Nautilus still refuses to respond to a blank cd in the drive and only offers the file image option when trying to burn a cd.  The /dev/sr0 device has been created and has its group set to cdrom and I am a member of this group.  I can successfully mount /dev/sr0 to read cds.

Note that I can record a cd using cdrecord, with no problems.

Any ideas on how I can get Nautilus to recognise the burner?

Regards,

Mal

---

### Post by az on 2004-11-20
You have a scsi burner?

Do you have k3b installed?  K3b really screwed up my cdrecord permissions ans such so that it did not work anymore.

---

### Post by mal on 2004-11-20
[QUOTE=azz]You have a scsi burner?

Do you have k3b installed?  K3b really screwed up my cdrecord permissions ans such so that it did not work anymore.[/QUOTE]

My CD is an IDE drive (vendor: HL-DT-ST Model: CD-RW GCE-8525B).  I have loaded ide-scsi to provide scsi emulation.

I have not loaded K3b as I was hoping to be able to burn CDs with Nautilus and avoid loading another app (I would like to keep things simple for other users of the computer).

As I have been able to burn with cdrecord, I assume it is OK.

Thanks,

Mal

---

### Post by wallijonn on 2004-11-26
What is available under SPM? It should have installed [COLOR=Red]nautilus-cd-burner[/COLOR], but you may want to re-install it.

---

### Post by mal on 2004-11-27
[QUOTE=wallijonn]What is available under SPM? It should have installed [COLOR=Red]nautilus-cd-burner[/COLOR], but you may want to re-install it.[/QUOTE]

Yes - nautilus-cd-burner is installed.  However, I will take up your suggestion to re-install it.

I will be away for a week or so and will not be able to try this until then.  I'll post the result.

Thanks for the suggestion.

Mal

---

### Post by mal on 2004-12-18
I still havn't resolved this.  I have removed the scsi emulation settings and can burn CDs with cdrecord using dev=/dev/hdc.  I have also tried a re-install of nautilus-cd-burner.  However, nautilus still refuses to recognise that I have a cd burner device.

Somewhere there must be a configuration entry that tells nautilus which device to use for burning CDs.  It would be appreciated if anyone can give me a clue to fix this.

Thanks,

Mal

---

### Post by topcop on 2004-12-20
nautilus recognises my burner but gnomebaker cant. Can someone help please?  ](*,)

---

