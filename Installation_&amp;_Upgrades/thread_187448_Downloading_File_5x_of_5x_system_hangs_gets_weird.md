---
title: "Downloading File 5x of 5x system hangs gets weird"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Grafster on 2006-06-03
Trying to download through the Update Manager (Breezy -> Dapper)
On the Prepering the Upgrade stage it downloads around 50 files... it gets to 53 of 53 and then goes all spastic.
The numbers after the 5 change. So first its 58 of 58 then 53 of 55 then 55 of 57... it does this for an hour or so. Then quits out with an error.

If it were just the servers being hammered and not able to download the files that would be fine but the number hopping makes me think its something else.

Are there plans to get the Update Manager fixed at some point (maybe so it lets you click on the terminal box and see what its downloading...) or is this all she wrote?

---

### Post by Grafster on 2006-06-03
The error message is:
(but this doesn't explain the number hopping and why does it leave you sitting there for an hour?)

Failed to fetch [http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release.gpg](http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release.gpg) Connection failed
Failed to fetch [http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/binary-i386/Packages.gz](http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/binary-i386/Packages.gz) Could not connect to seveas.ubuntulinux.nl:80 (83.160.7.26), connection timed out
Failed to fetch [http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/source/Sources.gz](http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/source/Sources.gz) Could not connect to seveas.ubuntulinux.nl:80 (83.160.7.26), connection timed out

---

### Post by Grafster on 2006-06-03
Anybody?

---

