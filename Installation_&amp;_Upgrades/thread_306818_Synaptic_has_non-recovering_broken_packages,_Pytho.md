---
title: "Synaptic has non-recovering broken packages, Python problems suspected"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by Enselic on 2006-11-25
Hi there,

I get these errors everytime I do something with synaptic:

```

scons is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up pitivi (0.10.1-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 876, in run
    self.options.exclude, byte_compile_default=True)
  File "/usr/bin/pycentral", line 668, in install
    self.default_runtime.byte_compile(self.private_files,
AttributeError: 'NoneType' object has no attribute 'byte_compile'
dpkg: error processing pitivi (--configure):
 subprocess post-installation script returned error exit status 1
Setting up scons (0.96.92-2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 876, in run
    self.options.exclude, byte_compile_default=True)
  File "/usr/bin/pycentral", line 668, in install
    self.default_runtime.byte_compile(self.private_files,
AttributeError: 'NoneType' object has no attribute 'byte_compile'
dpkg: error processing scons (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pitivi
 scons
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I don't know where to start looking, what could I do?

---

### Post by Enselic on 2006-12-03
A googling only gives me that I should have python2.4 installed, which I do have, so I am bumping this in hope that it will be noticed by someone who has a clue of what to do.

---

### Post by sp1nm0nkey on 2006-12-10
Bump. I'm having the exact same problem.

---

### Post by dangriffin on 2006-12-10
I had a similar experience with python-uno (OpenOffice.org) integration. My problem was down in a bug in pyversions (part of pycentral, the system that manages python packages for dpkg/apt/synaptic). 

There is a bug in my current version of pyversions that stops it from correctly returning the default version of python. Try running this:

:~$ pyversions -vd

My system comes back with this:

in/python2.4

This should have returned '2.4', but a bit of dodgy python string slicing makes it return a meaningless string (the correct location of my python interpreter is /usr/bin/python2.4). This bug prevents pycentral from being able to find a default python runtime (it gets set to None), so when synaptic tries to use it when installing/fixing packages, it fails miserably with errors relating to 'NoneType' (as I see you are having)

As a hack, you can temporarily force pycentral to a default version (for example '2.4'. To do this, become root (sudo -i) and then make a backup of the file:

/usr/bin/pycentral

Change this file on your system in the following way:

1) Locate the section of the file that looks like this:

```
def get_installed_runtimes(with_unsupported=False):
    global installed_runtimes
    global default_runtime

    if not installed_runtimes:
        import glob
        installed_runtimes = []
        default_version = pyversions.default_version(version_only=True)
        supported = pyversions.supported_versions()
        old = pyversions.old_versions()
        if with_unsupported:
            unsupported = pyversions.unsupported_versions()
        else:
            unsupported = []
        for interp in glob.glob('/usr/bin/python[0-9].[0-9]'):
            if old and os.path.basename(interp) in old:
                print "INFO: using old version '%s'" % interp
            elif unsupported and os.path.basename(interp) in unsupported:
                print "INFO: using unsupported ver

...
```

2) Change the line "default_version = pyversions.default_version(version_only=True)" to:

default_version = "2.4"

3) Save out the file.

Try running the synaptic job again. Hopefully now it should find a default runtime and work correctly.

---

### Post by trashie on 2006-12-14
Thanks a lot !
Your hack worked fine for me.

Mathieu

---

