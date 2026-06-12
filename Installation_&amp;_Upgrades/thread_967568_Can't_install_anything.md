---
title: "Can't install anything"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by LucasQueiroz on 2008-11-02
To I installed the 8.10, but, every time I try to update the repositories I get the very same error, even if there's no Repository Source. 

Could some one help?

#W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-pt_BR.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-pt_BR.bz2)  Não foi possível resolver 'archive.ubuntu.com'

W: Alguns arquivos de índice falharam para baixar, eles foram ignorados ou os antigos foram usados no lugar.#

---

### Post by Pumalite on 2008-11-02
Check your connection and/or change Server.
Administration>Software Sources>Download From>Other>Best Server

---

### Post by LucasQueiroz on 2008-11-02
I tried to change from Brazilian to he Main one, but I'll try to do your way. Hope it works :)

---

### Post by Pumalite on 2008-11-02
In the meantime, post:
cat /etc/apt/sources.list

---

