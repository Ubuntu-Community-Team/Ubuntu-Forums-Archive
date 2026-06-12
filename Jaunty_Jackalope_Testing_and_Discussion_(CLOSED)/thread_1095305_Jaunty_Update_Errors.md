---
title: "Jaunty Update Errors"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dazzler on 2009-03-13
Hi ive just updated from 8.10 to Jaunty 9.04 alpha 6 however i've got a few packages which arent playing nice and i cant seem to upgrade with apt-get install -f

Can someone point me in the right direction, what do i need to give you guys more detailed logs.

Main culprits are python, and ubuntu-desktop

---

### Post by dazzler on 2009-03-13
Further info:-

Unpacking checkbox (from .../archives/checkbox_0.5_all.deb) ...
dpkg: serious warning: files list file for package `checkbox' missing, assuming package has no files currently installed.
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2151, in <module>
    main()
  File "/usr/bin/pycentral", line 2145, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 855, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing /var/cache/apt/archives/checkbox_0.5_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Unpacking checkbox-gtk (from .../checkbox-gtk_0.5_all.deb) ...
dpkg: serious warning: files list file for package `checkbox-gtk' missing, assuming package has no files currently installed.
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2151, in <module>
    main()
  File "/usr/bin/pycentral", line 2145, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 855, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing /var/cache/apt/archives/checkbox-gtk_0.5_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/checkbox_0.5_all.deb
 /var/cache/apt/archives/checkbox-gtk_0.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Rocket2DMn on 2009-03-13
Moved to Jaunty Jackalope Testing and Discussion

---

### Post by Therion on 2009-03-13
Whoopsie.  Double-post...  My bad.

---

### Post by Therion on 2009-03-13
> **dazzler said:**
> [COLOR="White"]...[/COLOR]
I'm sorry, I can't hear you over the awesomeness of your Avatar...

<cough>



What about doing```
sudo apt-get update && sudo apt-get dist-upgrade
```or for that matter just ```
sudo sudo apt-get dist-upgrade
```Joy?

---

### Post by dazzler on 2009-03-13
Sorry didnt work, resigned to doing a fresh install now me thinks

The following NEW packages will be installed
  checkbox checkbox-gtk
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/107kB of archives.
After this operation, 1442kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 180290 files and directories currently installed.)
Unpacking checkbox (from .../archives/checkbox_0.5_all.deb) ...
dpkg: serious warning: files list file for package `checkbox' missing, assuming package has no files currently installed.
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2151, in <module>
    main()
  File "/usr/bin/pycentral", line 2145, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 855, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing /var/cache/apt/archives/checkbox_0.5_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Unpacking checkbox-gtk (from .../checkbox-gtk_0.5_all.deb) ...
dpkg: serious warning: files list file for package `checkbox-gtk' missing, assuming package has no files currently installed.
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2151, in <module>
    main()
  File "/usr/bin/pycentral", line 2145, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 855, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing /var/cache/apt/archives/checkbox-gtk_0.5_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/checkbox_0.5_all.deb
 /var/cache/apt/archives/checkbox-gtk_0.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dazzler@dazzler-laptop:~$

---

### Post by rajeev1204 on 2009-03-13
> **dazzler said:**
> Further info:-

Unpacking checkbox (from .../archives/checkbox_0.5_all.deb) ...
dpkg: serious warning: files list file for package `checkbox' missing, assuming package has no files currently installed.
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2151, in <module>
    main()
  File "/usr/bin/pycentral", line 2145, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 855, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing /var/cache/apt/archives/checkbox_0.5_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Unpacking checkbox-gtk (from .../checkbox-gtk_0.5_all.deb) ...
dpkg: serious warning: files list file for package `checkbox-gtk' missing, assuming package has no files currently installed.
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2151, in <module>
    main()
  File "/usr/bin/pycentral", line 2145, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 855, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing /var/cache/apt/archives/checkbox-gtk_0.5_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/checkbox_0.5_all.deb
 /var/cache/apt/archives/checkbox-gtk_0.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I just upgraded a few minutes ago to alpha6.

Got the exact same errors.


Ok did an apt get update and problem solved.

---

### Post by dazzler on 2009-03-13
Is it wrong of me to be a little bit happy about that ;)

It might not be a crazy app or whatever on my rig then

---

### Post by dazzler on 2009-03-13
> **rajeev1204 said:**
> I just upgraded a few minutes ago to alpha6.

Got the exact same errors.


Ok did an apt get update and problem solved.

Eh mine wont fix after apt-get update can you explain further what you did?

Did you do it in recovery or what?

---

### Post by rajeev1204 on 2009-03-13
> **dazzler said:**
> Eh mine wont fix after apt-get update can you explain further what you did?

Did you do it in recovery or what?


First i did  a 'fix broken pacakages' using synaptic.

Then sudo apt-get update.

---

### Post by dazzler on 2009-03-13
Thanks rajeev1204, still not working for me but i've found several others reporting it as a bug, ill hold on till a fix is available.

---

### Post by dazzler on 2009-03-13
[FIXED]

Just changed from uk server to usa one in synaptic and its fixed the apt-gets.

So anyone else try that :)

Thanks all

---

