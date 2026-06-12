---
title: "prism card and hostap driver"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by weaklingkiller on 2007-03-05
hello
i'm trying to get get my prism-card work with the hostapdriver. i've blacklisted orinoco(_cs) but when i put my card into the slot nothing happens.
dmesg:
```

[17181228.980000] pccard: PCMCIA card inserted into slot 0
[17181228.980000] pcmcia: registering new device pcmcia0.0

```
pccardctl ident:
```

Socket 0:
  product info: "Wireless LAN", "11Mbps PC Card", "Version 01.02", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

```

i'm using edgy eft.
can you help me?

---

