---
title: "Upgrade partially failed 20.04 to 21.04"
date: 2021-10-16
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2021-10-16
The problem is obviously connected with python3. How do I correct it? There is no code options showing in firefox, hence the pure listing below;

```
<pre>Setting up python3 (3.9.4-1) ...
running python rtupdate hooks for python3.9...
/usr/share/bleachbit/bleachbit/__init__.py:260: SyntaxWarning: &quot;is not&quot; with a literal. Did you mean &quot;!=&quot;?
  if msgctxt is not None and msgctxt is not &quot;&quot;:
dpkg-query: package &apos;gdebi-core&apos; is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Traceback (most recent call last):
  File &quot;/usr/bin/py3clean&quot;, line 210, in &lt;module&gt;
    main()
  File &quot;/usr/bin/py3clean&quot;, line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File &quot;/usr/share/python3/debpython/files.py&quot;, line 53, in from_package
    raise Exception(&quot;cannot get content of %s&quot; % package_name)
Exception: cannot get content of gdebi-core
error running python rtupdate hook gdebi-core
dpkg-query: package &apos;gdebi&apos; is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Traceback (most recent call last):
  File &quot;/usr/bin/py3clean&quot;, line 210, in &lt;module&gt;
    main()
  File &quot;/usr/bin/py3clean&quot;, line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File &quot;/usr/share/python3/debpython/files.py&quot;, line 53, in from_package
    raise Exception(&quot;cannot get content of %s&quot; % package_name)
Exception: cannot get content of gdebi
error running python rtupdate hook gdebi
<b>dpkg:</b> error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
<b>dpkg:</b> dependency problems prevent configuration of gconf2:
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package gconf2 (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-click:
 python3-click depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-click (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-xdg:
 python3-xdg depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-xdg (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-chm:
 python3-chm depends on python3 (&lt;&lt; 3.10); however:
  Package python3 is not configured yet.
 python3-chm depends on python3 (&gt;= 3.9~); however:
  Package python3 is not configured yet.
 python3-chm depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-chm (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-markupsafe:
 python3-markupsafe depends on python3 (&lt;&lt; 3.10); however:
  Package python3 is not configured yet.
 python3-markupsafe depends on python3 (&gt;= 3.9~); however:
  Package python3 is not configured yet.
 python3-markupsafe depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-markupsafe (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-nose:
 python3-nose depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-nose (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-webencodings:
 python3-webencodings depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-webencodings (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of openprinting-ppds:
 openprinting-ppds depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package openprinting-ppds (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3; however:
  Package python3 is not configured yet.
 software-properties-common depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package software-properties-common (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-psutil:
 python3-psutil depends on python3 (&lt;&lt; 3.10); however:
  Package python3 is not configured yet.
 python3-psutil depends on python3 (&gt;= 3.9~); however:
  Package python3 is not configured yet.
 python3-psutil depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-psutil (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of apport:
 apport depends on python3; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package apport (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-tz:
 python3-tz depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-tz (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-bs4:
 python3-bs4 depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-bs4 (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-pikepdf:
 python3-pikepdf depends on python3 (&lt;&lt; 3.10); however:
  Package python3 is not configured yet.
 python3-pikepdf depends on python3 (&gt;= 3.9~); however:
  Package python3 is not configured yet.
 python3-pikepdf depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-pikepdf (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-natsort:
 python3-natsort depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-natsort (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of pdfarranger:
 pdfarranger depends on python3-pikepdf; however:
  Package python3-pikepdf is not configured yet.
 pdfarranger depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package pdfarranger (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-apport:
 python3-apport depends on python3:any (&gt;= 3.0~); however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-apport (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of netplan.io:
 netplan.io depends on python3; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package netplan.io (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-ifaddr:
 python3-ifaddr depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-ifaddr (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-cupshelpers:
 python3-cupshelpers depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-cupshelpers (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-monotonic:
 python3-monotonic depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-monotonic (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-routes:
 python3-routes depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-routes (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-six:
 python3-six depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-six (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-simplejson:
 python3-simplejson depends on python3 (&lt;&lt; 3.10); however:
  Package python3 is not configured yet.
 python3-simplejson depends on python3 (&gt;= 3.9~); however:
  Package python3 is not configured yet.
 python3-simplejson depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-simplejson (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-ecdsa:
 python3-ecdsa depends on python3-six (&gt;= 1.9.0); however:
  Package python3-six is not configured yet.
 python3-ecdsa depends on python3:any (&gt;= 3.6~); however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-ecdsa (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of ibus-table:
 ibus-table depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package ibus-table (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-pil:amd64:
 python3-pil:amd64 depends on python3 (&lt;&lt; 3.10); however:
  Package python3 is not configured yet.
 python3-pil:amd64 depends on python3 (&gt;= 3.9~); however:
  Package python3 is not configured yet.
 python3-pil:amd64 depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-pil:amd64 (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-cups:amd64:
 python3-cups:amd64 depends on python3 (&lt;&lt; 3.10); however:
  Package python3 is not configured yet.
 python3-cups:amd64 depends on python3 (&gt;= 3.9~); however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-cups:amd64 (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of unattended-upgrades:
 unattended-upgrades depends on python3; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-pygments:
 python3-pygments depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-pygments (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-packaging:
 python3-packaging depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-packaging (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-oauthlib:
 python3-oauthlib depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-oauthlib (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-chardet:
 python3-chardet depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-chardet (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-louis:
 python3-louis depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-louis (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-secretstorage:
 python3-secretstorage depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-secretstorage (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-pyparsing:
 python3-pyparsing depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-pyparsing (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3; however:
  Package python3 is not configured yet.
 python3-software-properties depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-software-properties (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of system-config-printer:
 system-config-printer depends on python3-cups (&gt;= 1.9.60); however:
  Package python3-cups:amd64 is not configured yet.
 system-config-printer depends on python3-cupshelpers (= 1.5.15-0ubuntu1); however:
  Package python3-cupshelpers is not configured yet.
 system-config-printer depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package system-config-printer (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-certifi:
 python3-certifi depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-certifi (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of inkscape:
 inkscape depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package inkscape (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-pexpect:
 python3-pexpect depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-pexpect (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-cryptography:
 python3-cryptography depends on python3 (&gt;= 3~); however:
  Package python3 is not configured yet.
 python3-cryptography depends on python3-six (&gt;= 1.4.1); however:
  Package python3-six is not configured yet.
 python3-cryptography depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-cryptography (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-wadllib:
 python3-wadllib depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-wadllib (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-debian:
 python3-debian depends on python3-chardet; however:
  Package python3-chardet is not configured yet.
 python3-debian depends on python3-six (&gt;&gt; 1.4~); however:
  Package python3-six is not configured yet.
 python3-debian depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-debian (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-pyatspi:
 python3-pyatspi depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-pyatspi (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-gi:
 python3-gi depends on python3 (&lt;&lt; 3.10); however:
  Package python3 is not configured yet.
 python3-gi depends on python3 (&gt;= 3.9~); however:
  Package python3 is not configured yet.
 python3-gi depends on python3:any; however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-gi (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> dependency problems prevent configuration of python3-reportlab-accel:amd64:
 python3-reportlab-accel:amd64 depends on python3 (&lt;&lt; 3.10); however:
  Package python3 is not configured yet.
 python3-reportlab-accel:amd64 depends on python3 (&gt;= 3.9~); however:
  Package python3 is not configured yet.

<b>dpkg:</b> error processing package python3-reportlab-accel:amd64 (--configure):
 dependency problems - leaving unconfigured
<b>dpkg:</b> too many errors, stopping
Errors were encountered while processing:
 python3
 gconf2
 python3-click
 python3-xdg
 python3-chm
 python3-distupgrade
 python3-markupsafe
 python3-nose
 printer-driver-postscript-hp
 python3-webencodings
 openprinting-ppds
 software-properties-common
 python3-psutil
 apport
 python3-tz
 python3-bs4
 python3-pikepdf
 python3-natsort
 pdfarranger
 python3-apport
 netplan.io
 python3-ifaddr
 python3-cupshelpers
 python3-monotonic
 python3-routes
 python3-six
 python3-simplejson
 python3-ecdsa
 ibus-table
 python3-pil:amd64
 python3-cups:amd64
 unattended-upgrades
 python3-pygments
 python3-packaging
 python3-oauthlib
 python3-chardet
 python3-louis
 python3-secretstorage
 python3-pyparsing
 python3-software-properties
 system-config-printer
 python3-certifi
 inkscape
 python3-pexpect
 python3-cryptography
 python3-wadllib
 python3-debian
 python3-pyatspi
 python3-gi
 python3-reportlab-accel:amd64
Processing was halted because there were too many errors.
<font color="#4E9A06"><b>robins@robins-desktop</b></font>:<font color="#3465A4"><b>~</b></font>$ 

</pre>
```

