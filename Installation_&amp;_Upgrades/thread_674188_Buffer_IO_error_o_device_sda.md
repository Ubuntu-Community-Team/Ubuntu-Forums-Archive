---
title: "Buffer I/O error o device sda"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by warnec on 2008-01-21
Hello! Recently (5 minutes ago) i wanted to install Ubuntu 7.10 Polish (don't know if it does make any difference, I don't think so) And during booting LiveCD it gave me a bunch of errors. I started like this: chose CD-ROM to be first boot device, then after restart, i chose to boot from CD. After waiting few minutes in front of the loading Ubuntu screen, it gave me this error in text mode:

```

[ 164.774278] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

```

Then, about 10 seconds later:

```

[ 164.774325] ata5.00 cmd c8/00:00:08:00:00:00/00:00:00:00:00/e0 tag 0cdb 0x0 data 4096 in

```

Then, these messages shown 2 times more (with about 10 second break between a new one)
After that (around 10 seconds again) I got:
```

[ 225.234980] Buffer I/O error on device sda, logical block 0

```

And then the two previous messages reappear. (Each  new one comes after 10 seconds)

Note: I'm only a human, I could have done some mistakes when re-writing this from computer screen. So sorry, if i ddi some. I still hope you can help me ;)

PS.: I have 4 partitions:

-20 GB one, Windows XP on it (Xp works fine) 

-20 GB one , raw (unformatted, I wanted to install Ubuntu on it)

-30 GB one, raw (unformatted, I wanted to install Mac OS X Leopard (:D) on it)

-227 GB one, NTFS (for my games etc.)

Strange thing is, Ubuntu already worked on that HDD (I suppose it causes problems)
I recently ahd problems with HDD and linux, but i thought it would be over as soon as i format everything (cause i changed my PC, only old DVD drive and HDD remained)

Hope you can help me :D I really wanted to use compiz fusion again :P

---

### Post by warnec on 2008-01-21
I heard that this error may be caused by dying HDD, but i think screenshot below explains that my HDD is not dying at all.

Edited 23.01:

Changing SATA cables (I heard that it might help) also didn't do it :( HELP ME!

---

