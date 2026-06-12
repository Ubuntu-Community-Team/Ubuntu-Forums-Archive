---
title: "Issues to install modules on python3"
date: 2018-01-30
forum: Installation &amp; Upgrades
---

### Post by romzy on 2018-01-30
I recently reinstalled kubuntu 17.04, miniconda, pyzo and pip using 

```
sudo apt-get install python3-pip
```

 but now I can't install modules in python shell using : ```
pip install matplotlib
```

it prints : ```
PermissionError: [Errno 13] Permission denied: '/home/romrom/miniconda3/lib/python3.6/site-packages/python_dateutil-2.6.1.dist-info'
```

I tried to type in a terminal this :  ```
python3 -m pip install numpy
```

but it returns in red : 
```
Exception:
Traceback (most recent call last):
  File "/home/romrom/miniconda3/lib/python3.6/site-packages/pip/basecommand.py", line 215, in main
    status = self.run(options, args)
  File "/home/romrom/miniconda3/lib/python3.6/site-packages/pip/commands/install.py", line 342, in run
    prefix=options.prefix_path,
  File "/home/romrom/miniconda3/lib/python3.6/site-packages/pip/req/req_set.py", line 784, in install
    **kwargs
  File "/home/romrom/miniconda3/lib/python3.6/site-packages/pip/req/req_install.py", line 851, in install                            
    self.move_wheel_files(self.source_dir, root=root, prefix=prefix)                                                                 
  File "/home/romrom/miniconda3/lib/python3.6/site-packages/pip/req/req_install.py", line 1064, in move_wheel_files                  
    isolated=self.isolated,                                                                                                          
  File "/home/romrom/miniconda3/lib/python3.6/site-packages/pip/wheel.py", line 345, in move_wheel_files                             
    clobber(source, lib_dir, True)                                                                                                   
  File "/home/romrom/miniconda3/lib/python3.6/site-packages/pip/wheel.py", line 316, in clobber                                      
    ensure_dir(destdir)                                                                                                              
  File "/home/romrom/miniconda3/lib/python3.6/site-packages/pip/utils/__init__.py", line 83, in ensure_dir                           
    os.makedirs(path)                                                                                                                
  File "/home/romrom/miniconda3/lib/python3.6/os.py", line 220, in makedirs                                                          
    mkdir(name, mode)                                                                                                                
PermissionError: [Errno 13] Permission denied: '/home/romrom/miniconda3/lib/python3.6/site-packages/numpy-1.14.0.dist-info' 

```

I don't know what to do.. should I use Virtualbox ?

Thanks

---

### Post by TheFu on 2018-01-30
17.04 support ended.  
Move the 17.10 for the next 6 months before support for it ends or back to 16.04 which is an LTS release.

There are 3 ways to manage python, perl, ruby, .... libraries. Each has pros and cons.
1) Use the system installer for everything.  When using the system python, this is preferred, since the system installer will have python modules and libraries for the same version.  For using system tools, this is smart.

2) Use pip for everything.  When using a newer python or different, non-system python, then the modules and libraries need to be managed OUTSIDE the system areas. This is smart for people needing newer libraries than the system versions, but all dependency management is left to you.

3) Use a python environment tool, like pyenv.  This is for python developers who need to have complete control over the version of python and the libraries/modules.  This is smart for professional developers working on webapps. The entire setup - python, libraries, modules are all contained and aren't tied to the system python in any way.

Not sure what virtualbox has to do with this question.  Shouldn't matter.

Permissions issues are something that every developer or **any** Linux user needs to understand and fix.  Linux is multi-user from the base up.  It will always be multi-user.  Learn to correct permissions issues.  Ubuntu has a file and directory permissions tutorial, which might be a helpful introduction.  
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

In my years of helping students learn this stuff, I've found that the only way to learn permissions is to take about 45 minutes and play around with 3 different userids, 3 different groupid  in some temporary directories trying every possible combination of permissions, grouping, non-grouping, and seeing what can be read, modified, deleted by each different userid in all the different situations.  Once you learn this, it is applicable to **every other popular OS** in the world.  It is mainly useful for Unix-based systems, which is effectively everything, except MS-Windows.

And as a coder, file and directory permissions is basic knowledge to have.  Without a good understanding, there will be hours, days, weeks, months of frustration using any Unix-like system.

OTOH, if you just want to know what to type, then try **sudo chmod -R romrom ~/** and hope that doesn't screw things up.  It is unlikely, but impossible to know what is and isn't setup on your system from here.  "romrom" is assumed to be your userid on the system.  It would usually follow that pattern, but may not.

Good luck.

---

### Post by romzy on 2018-01-30
You really got me..
After half an hour of rage, I'm gonna thank you for solving the monstruous problem I've been facing !

How do you put the topic in solved ?

---

### Post by TheFu on 2018-01-30
thread tools at the top of the page has a "mark solved" choice.

BTW, we all started out where you are today.  Unix isn't intuitive in the beginning, but the more you learn the more things "fit" and knowledge builds on what you already know.  Permissions are the cornerstone of all Unix security and access controls, so they really are important to know.

---

