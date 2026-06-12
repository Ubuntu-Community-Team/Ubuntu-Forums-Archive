---
title: "Immutable bit"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by thirteen on 2007-08-07
Hi all,

Is there anything in the Ubuntu install that sets the immutable bit on system files? In particular, I'm wondering about stuff in /usr/bin like ls, rm, etc.

I tried to upgrade a system and got errors when dpkg tried to install. "Operation not permitted" when trying to replace these system files. 

I'm pretty much assuming the machine was hacked, but chkrootkit found nothing, so I thought I'd ask.

Thanks in advance.

---

### Post by kidders on 2007-08-08
Hi there & welcome,

> **thirteen said:**
> Is there anything in the Ubuntu install that sets the immutable bit on system files?Not as far as I'm aware. It not something that's very often used, since Ext2/3 are the only filesystems that support the concept, making it essentially useless.

> **thirteen said:**
> I tried to upgrade a system and got errors when dpkg tried to install. "Operation not permitted" when trying to replace these system files.If you can, you should put together some details and post a thread on this issue.

> **thirteen said:**
> I'm pretty much assuming the machine was hackedUnless you've done something blatantly daft with your box's security, that's very unlikely imo. Have you done something to put your box at risk, or maybe discovered something odd going on?

---

### Post by psusi on 2007-08-08
You also might have a corrupt filesystem.  Run a fsck -f on it from the livecd.

---

