---
title: "RAID + LVM with SCSI and IDE setup recommendations"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by diacono on 2007-07-02
Hi all,

I've collected some spares recently and would like to replace my old gentoo home server but I'm not too hot on RAID and LVM. Here are some background details.

[LIST]
[*]I will use gallery2 to server vast amounts of photos, used it as a UPNP MP3 server and as fileserver for videos, documents etc.
[*]I  have 3x identical 70Gb IDE drives and 1x 9Gb SCSI drive
[*]I would like to have a RAID-5 setup but also make good use of the SCSI drive performance wise
[*]I have not controller, so it would have to be software RAID
[/LIST]

Surely it would be better if my servers (apache, mysql, etc) ran off the SCSI drive and the bulk data of the 3 drives in RAID but I don't know how LVM fits in with this as I really want the flexibility of being able to increase the volume on demand. 

Also, I just don't trust drives that are 3+ years and if you anything like me, when was the last time you backed up your home data??!

So does anyone have any recommendations? For example, can you create raid with these 4 drives but also make sure that / is mounted on the scsi drive?

Many thanks...

---

