---
title: "Is boot log saved?"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2007-06-24
When booting, I see lots of messages, and I do not see those messages in the system log.

Where are the messages issued during a boot saved?

---

### Post by thelinuxguy on 2007-06-24
I guess dmesg prints out the boot logs. If you want to save it somewhere, redirect the output
```

dmesg > boot.log

```

---

### Post by Howard Kaikow on 2007-06-24
> **thelinuxguy said:**
> I guess dmesg prints out the boot logs. If you want to save it somewhere, redirect the output
```

dmesg > boot.log

```

Is there a file in which I have to insert that instruction?

---

### Post by thelinuxguy on 2007-06-24
> **Howard Kaikow said:**
> Is there a file in which I have to insert that instruction?

Open a terminal and run it.
(Applications >> Accessories >> Terminal)

The entries seem to be same as those under kern.log in System Log Viewer.

---

### Post by Howard Kaikow on 2007-06-24
Unfortunately, certain messages that appear during a boot are not included in the file produced using dmesg.

The messages are stating something like "there are differences between the boot sector and its backup".

I can believe that due to the [shennanigans that were used to create the boot sector]("http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=21;t=5731").

This caused me to want to see the actual messages, perhaps there's a way to eliminate the issue by recreating the backup of  the boot sector?

I would think that those messages are logged somewhere.

---

