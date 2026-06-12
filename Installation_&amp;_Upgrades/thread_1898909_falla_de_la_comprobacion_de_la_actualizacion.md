---
title: "falla de la comprobacion de la actualizacion"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by evilution on 2011-12-22
hola a todos:

esta es mi situacion.cada vez que quiero comprobar las actualizaciones,me sale este error:
W:GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783, W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease: File /var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-x-swat?x-update_ppa_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message, W:GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783, W:Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-x-swat?x-update_ppa_ubuntu_dists_oneiric_main_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-x-swat?x-update_ppa_ubuntu_dists_oneiric_main_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat?x-update/ppa/ubuntu/dists/oneiric/main/i18n/Index](http://ppa.launchpad.net/ubuntu-x-swat?x-update/ppa/ubuntu/dists/oneiric/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-x-swat?x-update_ppa_ubuntu_dists_oneiric_main_i18n_Index
, W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-update/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/ubuntu-x-swat/x-update/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-update/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-x-swat/x-update/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
He intentado solucionar esto pero sin exito.he revizado los paquetes,autenticaciones,otros softwares,etc.

claro,cuando hay actualizaciones disponibles las instalo.el problema es cuando quiero hacer la comprobacion.

no he tenido,hasta ahora,problemas de ningun tipo con el OS y sus funciones.pero me gustaria saber por que y como puedo solucionar esto.

Agradecido sde ante mano. ><

---

### Post by sikander3786 on 2011-12-22
Welcome to the forums. :)

The preferred language on Ubuntu Forums is English. I don't understand this Language and if you don't know English, you should post in the appropriate local forums. A list can be found here:

[http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183)

From the errors above, if you could understand English, I can tell you that you probably upgraded from an earlier version of Ubuntu to Oneiric and those PPAs are not available for Oneiric. You can remove them by searching the Dash for 'Software Sources' > Other Software tab and deleting the offensive PPAs.

You've also got a mix of Oneiric and older software sources so please post the output of these commands also:

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

---

