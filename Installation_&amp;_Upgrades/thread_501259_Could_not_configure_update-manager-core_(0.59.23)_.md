---
title: "Could not configure update-manager-core (0.59.23) in Feisty"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by cropr on 2007-07-15
I get following error message after doing a software update in Feisty.

```
sudo apt-get install -f
Password:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
Reading state information... Klaar
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0
niet opgewaardeerd.
21 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B aan archieven opgehaald worden.
Na het uitpakken zal er 0B extra schijfruimte gebruikt worden.
Instellen van update-manager-core (0.59.23) ...
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/py_compilefiles", line 3, in ?
    import os
ImportError: No module named os
pycentral: pycentral pkginstall: error byte-compiling files (4)
pycentral pkginstall: error byte-compiling files (4)
dpkg: fout bij afhandelen van update-manager-core (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
Instellen van python-imaging (1.1.6-0ubuntu3) ...
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/py_compilefiles", line 3, in ?
    import os
ImportError: No module named os
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 899, in run
    self.options.exclude, byte_compile_default=True)
  File "/usr/bin/pycentral", line 672, in install
    rt.byte_compile(linked_files, bc_option, exclude_regex, ignore_errors)
  File "/usr/bin/pycentral", line 162, in byte_compile
    fd.write(fn + '\n')
IOError: [Errno 32] Broken pipe
dpkg: fout bij afhandelen van python-imaging (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
Instellen van python-zopeinterface (3.3.1-0ubuntu3) ...
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/py_compilefiles", line 3, in ?
    import os
ImportError: No module named os
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 899, in run
    self.options.exclude, byte_compile_default=True)
  File "/usr/bin/pycentral", line 672, in install
    rt.byte_compile(linked_files, bc_option, exclude_regex, ignore_errors)
  File "/usr/bin/pycentral", line 162, in byte_compile
    fd.write(fn + '\n')
IOError: [Errno 32] Broken pipe
dpkg: fout bij afhandelen van python-zopeinterface (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van python-twisted-core:
 python-twisted-core is afhankelijk van python-zopeinterface (>= 3.2.1-3); maar:
  Pakket python-zopeinterface is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-twisted-core (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Instellen van python-crypto (2.0.1+dfsg1-1.2ubuntu1) ...
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/py_compilefiles", line 3, in ?
    import os
ImportError: No module named os
pycentral: pycentral pkginstall: error byte-compiling files (22)
pycentral pkginstall: error byte-compiling files (22)
dpkg: fout bij afhandelen van python-crypto (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van python-twisted-conch:
 python-twisted-conch is afhankelijk van python-crypto (>= 2.0.1+dfsg1-1.1); maar:
  Pakket python-crypto is nog niet geconfigureerd.
 python-twisted-conch is afhankelijk van python-twisted-core (>= 2.5); maar:
  Pakket python-twisted-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-twisted-conch (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-twisted-mail:
 python-twisted-mail is afhankelijk van python-twisted-core (>= 2.5); maar:
  Pakket python-twisted-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-twisted-mail (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-twisted-web:
 python-twisted-web is afhankelijk van python-twisted-core (>= 2.5); maar:
  Pakket python-twisted-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-twisted-web (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-twisted-lore:
 python-twisted-lore is afhankelijk van python-twisted-web (>= 0.3); maar:
  Pakket python-twisted-web is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-twisted-lore (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-twisted-names:
 python-twisted-names is afhankelijk van python-twisted-core (>= 2.5); maar:
  Pakket python-twisted-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-twisted-names (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-twisted-news:
 python-twisted-news is afhankelijk van python-twisted-core (>= 2.5); maar:
  Pakket python-twisted-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-twisted-news (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-twisted-runner:
 python-twisted-runner is afhankelijk van python-twisted-core (>= 2.4); maar:
  Pakket python-twisted-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-twisted-runner (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-twisted-words:
 python-twisted-words is afhankelijk van python-twisted-core (>= 2.5); maar:
  Pakket python-twisted-core is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-twisted-words (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-twisted:
 python-twisted is afhankelijk van python-twisted-core (>= 2.5); maar:
  Pakket python-twisted-core is nog niet geconfigureerd.
 python-twisted is afhankelijk van python-twisted-conch (>= 1:0.8); maar:
  Pakket python-twisted-conch is nog niet geconfigureerd.
 python-twisted is afhankelijk van python-twisted-mail (>= 0.4); maar:
  Pakket python-twisted-mail is nog niet geconfigureerd.
 python-twisted is afhankelijk van python-twisted-lore (>= 0.2); maar:
  Pakket python-twisted-lore is nog niet geconfigureerd.
 python-twisted is afhankelijk van python-twisted-names (>= 0.4); maar:
  Pakket python-twisted-names is nog niet geconfigureerd.
 python-twisted is afhankelijk van python-twisted-news (>= 0.3); maar:
  Pakket python-twisted-news is nog niet geconfigureerd.
 python-twisted is afhankelijk van python-twisted-runner (>= 0.2); maar:
  Pakket python-twisted-runner is nog niet geconfigureerd.
 python-twisted is afhankelijk van python-twisted-web (>= 0.7); maar:
  Pakket python-twisted-web is nog niet geconfigureerd.
 python-twisted is afhankelijk van python-twisted-words (>= 0.5); maar:
  Pakket python-twisted-words is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-twisted (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-tofu:
 python-tofu is afhankelijk van python-twisted; maar:
  Pakket python-twisted is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-tofu (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van balazar:
 balazar is afhankelijk van python-tofu (>= 0.5); maar:
  Pakket python-tofu is nog niet geconfigureerd.
dpkg: fout bij afhandelen van balazar (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Instellen van hwdb-client-common (0.6.10.1) ...
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/py_compilefiles", line 3, in ?
    import os
ImportError: No module named os
pycentral: pycentral pkginstall: error byte-compiling files (3)
pycentral pkginstall: error byte-compiling files (3)
dpkg: fout bij afhandelen van hwdb-client-common (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van hwdb-client-kde:
 hwdb-client-kde is afhankelijk van hwdb-client-common; maar:
  Pakket hwdb-client-common is nog niet geconfigureerd.
dpkg: fout bij afhandelen van hwdb-client-kde (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-imaging-tk:
 python-imaging-tk is afhankelijk van python-imaging (= 1.1.6-0ubuntu3); maar:
  Pakket python-imaging is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-imaging-tk (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van python-soya:
 python-soya is afhankelijk van python-imaging-tk; maar:
  Pakket python-imaging-tk is nog niet geconfigureerd.
dpkg: fout bij afhandelen van python-soya (--configure):
 vereistenproblemen - blijft ongeconfigureerd
dpkg: vereistenproblemen verhinderen de configuratie van slune:
 slune is afhankelijk van python-soya (>= 0.12-1); maar:
  Pakket python-soya is nog niet geconfigureerd.
dpkg: fout bij afhandelen van slune (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 update-manager-core
 python-imaging
 python-zopeinterface
 python-twisted-core
 python-crypto
 python-twisted-conch
 python-twisted-mail
 python-twisted-web
 python-twisted-lore
 python-twisted-names
 python-twisted-news
 python-twisted-runner
 python-twisted-words
 python-twisted
 python-tofu
 balazar
 hwdb-client-common
 hwdb-client-kde
 python-imaging-tk
 python-soya
 slune
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I did a *dpkg --configure -a*  and a *apt-get install -f*, but the error remained.  Starting a normal python shell and doing an *import os* works fine. Any clue?

---

