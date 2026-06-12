---
title: "Installed 10.04 and now I can't boot XP"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by yamis on 2010-05-25
I have just installed Ubuntu 10.04. It works fine, but if I try to boot into XP. I got error after booting screen something like that: 
"A problem has been detected and Windows has been shut down to prevent damage to your computer. 
If this is your first time....
...
...
Technical information:

*** STOP: 0x0000007B (0xF78AE524, 0xC0000034, 0x00000000, 0x00000000)"

I add my result file.

So what to do to repair everything?

Thanks in advance

---

### Post by darkod on 2010-05-25
It seems your XP partition got corrupted, maybe if there was a resize done.

You can try and force a chkdsk on it from ubuntu by using ntfsfix:

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1

That can't really repair it, it will only do some basic checks. But it should force a disk check by the windows tool chkdsk next time you try to boot XP. So just reboot and select XP in the menu and hopefully it will start a disk check.

---

### Post by yamis on 2010-05-25
Well I did it. Now I will reboot PC...

And same >.<" So what do I have to do to repair it?

---

### Post by darkod on 2010-05-25
> **yamis said:**
> Well I did it. Now I will reboot PC...

And same >.<" So what do I have to do to repair it?

If that didn't work, I have no clue. This is a windows error it has nothing to do with ubuntu.

Maybe search for windows forums and guides, how to run some checks on it.

You can also try a repair function from the XP install cd.

---

