---
title: "apt-get/aptitude stuck on (mostly) python packages after upgrade to 11.04"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by cazabon on 2011-10-23
I have an amd64 system, upgraded several times from hardy and was running lucid for quite some time.  Today I upgraded to maverick without any issues (though I did remove all nonstandard repos from my apt config first), but then did another upgrade to natty/11.04 to try to get some improved hardware support, and the upgrader got stuck and bailed out.

Most of the way through the install it said there had been an (unspecified) error and now apt-get/aptitude report problems with unconfigured packages and missing dependencies.  I've tried the standard recommended solutions like `dpkg --configure -a`, `apt-get install -f`, etc.  Running dpkg --configure -a gives a list of mostly Python-related packages that aren't fully/correctly installed, but I've been unable to force those to install.  The py_compile.py step in installing packages gives errors as well during this.  Full output is long (using --abort-after=1000 to prevent it bailing out early) but here it is:

```

$ sudo dpkg --configure -a --abort-after=1000
Setting up python (2.7.1-0ubuntu5) ...
Linking and byte-compiling packages for runtime python2.7...
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/runpy.py", line 162, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/local/lib/python2.7/runpy.py", line 72, in _run_code
    exec code in run_globals
  File "/usr/local/lib/python2.7/py_compile.py", line 168, in <module>
    sys.exit(main())
  File "/usr/local/lib/python2.7/py_compile.py", line 160, in main
    compile(filename, doraise=True)
  File "/usr/local/lib/python2.7/py_compile.py", line 115, in compile
    f = open(file, 'U')
IOError: [Errno 2] No such file or directory: '-'

WARNING: ignoring errors during python-defaults update.
WARNING: please check if these are already reported, and
WARNING: if not, file a bug report against the 
WARNING: python-defaults package

running python rtupdate hooks for python2.7...
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/runpy.py", line 162, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/local/lib/python2.7/runpy.py", line 72, in _run_code
    exec code in run_globals
  File "/usr/local/lib/python2.7/py_compile.py", line 168, in <module>
    sys.exit(main())
  File "/usr/local/lib/python2.7/py_compile.py", line 160, in main
    compile(filename, doraise=True)
  File "/usr/local/lib/python2.7/py_compile.py", line 115, in compile
    f = open(file, 'U')
IOError: [Errno 2] No such file or directory: '-'
error running python rtupdate hook python-gobject-dev
dpkg: error processing python (--configure):
 subprocess installed post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of gdebi-core:
 gdebi-core depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 gdebi-core depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing gdebi-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-aptdaemon.gtk3widgets depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-runner:
 python-twisted-runner depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-twisted-runner depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-twisted-runner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-lazr.uri:
 python-lazr.uri depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
dpkg: error processing python-lazr.uri (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pygments:
 python-pygments depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
dpkg: error processing python-pygments (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 update-manager-core depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-words:
 python-twisted-words depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-twisted-words depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-twisted-words (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-lore:
 python-twisted-lore depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-twisted-lore depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-twisted-lore (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gobject-dev:
 python-gobject-dev depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
dpkg: error processing python-gobject-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-keyring:
 python-keyring depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
dpkg: error processing python-keyring (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-imaging-sane:
 python-imaging-sane depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-imaging-sane depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-imaging-sane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-scour:
 python-scour depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-scour depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-scour (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-bzrlib:
 python-bzrlib depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
dpkg: error processing python-bzrlib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-packagekit:
 python-packagekit depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-packagekit depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-packagekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-serial:
 python-serial depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-serial depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-serial (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtkwidgets:
 python-aptdaemon.gtkwidgets depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-aptdaemon.gtkwidgets depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-aptdaemon.gtkwidgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ufw:
 ufw depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 ufw depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing ufw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gobject:
 python-gobject depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-gobject depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-gobject (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-simplejson:
 python-simplejson depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
dpkg: error processing python-simplejson (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-core:
 python-twisted-core depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-twisted-core depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-twisted-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 gdebi depends on python (<< 2.8); however:
  Package python is not configured yet.
 gdebi depends on gdebi-core (= 0.7.0); however:
  Package gdebi-core is not configured yet.
dpkg: error processing gdebi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-wadllib:
 python-wadllib depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-wadllib depends on python-lazr.uri; however:
  Package python-lazr.uri is not configured yet.
 python-wadllib depends on python-simplejson; however:
  Package python-simplejson is not configured yet.
dpkg: error processing python-wadllib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-markupsafe:
 python-markupsafe depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-markupsafe depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-markupsafe (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-imaging:
 python-imaging depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-imaging depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-imaging (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apt:
 python-apt depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-apt depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-common:
 nvidia-common depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 nvidia-common depends on python (<< 2.8); however:
  Package python is not configured yet.
 nvidia-common depends on python-apt; however:
  Package python-apt is not configured yet.
dpkg: error processing nvidia-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-openssl:
 python-openssl depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-openssl depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-openssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-piston-mini-client:
 python-piston-mini-client depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-piston-mini-client depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-piston-mini-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 language-selector-common depends on python (<< 2.8); however:
  Package python is not configured yet.
 language-selector-common depends on python-apt (>= 0.7.12.0); however:
  Package python-apt is not configured yet.
dpkg: error processing language-selector-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-mail:
 python-twisted-mail depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-twisted-mail depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-twisted-mail depends on python-twisted-core (>= 10.2); however:
  Package python-twisted-core is not configured yet.
 python-twisted-mail depends on python-openssl; however:
  Package python-openssl is not configured yet.
dpkg: error processing python-twisted-mail (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-news:
 python-twisted-news depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-twisted-news depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-twisted-news depends on python-twisted-core (>= 10.2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-news (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-httplib2:
 python-httplib2 depends on python (>= 2.6.5-11~); however:
  Package python is not configured yet.
dpkg: error processing python-httplib2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-setuptools:
 python-setuptools depends on python (>= 2.5); however:
  Package python is not configured yet.
 python-setuptools depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-setuptools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 update-manager depends on python (<< 2.8); however:
  Package python is not configured yet.
 update-manager depends on update-manager-core (= 1:0.150.4); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-uno depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-lazr.restfulclient:
 python-lazr.restfulclient depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-lazr.restfulclient depends on python-httplib2; however:
  Package python-httplib2 is not configured yet.
 python-lazr.restfulclient depends on python-wadllib (>= 1.1.4); however:
  Package python-wadllib is not configured yet.
 python-lazr.restfulclient depends on python-simplejson; however:
  Package python-simplejson is not configured yet.
dpkg: error processing python-lazr.restfulclient (--configure):
 dependency problems - leaving unconfigured
Setting up gir1.2-dee-0.5 (0.5.18-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 322, in <module>
    main()
  File "/usr/bin/pycompile", line 299, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 217, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 180, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing gir1.2-dee-0.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-twisted-names:
 python-twisted-names depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-twisted-names depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-twisted-names depends on python-twisted-core (>= 10.1); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-names (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pkg-resources:
 python-pkg-resources depends on python (>= 2.5); however:
  Package python is not configured yet.
 python-pkg-resources depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-conch:
 python-twisted-conch depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-twisted-conch depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-twisted-conch depends on python-twisted-core (>= 10.2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-conch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-lxml:
 python-lxml depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-lxml depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-lxml (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl-common:
 apturl-common depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 apturl-common depends on python (<< 2.8); however:
  Package python is not configured yet.
 apturl-common depends on python-apt; however:
  Package python-apt is not configured yet.
dpkg: error processing apturl-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon:
 python-aptdaemon depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-aptdaemon depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-aptdaemon depends on python-apt (>= 0.7.96.1ubuntu9); however:
  Package python-apt is not configured yet.
 python-aptdaemon depends on python-gobject; however:
  Package python-gobject is not configured yet.
dpkg: error processing python-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 apturl depends on python (<< 2.8); however:
  Package python is not configured yet.
 apturl depends on apturl-common (= 0.4.2ubuntu5.1); however:
  Package apturl-common is not configured yet.
 apturl depends on python-gobject; however:
  Package python-gobject is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-reportlab:
 python-reportlab depends on python (>= 2.6.5-11~); however:
  Package python is not configured yet.
 python-reportlab depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-reportlab (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-mako:
 python-mako depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-mako depends on python-markupsafe; however:
  Package python-markupsafe is not configured yet.
dpkg: error processing python-mako (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-defer:
 python-defer depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-defer depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-defer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-common:
 jockey-common depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 jockey-common depends on python (<< 2.8); however:
  Package python is not configured yet.
 jockey-common depends on python-apt; however:
  Package python-apt is not configured yet.
dpkg: error processing jockey-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-web:
 python-twisted-web depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-twisted-web depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-twisted-web depends on python-twisted-core (>= 10.2); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-web (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-unity-3.0:
 gir1.2-unity-3.0 depends on gir1.2-dee-0.5; however:
  Package gir1.2-dee-0.5 is not configured yet.
dpkg: error processing gir1.2-unity-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-gnome:
 language-selector-gnome depends on language-selector-common (= 0.34.2); however:
  Package language-selector-common is not configured yet.
 language-selector-gnome depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 language-selector-gnome depends on python (<< 2.8); however:
  Package python is not configured yet.
 language-selector-gnome depends on python-gobject (>= 2.27.91); however:
  Package python-gobject is not configured yet.
 language-selector-gnome depends on python-apt (>= 0.6.12); however:
  Package python-apt is not configured yet.
 language-selector-gnome depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing language-selector-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-beautifulsoup:
 python-beautifulsoup depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
dpkg: error processing python-beautifulsoup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-configobj:
 python-configobj depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
dpkg: error processing python-configobj (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python
 gdebi-core
 python-aptdaemon.gtk3widgets
 python-twisted-runner
 python-lazr.uri
 python-pygments
 update-manager-core
 python-twisted-words
 python-twisted-lore
 python-gobject-dev
 python-keyring
 python-imaging-sane
 python-scour
 python-bzrlib
 python-packagekit
 python-serial
 python-aptdaemon.gtkwidgets
 ufw
 python-gobject
 python-simplejson
 python-twisted-core
 gdebi
 python-wadllib
 python-markupsafe
 python-imaging
 python-apt
 nvidia-common
 python-openssl
 python-piston-mini-client
 language-selector-common
 python-twisted-mail
 python-twisted-news
 python-httplib2
 python-setuptools
 update-manager
 python-uno
 python-lazr.restfulclient
 gir1.2-dee-0.5
 python-twisted-names
 python-pkg-resources
 python-twisted-conch
 python-lxml
 apturl-common
 python-aptdaemon
 apturl
 python-reportlab
 python-mako
 python-defer
 jockey-common
 python-twisted-web
 gir1.2-unity-3.0
 language-selector-gnome
 python-beautifulsoup
 python-configobj

```I'm looking for a way to get dpkg/apt-get/aptitude back to sanity, preferably without trying to do a reinstall of the system, as the system configuration is fairly complex and other than these problems, the system is still usable.

