---
title: "gdebi, apt-get, and dpkg not working."
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by divali on 2008-01-20
Ever since the new updates, I have been having problems and cannot fix the new Xorg/Nvidia 
situation it has left me with due to the other breakages , as above.

Any help here would be grateully appreciated.

> divali@ubuntu:~$ sudo apt-get update
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB                     
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Get: 3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB               
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_GB             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_GB         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB       
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_GB      
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_GB           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_GB       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Get: 7 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]         
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_GB        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Fetched 7B in 1s (6B/s)  
Reading package lists... Done

As you can see update is ok

But here comes the errors and I don't know what to do to resolve them.

> [I]divali@ubuntu:~$ sudo dpkg --configure -a && sudo apt-get -f install
dpkg: error processing restricted-manager (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: error processing gdebi (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 restricted-manager
 gdebi[/I]

---

### Post by divali on 2008-01-20
Any help here?

---

### Post by kellemes on 2008-01-20
Never heard of this one, not sure if this is bad news to be honest..

You can try the following, simply do what's advised..
Namely, reinstall the packages[I].

[/I]from terminal..
```

sudo apt-get remove --purge restricted-manager
sudo apt-get remove --purge gdebi
sudo apt-get install restricted-manager
sudo apt-get install gdebi

```

Hope this helps..

---

### Post by divali on 2008-01-20
Here's the result for the first line of code.
And the othe lines produce a negative response as well.

divali@ubuntu:~$ sudo apt-get remove --purge restricted-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python2.4-minimal python2.4 restricted-manager-core
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  restricted-manager*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/30.0kB of archives.
After unpacking 324kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing restricted-manager (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 restricted-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by erginemr on 2008-01-20
What is the outcome of the command:

```
dpkg -l restricted-manager*
```

and also of the command:

```
cat /var/lib/dpkg/status | grep -A 1 "Package: restricted-manager"
```

---

### Post by divali on 2008-01-20
```
dpkg -l restricted-manager*
```


divali@ubuntu:~$ dpkg -l restricted-manager*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iFR restricted-man 0.33.1         manage non-free hardware drivers - GNOME fro
ii  restricted-man 0.33.1         manage non-free hardware drivers

---

### Post by divali on 2008-01-20
divali@ubuntu:~$ cat /var/lib/dpkg/status | grep -A 1 "Package: restricted-manager"
Package: restricted-manager-core
Status: install ok installed
--
Package: restricted-manager
Status: install reinstreq half-configured

---

### Post by erginemr on 2008-01-20
So, it seems the package "restricted-manager" is semi-broken.
Dpkg manual page, "man dpkg" says, to force-remove any package, even if it is broken, you need to issue the following command:
```
sudo dpkg --force-remove-reinstreq --remove restricted-manager
```

If it works, then reinstall it with:
```
sudo aptitude install restricted-manager
```

Good Luck...

P.S. Same story with gdebi...

---

### Post by divali on 2008-01-20
I tried to install automatix2 and got errors. Thus:

divali@ubuntu:~$ sudo aptitude install automatix2
[sudo] password for divali:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  python2.4 python2.4-minimal 
The following partially installed packages will be configured:
  gdebi restricted-manager 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/69.9kB of archives. After unpacking 12.8MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 107910 files and directories currently installed.)
Preparing to replace restricted-manager 0.33.1 (using .../restricted-manager_0.33.1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/subprocess.py", line 400, in <module>
    import select
ImportError: No module named select

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/subprocess.py", line 400, in <module>
    import select
ImportError: No module named select

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
dpkg: error processing /var/cache/apt/archives/restricted-manager_0.33.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 879, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/subprocess.py", line 400, in <module>
    import select
ImportError: No module named select

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 879, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace gdebi 0.3.2ubuntu1 (using .../gdebi_0.3.2ubuntu1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/subprocess.py", line 400, in <module>
    import select
ImportError: No module named select

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/subprocess.py", line 400, in <module>
    import select
ImportError: No module named select

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
dpkg: error processing /var/cache/apt/archives/gdebi_0.3.2ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 879, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/subprocess.py", line 400, in <module>
    import select
ImportError: No module named select

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 879, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 544, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/python/pyversions.py", line 29, in parse_versions
    import operator
ImportError: No module named operator
> dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/restricted-manager_0.33.1_all.deb
 /var/cache/apt/archives/gdebi_0.3.2ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing restricted-manager (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: error processing gdebi (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 restricted-manager
 gdebi
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
divali@ubuntu:~$ automatix2

(gksudo:5752): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
divali@ubuntu:~$ 


I'll try gdebi tomorrow. (I'm going to bed now. Tired). Thanks for your help.

---

### Post by erginemr on 2008-01-20
Once again...

> **erginemr said:**
> So, it seems the package "restricted-manager" is semi-broken.
Dpkg manual page, "man dpkg" says, to force-remove any package, even if it is broken, you need to issue the following command:
```
sudo dpkg --force-remove-reinstreq --remove restricted-manager
```

If it works, then reinstall it with:
```
sudo aptitude install restricted-manager
```

Good Luck...

P.S. Same story with gdebi...

---

### Post by divali on 2008-01-21
Sorry.  I don't understand.   I thought I had just issued those commands above. Did I do something wrong?
  
And when I give the commands for dpkg I get this:

divali@ubuntu:~$ sudo dpkg --force-remove-reinstreq --remove dpkg
[sudo] password for divali:
dpkg: error processing dpkg (--remove):
 This is an essential package - it should not be removed.
Errors were encountered while processing:
 dpkg

---

### Post by erginemr on 2008-01-21
No problem, maybe I misunderstood your latest post. The correct commands are:
```
sudo dpkg --force-remove-reinstreq --remove restricted-manager
sudo dpkg --force-remove-reinstreq --remove gdebi
```
and if it works:
```
sudo aptitude install restricted-manager
sudo aptitude install gdebi
```

If not, on to Plan-B:

What I am trying to do is to force a reinstallation of the two problematic packages "restricted-manager" and "gdebi".

I will now try to cheat the dpkg database to believe that everything is OK. The database is a big file: 
```
/var/lib/dpkg/status
```

First let us back it up so that we can restore it in case of a serious problem:
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak
```

Then let us open it with Gnome Editor with root permissions:
```
sudo gedit /var/lib/dpkg/status
```

Use the search menu to find the lines:
```
Status: install reinstreq half-configured
```

You should normally find two such lines, one for  "restricted-manager" and one for "gdebi". Replace them with:
```
Status: install ok installed
```

Save and close. Then, run the following command from the console:
```
sudo aptitude update
```
to put the changes into effect. 

Now, if everything goes well, it is time to reinstall those two essential packages:
```
sudo aptitude reinstall restricted-manager
sudo aptitude reinstall gdebi
```

Good Luck...

---

### Post by divali on 2008-01-21
Plan A  would not work. As previous.
And then I was not able to go further than this in Plan B.

```
divali@ubuntu:/var/lib/dpkg$ sudo /var/lib/dpkg/status
sudo: /var/lib/dpkg/status: command not found
divali@ubuntu:/var/lib/dpkg$ cd status
bash: cd: status: Not a directory
```

---

### Post by erginemr on 2008-01-21
Regarding Plan A:
-------------------------
You seem to have issued:
```
sudo dpkg --force-remove-reinstreq --remove dpkg
```
whereas you should have issued:
```
sudo dpkg --force-remove-reinstreq --remove restricted-manager
```

Regarding Plan B:
-------------------------
You seem to have issued:
```
sudo /var/lib/dpkg/status
```
```
cd status
```

whereas you should have issued:
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak
```

to make a backup of the file "status" and:
```
sudo gedit /var/lib/dpkg/status
```
to edit the file.

Please read my post (esp. the codes) carefully and apply the commands to the letter.

---

### Post by divali on 2008-01-21
Using cut/past: 

```
sudo gedit /var/lib/dpkg/status
```

```
Status: install reinstreq half-configured    
```    not found. Same for gdebi.

Hmmm.

---

### Post by erginemr on 2008-01-21
> **divali said:**
> divali@ubuntu:~$ cat /var/lib/dpkg/status | grep -A 1 "Package: restricted-manager"
Package: restricted-manager-core
Status: install ok installed
--
Package: restricted-manager
Status: install reinstreq half-configured

Hmm, strange... Because the above output clearly indicates that there is at least one line with "reinstreq" in that file. Could you please search for this keyword once again?

Alternatively, you can search for:
"Package: restricted-manager" and "Package: gdebi"

The lines you need to change are just the ones beneath those.

---

### Post by divali on 2008-01-22
Changed the lines in 'status' and this was the result. I noticed I'm now getting an error code 2.
I'm pretty sure I changed the correct lines in the text.

divali@ubuntu:~$ sudo aptitude reinstall restricted-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  python2.4 python2.4-minimal 
The following packages have been automatically kept back:
  ghostscript ghostscript-x libbind9-30 libdns32 libgs8 libisc32 libisccc30 
  libisccfg30 liblwres30 
The following packages have been kept back:
  bind9-host dnsutils gs-common gs-esp gs-esp-x 
The following packages will be REINSTALLED:
  restricted-manager 
0 packages upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 14 not upgraded.
Need to get 0B/39.9kB of archives. After unpacking 12.8MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: parse error, in file `/var/lib/dpkg/status' near line 13195 package `restricted-manager':
 Configured-Version for package with inappropriate Status
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 13195 package `restricted-manager':
 Configured-Version for package with inappropriate Status
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
divali@ubuntu:~$ sudo aptitude reinstall gdebi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  python2.4 python2.4-minimal 
The following packages have been automatically kept back:
  ghostscript ghostscript-x libbind9-30 libdns32 libgs8 libisc32 libisccc30 
  libisccfg30 liblwres30 
The following packages have been kept back:
  bind9-host dnsutils gs-common gs-esp gs-esp-x 
The following packages will be REINSTALLED:
  gdebi 
0 packages upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 14 not upgraded.
Need to get 0B/30.0kB of archives. After unpacking 12.8MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: parse error, in file `/var/lib/dpkg/status' near line 13195 package `restricted-manager':
 Configured-Version for package with inappropriate Status
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 13195 package `restricted-manager':
 Configured-Version for package with inappropriate Status
Reading package lists... Done             
Building dependency tree        
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
divali@ubuntu:~$

---

### Post by erginemr on 2008-01-22
I am sorry, apparently Plan B didn't work. You are pretty sure that you have changed the two lines into:
```
Status: install ok installed
```
I believe. If so, then you can at least revert back to your previous status by restoring your backup file with:
```
sudo cp /var/lib/dpkg/status.bak /var/lib/dpkg/status
```
I thought we could cheat dpkg database this way, but I was wrong...

---

### Post by erginemr on 2008-01-22
If you can still bear with my hit-and-miss techniques... But you should first restore your backup as I have explained in my previous post. 

There is an option for dpkg, "--force-all", which forces a reinstallation of a broken package. But to use this command, you need to first download the problematic packages to a folder of your choice. You can do this with 
```
aptitude download restricted-manager
aptitude download gdebi
```

These two commands will download the two debian (*.deb) packages to your home folder. Then, "cd" to your home folder with
```
cd ~
```
To see where you are, use:
```
pwd
```
Make sure that the Debian packages are in the same folder with:
```
ls
```
and issue the following force-install commands:
```
sudo dpkg --force-all --install <the package name for restricted manager>
sudo dpkg --force-all --install <the package name for gdebi>
```

When writing the part <package names> without the < and > signs of course, write the first letter of the package name and use the Tab on your keyboard to auto-complete the full name of the Debian package.

---

### Post by divali on 2008-01-23
Ok thanks. But I'm still getting the errors. Here's the last few lines for the command: 

sudo dpkg --force-all --install gdebi_0.3.2ubuntu1_all.deb  

ImportError: No module named operator
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gdebi_0.3.2ubuntu1_all.deb
divali@ubuntu:~$ 

Same for:  sudo dpkg --force-all --install restricted-manager_0.33.1_all.deb

Any thoughts...

---

### Post by erginemr on 2008-01-24
The following Debian forum thread deals with a similar issue to yours:
[http://forums.debian.net/viewtopic.php?t=8427&sid=a5541a5e5da09db6bb2f14431751364b](http://forums.debian.net/viewtopic.php?t=8427&sid=a5541a5e5da09db6bb2f14431751364b)

In this respect, you can give a try to the following paths:

----------
PLAN-C:
----------
1. Try these two simple commands to reconfigure dpkg:
```
sudo dpkg-reconfigure gdebi
sudo dpkg-reconfigure restricted-manager
```

----------
PLAN-D:
----------
Following the footsteps of the a/m forum thread:

1. Try to purge the two packages from your system with
```
sudo dpkg --purge gdebi
sudo dpkg --purge restricted-manager
```

Carry on with the following steps even if the purge commnad doesn't work.

2. Delete all lines belonging to "restricted-manager" and "gdebi" from the file:
```
/var/lib/dpkg/status
```
with the command:
```
gksu gedit /var/lib/dpkg/status
```
and save and close it afterwards.

For instance the corresponding lines in my "status" file are as follows:
```
..........
Package: gdebi
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 220
Maintainer: Michael Vogt <mvo@ubuntu.com>
Architecture: all
Version: 0.3.2ubuntu1
Depends: python, python-central (>= 0.5.8), gdebi-core (= 0.3.2ubuntu1), python-gtk2 (>= 2.6.3-2),  python-glade2 (>= 2.6.3-2), python-vte (>= 1:0.11.15-4), gksu (>= 2.0.0-1ubuntu3), gnome-icon-theme (>=  2.14.0-1)
Recommends: libgnome2-perl
Description: Simple tool to install deb files
 gdebi lets you install local deb packages resolving and installing
 its dependencies. apt does the same, but only for remote (http, ftp)
 located packages.
 .
 This package contains the graphical user interface.
Original-Maintainer: Gustavo Franco <stratus@debian.org>
Python-Version: current
..........
```
and
```
..........
Package: restricted-manager
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 316
Maintainer: Martin Pitt <martin.pitt@ubuntu.com>
Architecture: all
Version: 0.33.1
Depends: python2.5, python-central (>= 0.5.8), python (>= 2.5), python (<< 2.6),  restricted-manager-core (= 0.33.1), synaptic
Pre-Depends: python-notify (>= 0.1.1-0ubuntu2), python-glade2, python-xdg
Conffiles:
 /etc/xdg/autostart/restricted-manager.desktop f09c490f1ac489c9036738038badb057
Description: manage non-free hardware drivers - GNOME frontend
 Restricted Manager provides a user interface for configuring
 non-free hardware drivers, such as the Nvidia and ATI fglrx X.org
 and various Wireless LAN kernel modules.
 .
 This package contains the GNOME frontend.
Python-Version: 2.5
..........
```

You should make the package manager believe that these packages have not been installed, is the reason  why you should delete those chunks of lines.

3. Issue the following command:
```
sudo dpkg --configure -a
```
To put the changes into effect.

4. Eventually, you can reinstall these two packages with a standard:
```
sudo aptitude install gdebi
sudo aptitude install restricted-manager
```

----------
PLAN-E:
----------

Unfortunately there is no Plan-E. If neither of the above tricks works, then unfortunately, I am out of  my resources. I hope someone else will notice your thread and will come up with a plausible remedy.

On a final note, I know that this is too much hard work for an ordinary computer user, but sometimes  you need to get your hands dirty. And this is pretty much the way how noobs become geeks.

---

### Post by erginemr on 2008-01-24
If your problem still persists, I believe it is time give up following this thread and start a new one with your initial message, and post a link to its location here. I know that forum moderators will not tolerate starting identical threads simultaneously, but I believe they will understand your situation.

Many forum followers (including me) start by searching for new or unanswered posts, because a post that has a long history often (but not always) means it has been addressed and a solution is underway. So, you will have more chances to be noticed by other Ubuntu users, who are more knowledgeable than me, if you just drop this thread and start a new one.

Good Luck...

---

### Post by divali on 2008-01-24
**erginemr.**
Thanks for all your help and all the time and patience you spent on this issue. Yes, I still am unable to get these packages to work. I even tried using brute force, by way of deleting the offending items
using Midnight commander, as a last resort.
 Your right I should re-start this thread, but I'll do a bit more research first.
Thanks again. I really appreciate the help.  Divali.

---

