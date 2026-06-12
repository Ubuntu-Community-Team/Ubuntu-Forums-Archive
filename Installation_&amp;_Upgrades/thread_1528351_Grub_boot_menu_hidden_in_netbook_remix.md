---
title: "Grub boot menu hidden in netbook remix?"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by madiyaan on 2010-07-10
Hello,

I installed Ubuntu netbook remix 9.10 and it ran fine. However, the boot menu is hidden and by default it always boots into Ubuntu (I don't know.. maybe the timeout was 0).

I wanted to switch to a different kernel so I compiled a new kernel and installed it. But upon reboot it would always boot into the old kernel. So I updated grub and made the new kernel the default.

Now the new kernel is givine me a kernel panic and I can't access my system because the grub boot menu doesn't show anything (just boots into the newly compiled kernel and gives me a panic message).

I don't have a recovery cd/usb. Is there a way for me to somehow slow grub down or show a menu? Pressing esc at boot doesn't help. 

I think this is a netbook remix specific issue.

---

### Post by mikewhatever on 2010-07-10
Nope, nothing to do with the netbook remix. That's the way grub2 is configured. Anyway, holding the shift key should show the menu.

---

### Post by drs305 on 2010-07-10
Try holding down the SHIFT key during the first stage of the boot process. This should display your menu and allow you to choose another kernel. 

If you don't have additional menu items, you can edit the current kernel option by highlighting it and then pressing "e". Then change the kernel number to one you want (assuming it is installed) on the "linux" and "initrd" lines. Then boot with "CTRL-x".

---

### Post by madiyaan on 2010-07-10
Thanks. Pressing the shift key at the start worked!

---

