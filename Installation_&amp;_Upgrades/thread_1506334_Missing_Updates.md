---
title: "Missing Updates"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by jarviser on 2010-06-10
In general, as well as in this particular instance, what do I do if the Update Manager tries to download packages that are apparently "Not Found"?

like this week...

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox-plugin-cdrecorder_0.12.8-0ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox-plugin-cdrecorder_0.12.8-0ubuntu5_i386.deb)
  404  Not Found
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox-plugins_0.12.8-0ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox-plugins_0.12.8-0ubuntu5_i386.deb)
  404  Not Found
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.12.8-0ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.12.8-0ubuntu5_i386.deb)
  404  Not Found

---

### Post by Peter09 on 2010-06-10
This is to do with your repositories. What version of UBuntu are you using, and are you sure you were online at the time.

---

### Post by jarviser on 2010-06-10
Ubuntu 10.4 LTS as per sig.

Yep online, because I also installed >100MB of other updates. Tried this last three Rhythmbox updates 3 times at different times of the day.

I wonder is the "gb" file prefix a Great Britain archive which may have some files missing, or be completely missing? Can I choose an alternative archive and if so, how?

Thanks.

---

### Post by jarviser on 2010-06-10
OK I went into Settings in Update Manager and changed the first tab to use the "Main server" rather than "United Kingdom Server" and I checked the three Rhythmbox updates and installed them, then reverted to UK Server.

Must be missing on the UK (=gb) archive.

Thanks for pointing me in that direction.

---

