---
title: "openoffice.org2 help package holding back upgrade"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by Tralobyte on 2005-10-15
Synaptic gave me an error about installing an openoffice.org2 help package on the smart upgrade. I closed synaptic and did an apt-get -f install. I got this:```

dpkg: error processing /cdrom//pool/main/o/openoffice.org2-helpcontent/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice2/help/en/scalc.idx/DOCS.TAB', which is also in package openoffice.org2-calc
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /cdrom//pool/main/o/openoffice.org2-helpcontent/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb
```

When I try running synaptic, I get this:
```

(synaptic:1740): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Segmentation fault
```

Any ideas on how to fix the upgrade?

---

### Post by Tralobyte on 2005-10-15
I solved the problem with "sudo dpkg -r openoffice.org2-calc openffice.org2-draw openoffice.org2-impress openoffice.org2-math openoffice.org2-writer"

---

### Post by mde on 2006-01-26
This same issue was seriously blocking me during an upgrade from Hoary to Breezy. Thanks a lot for posting your fix. 

Worked like a charm and I'm chugging ahead here.

---

