---
title: "Unable to install pygraphviz from pip? Can't find graphviz."
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by victorhooi on 2011-01-31
heya,

I'm having some issues installing pygraphviz from pip - yes, I know pygraphviz is in the repositories, but this is for a Django project, and I'm using virtualenv/virtualenvwrapper, hence the requirement for using pip.

```
Downloading/unpacking pygraphviz (from -r requirements.txt (line 2))
  Running setup.py egg_info for package pygraphviz
    /bin/sh: pkg-config: not found
    /bin/sh: pkg-config: not found
    Trying pkg-config
    Trying dotneato-config
    Failed to find dotneato-config

    Your graphviz installation could not be found.
    
    Either the graphviz package is missing on incomplete
    (binary packages graphviz-dev or graphviz-devel missing?).
    
    If you think your installation is correct you will need to manually
    change the include_path and library_path variables in setup.py to
    point to the correct locations of your graphviz installation.
    
    The current setting of library_path and include_path is:
    library_path=None
    include_path=None
    
    Traceback (most recent call last):
      File "<string>", line 14, in <module>
      File "/sites/.virtualenvs/colloquium/build/pygraphviz/setup.py", line 78, in <module>
        raise OSError,"Error locating graphviz."
    OSError: Error locating graphviz.
    Complete output from command python setup.py egg_info:
    /bin/sh: pkg-config: not found

/bin/sh: pkg-config: not found

Trying pkg-config

Trying dotneato-config

Failed to find dotneato-config



Your graphviz installation could not be found.



Either the graphviz package is missing on incomplete

(binary packages graphviz-dev or graphviz-devel missing?).



If you think your installation is correct you will need to manually


change the include_path and library_path variables in setup.py to

point to the correct locations of your graphviz installation.



The current setting of library_path and include_path is:

library_path=None

include_path=None



Traceback (most recent call last):

  File "<string>", line 14, in <module>

  File "/sites/.virtualenvs/colloquium/build/pygraphviz/setup.py", line 78, in <module>

    raise OSError,"Error locating graphviz."

OSError: Error locating graphviz.

----------------------------------------
Command python setup.py egg_info failed with error code 1
Storing complete log in /home/victorhooi/.pip/pip.log
Traceback (most recent call last):
  File "/sites/.virtualenvs/colloquium/bin/pip", line 8, in <module>
    load_entry_point('pip==0.8.1', 'console_scripts', 'pip')()
  File "/sites/.virtualenvs/colloquium/lib/python2.6/site-packages/pip-0.8.1-py2.6.egg/pip/__init__.py", line 116, in main
    return command.main(initial_args, args[1:], options)
  File "/sites/.virtualenvs/colloquium/lib/python2.6/site-packages/pip-0.8.1-py2.6.egg/pip/basecommand.py", line 149, in main
    log_fp = open_logfile(log_fn, 'w')
  File "/sites/.virtualenvs/colloquium/lib/python2.6/site-packages/pip-0.8.1-py2.6.egg/pip/basecommand.py", line 178, in open_logfile
    log_fp = open(filename, mode)
IOError: [Errno 13] Permission denied: '/home/victorhooi/.pip/pip.log'
```

I've installed python-dev, graphviz, graphviz-dev, and libgraphviz-dev, and it still doesn't seem to find it?

Any suggestions? Any help at all is greatly appreciated.

Cheers,
Victor

---

### Post by graingert on 2011-12-08
It seems install graphviz-dev and graphviz then doing pip install pygraphviz just works

---

### Post by drewbuschhorn on 2011-12-22
At little late to the party, but, one thing that worked for me was to install pkg-config .  Looks like easy_install / pygraphviz really prefers that on Ubuntu.

---

