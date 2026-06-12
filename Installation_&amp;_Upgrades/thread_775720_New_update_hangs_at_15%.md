---
title: "New update hangs at 15%"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by ruetheday on 2008-04-30
**[SIZE=5]     T[/SIZE]**here are updates in the update manager, however, it hangs when reaching 15%. 

            I have also used the terminal using sudo apt-get update and that hangs around the same place. 

 what do i do next[SIZE=7]**?**[/SIZE]

---

### Post by Pumalite on 2008-04-30
Is this an 'update' or an 'upgrade'. If so of what OS or from what OS to what other OS?

---

### Post by ruetheday on 2008-04-30
Ubuntu 8.04 LTS (Hardy Heron)

and it is an "Update"  using the update manager  or terminal command   sudo apt-get update

---

### Post by Pumalite on 2008-04-30
Is there an error message?

---

### Post by ruetheday on 2008-04-30
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (***.**.***.**), connection timed out

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2)  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2)  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2)  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2)  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2)  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2)  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_CA.bz2)  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_CA.bz2)  Unable to connect to ca.archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by trginter on 2008-04-30
Same thing is happening to me, except I don't see a progress bar.  Update Manager says there are two updates, libgtkimageview0 and libkdcraw3.  This happened after I upgraded to the new Ubuntu version.  The Update Manager screen is greyed out and won't let me exit out of it.

---

### Post by Pumalite on 2008-04-30
Check your connection and try changing Server if your connection is OK:
System>Administration>Software Sources>Download From>Other>Let it choose the best mirror for you.

---

### Post by Pumalite on 2008-04-30
Post:
cat /etc/apt/sources.list

---

### Post by ruetheday on 2008-04-30
[COLOR=Gray]> **Pumalite said:**
> Check your connection and try changing Server if your connection is OK:
System>Administration>Software Sources>Download From>Other>Let it choose the best mirror for you.[/COLOR]

Yes this was the problem!!  I think UWO in london may have a problem, or are slowing traffic....  this Ubuntu REVOLUTION is tearing up servers baby!!!!

---

### Post by trginter on 2008-04-30
> **Pumalite said:**
> Check your connection and try changing Server if your connection is OK:
System>Administration>Software Sources>Download From>Other>Let it choose the best mirror for you.

That did it!  Thanks!

---

### Post by Pumalite on 2008-04-30
You are welcome. Good luck.

---

