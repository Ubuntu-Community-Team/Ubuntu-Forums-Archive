---
title: "Reusing partitions"
date: 2005-06-13
forum: Installation &amp; Upgrades
---

### Post by spiffytech on 2005-06-13
OK, I want to instal Ubuntu on my computer. I am currently running SimplyMepis 3.3, and waht to keep all of my data, applications, and settings that I have. Can I do this? Will I be able to transfer my kmail emails to evolution?

---

### Post by trivialpackets on 2005-06-13
[QUOTE=spiffytech]OK, I want to instal Ubuntu on my computer. I am currently running SimplyMepis 3.3, and waht to keep all of my data, applications, and settings that I have. Can I do this? Will I be able to transfer my kmail emails to evolution?[/QUOTE]
 If you will be overwriting Mepis, then no, I don't believe you can, but I could be wrong on this.  It makes sense that you could not format but just overwrite the /, /bin, /home etc...but again, if you overwrite all of this, you'll likely be overwriting the very things you want to save.  So in short, no, I don't believe you can.  If it's a separate partition, then you may be alright, but it didn't sound like that is what you were talking about.

---

### Post by alastair on 2005-06-13
All your "user" config data is generally stored under your home directory i.e. under /home.

If you install Ubuntu, you do not need to format (or touch) your home directory - just choose to mount the partition "home" under /home. But "leave as is" (or whatever) i.e. no format, no new filesystem.

Note - you might still have a few issues - because Ubuntu's applications might ne different versions than you are used to. But, hopefully, the Ubuntu applications (e.g. KMail) will carry on using /home/<user>/. configurations as usual.

You might want to  copy/backup a few things to your home partition before an install/upgrade.

P.S. I (sort of) assume /home is a separate partition. If not, you cannot really do this.

---

