---
title: "Any way round update that asks: Please insert the disk..."
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by Jamface on 2011-04-02
I have Ubuntu 10.04 dual boot with XP on my desktop machine.  Now, when I run Update Manager a few seconds into the update process I get the message:
Please insert the disk labelled: Lubuntu 10.10_Maverick Meercat_.i386(20101010) in drive /cdrom/

I do remember having a look at Lubuntu some time ago but I have no idea now which disk I was trying to run as LiveCD at the time.

Why does Update Manager want this disk?  Is there any way I can delete or bypass this request, i.e stop it arising in the first place?  If I cancel the request I get a list of error messages all starting with variations on the theme: W:failed to fetch cdrom ....

---

### Post by Quackers on 2011-04-02
Untick the cdrom entry in Software Sources.

---

### Post by howefield on 2011-04-02
Try going to System > Administration > Synaptic Package Manager > Settings > Repositories > Other Software tab and deselect any checks in the "Installable from CD-ROM/DVD" options box.

---

### Post by Jamface on 2011-04-03
Many thanks for the help.  Problem solved.  Updates installed.

---

