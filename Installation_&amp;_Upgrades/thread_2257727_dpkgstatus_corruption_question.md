---
title: "dpkg/status corruption question"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by f3isar on 2014-12-22
Hi All,

I've just had a strange thing happen, my /var/lib/dpkg/status file got currupted. I clean installed xubuntu a couple of days ago, then the nvidia drivers and then Steam a long with a couple of games.

I was then given this error when attempting to install/update packages:

```
dpkg: error: parsing file '/var/lib/dpkg/status' near line 27803 package 'gcr':
 field name `°[?@' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

So I checked /var/lib/dpkg/status and sure enough this appeared near 27803:

```
Description: GNOME crypto services (daemon and tools)
 GCR is a library for crypto UI and related tasks.
 .
 This package contai<9c>^@^@^@^D ÃÃJ^@^@^@^@^@^@^@^@^@^F^AÃ¯E^L^@r and prompter
^DÂ°^D[?@^@^@^@Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿<8c>ÃÃr^NÃÃ¿Ã¿Ã¿Ã¿Ã¿Ã¿pÃ£^@^Nairdrawndagger^A^D^B^D^K^V2^H^L^R^X$0H`l-^Zl^X^ZÃ¿Ã¿^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^^A^@^A^@^C^E^@^@^@^@^@Ã^^^@<90>L3l^X^ZÃ¿Ã¿^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^A^A^@^@Ã¿^A^@^@^@^@^@1Ã ^K^Salled
```

The entries for GCR and ALSA-Utils had kinda merged with the above garbage in between. I was able to copy them back in from the /var/lib/dpkg/status-old file and the system can update again.

What I find really odd is that within that garbled text is the word 'airdrawndagger' which was, about a year ago, a wireless SSID I used. 

As this is a fresh install (in fact the hardware was not even in the house when airdrawndagger existed), does anyone have any idea how that word would have ended up in my /var/lib/dpkg/status file?

As far as I'm aware the only device which has connected to this xubuntu box and had previously connected to airdrawndagger is the smart TV it's connected to.

---

