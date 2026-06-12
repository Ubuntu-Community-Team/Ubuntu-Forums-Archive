---
title: "KTorrent Instillation"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by Tumpster on 2010-09-07
Trying to install KTorrent and this is what I get:

 ktorrent: Depends: libkdecore5 (>= 4:4.5.0b) but it is not installable
            Depends: libkdeui5 (>= 4:4.5.0b) but it is not installable
            Depends: libkdnssd4 (>= 4:4.5.0b) but it is not installable
            Depends: libkhtml5 (>= 4:4.5.0b) but it is not installable
            Depends: libkio5 (>= 4:4.5.0b) but it is not installable
            Depends: libkjsapi4 (>= 4:4.5.0b) but it is not installable
            Depends: libknotifyconfig4 (>= 4:4.5.0b) but it is not installable
            Depends: libkparts4 (>= 4:4.5.0b) but it is not installable
            Depends: libkrosscore4 (>= 4:4.5.0b) but it is not installable
            Depends: libktorrent1 but it is not going to be installed
            Depends: libkutils4 (>= 4:4.5.0b) but it is not installable
            Depends: libkworkspace4 (>= 4:4.5.0b) but 4:4.4.2-0ubuntu14 is to be installed
            Depends: libnepomuk4 (>= 4:4.5.0b) but it is not installable
            Depends: libphonon4 (>= 4:4.7.0really4.4.2) but 4:4.6.2-0ubuntu5 is to be installed
            Depends: libqt4-dbus (>= 4:4.7.0~beta2) but 4:4.6.2-0ubuntu5 is to be installed
            Depends: libqt4-network (>= 4:4.7.0~beta2) but 4:4.6.2-0ubuntu5 is to be installed
            Depends: libqt4-qt3support (>= 4:4.7.0~beta2) but 4:4.6.2-0ubuntu5 is to be installed
            Depends: libqt4-script (>= 4:4.7.0~beta2) but 4:4.6.2-0ubuntu5 is to be installed
            Depends: libqt4-svg (>= 4:4.7.0~beta2) but 4:4.6.2-0ubuntu5 is to be installed
            Depends: libqt4-xml (>= 4:4.7.0~beta2) but 4:4.6.2-0ubuntu5 is to be installed
            Depends: libqtcore4 (>= 4:4.7.0~beta2) but 4:4.6.2-0ubuntu5 is to be installed
            Depends: libqtgui4 (>= 4:4.7.0~beta2) but 4:4.6.2-0ubuntu5 is to be installed
            Depends: libsolid4 (>= 4:4.5.0b) but it is not installable
            Depends: libsolidcontrol4a (>= 4:4.5.0b) but it is not installable
            Depends: libsoprano4 (>= 2.5.0+dfsg.1) but 2.4.2+dfsg.1-0ubuntu1.1 is to be installed
            Depends: libsyndication4 (>= 4:4.5.0b) but it is not installable
E: Broken packages



Help?

---

### Post by zvacet on 2010-09-09
```
sudo apt-get -f install
```

---

### Post by Tumpster on 2010-09-09
> **zvacet said:**
> ```
sudo apt-get -f install
```
That does nothing....

---

### Post by DemanRisu on 2010-09-09
> **Tumpster said:**
> That does nothing....
sudo apt-get -f install ktorrent ?

---

### Post by zvacet on 2010-09-09
In **synaptic>edit tab>fix broken packages**.

---

### Post by Tumpster on 2010-09-11
> **zvacet said:**
> In **synaptic>edit tab>fix broken packages**.

Synaptic flashes and does nothing. Attempting reinstall still gives same errors.

---

### Post by zvacet on 2010-09-12
Where from you try to install Ktorrent?Synaptic or some other source?

---

