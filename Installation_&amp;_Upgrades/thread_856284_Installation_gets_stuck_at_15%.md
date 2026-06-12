---
title: "Installation gets stuck at 15%"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by august0 on 2008-07-11
i burned the default ubuntu into a cd.  i reboot with the cd inside.  i say install ubuntu.  i fill up the information and tell it to use the whole disk.  right now it is stuck at 15% and says "Detecting file systems..." . it has been like that for over an hour.  is that normal?  what can i do to make sure it works?

---

### Post by tech9 on 2008-07-11
> **august0 said:**
> i burned the default ubuntu into a cd.  i reboot with the cd inside.  i say install ubuntu.  i fill up the information and tell it to use the whole disk.  right now it is stuck at 15% and says "Detecting file systems..." . it has been like that for over an hour.  is that normal?  what can i do to make sure it works?

Do your hardware specs meet the system requirements?

---

### Post by VMC on 2008-07-11
Does it boot up okay with livecd, and just the install is the problem?
If that's correct, then first do a "Media check", then boot up the livecd.

Once booted go to  "Application > Accessories > Terminal", and type the following:

```
sudo fdisk -l
```

Also, I don't know if you can copy and paste , but the following will reveal your system specs:

```
sudo lshw -short
```

---

