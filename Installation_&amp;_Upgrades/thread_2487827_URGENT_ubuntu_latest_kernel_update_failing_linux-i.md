---
title: "URGENT: ubuntu latest kernel update failing linux-image-6.2.0-23-generic"
date: 2023-06-16
forum: Installation &amp; Upgrades
---

### Post by cmbdakri on 2023-06-16
```
root@kristof-Lenovo-YOGA-330-11IGM:/home/kristof# sudo apt update
Geraakt:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lunar-security InRelease
Geraakt:2 [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) stable InRelease                    
Geraakt:3 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) lunar InRelease                  
Geraakt:4 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) lunar-updates InRelease
Geraakt:5 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) lunar-backports InRelease
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar 
8 pakketten kunnen opgewaardeerd worden. Voer 'apt list --upgradable' uit om ze te zien.
root@kristof-Lenovo-YOGA-330-11IGM:/home/kristof# apt list --upgradable
Bezig met oplijsten... Klaar
dkms/lunar-updates,lunar-updates 3.0.10-7ubuntu2 all [opwaardeerbaar van: 3.0.10-7]
gdm3/lunar-updates 44.0-1ubuntu2 amd64 [opwaardeerbaar van: 44.0-1ubuntu1]
gir1.2-gdm-1.0/lunar-updates 44.0-1ubuntu2 amd64 [opwaardeerbaar van: 44.0-1ubuntu1]
libcupsfilters2-common/lunar-updates,lunar-updates 2.0~rc1-0ubuntu1.1 all [opwaardeerbaar van: 2.0~rc1-0ubuntu1]
libcupsfilters2/lunar-updates 2.0~rc1-0ubuntu1.1 amd64 [opwaardeerbaar van: 2.0~rc1-0ubuntu1]
libgdm1/lunar-updates 44.0-1ubuntu2 amd64 [opwaardeerbaar van: 44.0-1ubuntu1]
libppd2-common/lunar-updates,lunar-updates 2:2.0~rc1-0ubuntu1.1 all [opwaardeerbaar van: 2:2.0~rc1-0ubuntu1]
libppd2/lunar-updates 2:2.0~rc1-0ubuntu1.1 amd64 [opwaardeerbaar van: 2:2.0~rc1-0ubuntu1]
root@kristof-Lenovo-YOGA-330-11IGM:/home/kristof# sudo apt upgrade
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar 
Opwaardering wordt doorgerekend... Klaar
De volgende pakketten zijn achtergehouden:
  dkms gdm3 gir1.2-gdm-1.0 libcupsfilters2 libcupsfilters2-common libgdm1
  libppd2 libppd2-common
0 opgewaardeerd, 0 nieuw geïnstalleerd, 0 te verwijderen en 8 niet opgewaardeerd.
6 niet volledig geïnstalleerd of verwijderd.
Na deze bewerking zal er 0 B extra schijfruimte gebruikt worden.
Wilt u doorgaan? [J/n] n
Afbreken.
root@kristof-Lenovo-YOGA-330-11IGM:/home/kristof# apt install dkms gdm3 gir1.2-gdm-1.0 libcupsfilters2 libcupsfilters2-common libgdm1
  libppd2 libppd2-common
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar 
Voorgestelde pakketten:
  libpam-pkcs11
De volgende pakketten zullen opgewaardeerd worden:
  dkms gdm3 gir1.2-gdm-1.0 libcupsfilters2 libcupsfilters2-common libgdm1
6 opgewaardeerd, 0 nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
6 niet volledig geïnstalleerd of verwijderd.
Er moeten 980 kB aan archieven opgehaald worden.
Na deze bewerking zal er 0 B extra schijfruimte gebruikt worden.
Ophalen:1 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) lunar-updates/main amd64 dkms all 3.0.10-7ubuntu2 [48,4 kB]
Ophalen:2 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) lunar-updates/main amd64 gdm3 amd64 44.0-1ubuntu2 [301 kB]
Ophalen:3 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) lunar-updates/main amd64 libgdm1 amd64 44.0-1ubuntu2 [70,1 kB]
Ophalen:4 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) lunar-updates/main amd64 gir1.2-gdm-1.0 amd64 44.0-1ubuntu2 [9.882 B]
Ophalen:5 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) lunar-updates/main amd64 libcupsfilters2-common all 2.0~rc1-0ubuntu1.1 [245 kB]
Ophalen:6 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) lunar-updates/main amd64 libcupsfilters2 amd64 2.0~rc1-0ubuntu1.1 [307 kB]
980 kB opgehaald in 0s (2.013 kB/s)      
Voorconfigureren van pakketten ...
(Database wordt ingelezen ... 223067 bestanden en mappen momenteel geïnstalleerd
.)
Uitpakken van .../0-dkms_3.0.10-7ubuntu2_all.deb wordt voorbereid...
Bezig met uitpakken van dkms (3.0.10-7ubuntu2) over (3.0.10-7) ...
Uitpakken van .../1-gdm3_44.0-1ubuntu2_amd64.deb wordt voorbereid...
Bezig met uitpakken van gdm3 (44.0-1ubuntu2) over (44.0-1ubuntu1) ...
Uitpakken van .../2-libgdm1_44.0-1ubuntu2_amd64.deb wordt voorbereid...
Bezig met uitpakken van libgdm1 (44.0-1ubuntu2) over (44.0-1ubuntu1) ...
Uitpakken van .../3-gir1.2-gdm-1.0_44.0-1ubuntu2_amd64.deb wordt voorbereid...
Bezig met uitpakken van gir1.2-gdm-1.0 (44.0-1ubuntu2) over (44.0-1ubuntu1) ...
Uitpakken van .../4-libcupsfilters2-common_2.0~rc1-0ubuntu1.1_all.deb wordt voor
bereid...
Bezig met uitpakken van libcupsfilters2-common (2.0~rc1-0ubuntu1.1) over (2.0~rc
1-0ubuntu1) ...
Uitpakken van .../5-libcupsfilters2_2.0~rc1-0ubuntu1.1_amd64.deb wordt voorberei
d...
Bezig met uitpakken van libcupsfilters2:amd64 (2.0~rc1-0ubuntu1.1) over (2.0~rc1
-0ubuntu1) ...
Instellen van libgdm1 (44.0-1ubuntu2) ...
Instellen van linux-headers-6.2.0-23-generic (6.2.0-23.23) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-23-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j4 KERNELRELEASE=6.2.0-23-generic KVER=6.2.0-23-generic...(bad exit status
: 2)
ERROR (dkms apport): binary package for rtl8812au: #MODULE_VERSION# not found
Error! Bad return status for module build on kernel: 6.2.0-23-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/#MODULE_VERSION#/build/make.log for more informa
tion.
dkms autoinstall on 6.2.0-23-generic/x86_64 succeeded for 8812au 8812au rtl8821a
u rtl8821au rtl88x2bu rtl88x2bu
dkms autoinstall on 6.2.0-23-generic/x86_64 failed for rtl8812au(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: fout bij verwerken van pakket linux-headers-6.2.0-23-generic (--configure)
:
 subproces van pakket linux-headers-6.2.0-23-generic werd script post-installati
on geïnstalleerd gaf de foutwaarde 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van linux-headers-generic:
 linux-headers-generic is afhankelijk van linux-headers-6.2.0-23-generic; maar:
  Pakket linux-headers-6.2.0-23-generic is nog niet geconfigureerd.

dpkg: fout bij verwerken van pakket linux-headers-generic (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Instellen van dkms (3.0.10-7ubuntu2) ...
Er is geen apport-verslag weggeschreven omdat de foutmelding aangeeft dat de fou
t het gevolg is van een eerdere mislukking.
                                           Instellen van libcupsfilters2-common 
(2.0~rc1-0ubuntu1.1) ...
Instellen van linux-image-6.2.0-23-generic (6.2.0-23.23) ...
dpkg: vereistenproblemen verhinderen de configuratie van linux-headers-generic-h
we-22.04:
 linux-headers-generic-hwe-22.04 is afhankelijk van linux-headers-6.2.0-23-gener
ic; maar:
  Pakket linux-headers-6.2.0-23-generic is nog niet geconfigureerd.

dpkg: fout bij verwerken van pakket linux-headers-generic-hwe-22.04 (--configure
):
 vereistenproblemen - blijft ongeconfigureerd
Er is geen apport-verslag weggeschreven omdat de foutmelding aangeeft dat de fou
t het gevolg is van een eerdere mislukking.
                                           Instellen van libcupsfilters2:amd64 (
2.0~rc1-0ubuntu1.1) ...
dpkg: vereistenproblemen verhinderen de configuratie van linux-generic-hwe-22.04
:
 linux-generic-hwe-22.04 is afhankelijk van linux-headers-generic-hwe-22.04 (= 6
.2.0.23.23); maar:
  Pakket linux-headers-generic-hwe-22.04 is nog niet geconfigureerd.

dpkg: fout bij verwerken van pakket linux-generic-hwe-22.04 (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van linux-generic:
 linux-generic is afhankelijk van linux-headers-generic (= 6.2.0.23.23); maar:
  Pakket linux-headers-generic is nog niet geconfigureerd.

dpkg: fout bij verwerken van pakket linux-generic (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Er is geen apport-verslag weggeschreven omdat het maximum aantal verslagen (MaxR
eports) al is bereikt
                     Er is geen apport-verslag weggeschreven omdat het maximum a
antal verslagen (MaxReports) al is bereikt
                                          Bezig met afhandelen van triggers voor
 libglib2.0-0:amd64 (2.76.1-1) ...
Bezig met afhandelen van triggers voor libc-bin (2.37-0ubuntu2) ...
Bezig met afhandelen van triggers voor man-db (2.11.2-1) ...
Bezig met afhandelen van triggers voor dbus (1.14.4-1ubuntu1) ...
Instellen van gir1.2-gdm-1.0 (44.0-1ubuntu2) ...
Instellen van gdm3 (44.0-1ubuntu2) ...
Bezig met afhandelen van triggers voor linux-image-6.2.0-23-generic (6.2.0-23.23
) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-23-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j4 KERNELRELEASE=6.2.0-23-generic KVER=6.2.0-23-generic...(bad exit status
: 2)
ERROR (dkms apport): binary package for rtl8812au: #MODULE_VERSION# not found
Error! Bad return status for module build on kernel: 6.2.0-23-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/#MODULE_VERSION#/build/make.log for more informa
tion.
dkms autoinstall on 6.2.0-23-generic/x86_64 succeeded for 8812au 8812au rtl8821a
u rtl8821au rtl88x2bu rtl88x2bu
dkms autoinstall on 6.2.0-23-generic/x86_64 failed for rtl8812au(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: fout bij verwerken van pakket linux-image-6.2.0-23-generic (--configure):
 subproces van pakket linux-image-6.2.0-23-generic werd script post-installation
 geïnstalleerd gaf de foutwaarde 1 terug
Er is geen apport-verslag weggeschreven omdat het maximum aantal verslagen (MaxR
eports) al is bereikt
                     Fouten gevonden tijdens verwerken van:
 linux-headers-6.2.0-23-generic
 linux-headers-generic
 linux-headers-generic-hwe-22.04
 linux-generic-hwe-22.04
 linux-generic
 linux-image-6.2.0-23-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
^[[Alibppd2: opdracht niet gevonden
root@kristof-Lenovo-YOGA-330-11IGM:/home/kristof# sudo apt upgrade
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar 
Opwaardering wordt doorgerekend... Klaar
De volgende pakketten zijn achtergehouden:
  libppd2 libppd2-common
0 opgewaardeerd, 0 nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
6 niet volledig geïnstalleerd of verwijderd.
Na deze bewerking zal er 0 B extra schijfruimte gebruikt worden.
Wilt u doorgaan? [J/n] j
Instellen van linux-headers-6.2.0-23-generic (6.2.0-23.23) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-23-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j4 KERNELRELEASE=6.2.0-23-generic KVER=6.2.0-23-generic...(bad exit status
: 2)
ERROR (dkms apport): binary package for rtl8812au: #MODULE_VERSION# not found
Error! Bad return status for module build on kernel: 6.2.0-23-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/#MODULE_VERSION#/build/make.log for more informa
tion.
dkms autoinstall on 6.2.0-23-generic/x86_64 succeeded for 8812au 8812au rtl8821a
u rtl8821au rtl88x2bu rtl88x2bu
dkms autoinstall on 6.2.0-23-generic/x86_64 failed for rtl8812au(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: fout bij verwerken van pakket linux-headers-6.2.0-23-generic (--configure)
:
 subproces van pakket linux-headers-6.2.0-23-generic werd script post-installati
on geïnstalleerd gaf de foutwaarde 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van linux-headers-generic:
 linux-headers-generic is afhankelijk van linux-headers-6.2.0-23-generic; maar:
  Pakket linux-headers-6.2.0-23-generic is nog niet geconfigureerd.

dpkg: fout bij verwerken van pakket linux-headers-generic (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Instellen van linux-image-6.2.0-23-generic (6.2.0-23.23) ...
Er is geen apport-verslag weggeschreven omdat de foutmelding aangeeft dat de fou
t het gevolg is van een eerdere mislukking.
                                           dpkg: vereistenproblemen verhinderen 
de configuratie van linux-headers-generic-hwe-22.04:
 linux-headers-generic-hwe-22.04 is afhankelijk van linux-headers-6.2.0-23-gener
ic; maar:
  Pakket linux-headers-6.2.0-23-generic is nog niet geconfigureerd.

dpkg: fout bij verwerken van pakket linux-headers-generic-hwe-22.04 (--configure
):
 vereistenproblemen - blijft ongeconfigureerd
Er is geen apport-verslag weggeschreven omdat de foutmelding aangeeft dat de fou
t het gevolg is van een eerdere mislukking.
                                           Er is geen apport-verslag weggeschrev
en omdat het maximum aantal verslagen (MaxReports) al is bereikt
                                                                Er is geen appor
t-verslag weggeschreven omdat het maximum aantal verslagen (MaxReports) al is be
reikt
     dpkg: vereistenproblemen verhinderen de configuratie van linux-generic-hwe-
22.04:
 linux-generic-hwe-22.04 is afhankelijk van linux-headers-generic-hwe-22.04 (= 6
.2.0.23.23); maar:
  Pakket linux-headers-generic-hwe-22.04 is nog niet geconfigureerd.

dpkg: fout bij verwerken van pakket linux-generic-hwe-22.04 (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van linux-generic:
 linux-generic is afhankelijk van linux-headers-generic (= 6.2.0.23.23); maar:
  Pakket linux-headers-generic is nog niet geconfigureerd.

dpkg: fout bij verwerken van pakket linux-generic (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Bezig met afhandelen van triggers voor linux-image-6.2.0-23-generic (6.2.0-23.23
) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-23-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
make -j4 KERNELRELEASE=6.2.0-23-generic KVER=6.2.0-23-generic...(bad exit status
: 2)
ERROR (dkms apport): binary package for rtl8812au: #MODULE_VERSION# not found
Error! Bad return status for module build on kernel: 6.2.0-23-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/#MODULE_VERSION#/build/make.log for more informa
tion.
dkms autoinstall on 6.2.0-23-generic/x86_64 succeeded for 8812au 8812au rtl8821a
u rtl8821au rtl88x2bu rtl88x2bu
dkms autoinstall on 6.2.0-23-generic/x86_64 failed for rtl8812au(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: fout bij verwerken van pakket linux-image-6.2.0-23-generic (--configure):
 subproces van pakket linux-image-6.2.0-23-generic werd script post-installation
 geïnstalleerd gaf de foutwaarde 1 terug
Er is geen apport-verslag weggeschreven omdat het maximum aantal verslagen (MaxR
eports) al is bereikt
                     Fouten gevonden tijdens verwerken van:
 linux-headers-6.2.0-23-generic
 linux-headers-generic
 linux-headers-generic-hwe-22.04
 linux-generic-hwe-22.04
 linux-generic
 linux-image-6.2.0-23-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@kristof-Lenovo-YOGA-330-11IGM:/home/kristof#
```

---

### Post by cmbdakri on 2023-06-16
it has to do with a compiled driver dkms autoinstall on 6.2.0-23-generic/x86_64 failed for rtl8812au(10)
Error! One or more modules failed to install during autoinstall.

how do i uninstall it? please help

---

### Post by cmbdakri on 2023-06-16
the problem is fixed i erased all realtek drivers and then the latest ubuntu kernel installed

---

