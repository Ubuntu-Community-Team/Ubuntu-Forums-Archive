---
title: "[ Ubuntu 20.04 ] : PSAD"
date: 2020-12-22
forum: Installation &amp; Upgrades
---

### Post by rbn3131 on 2020-12-22
Hello,
with
Following to an upgrade from 18.04 to 20.04 i have a problem with the software psad :

```
# apt install psad
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Paquets suggérés :
  fwsnort
Les NOUVEAUX paquets suivants seront installés :
  psad
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0 o/150 ko dans les archives.
Après cette opération, 711 ko d'espace disque supplémentaires seront utilisés.
Sélection du paquet psad précédemment désélectionné.
(Lecture de la base de données... 135979 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de .../psad_2.4.3-1.2_amd64.deb ...
Dépaquetage de psad (2.4.3-1.2) ...
Paramétrage de psad (2.4.3-1.2) ...
Job for psad.service failed because the control process exited with error code.
See "systemctl status psad.service" and "journalctl -xe" for details.
invoke-rc.d: initscript psad, action "start" failed.
&#9679; psad.service - LSB: Port Scan Attack Detector (psad)
     Loaded: loaded (/etc/init.d/psad; generated)
     Active: failed (Result: exit-code) since Tue 2020-12-22 20:47:36 CET; 20ms ago
       Docs: man:systemd-sysv-generator(8)
    Process: 193473 ExecStart=/etc/init.d/psad start (code=exited, status=1/FAILURE)

déc. 22 20:47:35 sd-129303 systemd[1]: Starting LSB: Port Scan Attack Detector (psad)...
déc. 22 20:47:36 sd-129303 psad[193491]: 
[*] Could not find/execute iptables, specify path via _iptables
déc. 22 20:47:36 sd-129303 psad[193491]:  at /usr/share/perl5/IPTables/ChainMgr.pm line 37.
déc. 22 20:47:36 sd-129303 psad[193473]:  * Unable to start the daemon
déc. 22 20:47:36 sd-129303 psad[193473]:  * Starting Port Scan Attack Detector psad
déc. 22 20:47:36 sd-129303 psad[193473]:    ...fail!
déc. 22 20:47:36 sd-129303 systemd[1]: psad.service: Control process exited, code=exited, status=1/FAILURE
déc. 22 20:47:36 sd-129303 systemd[1]: psad.service: Failed with result 'exit-code'.
déc. 22 20:47:36 sd-129303 systemd[1]: Failed to start LSB: Port Scan Attack Detector (psad).
dpkg: erreur de traitement du paquet psad (--configure) :
 installed psad package post-installation script subprocess returned error exit status 1
Traitement des actions différées (« triggers ») pour man-db (2.9.1-1) ...
Traitement des actions différées (« triggers ») pour ureadahead (0.100.0-21) ...
Traitement des actions différées (« triggers ») pour systemd (245.4-4ubuntu3.3) ...
Des erreurs ont été rencontrées pendant l'exécution :
 psad
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anybody has an idea about this python bug ?

Thanks for help.

Best Regards.

Rémi

---

### Post by TheFu on 2020-12-22
```
déc. 22 20:47:36 sd-129303 psad[193491]: [*] Could not find/execute iptables, specify path via _iptables
```
fix that.

---

### Post by rbn3131 on 2020-12-23
Thanks ...

---

