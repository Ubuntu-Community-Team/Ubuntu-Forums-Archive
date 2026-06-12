---
title: "ttf-mscorefonts-installer installation failure 16.04 LTS"
date: 2017-01-13
forum: Installation &amp; Upgrades
---

### Post by Bill Roberts on 2017-01-13
ttf-mscorefonts-installer failed to completely install

Synaptic messages are:
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) [198 kB]
Fetched 198 kB in 1s (141 kB/s)                                                
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
Err:1 [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
  The HTTP server sent an invalid Content-Range header
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arial32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch [https://superb-sea2.dl.sourceforge.net/project/corefonts/the](https://superb-sea2.dl.sourceforge.net/project/corefonts/the) fonts/final/arial32.exe  The HTTP server sent an invalid Content-Range header

E: Download Failed

An Information window periodically opens to request  action, but it always fails.

---

### Post by howefield on 2017-01-13
The 3.4 version of the ttf-mecorefonts-installer package is broken.

Sourceforge (where the actual font files are downloaded from) changed the location that the fonts are stored rendering the package broken. I'd suggest purging that broken 3.4 version of the package and instead install the 3.6 version of the package from an alternative source, eg

```
sudo apt purge ttf-mscorefonts-installer
```

to get rid of the current package

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

to download the 3.6 version of the package to your Downloads folder, and

```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

to install the new package.

---

### Post by Bill Roberts on 2017-01-13
That worked perfectly. Problem solved.

---

### Post by oldos2er on 2017-01-13
Would you please mark your thread 'Solved' under Thread Tools at the top of the page? It'll help others who might be having the same problem.

---

### Post by howefield on 2017-01-13
> **Bill Roberts said:**
> That worked perfectly. Problem solved.

Cool, thanks for the update, good to know.

---

### Post by Linuxratty on 2017-01-27
Yup. All good here too. THANK YOU howefield !!!!!!

---

### Post by oldrocker99 on 2017-01-28
Thanks, Howefield; it fixed my problem, too.

---

