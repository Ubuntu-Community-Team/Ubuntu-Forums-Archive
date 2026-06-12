---
title: "jaunty python/virtualenv bug?"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jpt2433 on 2009-03-13
Hi,

I have a somewhat weird installation on my laptop and can't really do a fresh one right now, so I'm not sure but I think I've run into a bug caused by Jaunty's adoption of Python 2.6.

This should be fairly easy to confirm though:

```

$ sudo apt-get install python-virtualenv
$ virtualenv test
New python executable in test/bin/python
Installing setuptools...................
  Complete output from command test/bin/python -c "#!python
\"\"\"Bootstrap setuptoo...




" /usr/local/lib/python2.6/dist-...6.egg:
  error: can't create or remove files in install directory

The following error occurred while trying to add or remove files in the
installation directory:

    [Errno 2] No such file or directory: '/home/james/Desktop/test/local/lib/python2.6/dist-packages/test-easy-install-11092.pth'

The installation directory you specified (via --install-dir, --prefix, or
the distutils default setting) was:

    /home/james/Desktop/test/local/lib/python2.6/dist-packages/

This directory does not currently exist.  Please create it and try again, or
choose a different installation directory (using the -d or --install-dir
option).

----------------------------------------
...Installing setuptools...done.
Traceback (most recent call last):
  File "/usr/local/bin/virtualenv", line 8, in <module>
    load_entry_point('virtualenv==1.3.3', 'console_scripts', 'virtualenv')()
  File "/usr/local/lib/python2.6/dist-packages/virtualenv-1.3.3-py2.6.egg/virtualenv.py", line 420, in main
    unzip_setuptools=options.unzip_setuptools)
  File "/usr/local/lib/python2.6/dist-packages/virtualenv-1.3.3-py2.6.egg/virtualenv.py", line 507, in create_environment
    install_setuptools(py_executable, unzip=unzip_setuptools)
  File "/usr/local/lib/python2.6/dist-packages/virtualenv-1.3.3-py2.6.egg/virtualenv.py", line 295, in install_setuptools
    cwd=cwd)
  File "/usr/local/lib/python2.6/dist-packages/virtualenv-1.3.3-py2.6.egg/virtualenv.py", line 481, in call_subprocess
    % (cmd_desc, proc.returncode))
OSError: Command test/bin/python -c "#!python
\"\"\"Bootstrap setuptoo...




" /usr/local/lib/python2.6/dist-...6.egg failed with error code 1

```

can someone else try this out and verify?  I'd like to file a bug but I'm not convinced that this isn't my own semi-messed up python installation that is causing this.

---

### Post by piquadrat on 2009-03-18
Yeah, it's a bug

[https://bugs.launchpad.net/ubuntu/+source/python-virtualenv/+bug/339904/](https://bugs.launchpad.net/ubuntu/+source/python-virtualenv/+bug/339904/)

---