---

### Post by Robbyx on 2021-10-16
I have just tried a further upgrade but get the following error messages:

```
E: python3: installed python3 package post-installation script subprocess returned error exit status 4
E: gconf2: dependency problems - leaving unconfigured
E: python3-click: dependency problems - leaving unconfigured
E: python3-xdg: dependency problems - leaving unconfigured
E: python3-chm: dependency problems - leaving unconfigured
E: python3-distupgrade: dependency problems - leaving unconfigured
E: python3-markupsafe: dependency problems - leaving unconfigured
E: python3-nose: dependency problems - leaving unconfigured
E: printer-driver-postscript-hp: dependency problems - leaving unconfigured
E: python3-webencodings: dependency problems - leaving unconfigured
E: openprinting-ppds: dependency problems - leaving unconfigured
E: software-properties-common: dependency problems - leaving unconfigured
E: python3-psutil: dependency problems - leaving unconfigured
E: apport: dependency problems - leaving unconfigured
E: python3-tz: dependency problems - leaving unconfigured
E: python3-bs4: dependency problems - leaving unconfigured
E: python3-pikepdf: dependency problems - leaving unconfigured
E: python3-natsort: dependency problems - leaving unconfigured
E: pdfarranger: dependency problems - leaving unconfigured
E: python3-apport: dependency problems - leaving unconfigured
E: netplan.io: dependency problems - leaving unconfigured
E: python3-ifaddr: dependency problems - leaving unconfigured
E: python3-cupshelpers: dependency problems - leaving unconfigured
E: python3-monotonic: dependency problems - leaving unconfigured
E: python3-routes: dependency problems - leaving unconfigured
E: python3-six: dependency problems - leaving unconfigured
E: python3-simplejson: dependency problems - leaving unconfigured
E: python3-ecdsa: dependency problems - leaving unconfigured
E: ibus-table: dependency problems - leaving unconfigured
E: python3-pil: 34.7408:dependency problems - leaving unconfigured
E: python3-cups: 34.7408:dependency problems - leaving unconfigured
E: unattended-upgrades: dependency problems - leaving unconfigured
E: python3-pygments: dependency problems - leaving unconfigured
E: python3-packaging: dependency problems - leaving unconfigured
E: python3-oauthlib: dependency problems - leaving unconfigured
E: python3-chardet: dependency problems - leaving unconfigured
E: python3-louis: dependency problems - leaving unconfigured
E: python3-secretstorage: dependency problems - leaving unconfigured
E: python3-pyparsing: dependency problems - leaving unconfigured
E: python3-software-properties: dependency problems - leaving unconfigured
E: system-config-printer: dependency problems - leaving unconfigured
E: python3-certifi: dependency problems - leaving unconfigured
E: inkscape: dependency problems - leaving unconfigured
E: python3-pexpect: dependency problems - leaving unconfigured
E: python3-cryptography: dependency problems - leaving unconfigured
E: python3-wadllib: dependency problems - leaving unconfigured
E: python3-debian: dependency problems - leaving unconfigured
E: python3-pyatspi: dependency problems - leaving unconfigured
E: python3-gi: dependency problems - leaving unconfigured
E: python3-reportlab-accel: 35.4890:dependency problems - leaving unconfigured
```

---

### Post by Robbyx on 2021-10-16
As the error messages first appeared during the upgrade to 21.04, as I have gone back to 20.04 what should I now check?

---

### Post by Impavidus on 2021-10-16
It complains that the packages gdebi-core and gdebi are not installed. Have you made sure they're actually installed?

There's also a syntax warning (just a warning) from a python script belonging to bleachbit, which is apparently triggered when python is upgraded. That might be an issue too.

Generally, don't spend too much time troubleshooting failed release upgrades. Just fresh install.

---

