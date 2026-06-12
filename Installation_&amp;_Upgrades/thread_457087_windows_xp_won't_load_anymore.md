---
title: "windows xp won't load anymore"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by jon.reeve on 2007-05-28
I just installed ubuntu onto my laptop by using my windows xp desktop to install to an external SCSI drive that I later removed and put into the laptop. The problem this created is that somehow there's a grub loader in the master boot record of the desktop (which should only be running windows xp), and every time I start up the desktop it reports

GRUB Loading stage1.5
Error 21

which I take to mean that the master boot record is looking for GRUB on the external HD and can't find it. 

How can I restore my master boot record for windows XP? I have my XP recovery disk, and I tried running fixmbr but I get a message saying I have a nonstandard partition table and that I therefore shouldn't try rewriting the mbr unless I have troubles accessing the disk. So I definitely don't want to run fixmbr unless I know for sure that it won't make my HD totally inaccessable. This might have something to do with the fact that it's a DELL with a utility partition before the main partition. 

I don't want to have to reinstall XP altogether. Is there another way I can fix the master boot record on XP?

---

