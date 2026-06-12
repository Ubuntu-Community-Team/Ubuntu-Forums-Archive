---
title: "Migrating Notes from nautilus"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by Maverickprowls on 2009-12-19
Hi there,

I've just upgraded to 9.10 on several machines, coming from 8.10 on a couple, and 9.04 on a third.  One of my friends stored a lot of info in the nautilus notes feature, and needs to recover that data for use in his shiny new Karmic install.

A little trawling on the web has found that the metadata is normally stored under ~/.nautilus/metafiles/ as xml files, and this is fine, I've located these folders on the backed-up /home partitions from the old machines.  My problem is that in 9.10 there doesn't appear to be a metadata folder under ~/.nautilus.  

I've tried adding some notes to some pre-existing files on the new install in case this would cause nautilus to generate the folder and its files, but to no avail.  Stat-ing the files reveals no modification time changes, nor change in bytesize, so I'm reasonably sure the notes aren't being added as metadata in the actual file somewhere.  Searching for recently modified files doesn't show up anything which appears relevant, so I'm at a loss.

Put simply, my question is this:  Does anyone know if Nautilus 2.28.1 (the version included in Karmic) stores the file metadata anywhere other than ~/.nautilus/metafiles/ and if so, could you please let me know where that is.

Thanks very much!

---

### Post by mal on 2009-12-23
Maverickprowls,

It seems that the new location for the notes and other metadata is "~/.local/share/gvfs-metadata/" .  I'm not sure about the storage format, or how the data is migrated during upgrade.

Regards,

Mal

---

### Post by SabreWolfy on 2010-01-05
> **mal said:**
> 
<snip>
It seems that the new location for the notes and other metadata is "~/.local/share/gvfs-metadata/"
<snip>

Confirmed in Karmic.

What a pity that Notes don't move with the file; kind of useless for any files on removable storage ...

---

### Post by mal on 2010-01-07
> **SabreWolfy said:**
> Confirmed in Karmic.

What a pity that Notes don't move with the file; kind of useless for any files on removable storage ...

I agree.  Notes are also not much use for folders that are shared between multiple users.  Each user can have their own notes, but cannot share notes for the same files.

Note that there are Extended Attributes available in most linux file systems.  These do stay with the file and can be seen by other users.  However, they are not really utilised in Ubuntu.  

Mal

---

### Post by SabreWolfy on 2010-01-07
Also the Nautilus Notes system appears to be [buggy]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/502020").

---

### Post by Maverickprowls on 2010-11-16
I rediscovered this thread after a good long time, and I'm sorry to say that I never thanked you all for your help.  I've managed to retrieve the metadata for my friend, and we're looking at ways of migrating it to his new 10.10 install.

---

