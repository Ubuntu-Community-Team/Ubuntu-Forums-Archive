---
title: "Will this work: copy ubuntu from HDD to SSD"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by pir on 2010-08-14
If I buy an SSD (OCZ Vertex 2 OCZSSD2-2VTXE60G 60GB), will this work?

[LIST=1][*]Power off PC, place SSD[*]Power on PC (which (only) has Ubuntu installed on it)[*]Format the SSD (through Disk utility?)[*]Clone my working disk to the ssd (via ddrescue)[*]Change GRUB to start from SSD
[/LIST]

I think it should work. What do you think? :)

---

### Post by ajgreeny on 2010-08-14
There will be a few other things to edit in order to get the SSD to boot at all, such as /etc/fstab.  By default this file now uses UUIDs and not /dev/sda etc, so the old UUID will now be incorrect, as I don't think that will be copied across with the ddrescue.  There may be other things as well, but I can't think of any at the moment.

Give it a try; if it does not work not a lot is lost except some time.  Backup everything first, just in case.

---

### Post by pir on 2010-08-14
Cool. So you think I should edit /etc/fstab. I might also have to change the bootloaders' startup HDD...

---

### Post by tommcd on 2010-08-14
To make this easy you may want to try the **Clonezilla** live CD. This is what Clonezilla is for:
[http://clonezilla.org/](http://clonezilla.org/)
[http://clonezilla.org/clonezilla-live/](http://clonezilla.org/clonezilla-live/)
Clonezilla live CD should allow you to clone your HDD to the SDD.

---

### Post by slakkie on 2010-08-16
> **ajgreeny said:**
> There will be a few other things to edit in order to get the SSD to boot at all, such as /etc/fstab.  By default this file now uses UUIDs and not /dev/sda etc, so the old UUID will now be incorrect, as I don't think that will be copied across with the ddrescue.  There may be other things as well, but I can't think of any at the moment.

Give it a try; if it does not work not a lot is lost except some time.  Backup everything first, just in case.


You can still use the old notation though, but changing the fstab is required, whatever notation is used.

---

