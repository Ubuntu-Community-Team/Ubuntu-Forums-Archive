---
title: "jaunty only boots read only"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Paul S on 2009-02-21
I can't get a boot to go normally today.  Actually, I got in once on the old kernel, uninstalled & reinstalled 2.6.28-8 (thinking maybe something was wrong with it), did updates, and now I can't get it to mount rw on either kernel.  It just boots up and hangs because it's read only.  I did a fsck (reiserfs) and it was clean.  I've accessed it successfully from another partition.

Weird.  Any ideas?  Guess it's time to reinstall again.

---

### Post by conehead77 on 2009-02-21
Does it really hang or can you get on the command line? I had a similar error and i could solve the dilemma with
```

mount -o remount,rw /

```

---

### Post by FranciscoBorges on 2009-02-22
I have had the same. Using a Asus P5N7A-VM motherboard.

I discovered that I can still boot with 2.6.28-6, but the system hangs for 1.5min before resuming and booting normally.

---

### Post by Paul S on 2009-02-22
I guess it's this udev bug [https://bugs.launchpad.net/ubuntu/jaunty/+source/udev/+bug/325690](https://bugs.launchpad.net/ubuntu/jaunty/+source/udev/+bug/325690)

If you can hang on for the fix, you won't have to reinstall.

---

