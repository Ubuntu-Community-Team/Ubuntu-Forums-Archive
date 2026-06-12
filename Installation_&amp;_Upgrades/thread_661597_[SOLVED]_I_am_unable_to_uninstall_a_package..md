---
title: "[SOLVED] I am unable to uninstall a package."
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by 16777216 on 2008-01-08
When trying to remove tango-generator I get this.

```
(Reading database ... 319162 files and directories currently installed.)
Removing tango-generator ...
The generated cache was invalid.
dpkg: error processing tango-generator (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 tango-generator
E: Sub-process /usr/bin/dpkg returned an error code (1)
```And now I am no longer able to install/uninstall any deb files.

---

### Post by Partyboi2 on 2008-01-08
What happens if you try purging
```
sudo apt-get remove --purge tango-generator
```

---

### Post by 16777216 on 2008-01-08
Ineffective

full output:

```
sudo apt-get remove --purge tango-generator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevas1-saver-tiff libevas1-loader-eet libecore1-x libecore1-con-dev
  libpth20 libevas1-loader-gif libecore1-file libecore1-bin librdf0
  kdebase-runtime-data-common libecore1-dev libecore1-con libecore1-evas
  libecore1-x-dev libevas1-loader-png libecore1-ipc libecore1-evas-dev
  libecore1-job libecore1 libevas1-loader-jpeg libevas1-loader-svg
  libecore1-config libevas1-loader-xpm libevas1-loaders-all librasqal0
  libecore1-txt libsoprano4 kdelibs5-data libevas1-saver-jpeg
  libevas1-engine-software-x11 libevas1-engines-all libevas1-savers-all
  libevas1-engine-software-generic libevas1-engine-buffer libecore1-job-dev
  libecore1-fb libstreamanalyzer0 libevas1-saver-eet libevas1-loader-tiff
  libevas1-engine-fb libevas1-engine-xrender libgpgme11 libecore1-file-dev
  libstreams0 libevas1-saver-png libclucene0 libevas1-dev kdebase-runtime-data
  kdepimlibs-data libecore1-fb-dev libevas1 libecore1-txt-dev
  libecore1-ipc-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  tango-generator
0 upgraded, 0 newly installed, 1 to remove and 172 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 717kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 319162 files and directories currently installed.)
Removing tango-generator ...
The generated cache was invalid.
dpkg: error processing tango-generator (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 tango-generator
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Every method I have tried gives me the same thing.
I am going to try to remove the files by hand.:(

---

### Post by 16777216 on 2008-01-08
That did not work either. :(

---

### Post by zvacet on 2008-01-08
```
sudo dpkg --remove --force-remove-reinstreq  tango-generator
```

---

### Post by 16777216 on 2008-01-09
```
sudo dpkg --remove --force-remove-reinstreq  tango-generator

(Reading database ... 319162 files and directories currently installed.)
Removing tango-generator ...
The generated cache was invalid.
dpkg: error processing tango-generator (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 tango-generator
```

I am beginning to think this is hopeless .
I wish I knew what went wrong in the first place.
Is there a way to force a reinstall then removal?

---

### Post by 16777216 on 2008-01-09
I downloaded the deb again and then ran
```
sudo dpkg --install /media/storage/tango-generator_3.2.1-1_all.deb
```

The package works fine now thank you for all of your help.

---

