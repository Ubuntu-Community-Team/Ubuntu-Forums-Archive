---
title: "Weird error messages during bootup"
date: 2004-11-14
forum: Installation &amp; Upgrades
---

### Post by tidalwav1 on 2004-11-14
Whenever the system is booting up Ubuntu, the following messages appear after the screen displays "starting hotplug subsystem":

modprobe: FATAL: error inserting pciehp (<path to module would be here>) (operation not permitted)
modprobe: FATAL: error inserting shpchp (<path to module would be here>) (operation not permitted)

There is about a 30 second period when nothing happens while these messages are displayed, and then the system continues through the bootup sequence like nothing ever happened. Is there a way to get rid of these messages?

---

### Post by tog on 2004-11-14
I don't remember the post, but this appears to be normal in the sense that it will give Fatal error messages, but actually everything is normal. There was a post elsewhere that they are trying to suppress these errors, but nothing resolved yet. 

Murali

---

