---
title: "Problems installing Slimserver with aptitude..."
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by amokk on 2006-09-05
I use the newest Ubuntu Dapper 6.06 server and I've followed this guide:
[http://wiki.slimdevices.com/index.cgi?DebianPackage](http://wiki.slimdevices.com/index.cgi?DebianPackage)

But it doesn't seem to work... i've edited my sources.list to include the slimdevices repository....

The aptitude program does as seen below, but afterwards, no slimserver is found in the system?

```
esben@sbn-linuxserver:/usr/local$ sudo aptitude install slimserver
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libcache-cache-perl libclass-accessor-chained-perl libclass-dbi-perl libclass-trigger-perl librpc-xml-perl libtest-exception-perl libxml-twig-perl libxml-xpath-perl slimserver sox
The following NEW packages will be automatically installed:
  libCGI-perl libalgorithm-c3-perl libanydata-perl libcarp-assert-perl libclass-c3-perl libclass-data-accessor-perl libclass-data-inheritable-perl libclass-dbi-abstractsearch-perl
  libclass-inspector-perl libclass-singleton-perl libclass-virtual-perl libclass-whitehole-perl libdata-dump-perl libdata-page-perl libdata-vstring-perl libdbd-anydata-perl libdbd-csv-perl
  libdbix-class-perl libdbix-contextualfetch-perl libdbix-migration-perl libenum-perl liberror-perl libfile-bom-perl libfile-find-rule-perl libfile-slurp-perl libfile-which-perl libfilter-perl
  libfont-afm-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libima-dbi-perl libipc-sharelite-perl liblingua-en-inflect-perl libmp4-info-perl libmpeg-audio-frame-perl
  libmysqlclient14 libmysqlclient14-dev libnet-upnp-perl libnumber-compare-perl libpath-class-perl libpoe-perl libproc-background-perl libreadonly-perl libsql-abstract-limit-perl libsql-abstract-perl
  libsql-statement-perl libsub-uplevel-perl libtext-csv-perl libtext-glob-perl libtext-unidecode-perl libtie-cache-lru-expires-perl libtie-cache-lru-perl libtie-cache-perl libtie-llhash-perl
  libtie-regexphash-perl libtime-modules-perl libtimedate-perl libuniversal-moniker-perl liburi-find-perl liburi-perl libwww-perl libxml-writer-perl libxml-xspf-perl libyaml-perl libyaml-syck-perl
  zlib1g-dev
The following NEW packages will be installed:
  libCGI-perl libalgorithm-c3-perl libanydata-perl libcarp-assert-perl libclass-c3-perl libclass-data-accessor-perl libclass-data-inheritable-perl libclass-dbi-abstractsearch-perl
  libclass-inspector-perl libclass-singleton-perl libclass-virtual-perl libclass-whitehole-perl libdata-dump-perl libdata-page-perl libdata-vstring-perl libdbd-anydata-perl libdbd-csv-perl
  libdbix-class-perl libdbix-contextualfetch-perl libdbix-migration-perl libenum-perl liberror-perl libfile-bom-perl libfile-find-rule-perl libfile-slurp-perl libfile-which-perl libfilter-perl
  libfont-afm-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libima-dbi-perl libipc-sharelite-perl liblingua-en-inflect-perl libmp4-info-perl libmpeg-audio-frame-perl
  libmysqlclient14 libmysqlclient14-dev libnet-upnp-perl libnumber-compare-perl libpath-class-perl libpoe-perl libproc-background-perl libreadonly-perl libsql-abstract-limit-perl libsql-abstract-perl
  libsql-statement-perl libsub-uplevel-perl libtext-csv-perl libtext-glob-perl libtext-unidecode-perl libtie-cache-lru-expires-perl libtie-cache-lru-perl libtie-cache-perl libtie-llhash-perl
  libtie-regexphash-perl libtime-modules-perl libtimedate-perl libuniversal-moniker-perl liburi-find-perl liburi-perl libwww-perl libxml-writer-perl libxml-xspf-perl libyaml-perl libyaml-syck-perl
  zlib1g-dev
0 packages upgraded, 78 newly installed, 0 to remove and 0 not upgraded.
Need to get 31,1MB/32,3MB of archives. After unpacking 94,7MB will be used.
The following packages have unmet dependencies:
  libtest-exception-perl: Depends: libtest-builder-tester-perl which is a virtual package.
  libclass-trigger-perl: Depends: libio-stringy-perl which is a virtual package.
  libclass-accessor-chained-perl: Depends: libclass-accessor-perl which is a virtual package.
  libcache-cache-perl: Depends: libdigest-sha1-perl (>= 2.02) which is a virtual package.
  libxml-twig-perl: Depends: libxml-parser-perl which is a virtual package.
  librpc-xml-perl: Depends: libxml-parser-perl which is a virtual package.
  sox: Depends: libmad0 (>= 0.15.1b) which is a virtual package.
       Depends: libogg0 (>= 1.1.3) which is a virtual package.
       Depends: libvorbis0a (>= 1.1.2) which is a virtual package.
       Depends: libvorbisenc2 (>= 1.1.2) which is a virtual package.
       Depends: libvorbisfile3 (>= 1.1.2) which is a virtual package.
  libxml-xpath-perl: Depends: libxml-parser-perl which is a virtual package.
  slimserver: Depends: libgd-gd2-noxpm-perl which is a virtual package. or
                       libgd-gd2-perl which is a virtual package.
              Depends: libio-string-perl which is a virtual package.
              Depends: libio-socket-ssl-perl which is a virtual package.
              Depends: libnet-dns-perl which is a virtual package.
              Depends: libtemplate-perl which is a virtual package.
              Depends: libnet-ip-perl which is a virtual package.
              Depends: libdigest-sha1-perl which is a virtual package.
              Depends: libcarp-clan-perl which is a virtual package.
              Depends: libxml-parser-perl which is a virtual package.
              Depends: flac which is a virtual package.
  libclass-dbi-perl: Depends: libclass-accessor-perl (>= 0.18) which is a virtual package.
Resolving dependencies...
[B]The following actions will resolve these dependencies:

Keep the following packages at their current version:[/B]
libanydata-perl [Not Installed]
libcache-cache-perl [Not Installed]
libclass-accessor-chained-perl [Not Installed]
libclass-dbi-abstractsearch-perl [Not Installed]
libclass-dbi-perl [Not Installed]
libclass-trigger-perl [Not Installed]
libdata-page-perl [Not Installed]
libdbd-anydata-perl [Not Installed]
librpc-xml-perl [Not Installed]
libsql-abstract-limit-perl [Not Installed]
libtest-exception-perl [Not Installed]
libxml-twig-perl [Not Installed]
libxml-xpath-perl [Not Installed]
slimserver [Not Installed]
sox [Not Installed]

[B]Leave the following dependencies unresolved:
libwww-perl recommends libmailtools-perl
Score is -75

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
esben@sbn-linuxserver:/usr/local$ ls
bin  games  include  lib  man  sbin  share  src
esben@sbn-linuxserver:/usr/local$[/B]
```

---

### Post by dog on 2006-09-05
Slimserver was not installed because of broken dependencies for several packages.

Did you see the sentences:

Ubuntu users may need to add Universe to their sources.list file. There will be two lines near the top of your existing sources.list ending in "universe" that will need to be uncommented.

Did you do this?

If you did, then you may have other issues.

Try sudo apt-get update       then 

sudo apt-get dist-upgrade

and try again.

I just followed the install procedures on slimdevices web-site (but using apt-get instead of aptitude) and it worked fine.



dog

---

### Post by amokk on 2006-09-11
now i get this:

```

esben@sbn-linuxserver:~$ sudo apt-get install slimserver
Reading package lists... Done
Building dependency tree... Done
Package slimserver is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package slimserver has no installation candidate

```

---

### Post by dog on 2006-09-11
amokk,

I see from the slimdevices forum where you posted more details that your sources.list file contains some depositories that are commented out because they were not verified at some stage. Try uncommenting each line beginning '# deb' then sudo apt-get update to see if this allows you to download more of the files on which slimserver is dependent.


dog

---

### Post by amokk on 2006-09-14
i think the shit works now! i uncommented all deb lines from sources.list... :-)

---

