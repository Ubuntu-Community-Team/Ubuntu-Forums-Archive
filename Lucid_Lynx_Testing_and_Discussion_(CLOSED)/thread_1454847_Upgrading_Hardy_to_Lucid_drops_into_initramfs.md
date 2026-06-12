---
title: "Upgrading Hardy to Lucid drops into initramfs"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mister_p_1998 on 2010-04-15
Did an update manager upgrade from Hardy to Lucid today, now when booting, gets to initramfs and stops. One thing I may have done wrong was to tell the system to keep the old mnu.lst, other than that I cant see what I've done wrong, can this install be repaired?
Steve

---

### Post by mister_p_1998 on 2010-04-15
Fixed it!
I had to boot off a live CD and edit /boot/grub/menu.lst and manually type in the correct kernel to load (VMlinuz-2.6.32.20-generic) then run update-grub. I re-booted and it all seems to work!
Remember guys, select "Install Package Maintainer Version" of Menu.lst when running the update.
Steve

---

