---
title: "I/O error"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by lanp900 on 2007-02-27
I was trying to boot Ubuntu for the first time but there was an error that read:

[17179702.66400] Buffer I/O error on device hdb, logical block 296155


Any input will be helpful

---

### Post by tgalati4 on 2007-02-27
Welcome to the community.

Was this a new large-capacity drive?

Was this a 5-year-old laptop drive?

Was this an atticware machine that hasn't been turned on for 4 years?

Was this the 4th drive hung off of a Promise ATA controller?

---

### Post by Co.Sinecure on 2007-03-05
Hi, 

I'm getting the same problem each time i boot on my work machine (20gb, dual boot w/ win2k).
Ubuntu starts fine after that, but it makes me worried...

in response to tgalati4: None of the above.

---

### Post by tgalati4 on 2007-03-05
Post the specs of your machine and what version of Ubuntu that you installed.

In the meantime, boot the live CD

Open a terminal

sudo fsck /dev/hda1
sudo fsck /dev/hda2
sudo fsck /dev/hda3

Follow the prompts to correct errors (if any)

---

