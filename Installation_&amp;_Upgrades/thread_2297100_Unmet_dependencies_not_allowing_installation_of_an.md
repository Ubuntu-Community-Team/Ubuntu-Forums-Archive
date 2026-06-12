---
title: "Unmet dependencies not allowing installation of anything else"
date: 2015-10-01
forum: Installation &amp; Upgrades
---

### Post by Shazer2 on 2015-10-01
[COLOR=#111111][FONT=Ubuntu]I was trying to install gSTM (a tunnel manager) because of some error in MySQL workbench but for some reason it has not worked and now I have a bunch of unmet dependency errors which arise when I try and install anything. I also can't remove anything (i.e. gSTM), because of these errors, below is a log.
[/FONT][/COLOR]
```
shannon@shannon:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer     required:
  python3-minimal libmono-sqlite4.0-cil
  libmono-system-web-services4.0-cil python-numpy python-matplotlib
  libwnck2.20-cil libmono-web4.0-cil kakasi-dic
  libmono-system-transactions4.0-cil python-matplotlib-data
  python-mutagen kakasi liblapack3gf python-mpd
  libmono-system-data4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libgnome-desktop-2-17 python-tz
  libmono-system-enterpriseservices4.0-cil libgnomedesktop2.20-cil
  librsvg2-2.18-cil libmono-system-web4.0-cil libblas3gf dockmanager
  libjpeg62:i386 libgfortran3 libgnome-keyring1.0-cil python3.2-dbg
  python-beautifulsoup libmono-system-xml-linq4.0-cil
  libmono-data-tds4.0-cil python-pyparsing
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libart-2.0-2:i386
The following NEW packages will be installed
  libart-2.0-2:i386
0 to upgrade, 1 to newly install, 0 to remove and 246 not to upgrade.
4 not fully installed or removed.
Need to get 0 B/64.4 kB of archives.
After this operation, 148 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 345875 files and directories currently installed.)
Unpacking libart-2.0-2:i386 (from .../libart-2.0-2_4%3a14.0.0-r5-0ubuntu12.04.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libart-2.0-2_4%3a14.0.0-r5-0ubuntu12.04.1_i386.deb (--unpack):
 './usr/lib/libart_lgpl_2.so.2.3.21' is different from the same file on the system
dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libart-2.0-2_4%3a14.0.0-r5-0ubuntu12.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

[COLOR=#111111][FONT=Ubuntu]No matter what I try I can't install any other packages. I even tried ```
sudo dpkg --configure -a
``` and I get similar errors.

Thanks.[/FONT][/COLOR]

---

### Post by dino99 on 2015-10-01
try :
sudo rm -f /var/cache/apt/archives/libart*

---

