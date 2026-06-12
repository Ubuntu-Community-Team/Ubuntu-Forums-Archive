---
title: "misplaced data?"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by jord1981 on 2012-01-28
I have an Ubuntu 11.10 installation that recently stopped booting to the GUI. I couldn't figure out how to fix it so I used the installation disc to try to get back on track. I chose 'upgrade from 11.10 to 11.10' in order to save ny files. My home folder remains as it was but my /var/www folder (where I had spent a lot of time coding a website) is gone. Is it possible that this data has just been moved/hidden or is it lost?

---

### Post by varunendra on 2012-01-29
AFAIK, 'upgrading' won't move any files/folders. So if it is not there, it most probably is gone :(

Try testdisk/photorec (in a live session to avoid further writing on the partition) to see if it can find something. If that directory is really important to you, I would suggest to STOP using the installed Ubuntu, since each booting attempt will increase the chances of the files being overwritten (which might otherwise be recovered with tools like testdisk).

---

### Post by jord1981 on 2012-01-29
I don't have test disk on my live cd, nor do I have internet access there. Suggestions?

---

### Post by varunendra on 2012-01-29
> **jord1981 said:**
> I don't have test disk on my live cd, nor do I have internet access there. Suggestions?
Yeah, just download its .deb package from [here]("http://packages.ubuntu.com/oneiric/testdisk") on some other computer, copy it to a USB drive, then install it from there when booted in a live session.

**PS: **you may have to download the dependencies as well, following the same page.

---

