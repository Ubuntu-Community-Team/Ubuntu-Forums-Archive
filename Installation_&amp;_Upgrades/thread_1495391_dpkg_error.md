---
title: "dpkg error"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by rasanpreetkaur on 2010-05-28
hi ppl....i am getting this error whenevr i try to install anything or even upgrade my system....:confused:...help..:(

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 2, in <module>
    import NvidiaDetector
ImportError: No module named NvidiaDetector
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-21-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libgcj-common (1:4.4.1-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1478, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 279, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error processing libgcj-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libgcj10:
 libgcj10 depends on libgcj-common (>= 1:4.1.1-21); however:
  Package libgcj-common is not configured yet.
dpkg: error processing libgcj10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcj-4.4-jre-headless:
 gcj-4.4-jre-headless depends on libgcj10 (= 4.4.1-5ubuntu2); however:
  Package libgcj10 is not configured yet.
dpkg: error processing gcj-4.4-jre-headless (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcj-4.4-jre-lib:
 gcj-4.4-jre-lib depends on libgcj10 (>= 4.4.0-8); however:
  Package libgcj10 is not configured yet.
dpkg: error processing gcj-4.4-jre-lib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-21-generic; however:
  Package linux-image-2.6.31-21-generic is notNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                        No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                                                                                                            No apport report written because MaxReports is reached already

Errors were encountered while processing:
 linux-image-2.6.31-21-generic
 libgcj-common
 libgcj10
 gcj-4.4-jre-headless
 gcj-4.4-jre-lib
 linux-image-generic
 linux-generic
 linux-headers-2.6.31-21-generic
 linux-headers-generic
 mgltools-bhtree
 mgltools-geomutils
 mgltools-networkeditor
 mgltools-pybabel
 mgltools-pyglf
 mgltools-scenario
 mgltools-support
 mgltools-utpackages
 python-imaging-tk
 python-numpy
 python-lasso
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by SlidingHorn on 2010-05-28
Sounds like your HDD (or @ least your partition) is full...clear some space and take another shot

```
sudo apt-get clean
```

and delete any unnecessary files

---

### Post by rasanpreetkaur on 2010-05-28
> **SlidingHorn said:**
> Sounds like your HDD (or @ least your partition) is full...clear some space and take another shot

```
sudo apt-get clean
```and delete any unnecessary files


i tried tht but it didnt work...i have edited the post ..i have included the complete error
thanks for help

---

### Post by dino99 on 2010-05-28
check your synaptic repo: be sure you only use genuine ubuntu repo (no mixed releases, no third party, no ppa)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a

---

### Post by rasanpreetkaur on 2010-05-29
> **dino99 said:**
> check your synaptic repo: be sure you only use genuine ubuntu repo (no mixed releases, no third party, no ppa)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a



it still gives the same error..i tried to check to repo...it tells me to reload and wen i do tht it does not reload...so i cannot even access repositories.....
i guess it's some python problem but am unable to figure out wat


thx for help

---

### Post by rasanpreetkaur on 2010-05-29
ok guys its done:guitar:
i checked other posts and solved it..
this command solved it:
sudo rm /usr/bin/python && sudo ln -s python2.6 /usr/bin/python
thx once again:P:P:P:P

---

