---
title: "cupsys broken on update"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by andy8080 on 2006-08-23
I all,

I have a remote printer - a brother HL1430 connected via IPP protocol.

This was working fine until I updated the clients via apt recently.

Looks like the cupsys version 1.2.2-0ubuntu0.6.06_i386 broke it - instead of printing the document I just get a bunch of printer-control codes (this happened on two different machines).

I downgraded cupsys back to version 1.2.1-0ubuntu2_i386 and everything is OK again. (Note this is on the client machines not the server - it is unchanged - a stock debian install)

Has anyone else had this problem?

BTW - I downgraded like so:

cd /var/cache/apt/archives
sudo dpkg -i cupsys_1.2.1-0ubuntu2_i386.deb

regards
- andy

---

### Post by dv_ on 2006-08-27
Do you mean these codes? [http://www.ubuntuforums.org/showthread.php?t=244942](http://www.ubuntuforums.org/showthread.php?t=244942)

---

### Post by gborzi on 2006-08-27
This problem has been discussed (and partially fixed) in this thread: [http://www.ubuntuforums.org/showthread.php?t=230914](http://www.ubuntuforums.org/showthread.php?t=230914)

---

### Post by tagra123 on 2006-08-27
I had a similar problem Here's how I worked around it until it gets fixed:

[http://ubuntuforums.org/showthread.php?p=1428724#post1428724](http://ubuntuforums.org/showthread.php?p=1428724#post1428724)

---

### Post by andy8080 on 2006-08-28
> **dv_ said:**
> Do you mean these codes? [http://www.ubuntuforums.org/showthread.php?t=244942](http://www.ubuntuforums.org/showthread.php?t=244942)

Yes - that is the sort of thing I got...

---

