---
title: "Opera browser takes a long time to to open and load on Ubuntu 22.04.2 LTS"
date: 2023-07-04
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2023-07-04
Running Opera One(version: 100.0.4815.21)
Opera is up to date

Opera opens and loads within seconds on Windows 10 but takes around 45 seconds to load on Ubuntu. 

Anyone know why?

---

### Post by Holger_Gehrke on 2023-07-04
Would that be the snap package of Opera ? Then it's normal. snaps are basically compressed file systems masquerading as packages. On first start it has to decompress the better part of 190 MB. If you close it and start it again later most of it is still in cache and therefore starts a lot faster. But that first start is slow. Firefox suffered from a similar problem until they switched to a different compression which is faster to decompress. There supposedly is a repository for installing Opera as a classic Debian package.

Holger

---

### Post by cybrsaylr on 2023-07-04
Don't know if it is  a snap package of Opera, probably is.

Just shut down Opera and reopened Opera and it took 95 seconds to open again! It's a real pain.

Firefox and Chromium take only a couple seconds to open.

I click on Ubuntu Software, which shows; Chromium needs to be updated to Chromium 114.0.5735.198

When clicking on Update get this message: 
Unable to Update Chromium:  
snap has no updates available

Firefox was in Ubuntu Software also needing to be updated and updated fine.

---

### Post by Rubi1200 on 2023-07-04
If it is a snap this command should show info including version:
```
snap info opera
```

---

### Post by cybrsaylr on 2023-07-04
Rubi1200

Here's what I get for: code, snap info opera

> Desktop$ snap info opera
name:      opera
summary:   Fast, secure, easy-to-use browser
publisher: Opera (opera-software&#10003;)
store-url: [https://snapcraft.io/opera](https://snapcraft.io/opera)
license:   unset
description: |
  Try the Opera browser - now with a built-in ad blocker, battery saver and
  free VPN.
commands:
  - opera
snap-id:      AljMvoQbHtnnrka00lIoxHJ6Qhfn0X8m
tracking:     latest/stable
refresh-date: 7 days ago, at 10:42 EDT
channels:
  latest/stable:    100.0.4815.21 2023-06-27 (242) 192MB -
  latest/candidate: &#8593;                                    
  latest/beta:      &#8593;                                    
  latest/edge:      100.0.4815.30 2023-06-29 (244) 195MB -
installed:          100.0.4815.21            (242) 192MB -

---

