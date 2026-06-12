---
title: "archive.canonical.com unresolvable - packet loss"
date: 2014-10-10
forum: Installation &amp; Upgrades
---

### Post by spacechampion on 2014-10-10
Hello, I'm trying to upgrade from 12.04 to 14.04.1 and getting a big fat fail when the installer tries to contact archive.canonical.com to get the repositories, though it gets the upgrade tool just fine from the archive.

I tried to send the output of do-release-upgrade to a file so I can copy it here but apparently it starts another (viritual?) screen in the terminal for that, so I get nothing piped to my output file.

Using mtr-tiny I see packet losses on the final hops to canonical, typical >70% up to 100%
```

HOST: home.interplanetary.ca      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.1.1                0.0%    10    0.3   0.3   0.2   0.4   0.0
  2.|-- lo-100.lns02.tor.packetfl  0.0%    10    7.5   8.7   7.4  11.7   1.6
  3.|-- ae1_2150-bdr04-tor.teksav  0.0%    10    6.7   7.1   6.7   7.5   0.2
  4.|-- 10ge2-1.core2.tor1.he.net  0.0%    10    6.8   7.2   6.5   8.0   0.5
  5.|-- 10ge1-1.core1.nyc5.he.net  0.0%    10   20.0  22.5  18.9  29.3   4.2
  6.|-- 10ge6-1.core1.nyc6.he.net  0.0%    10   23.3  21.5  18.4  30.8   4.4
  7.|-- xe-4-2-0-core1.thnor.uk.a  0.0%    10  209.5 185.4 170.8 209.5  11.9
  8.|-- ae1-core0.gsld2.uk.as6908 70.0%    10  180.2 2520. 180.2 4209. 2091.8
  9.|-- ae1-core0.gsld2.uk.as6908 40.0%    10   87.1  87.3  86.8  87.9   0.4
 10.|-- canonical-gw.datahop.net   0.0%    10   86.6  78.3   3.9  87.1  26.2
    |  `|-- 62.149.50.33
 11.|-- sadalbari.canonical.com    0.0%    10   87.1  78.7   3.0  87.4  26.6
    |  `|-- 78.41.155.186

```

I've tried switching mirrors, tried the main canonical site, tried main Canada site, nothing works.
Any ideas?  That uk site above with the packet losses appears to be owned by canonical too.

---

