---
title: "Hibernate to swap file on LUKS"
date: 2017-03-08
forum: Installation &amp; Upgrades
---

### Post by Tim474 on 2017-03-08
Hello. [Here]("https://ubuntuforums.org/showthread.php?t=1042946") is instruction how to use swap file for hibernate. But I want to use a swap file that is on the encrypted volume. I tried to follow this instruction but computer doesn't resume.

Is it possibe? If it how can I setup it?

---

### Post by DuckHook on 2017-03-09
The howto you link to is seven years old and covers a version that is long dead. Try these instructions from the official wiki: [https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap)

**CAUTION**

There is a reason that hibernation is disabled by default: many on these forums have run into file and disk corruption using it. It is especially problematic if you dual boot and unknowingly share a swap file between two distros. Even more dangerously, it creates problems for network shares including unreleased locks to other users, corrupted files and broken databases. Dual booting Windows will also lead to bad things happening.

Using the above instructions, I used to have an encrypted swap set up for hibernation a few years ago on a 14.04 install until I corrupted a database on a network share. Fortunately, I back up religiously, so I only lost a day's work, but I don't use hibernation any more for that and other reasons.

Consider yourself warned by one who has personally suffered the consequences.

---

### Post by Tim474 on 2017-03-09
It's for separated swap partition. I did it on another computer (where I encrypt only /home, not /). But on another computer (where / is encrypted) I want to use swap file instead swap partition. Is it possible?

---

### Post by DuckHook on 2017-03-09
> **Tim474 said:**
> …Is it possible?I don't really know, but if you asked me to guess, I would have to say that I don't think so. Consider: swap is set up early in the boot process at the fstab stage. But the user doesn't log in until very late in the process. The point of whole-disk encryption is keep the disk encrypted until the user successfully answers the challenge/response.

When swap has its own partition, the workaround is to create a new random password each time for the swap partition. The system can do this without waiting for the user. But if swap is a file in a wholly encrypted disk, then this strategy won't work. The disk must be decrypted by the user before any file is accessible.

I suppose that one could set swap to manual, then write a script to turn it on only after user login, but such a script would break hibernate because resuming from hibernation occurs before file decryption.

---

