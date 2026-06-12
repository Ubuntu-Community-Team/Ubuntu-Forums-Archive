---
title: "order of operating systems in GRUB"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-12-31
Is the last O/S that was installed on a system the first one that is called/listed in GRUB or is it the last one called ?

If I install Dapper then come back and install Edgy, which will boot by default ?

Thanks.

---

### Post by raul_ on 2006-12-31
I think you can simply change the order in /boot/groob/menu.lst

---

### Post by wpshooter on 2006-12-31
> **raul_ said:**
> I think you can simply change the order in /boot/groob/menu.lst

Thanks, I know I can change them but which one would boot by default if I installed first Dapper then Edgy ?

Thanks again.

---

### Post by raul_ on 2006-12-31
Since Ubuntu's installation messes with those settings, i think Edgy would be the default

---

### Post by moma on 2006-12-31
If you install Edgy after Dapper:
Edgy will install its own /boot/grub/menu.lst which will become the current one (be in charge).   Edgy's menu.lst will also include all lines from Dapper's menu.lst.

Just edit the Edgy's menu.lst and change the order of menu lines (titles and their definitions).  You can also change the default menu selection (0 is the first,  1 is the second title etc).

[COLOR="Green"]default     1    [/COLOR]

---

