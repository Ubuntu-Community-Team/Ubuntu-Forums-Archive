---
title: "quick apt-get question"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by one_stinky_bum on 2006-08-19
I'm upgrading my system but apt-get fails at a certain package: python2.4-minimal. Is there a way to tell apt-get to update the rest and leave this one (and the programs that depend on this) alone? Sort of like telling apt-get to re-order it's installation process.

Thanks.

---

### Post by melissawm on 2006-08-19
You can try this:

> 
[B]--ignore-missing

[/B]Ignore missing packages; If packages cannot be retrieved or fail the integrity check after retrieval (corrupted package files), hold back those packages and handle the result. Use of this option together with **-f** may produce an error in some situations. If a package is selected for installation (particularly if it is mentioned on the command line) and it could not be downloaded then it will be silently held back.
 
I found this here: [http://www.die.net/doc/linux/man/man8/apt-get.8.html](http://www.die.net/doc/linux/man/man8/apt-get.8.html)

---

### Post by one_stinky_bum on 2006-08-19
Tried that already... this is what I got:
```
user@pc:~$ sudo apt-get --ignore-missing -f dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  python2.4: Depends: python2.4-minimal (= 2.4.3-7ubuntu2) but 2.4.3-8 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

I wonder why it can't live with the higher number package installed (2.4.3 - 8 ).

Thanks for the tip though.

---

### Post by abeowitz on 2006-08-24
NEVERMIND... [https://launchpad.net/distros/ubuntu/+bug/57121](https://launchpad.net/distros/ubuntu/+bug/57121)


Similar problem here...  :(

Running Edgy Eft, upgraded from Dapper

apt-get --ignore-missing upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  apport apport-gtk libcairomm-1.0-dev libgtkmm-2.4-1c2a libgtkmm-2.4-dev
The following packages will be upgraded:
  acpi-support app-install-data gdm gnome-app-install libavahi-client-dev libavahi-client3 libavahi-common-data
  libavahi-common-dev libavahi-common3 libavahi-glib-dev libavahi-glib1 libvte-common libvte9 libx11-6 libx11-data
  libx11-dev python-problem-report python-vte python2.4-examples
19 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
3 not fully installed or removed.
Need to get 0B/9485kB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]?      
Preconfiguring packages ...
Setting up python2.4-minimal (2.4.3-7ubuntu4) ...
Linking and byte-compiling packages for runtime python2.4...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1325, in ?
    main()
  File "/usr/bin/pycentral", line 1319, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 954, in run
    requested = list(pyversions.requested_versions(vstring, version_only=True))
  File "/usr/share/python/pyversions.py", line 113, in requested_versions
    raise ValueError, 'empty set of versions'
ValueError: empty set of versions
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python2.4-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by markthecarp on 2006-08-24
> 
```
user@pc:~$ sudo apt-get --ignore-missing -f dist-upgrade Reading package lists... Done Building dependency tree... Done Correcting dependencies... failed. The following packages have unmet dependencies: python2.4: Depends: python2.4-minimal (= 2.4.3-7ubuntu2) but 2.4.3-8 is installed E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages. E: Unable to correct dependencies

```


You might try "sudo apt-get remove python2.4-minimal" then try the upgrade again.

-mark

---

### Post by one_stinky_bum on 2006-08-24
> **markthecarp said:**
> You might try "sudo apt-get remove python2.4-minimal" then try the upgrade again.

-mark
Switched back to Dapper. Thanks for the help.

---

### Post by ChantCd_com on 2006-08-24
But I AM using Dapper, and I get the same kind of error ALL THE TIME!

It says (= 4.2.4.4) instead of sometimes saying (>=4.2.4.0) -- an equal sign instead of a >=, and sometimes I have a MORE RECENT version of the library installed.

Why is that?

Should I stick to source-code installs as much as possible?

Thanks,

Matthew

---

