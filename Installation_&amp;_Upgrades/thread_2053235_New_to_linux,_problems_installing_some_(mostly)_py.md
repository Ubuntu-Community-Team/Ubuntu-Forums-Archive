---
title: "New to linux, problems installing some (mostly) python packages"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by brightstarvi on 2012-09-04
I'm pretty much brand new to linux. For obscure and mostly unintelligible reasons, I'm trying to set up a Ubuntu server 10.04 install on a second computer. Everything was going fine until I tried installing some node.js dependencies.

I've been roaming around the internet trying random commands to fix this mess, and it seems to be having no effect at all.

I'm willing to try just about anything here. I'm not terribly attached to this install, so if for whatever reason I have to start from scratch, that's doable.

I'd really like to just make this work, preferably sooner than later.

Here's the output from: sudo dpkg --configure -a

Let me know what else I could do that might give useful info.

```
Setting up python-pkg-resources (0.6.24-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 289, in <module>
    main()
  File "/usr/bin/pycompile", line 262, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 178, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 141, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing python-pkg-resources (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-dbus (1.1.1-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 289, in <module>
    main()
  File "/usr/bin/pycompile", line 262, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 178, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 141, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing python-dbus (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-zope.interface:
 python-zope.interface depends on python-pkg-resources; however:
  Package python-pkg-resources is not configured yet.
dpkg: error processing python-zope.interface (--configure):
 dependency problems - leaving unconfigured
Setting up lsb-release (4.1+Debian7) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 289, in <module>
    main()
  File "/usr/bin/pycompile", line 262, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 178, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 141, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing lsb-release (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-gi (3.2.2-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 289, in <module>
    main()
  File "/usr/bin/pycompile", line 262, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 178, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 141, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing python-gi (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-software-properties:
 python-software-properties depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing python-software-properties (--configure):
 dependency problems - leaving unconfigured
Setting up python-newt (0.52.14-11) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 289, in <module>
    main()
  File "/usr/bin/pycompile", line 262, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 178, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 141, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing python-newt (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-smartpm (1.4-2) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 289, in <module>
    main()
  File "/usr/bin/pycompile", line 262, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 178, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 141, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing python-smartpm (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-gobject-2 (2.28.6-10) ...
Traceback (most recent call last):
  File "/usr/lib/python2.6/runpy.py", line 122, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/lib/python2.6/runpy.py", line 34, in _run_code
    exec code in run_globals
  File "/usr/lib/python2.6/py_compile.py", line 168, in <module>
    sys.exit(main())
  File "/usr/lib/python2.6/py_compile.py", line 160, in main
    compile(filename, doraise=True)
  File "/usr/lib/python2.6/py_compile.py", line 115, in compile
    f = open(file, 'U')
IOError: [Errno 2] No such file or directory: '-'
dpkg: error processing python-gobject-2 (--configure):
 subprocess installed post-installation script returned error exit status 99
dpkg: dependency problems prevent configuration of unattended-upgrades:
 unattended-upgrades depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
Setting up ufw (0.31.1-2) ...
update-rc.d: warning: /etc/init.d/ufw missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 289, in <module>
    main()
  File "/usr/bin/pycompile", line 262, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 178, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 141, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing ufw (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-gobject:
 python-gobject depends on python-gi (>= 3.2.2-1); however:
  Package python-gi is not configured yet.
 python-gobject depends on python-gobject-2; however:
  Package python-gobject-2 is not configured yet.
dpkg: error processing python-gobject (--configure):
 dependency problems - leaving unconfigured
Setting up python-simplejson (2.6.1-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 289, in <module>
    main()
  File "/usr/bin/pycompile", line 262, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 178, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 141, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing python-simplejson (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-twisted-core:
 python-twisted-core depends on python-zope.interface (>= 3.5); however:
  Package python-zope.interface is not configured yet.
dpkg: error processing python-twisted-core (--configure):
 dependency problems - leaving unconfigured
Setting up python-apt (0.8.7) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 289, in <module>
    main()
  File "/usr/bin/pycompile", line 262, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 178, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 141, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing python-apt (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-lazr.restfulclient:
 python-lazr.restfulclient depends on python-zope.interface | python-zopeinterfa                         ce; however:
  Package python-zope.interface is not configured yet.
  Package python-zopeinterface is not installed.
  Package python-zope.interface which provides python-zopeinterface is not confi                         gured yet.
 python-lazr.restfulclient depends on python-pkg-resources; however:
  Package python-pkg-resources is not configured yet.
 python-lazr.restfulclient depends on python-simplejson; however:
  Package python-simplejson is not configured yet.
dpkg: error processing python-lazr.restfulclient (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-pkg-resources
 python-dbus
 python-zope.interface
 lsb-release
 python-gi
 python-software-properties
 python-newt
 python-smartpm
 python-gobject-2
 unattended-upgrades
 ufw
 python-gobject
 python-simplejson
 python-twisted-core
 python-apt
 python-lazr.restfulclient

```

---

### Post by brightstarvi on 2012-09-05
I really don't know what to try other than a fresh install. I'm pretty certain that the problem isn't that serious, and if I were working in a more familiar environment, I'm sure the answer would be obvious to me. Here I'm not even sure where to start.

I'll check back when I wake up. Any help would be appreciated very much.

---

### Post by brightstarvi on 2012-09-05
One last try, I guess. Anybody have any idea about this?

---

### Post by oldfred on 2012-09-08
In installing python did you overwrite or uninstall the standard version?
Ubuntu depends on whatever is the current version to run many internal things. If the default gets set to another version then Ubuntu does not work.

Sometimes reinstalling the standard version or looking at the links to python and making sure they are from the default not any other version.

---