Any help appreciated.  Thanks,

Charles

---

### Post by zvacet on 2011-10-24
It looks that python package is one witch prevent others to be installed.Try with 

```
sudo dpkg --configure python
```

---

### Post by cazabon on 2011-10-24
Thanks for looking at this - but trying to configure just python results in a similar problem:

```
$ sudo dpkg --configure python
Setting up python (2.7.1-0ubuntu5) ...
Linking and byte-compiling packages for runtime python2.7...
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/runpy.py", line 162, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/local/lib/python2.7/runpy.py", line 72, in _run_code
    exec code in run_globals
  File "/usr/local/lib/python2.7/py_compile.py", line 168, in <module>
    sys.exit(main())
  File "/usr/local/lib/python2.7/py_compile.py", line 160, in main
    compile(filename, doraise=True)
  File "/usr/local/lib/python2.7/py_compile.py", line 115, in compile
    f = open(file, 'U')
IOError: [Errno 2] No such file or directory: '-'

WARNING: ignoring errors during python-defaults update.
WARNING: please check if these are already reported, and
WARNING: if not, file a bug report against the 
WARNING: python-defaults package

running python rtupdate hooks for python2.7...
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/runpy.py", line 162, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/local/lib/python2.7/runpy.py", line 72, in _run_code
    exec code in run_globals
  File "/usr/local/lib/python2.7/py_compile.py", line 168, in <module>
    sys.exit(main())
  File "/usr/local/lib/python2.7/py_compile.py", line 160, in main
    compile(filename, doraise=True)
  File "/usr/local/lib/python2.7/py_compile.py", line 115, in compile
    f = open(file, 'U')
IOError: [Errno 2] No such file or directory: '-'
error running python rtupdate hook python-gobject-dev
dpkg: error processing python (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 python

```

Any further ideas appreciated.

Charles

---

### Post by cazabon on 2011-10-24
Answering my own question, for the benefit of anyone else running into this problem: I had a local (non-deb/apt) installation of Python 2.7 in /usr/local/, and apparently it was causing this problem (even though root's PATH shouldn't be using /usr/local/bin/).  Removing/renaming the python executable in that fixed this issue, allowing `dpkg --configure -a` to fix the rest of the half-installed/unconfigured packages.

Thanks to all who looked into this.

Charles

---

