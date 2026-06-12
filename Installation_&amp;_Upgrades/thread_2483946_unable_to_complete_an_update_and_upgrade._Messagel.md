---
title: "unable to complete an update and upgrade. Message:libdvd-pkg: `apt-get check` failed,"
date: 2023-02-13
forum: Installation &amp; Upgrades
---

### Post by rhyter on 2023-02-13
Hello! When I am trying to proceed to a new update and upgrade the following message appears in the bottom line of the terminal: libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting... Does anyone know how to deal with this problem? Thanks

---

### Post by SeijiSensei on 2023-02-13
Open a terminal and type
```
sudo dpkg --configure -a
```
Watch to see if it reports any errors. If not, try updating again.

---

### Post by ajgreeny on 2023-02-13
After installing libdvd-pkg you need to follow the instructions that configure it and move on to the installation of libdvd.css.
Depending on how you installed it this requirement information may be missing.
See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) for all the details, not worrying about the fact that this appears to go up to Ubuntu 15.10; it is still current and you need to run command ```
sudo dpkg-reconfigure libdvd-pkg
```
The command shown by SeijiSensei will do this but now you will understand why

---

