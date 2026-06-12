---
title: "Help - Install ubuntu on new laptop"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by kiv on 2007-08-23
Hi!

I have just purchased a new laptop with vista and I wish to install ubuntu on it using the entire hard drive. After using ubuntu for 8 months on my pc I cannot live with windows any more,

However, when running the live install I get this error on the 7th step just after I click "Install"

"file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."

I have tried briefly setting up the partitions manually but resulted in the same error.

What do I do? .. Thank you!!

---

### Post by merlinus on 2007-08-23
Try gparted live cd to completely erase all partitions and start afresh.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by Pumalite on 2007-08-23
Use DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/) Then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and make one large partition of your hard drive; formatted ext3 if you want. Then install : Guided> Use Entire Disk.

---

### Post by kiv on 2007-08-23
> **merlinus said:**
> Try gparted live cd to completely erase all partitions and start afresh.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

Thanks!

Could I download gparted on the ubuntu live cd and do it that way ?

---

### Post by Pumalite on 2007-08-23
Gparted, the stand alone program is better

---

### Post by kiv on 2007-08-23
> **Pumalite said:**
> Gparted, the stand alone program is better

so the gparted live cd is best.. or downloading it while running the ubuntu live cd?

---

### Post by Pumalite on 2007-08-23
The Live CD comes with gparted, but I recommend that you use link provided by merlinus and me to download the iso that you then burn as an image to a CD and later you boot from it and use as indicated.

---

### Post by merlinus on 2007-08-23
It is a bootable cd -- small download.  Burn it the same way as the live cd -- disk image, not data disk.

It is a newer version than the one on the ubuntu cd, with more features and capabilities.

Hopefully it can kill vista and let you install ubuntu.

-merlin

---

### Post by kiv on 2007-08-23
okay I will do that now!

thank you all!

---

### Post by kiv on 2007-08-24
I didn't need to use gparted in the end.

I rebooted and there was a message saying "missing operating system". So I tried Ubuntu again and it worked fine :)

Thank you.

---

