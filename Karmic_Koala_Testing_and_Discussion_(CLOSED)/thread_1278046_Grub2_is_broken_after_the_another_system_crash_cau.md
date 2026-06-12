---
title: "Grub2 is broken after the another system crash caused by xl2tpd"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Joe_Bishop on 2009-09-29
Well, the system hung up, so I need to manually reset it. Grub2 refuses to load any linux listed in a menu after the reboot but tells: "invalid environment block". I've checked FS with fsck from LiveCD, it's clean. How can I repair it?

---

### Post by ranch hand on 2009-09-29
Can you boot in recovery?

Is this the only Ubuntu OS on your box?

---

### Post by Joe_Bishop on 2009-09-29
> **ranch hand said:**
> Can you boot in recovery?

Is this the only Ubuntu OS on your box?
No, I said I couldn't boot in ANY linux from the menu, including recovery one. I have also Windows XP, which boots OK.

---

### Post by kamrog on 2009-09-29
Hi,
same problem here after the last sudo-apt upgrade.

I can't run it in recovery as well.

---

### Post by ranch hand on 2009-09-29
What are the other linux OS' on your box?

---

### Post by Joe_Bishop on 2009-09-29
Only one, I meant common boot and recovery boot.

---

### Post by VMC on 2009-09-29
> **Joe_Bishop said:**
> Well, the system hung up, so I need to manually reset it. Grub2 refuses to load any linux listed in a menu after the reboot but tells: "invalid environment block". I've checked FS with fsck from LiveCD, it's clean. How can I repair it?

From reading some grub2 patches, I found this:
"...environment block support, which can be used to locate
root device using uuid or label"

That tells me something going on with using uuid. Output one of the menuentry's and "sudo blkid"

---

### Post by gali98 on 2009-09-29
You could always use an older ubuntu to disk to reinstall grub...
Kory

(edit: grub-legacy that is)

---

### Post by Joe_Bishop on 2009-09-30
> **VMC said:**
> From reading some grub2 patches, I found this:
"...environment block support, which can be used to locate
root device using uuid or label"

That tells me something going on with using uuid. Output one of the menuentry's and "sudo blkid"
No, uuids are the same.

---

### Post by Joe_Bishop on 2009-09-30
> **gali98 said:**
> You could always use an older ubuntu to disk to reinstall grub...
Kory

(edit: grub-legacy that is)
Yeah, it seems I need to do this: install old good grub instead of buggy grub2 :)

---

### Post by Joe_Bishop on 2009-10-01
I've found out it wasn't FS corruption bug, but newest GRUB2 one, because of the newest feature, "environment block". Although I'm on old grub now, so I can't check it anymore.

---

