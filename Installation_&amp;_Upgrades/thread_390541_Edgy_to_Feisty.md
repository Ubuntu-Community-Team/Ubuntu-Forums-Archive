---
title: "Edgy to Feisty"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by Carlton1 on 2007-03-22
Hi,

I have just used the official upgrade method to get to Feisty.  Everything has gone well untill re-boot.   The screen just hangs, with the status bar right at the beginning.

Any suggestions?

Many thanks,

Carlton.

---

### Post by lukew on 2007-03-22
> **Carlton1 said:**
> Hi,

I have just used the official upgrade method to get to Feisty.  Everything has gone well untill re-boot.   The screen just hangs, with the status bar right at the beginning.

Any suggestions?

Many thanks,

Carlton.

Remove the quiet option from the grub parameters. This will let you know where it is getting stuck. You might beable to Ctrl-C to cancel the process which is failing to init. You can also check your logs.

Luke

---

### Post by Carlton1 on 2007-03-22
Luke,

Sorry, can you explain how to do that?

Thanks,

Carlton.

---

### Post by lukew on 2007-03-22
> **Carlton1 said:**
> Luke,

Sorry, can you explain how to do that?

Thanks,

Carlton.

There is a quiet option in your grub file for you current kernel. I would remove it. It will give you verbose.

```
/boot/grub/menu.lst
```

Luke

---

