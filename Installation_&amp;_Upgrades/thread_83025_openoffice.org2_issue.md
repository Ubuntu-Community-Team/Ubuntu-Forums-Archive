---
title: "openoffice.org2 issue"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by CiberAmigo on 2005-10-27
I have upgraded to Breezy, but apt keep saying:

>  /var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have search the intire forum too find a solution, but either people saying: "I did'nt have any problem upgrading" or don't have the same issue.

Does eny one have a solution on this issue? still need a lot of package to bee upgraded.

Cencerly
CiberAmigo

---

### Post by denkedran on 2005-10-27
what does an
```
ls /var/cache/apt/archives/openoffice.org2*
```

says

try a
```
sudo apt-get update
sudo apt-get install openoffice.org2-help-en-us
```

---

### Post by CiberAmigo on 2005-10-27
hi denkedran

ls give this:
```

jan@Linux:~$ ls /var/cache/apt/archives/openoffice.org2*
/var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb

```

and:
```

sudo apt-get install openoffice.org2-help-en
Indlæser pakkelisterne... Færdig  (Reading packagelist... Done)
Opbygger afhængighedstræ... Færdig (building dependencies... Done)
E: Kunne ikke finde pakken openoffice.org2-help-en (could'nt find package openoffice.org2-help-en)

```

I have also tried:
```

sudo apt-get clean

```

And:
```

sudo apt-get -f install 

```

Even more, each on its own:
```

apt-get --fix-missing upgrade
sudo apt-get remove openoffice.org
sudo dpkg --install *.deb 

```

Cencerly
CiberAmigo

---

### Post by denkedran on 2005-10-29
[QUOTE=CiberAmigo]hi denkedran

ls give this:
```

jan@Linux:~$ ls /var/cache/apt/archives/openoffice.org2*
/var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb

```
[/QUOTE]

what does a sudp dpkg -i /var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb says ? If it does not install there has to be any kind of output, with error-messages.

You can also try to remove the corrupt file

[QUOTE=CiberAmigo]
and:
```

sudo apt-get install openoffice.org2-help-en
Indlæser pakkelisterne... Færdig  (Reading packagelist... Done)
Opbygger afhængighedstræ... Færdig (building dependencies... Done)
E: Kunne ikke finde pakken openoffice.org2-help-en (could'nt find package openoffice.org2-help-en)

```
[/QUOTE]
the packagname is "openoffice.org2-help-en-us" not "openoffice.org2-help-en"

You could try
```
sudo apt-get install --reinstall openoffice.org2-help-en-us
```

You could also try to remove the package:
```
rm /var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb
```

and then reinstall with
```
sudo apt-get install openoffice.org2-help-en-us
```

Be sure your repositories are up to date
```
sudo apt-get update
```

---

### Post by rodrigueskevin on 2007-07-28
i have a similar problem

here is the error

Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python2.4-minimal python2.4 python-wxversion libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openoffice.org-common openoffice.org-core
Recommended packages:
  openoffice.org-style-industrial openoffice.org-style-tango
  openoffice.org-style-crystal openoffice.org-style-andromeda
  openoffice.org-style-hicontrast nfs-common
The following packages will be upgraded:
  openoffice.org-common openoffice.org-core
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
12 not fully installed or removed.
Need to get 0B/47.5MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? (Reading database ... 95012 files and directories currently installed.)
Preparing to replace openoffice.org-common 2.2.0-1ubuntu3 (using .../openoffice.org-common_2.2.0-1ubuntu4_all.deb) ...
Unpacking replacement openoffice.org-common ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Preparing to replace openoffice.org-core 2.2.0-1ubuntu3 (using .../openoffice.org-core_2.2.0-1ubuntu4_i386.deb) ...
Unpacking replacement openoffice.org-core ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_2.2.0-1ubuntu4_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb
 /var/cache/apt/archives/openoffice.org-core_2.2.0-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

