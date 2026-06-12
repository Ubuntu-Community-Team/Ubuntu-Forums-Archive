---
title: "HARDY: The available CD is not an Ubuntu CD!"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by brendancaulfield on 2008-04-25
Hey All,

We have been waiting for some features available in Hardy so we were excited to see the official release date for 8.04 finally arrive.  In my environment, we have many Ubuntu servers and continue to add them.  As such, we have created a custom install ISO by creating several Preseed files and modifying the isolinux.cfg.  This evening, I downloaded the new ISOs (8.04), moved all of my preseeds and modified isolinux.cfg into place and started a new install.  Unfortunately, the install dies right after the CD-ROM detection.  The console window reports the following message:

cdrom-detect: The available CD is not an Ubuntu CD!

Has anyone else experienced this?  Were you able to work around it?  Has there been a change in how preseeded install should be handled?

Any input would be greatly appreciated - this is a show stopper for us!

Thanks in advance,

Brendan

---

### Post by FredB on 2008-04-25
Just try using torrent. And burn your CD at a slow speed.

---

### Post by brendancaulfield on 2008-04-25
Thanks for the response.  Unfortunately, there is nothing wrong with the ISO as I am able to install via the downloaded file.  The problem occurs once I modify the ISO to include my custom preseeds and isolinux.cfg.

I wonder if it is failing because of a checksum mismatch... the console does not give much information (just the message stated in the subject of this thread).

Thanks again,

Brendan

---

### Post by brendancaulfield on 2008-04-25
PROBLEM SOLVED - Dumb Mistake

So, (1) I mounted the ISO, (2) copied it to a directory I could write to, (3) modified the directory structure by adding my custom preseed files and isolinux.cfg, and (4) rebuilt the ISO.

The problem was I missed the .disk in step 2.

Sorry.

Brendan

---

