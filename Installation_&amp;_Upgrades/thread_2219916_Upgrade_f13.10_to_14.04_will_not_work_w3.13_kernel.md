---
title: "Upgrade f/13.10 to 14.04 will not work w/3.13 kernel but will w/last 3.11 from 13.10"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by BazBear on 2014-04-25
I did the same inplace upgrade of I've done for this Asus 1005ha netbook (1.8 ghz Atom, 2 GB RAM, 32 bit, dual boot with Win7) since I originally 12.04. All seemed to go well until it did the reboot after upgrade. At the splash screen (as well as when I try to boot from the advanced options for the 3.13 kernel in GRUB) on a straight boot into 14.04 I get...

```
serious errors were found while checking disk drive for for /. Press I to igore, S to skip mounting, M for manual recovery.
```

Ignoring it does nothing, skipping the mounting tells me the Temp partition isn't there or isn't set up, and I have no idea what to do in manual recovery.

That said, if I run the advanced options and select the last kernel from 13.10 (3.11.0-I can't recall the last digits) it boots up and runs fine. The system benchmark app also tells me I am running Lubuntu 14.04, it appears I have all the new features and icons etc. that I should have as well.

I tried using Synaptics to reinstall the native to 14.04 3.13 kernel, but that didn't help at all.

I'm literally using the OS right now, no real funkiness that I can detect, but I would really like to straighten this out if anyone has any ideas. (if you need more info just let me know what commands to run).

---

### Post by BazBear on 2014-04-26
The solution is in this thread [http://ubuntuforums.org/showthread.php?t=2218439](http://ubuntuforums.org/showthread.php?t=2218439)

I will note that the particular line in that config file where you change ro to rw may vary from the op's, so be cautious!

My line looks like this (the change has already been made).

```
linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=5000166F00165BF2 loop=/ubuntu/disks/root.disk rw
```

---

