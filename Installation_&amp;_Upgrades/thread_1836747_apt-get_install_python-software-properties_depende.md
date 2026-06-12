---
title: "apt-get install python-software-properties dependency problems"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by tylerthemiler on 2011-08-31
Hey guys,

So, I was trying to add a repository using add-apt-repository and I got this error:

```
sudo add-apt-repository ppa:gijzelaar/opencv2
[sudo] password for foo: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 8, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties
ImportError: No module named softwareproperties.SoftwareProperties
```

Like a n00b, I thought it would be a good idea to simply uninstall and reinstall python-software-properties using apt.

Upon reinstall, i got this:

```
foo@ubuntu:/$ sudo apt-get install python-software-properties
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-software-properties is already the newest version.
The following packages were automatically installed and are no longer required:
  libswscale0 linux-headers-2.6.38-8-generic libtorque2 libavutil50
  libvtk5.4-qt3 fsl-mni-structural-atlas fsl-bangor-cerebellar-atlas
  fsl-atlases linux-headers-2.6.38-8 libnewmat10ldbl
  fsl-talairach-daemon-atlas fsl-harvard-oxford-atlases libgl2ps0 libcvaux2.1
  libgdchart-gd2-noxpm qt3-assistant liblapack3gf fsl-doc-4.1
  fsl-oxford-thalamic-connectivity-atlas libmysqlclient16 libavcodec52
  fslview-doc tcsh libhighgui2.1 libvtk5.4 libopenmpi1.3 fsl-mni152-templates
  fslview libqwt4c2 libcv2.1 libgsm1 libblas3gf libschroedinger-1.0-0
  libavformat52 libnuma1 libdc1394-22 qt3-doc libibverbs1 tk8.4 libpq5
  libgfortran3 fsl-jhu-dti-whitematter-atlas libva1 libqt3-mt
  fsl-juelich-histological-atlas libaudio2 mysql-common libnifti2 libmng1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
8 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up python-software-properties (0.80.9) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2327, in <module>
    main()
  File "/usr/bin/pycentral", line 2321, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing python-software-properties (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-aptdaemon:
 python-aptdaemon depends on python-software-properties; however:
  Package python-software-properties is not configured yet.
dpkg: error processing python-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python-aptdaemon (= 0.41+bzr646-0ubuntu2.1); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtkwidgets:
 python-aptdaemon.gtkwidgets depends on python-aptdaemon (= 0.41+bzr646-0ubuntu2.1); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing python-aptdaemon.gtkwidgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gNo apport report written because the error message indicates its a followup error from a previous failure.
                                             No apport report written because the error message indicates its a followup error from a previous failure.
                                                             tk3widgets depends on python-aptdaemon (= 0.41+bzr646-0ubuntu2.1); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon-gtk:
 python-aptdaemon-gtk depends on python-aptdaemon.gtkwidgets (= 0.41+bzr646-0ubuntu2.1); however:
  Package python-aptdaemon.gtkwidgets is not configured yet.
 python-aptdaemon-gtk depends on python-aptdaemon.gtk3widgets (= 0.41+bzr646-0ubuntu2.1); however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing python-aptdaemon-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on python-aptdaemon (>= 0.40); however:
  Package python-aptdaemon is not configured yet.
 software-center depends on python-aptdaemon-gtk; however:
  Package python-aptdaemon-gtk is not configured yet.
 software-center depends on aptdaemon (>= 0.40); however:
  Package aptdaemon is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python-software-properties; however:
  Package python-software-properties is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-software-properties
 python-aptdaemon
 aptdaemon
 python-aptdaemon.gtkwidgets
 python-aptdaemon.gtk3widgets
 python-aptdaemon-gtk
 software-center
 software-properties-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)                                         No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                 No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             tk3widgets depends on python-aptdaemon (= 0.41+bzr646-0ubuntu2.1); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon-gtk:
 python-aptdaemon-gtk depends on python-aptdaemon.gtkwidgets (= 0.41+bzr646-0ubuntu2.1); however:
  Package python-aptdaemon.gtkwidgets is not configured yet.
 python-aptdaemon-gtk depends on python-aptdaemon.gtk3widgets (= 0.41+bzr646-0ubuntu2.1); however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing python-aptdaemon-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on python-aptdaemon (>= 0.40); however:
  Package python-aptdaemon is not configured yet.
 software-center depends on python-aptdaemon-gtk; however:
  Package python-aptdaemon-gtk is not configured yet.
 software-center depends on aptdaemon (>= 0.40); however:
  Package aptdaemon is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python-software-properties; however:
  Package python-software-properties is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-software-properties
 python-aptdaemon
 aptdaemon
 python-aptdaemon.gtkwidgets
 python-aptdaemon.gtk3widgets
 python-aptdaemon-gtk
 software-center
 software-properties-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can I fix this?????? I don't want to reinstall python, as I have a lot of packages installed at this point...

Thanks a million,

tylerthemiler

---

