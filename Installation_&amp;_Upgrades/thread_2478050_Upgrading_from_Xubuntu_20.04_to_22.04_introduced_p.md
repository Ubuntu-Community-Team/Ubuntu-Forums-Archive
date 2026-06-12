---
title: "Upgrading from Xubuntu 20.04 to 22.04 introduced python related errors"
date: 2022-08-15
forum: Installation &amp; Upgrades
---

### Post by medianmajik2 on 2022-08-15
Seems dpkg and apt-get no longer work.  Wondering if I'm simply not understanding what this error means in regards to repairing or reinstalling python.  Perhaps I do not understand how to correctly define the pythonhome and path.  I see python3.10 and such within /usr/bin
Thanks for any suggestions!

```
[FONT=monospace][COLOR=#000000]$ sudo apt-get update [/COLOR]
Hit:1 https://packages.element.io/debian default InRelease                                       
Hit:2 http://us.archive.ubuntu.com/ubuntu jammy InRelease                                                
Hit:3 http://security.ubuntu.com/ubuntu jammy-security InRelease                                         
Hit:4 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease                                        
Hit:5 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease 
Could not find platform independent libraries <prefix> 
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>] 
Python path configuration: 
  PYTHONHOME = (not set) 
  PYTHONPATH = (not set) 
  program name = '/usr/bin/python3' 
  isolated = 0 
  environment = 1 
  user site = 1 
  import site = 1 
  sys._base_executable = '/usr/bin/python3' 
  sys.base_prefix = '/usr' 
  sys.base_exec_prefix = '/usr' 
  sys.platlibdir = 'lib' 
  sys.executable = '/usr/bin/python3' 
  sys.prefix = '/usr' 
  sys.exec_prefix = '/usr' 
  sys.path = [ 
    '/usr/lib/python310.zip', 
    '/usr/lib/python3.10', 
    '/usr/lib/python3.10/lib-dynload', 
  ] 
Fatal Python error: init_fs_encoding: failed to get the Python codec of the filesystem encoding 
Python runtime state: core initialized 
ModuleNotFoundError: No module named 'encodings' 

Current thread 0x00007f1f48c8c740 (most recent call first): 
  <no Python frame> 
Reading package lists... Done 
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi' 
E: Sub-process returned an error code
[/FONT]
```

---

### Post by TheFu on 2022-08-15
Have you tried to install a different version of python in either 20.04 or 22.04?  Generally, that's a terrible idea.  The system expects the system-provided (Canonical) version of python.

It is possible to run different versions of all the scripting languages from that included with the system, but to do it safely requires setting up a virtual environment. All the scripting languages that I know have at least 1, if not 3 tools, designed to make doing that and switching between the system version and other versions for non-system needs relatively easy.

But if you didn't do anything with Python, I can only guess that sometime funky happened with the upgrade and to try again, watching the questions carefully to see where the breakage happens.  Good thing you backed up everything before replacing the OS, right?

---

### Post by Impavidus on 2022-08-16
And if that doesn't work, I recommend you backup all your documents and try a frsh install of Ubuntu 22.04.

---

