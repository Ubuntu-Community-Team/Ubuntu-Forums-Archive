---
title: "Boot issues after migration to hyper-V"
date: 2016-01-10
forum: Installation &amp; Upgrades
---

### Post by ben193 on 2016-01-10
Hi, 

I took a backup of my Ubuntu 15.10 installation via CloneZilla, then restored it to a hyper-v host. The restore went successfully but I'm unable to boot - it launches into Emergency mode where I can view my files from the CLI. I have attempted to fix GRUB with a boot-repair disk but still not able to boot. My pastebin link is [here]("http://paste.ubuntu.com/14461681/"). Is anyone able to shed any light on what I should do to fix this?

Thanks in advance

---

### Post by ben193 on 2016-01-10
Mmmm, solved this one myself. I had a USB drive connected and mounted at startup. I commented out the line in /etc/fstab and booted successfully.

---

