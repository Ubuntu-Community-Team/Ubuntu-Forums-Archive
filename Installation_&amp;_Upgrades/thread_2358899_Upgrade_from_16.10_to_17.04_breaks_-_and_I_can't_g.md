---
title: "Upgrade from 16.10 to 17.04 breaks - and I can't get out of the rabbit hole"
date: 2017-04-18
forum: Installation &amp; Upgrades
---

### Post by marcelton on 2017-04-18
Today I upgraded my system from 16.10 to 17.04. Originally a 16.04 system, upgraded without any issues to 16.10. However the installer notes several errors and eventually fails, even though the upgrade somewhat completed. I was left with the following image:

[http://imgur.com/a/jARcm](http://imgur.com/a/jARcm)
[http://imgur.com/a/wMpxG](http://imgur.com/a/wMpxG)

So i start my fix attempts:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-tools cgmanager dns-root-data dnsmasq-base espeak-data
  fonts-stix gdebi-core hwdata imagemagick-common iproute libavcodec-ffmpeg56
  libavfilter-ffmpeg5 libavformat-ffmpeg56 libavresample-ffmpeg2
  libavutil-ffmpeg54 libbluray1 libboost-date-time1.61.0
  libboost-filesystem1.61.0 libboost-iostreams1.61.0 libboost-log1.61.0
  libboost-program-options1.61.0 libboost-regex1.61.0 libboost-system1.61.0
  libboost-thread1.61.0 libcgmanager0 libchromaprint0 libcolamd2 libespeak1
  libglew1.13 libgnome2-0 libgnome2-bin liblircclient0 libllvm3.8 liblouis10
  libmimic0 libmircommon6 libopencv-contrib2.4v5 libopencv-legacy2.4v5
  libopencv-ml2.4v5 libopenjpeg5 liborcus-0.11-0 libpam-cgfs libperl5.22
  libpoppler61 libpostproc-ffmpeg53 libraw15 libschroedinger-1.0-0
  libsuitesparseconfig4 libswresample-ffmpeg1 libswscale-ffmpeg3
  libubuntu-app-launch3 libubuntuoneauth-2.0-0 libvpx3 libwebp5 libx265-79
  libx86-1 libxapian22v5 linux-headers-4.8.0-45 linux-headers-4.8.0-45-generic
  linux-image-4.8.0-45-generic linux-image-extra-4.8.0-45-generic lp-solve
  perl-modules-5.22 pm-utils pyotherside signon-plugin-password snap-confine
  ubuntuone-client-data ubuntuone-credentials-common upstart vbetool
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  click-apparmor ubuntu-app-launch url-dispatcher
The following packages will be upgraded:
  click-apparmor ubuntu-app-launch url-dispatcher
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0 B/71,9 kB of archives.
After this operation, 80,9 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 262927 files and directories currently installed.)
Preparing to unpack .../ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../click-apparmor_0.3.18_amd64.deb ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: error processing archive /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb
 /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb
 /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Pretty sure the below command does the same thing, but since Ubuntu recommended it just for sanity:


```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-tools cgmanager dns-root-data dnsmasq-base espeak-data
  fonts-stix gdebi-core hwdata imagemagick-common iproute libavcodec-ffmpeg56
  libavfilter-ffmpeg5 libavformat-ffmpeg56 libavresample-ffmpeg2
  libavutil-ffmpeg54 libbluray1 libboost-date-time1.61.0
  libboost-filesystem1.61.0 libboost-iostreams1.61.0 libboost-log1.61.0
  libboost-program-options1.61.0 libboost-regex1.61.0 libboost-system1.61.0
  libboost-thread1.61.0 libcgmanager0 libchromaprint0 libcolamd2 libespeak1
  libglew1.13 libgnome2-0 libgnome2-bin liblircclient0 libllvm3.8 liblouis10
  libmimic0 libmircommon6 libopencv-contrib2.4v5 libopencv-legacy2.4v5
  libopencv-ml2.4v5 libopenjpeg5 liborcus-0.11-0 libpam-cgfs libperl5.22
  libpoppler61 libpostproc-ffmpeg53 libraw15 libschroedinger-1.0-0
  libsuitesparseconfig4 libswresample-ffmpeg1 libswscale-ffmpeg3
  libubuntu-app-launch3 libubuntuoneauth-2.0-0 libvpx3 libwebp5 libx265-79
  libx86-1 libxapian22v5 linux-headers-4.8.0-45 linux-headers-4.8.0-45-generic
  linux-image-4.8.0-45-generic linux-image-extra-4.8.0-45-generic lp-solve
  perl-modules-5.22 pm-utils pyotherside signon-plugin-password snap-confine
  ubuntuone-client-data ubuntuone-credentials-common upstart vbetool
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  click-apparmor ubuntu-app-launch url-dispatcher
The following packages will be upgraded:
  click-apparmor ubuntu-app-launch url-dispatcher
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0 B/71,9 kB of archives.
After this operation, 80,9 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 262927 files and directories currently installed.)
Preparing to unpack .../ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../click-apparmor_0.3.18_amd64.deb ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: error processing archive /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb
 /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb
 /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Allright let's follow the instruction, or at least the bit I can do, I uninstall the click package


```
sudo -H pip2 uninstall click
Uninstalling click-6.7:
  /usr/local/lib/python2.7/dist-packages/click-6.7.dist-info/DESCRIPTION.rst
  /usr/local/lib/python2.7/dist-packages/click-6.7.dist-info/INSTALLER
  /usr/local/lib/python2.7/dist-packages/click-6.7.dist-info/METADATA
  /usr/local/lib/python2.7/dist-packages/click-6.7.dist-info/RECORD
  /usr/local/lib/python2.7/dist-packages/click-6.7.dist-info/WHEEL
  /usr/local/lib/python2.7/dist-packages/click-6.7.dist-info/metadata.json
  /usr/local/lib/python2.7/dist-packages/click-6.7.dist-info/top_level.txt
  /usr/local/lib/python2.7/dist-packages/click/__init__.py
  /usr/local/lib/python2.7/dist-packages/click/__init__.pyc
  /usr/local/lib/python2.7/dist-packages/click/_bashcomplete.py
  /usr/local/lib/python2.7/dist-packages/click/_bashcomplete.pyc
  /usr/local/lib/python2.7/dist-packages/click/_compat.py
  /usr/local/lib/python2.7/dist-packages/click/_compat.pyc
  /usr/local/lib/python2.7/dist-packages/click/_termui_impl.py
  /usr/local/lib/python2.7/dist-packages/click/_termui_impl.pyc
  /usr/local/lib/python2.7/dist-packages/click/_textwrap.py
  /usr/local/lib/python2.7/dist-packages/click/_textwrap.pyc
  /usr/local/lib/python2.7/dist-packages/click/_unicodefun.py
  /usr/local/lib/python2.7/dist-packages/click/_unicodefun.pyc
  /usr/local/lib/python2.7/dist-packages/click/_winconsole.py
  /usr/local/lib/python2.7/dist-packages/click/_winconsole.pyc
  /usr/local/lib/python2.7/dist-packages/click/core.py
  /usr/local/lib/python2.7/dist-packages/click/core.pyc
  /usr/local/lib/python2.7/dist-packages/click/decorators.py
  /usr/local/lib/python2.7/dist-packages/click/decorators.pyc
  /usr/local/lib/python2.7/dist-packages/click/exceptions.py
  /usr/local/lib/python2.7/dist-packages/click/exceptions.pyc
  /usr/local/lib/python2.7/dist-packages/click/formatting.py
  /usr/local/lib/python2.7/dist-packages/click/formatting.pyc
  /usr/local/lib/python2.7/dist-packages/click/globals.py
  /usr/local/lib/python2.7/dist-packages/click/globals.pyc
  /usr/local/lib/python2.7/dist-packages/click/parser.py
  /usr/local/lib/python2.7/dist-packages/click/parser.pyc
  /usr/local/lib/python2.7/dist-packages/click/termui.py
  /usr/local/lib/python2.7/dist-packages/click/termui.pyc
  /usr/local/lib/python2.7/dist-packages/click/testing.py
  /usr/local/lib/python2.7/dist-packages/click/testing.pyc
  /usr/local/lib/python2.7/dist-packages/click/types.py
  /usr/local/lib/python2.7/dist-packages/click/types.pyc
  /usr/local/lib/python2.7/dist-packages/click/utils.py
  /usr/local/lib/python2.7/dist-packages/click/utils.pyc
Proceed (y/n)? y
  Successfully uninstalled click-6.7

sudo -H pip3 uninstall click
BUG: Is it bad if orig_path is not sorted correctly? https://github.com/pypa/pip/issues/4216
Uninstalling click-6.7:
  /usr/local/lib/python3.5/dist-packages/click-6.7.dist-info/DESCRIPTION.rst
  /usr/local/lib/python3.5/dist-packages/click-6.7.dist-info/INSTALLER
  /usr/local/lib/python3.5/dist-packages/click-6.7.dist-info/METADATA
  /usr/local/lib/python3.5/dist-packages/click-6.7.dist-info/RECORD
  /usr/local/lib/python3.5/dist-packages/click-6.7.dist-info/WHEEL
  /usr/local/lib/python3.5/dist-packages/click-6.7.dist-info/metadata.json
  /usr/local/lib/python3.5/dist-packages/click-6.7.dist-info/top_level.txt
  /usr/local/lib/python3.5/dist-packages/click/__init__.py
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/__init__.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/_bashcomplete.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/_compat.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/_termui_impl.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/_textwrap.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/_unicodefun.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/_winconsole.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/core.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/decorators.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/exceptions.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/formatting.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/globals.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/parser.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/termui.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/testing.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/types.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/__pycache__/utils.cpython-35.pyc
  /usr/local/lib/python3.5/dist-packages/click/_bashcomplete.py
  /usr/local/lib/python3.5/dist-packages/click/_compat.py
  /usr/local/lib/python3.5/dist-packages/click/_termui_impl.py
  /usr/local/lib/python3.5/dist-packages/click/_textwrap.py
  /usr/local/lib/python3.5/dist-packages/click/_unicodefun.py
  /usr/local/lib/python3.5/dist-packages/click/_winconsole.py
  /usr/local/lib/python3.5/dist-packages/click/core.py
  /usr/local/lib/python3.5/dist-packages/click/decorators.py
  /usr/local/lib/python3.5/dist-packages/click/exceptions.py
  /usr/local/lib/python3.5/dist-packages/click/formatting.py
  /usr/local/lib/python3.5/dist-packages/click/globals.py
  /usr/local/lib/python3.5/dist-packages/click/parser.py
  /usr/local/lib/python3.5/dist-packages/click/termui.py
  /usr/local/lib/python3.5/dist-packages/click/testing.py
  /usr/local/lib/python3.5/dist-packages/click/types.py
  /usr/local/lib/python3.5/dist-packages/click/utils.py
Proceed (y/n)? y
  Successfully uninstalled click-6.7
```

Okay let's try again:

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-tools cgmanager dns-root-data dnsmasq-base espeak-data fonts-stix gdebi-core hwdata imagemagick-common iproute libavcodec-ffmpeg56 libavfilter-ffmpeg5 libavformat-ffmpeg56
  libavresample-ffmpeg2 libavutil-ffmpeg54 libbluray1 libboost-date-time1.61.0 libboost-filesystem1.61.0 libboost-iostreams1.61.0 libboost-log1.61.0 libboost-program-options1.61.0 libboost-regex1.61.0
  libboost-system1.61.0 libboost-thread1.61.0 libcgmanager0 libchromaprint0 libcolamd2 libespeak1 libglew1.13 libgnome2-0 libgnome2-bin liblircclient0 libllvm3.8 liblouis10 libmimic0 libmircommon6
  libopencv-contrib2.4v5 libopencv-legacy2.4v5 libopencv-ml2.4v5 libopenjpeg5 liborcus-0.11-0 libpam-cgfs libperl5.22 libpoppler61 libpostproc-ffmpeg53 libraw15 libschroedinger-1.0-0
  libsuitesparseconfig4 libswresample-ffmpeg1 libswscale-ffmpeg3 libubuntu-app-launch3 libubuntuoneauth-2.0-0 libvpx3 libwebp5 libx265-79 libx86-1 libxapian22v5 linux-headers-4.8.0-45
  linux-headers-4.8.0-45-generic linux-image-4.8.0-45-generic linux-image-extra-4.8.0-45-generic lp-solve perl-modules-5.22 pm-utils pyotherside signon-plugin-password snap-confine ubuntuone-client-data
  ubuntuone-credentials-common upstart vbetool
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  click-apparmor ubuntu-app-launch url-dispatcher
The following packages will be upgraded:
  click-apparmor ubuntu-app-launch url-dispatcher
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0 B/71,9 kB of archives.
After this operation, 80,9 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 262927 files and directories currently installed.)
Preparing to unpack .../ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../click-apparmor_0.3.18_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: error processing archive /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb
 /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb
 /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Click is missing, surprising, so I reason it should be gotten from Ubuntu repo's itself:

```
sudo apt install click
Reading package lists... Done
Building dependency tree
Reading state information... Done
click is already the newest version (0.4.45.1+16.10.20160916-0ubuntu1).
click set to manually installed.
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 click-apparmor : Depends: python3-apparmor-click (= 0.3.17) but 0.3.18 is to be installed
 libubuntu-app-launch4 : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is to be installed
 ubuntu-app-launch-tools : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is to be installed
 url-dispatcher-tools : Depends: url-dispatcher (= 0.1+17.04.20170328-0ubuntu2) but 0.1+16.10.20160816.1-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

Here "sudo apt autoremove" gives the same error as above (logical I suppose) - so whereto now?

```
sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-tools cgmanager dns-root-data dnsmasq-base espeak-data fonts-stix gdebi-core hwdata imagemagick-common iproute libavcodec-ffmpeg56 libavfilter-ffmpeg5 libavformat-ffmpeg56
  libavresample-ffmpeg2 libavutil-ffmpeg54 libbluray1 libboost-date-time1.61.0 libboost-filesystem1.61.0 libboost-iostreams1.61.0 libboost-log1.61.0 libboost-program-options1.61.0 libboost-regex1.61.0
  libboost-system1.61.0 libboost-thread1.61.0 libcgmanager0 libchromaprint0 libcolamd2 libespeak1 libglew1.13 libgnome2-0 libgnome2-bin liblircclient0 libllvm3.8 liblouis10 libmimic0 libmircommon6
  libopencv-contrib2.4v5 libopencv-legacy2.4v5 libopencv-ml2.4v5 libopenjpeg5 liborcus-0.11-0 libpam-cgfs libperl5.22 libpoppler61 libpostproc-ffmpeg53 libraw15 libschroedinger-1.0-0
  libsuitesparseconfig4 libswresample-ffmpeg1 libswscale-ffmpeg3 libubuntu-app-launch3 libubuntuoneauth-2.0-0 libvpx3 libwebp5 libx265-79 libx86-1 libxapian22v5 linux-headers-4.8.0-45
  linux-headers-4.8.0-45-generic linux-image-4.8.0-45-generic linux-image-extra-4.8.0-45-generic lp-solve perl-modules-5.22 pm-utils pyotherside signon-plugin-password snap-confine ubuntuone-client-data
  ubuntuone-credentials-common upstart vbetool
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  click-apparmor ubuntu-app-launch url-dispatcher
The following packages will be upgraded:
  click-apparmor ubuntu-app-launch url-dispatcher
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0 B/71,9 kB of archives.
After this operation, 80,9 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 262927 files and directories currently installed.)
Preparing to unpack .../ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../click-apparmor_0.3.18_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: error processing archive /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb
 /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb
 /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Although the above doesn't mention libuntu-app-launch4, which was mentioned before. Sigh, so where am I at?

```
sudo apt autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done
```

```
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of url-dispatcher-tools:
 url-dispatcher-tools depends on url-dispatcher (= 0.1+17.04.20170328-0ubuntu2); however:
  Version of url-dispatcher:amd64 on system is 0.1+16.10.20160816.1-0ubuntu1.

dpkg: error processing package url-dispatcher-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-app-launch-tools:
 ubuntu-app-launch-tools depends on ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2); however:
  Version of ubuntu-app-launch on system is 0.9+16.10.20160928-0ubuntu1.

dpkg: error processing package ubuntu-app-launch-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libubuntu-app-launch4:amd64:
 libubuntu-app-launch4:amd64 depends on ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2); however:
  Version of ubuntu-app-launch on system is 0.9+16.10.20160928-0ubuntu1.

dpkg: error processing package libubuntu-app-launch4:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up libunity-scopes1.0:amd64 (1.0.8+17.04.20170116-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: error processing package libunity-scopes1.0:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-system-settings-online-accounts:
 ubuntu-system-settings-online-accounts depends on libubuntu-app-launch4 (>= 0.10); however:
  Package libubuntu-app-launch4:amd64 is not configured yet.

dpkg: error processing package ubuntu-system-settings-online-accounts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-datetime:
 indicator-datetime depends on libubuntu-app-launch4 (>= 0.10); however:
  Package libubuntu-app-launch4:amd64 is not configured yet.

dpkg: error processing package indicator-datetime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcontent-hub0:amd64:
 libcontent-hub0:amd64 depends on libubuntu-app-launch4 (>= 0.10); however:
  Package libubuntu-app-launch4:amd64 is not configured yet.

dpkg: error processing package libcontent-hub0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of content-hub:
 content-hub depends on libcontent-hub0; however:
  Package libcontent-hub0:amd64 is not configured yet.
 content-hub depends on libubuntu-app-launch4 (>= 0.10); however:
  Package libubuntu-app-launch4:amd64 is not configured yet.

dpkg: error processing package content-hub (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-greeter-session-broadcast:
 unity-greeter-session-broadcast depends on url-dispatcher-tools; however:
  Package url-dispatcher-tools is not configured yet.

dpkg: error processing package unity-greeter-session-broadcast (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-system-settings:
 ubuntu-system-settings depends on indicator-datetime; however:
  Package indicator-datetime is not configured yet.

dpkg: error processing package ubuntu-system-settings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of account-plugin-facebook:
 account-plugin-facebook depends on libaccount-plugin-facebook | ubuntu-system-settings-online-accounts; however:
  Package libaccount-plugin-facebook is not installed.
  Package ubuntu-system-settings-online-accounts is not configured yet.

dpkg: error processing package account-plugin-facebook (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-control-center:
 unity-control-center depends on indicator-datetime; however:
  Package indicator-datetime is not configured yet.

dpkg: error processing package unity-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libertine-xmir-tools:
 libertine-xmir-tools depends on libcontent-hub0; however:
  Package libcontent-hub0:amd64 is not configured yet.

dpkg: error processing package libertine-xmir-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-ubuntu-content1:
 qtdeclarative5-ubuntu-content1 depends on libcontent-hub0; however:
  Package libcontent-hub0:amd64 is not configured yet.

dpkg: error processing package qtdeclarative5-ubuntu-content1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of webbrowser-app:
 webbrowser-app depends on qtdeclarative5-ubuntu-content1; however:
  Package qtdeclarative5-ubuntu-content1 is not configured yet.

dpkg: error processing package webbrowser-app (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on unity-control-center; however:
  Package unity-control-center is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-bluetooth:
 indicator-bluetooth depends on unity-control-center | gnome-control-center | ubuntu-system-settings; however:
  Package unity-control-center is not configured yet.
  Package gnome-control-center is not installed.
  Package ubuntu-system-settings is not configured yet.

dpkg: error processing package indicator-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of webapp-container:
 webapp-container depends on qtdeclarative5-ubuntu-content1; however:
  Package qtdeclarative5-ubuntu-content1 is not configured yet.
 webapp-container depends on webbrowser-app (= 0.23+17.04.20170321-0ubuntu1); however:
  Package webbrowser-app is not configured yet.

dpkg: error processing package webapp-container (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.24-9ubuntu2) ...
Errors were encountered while processing:
 url-dispatcher-tools
 ubuntu-app-launch-tools
 libubuntu-app-launch4:amd64
 libunity-scopes1.0:amd64
 ubuntu-system-settings-online-accounts
 indicator-datetime
 libcontent-hub0:amd64
 content-hub
 unity-greeter-session-broadcast
 ubuntu-system-settings
 account-plugin-facebook
 unity-control-center
 libertine-xmir-tools
 qtdeclarative5-ubuntu-content1
 webbrowser-app
 ubuntu-desktop
 indicator-bluetooth
 webapp-container
```

Here I start reading [https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa) since I am out of ideas in this loop

```
sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 click-apparmor : Depends: python3-apparmor-click (= 0.3.17) but 0.3.18 is installed
 libubuntu-app-launch4 : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is installed
 ubuntu-app-launch-tools : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is installed
 url-dispatcher-tools : Depends: url-dispatcher (= 0.1+17.04.20170328-0ubuntu2) but 0.1+16.10.20160816.1-0ubuntu1 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 click-apparmor : Depends: python3-apparmor-click (= 0.3.17) but 0.3.18 is installed
 libubuntu-app-launch4 : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is installed
 ubuntu-app-launch-tools : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is installed
 url-dispatcher-tools : Depends: url-dispatcher (= 0.1+17.04.20170328-0ubuntu2) but 0.1+16.10.20160816.1-0ubuntu1 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

So at this point I will try removing them separately:

```
sudo apt remove click-apparmor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libubuntu-app-launch4 : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is to be installed
 ubuntu-app-launch : Depends: click-apparmor but it is not going to be installed
 ubuntu-app-launch-tools : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is to be installed
 url-dispatcher-tools : Depends: url-dispatcher (= 0.1+17.04.20170328-0ubuntu2) but 0.1+16.10.20160816.1-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

```
sudo apt remove libubuntu-app-launch4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 click-apparmor : Depends: python3-apparmor-click (= 0.3.17) but 0.3.18 is to be installed
 content-hub : Depends: libubuntu-app-launch4 (>= 0.10) but it is not going to be installed
 indicator-datetime : Depends: libubuntu-app-launch4 (>= 0.10) but it is not going to be installed
 libcontent-hub0 : Depends: libubuntu-app-launch4 (>= 0.10) but it is not going to be installed
 ubuntu-app-launch-tools : Depends: libubuntu-app-launch4 (>= 0.10) but it is not going to be installed
                           Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is to be installed
 ubuntu-system-settings-online-accounts : Depends: libubuntu-app-launch4 (>= 0.10) but it is not going to be installed
 url-dispatcher-tools : Depends: url-dispatcher (= 0.1+17.04.20170328-0ubuntu2) but 0.1+16.10.20160816.1-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

Working on this for hours now and the rabbit hole is only getting deeper ... can anybody help? My system is only partially usable right now and errs along the way.

---

### Post by marcelton on 2017-04-19
Another attempt:

```
sudo apt-get remove --purge url-dispatcher-tools
[sudo] password for marcelt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 click-apparmor : Depends: python3-apparmor-click (= 0.3.17) but 0.3.18 is to be installed
 libubuntu-app-launch4 : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is to be installed
 ubuntu-app-launch-tools : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is to be installed
 unity-greeter-session-broadcast : Depends: url-dispatcher-tools but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

Now trying to follow [https://askubuntu.com/questions/904952/the-package-system-is-broken-after-upgraded-to-ubuntu-17-04](https://askubuntu.com/questions/904952/the-package-system-is-broken-after-upgraded-to-ubuntu-17-04) or [https://askubuntu.com/questions/688338/e-sub-process-usr-bin-dpkg-returned-an-error-code-1-related-to-google-chrom](https://askubuntu.com/questions/688338/e-sub-process-usr-bin-dpkg-returned-an-error-code-1-related-to-google-chrom) suggestions, specifically the changes in the [COLOR=#111111][FONT=Consolas]/var/lib/dpkg/info/ directory.

[/FONT][/COLOR]
```
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r url-dispatcher-tools.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r ubuntu-app-launch-tools.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r libubuntu-app-launch4\:amd64.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r libunity-scopes1.0\:amd64.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r ubuntu-system-settings-online-accounts.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r indicator-datetime.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r libcontent-hub0\:amd64.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r content-hub.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r unity-greeter-session-broadcast.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r ubuntu-system-settings.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r account-plugin-facebook.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r unity-control-center.*     
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r libertine-xmir-tools.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r qtdeclarative5-ubuntu-content1.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r webbrowser-app.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r ubuntu-desktop.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r indicator-bluetooth.*
marcelt@marcelt-HP-EliteBook-840-G3:/var/lib/dpkg/info$ sudo rm -r webapp-container.*
```

Proceeding to purge them:

```
sudo apt remove --purge ubuntu-app-launch-tools 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 click-apparmor : Depends: python3-apparmor-click (= 0.3.17) but 0.3.18 is to be installed
 libubuntu-app-launch4 : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is to be installed
 url-dispatcher-tools : Depends: url-dispatcher (= 0.1+17.04.20170328-0ubuntu2) but 0.1+16.10.20160816.1-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

Great, just great. Pretty sure the next command is alias as is [COLOR=#000000][FONT=&amp]sudo apt --fix-broken install + [/FONT][/COLOR][COLOR=#000000][FONT=&amp]sudo apt-get install -f[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
```
sudo apt purge ubuntu-app-launch-tools 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 click-apparmor : Depends: python3-apparmor-click (= 0.3.17) but 0.3.18 is to be installed
 libubuntu-app-launch4 : Depends: ubuntu-app-launch (= 0.12+17.04.20170404.2-0ubuntu2) but 0.9+16.10.20160928-0ubuntu1 is to be installed
 url-dispatcher-tools : Depends: url-dispatcher (= 0.1+17.04.20170328-0ubuntu2) but 0.1+16.10.20160816.1-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

Grrr.

```

sudo -H pip2 install python3-apparmor-click==0.3.18
Collecting python3-apparmor-click==0.3.18
  Could not find a version that satisfies the requirement python3-apparmor-click==0.3.18 (from versions: )
No matching distribution found for python3-apparmor-click==0.3.18

sudo -H pip3 install python3-apparmor-click==0.3.18
BUG: Is it bad if orig_path is not sorted correctly?
Collecting python3-apparmor-click==0.3.18
  Could not find a version that satisfies the requirement python3-apparmor-click==0.3.18 (from versions: )
No matching distribution found for python3-apparmor-click==0.3.18

```




I was so happy when I switched to Ubuntu a few months ago, what kind of update can crap out an OS like this ...

---

### Post by marcelton on 2017-04-19
So I tried downloading all packages manually:

```

[COLOR=#111111][FONT=Ubuntu]/var/cache/apt/archives$ ls[/FONT][/COLOR]
account-plugin-facebook_0.13+17.04.20170314-0ubuntu1_all.deb
content-hub_0.3+17.04.20170403-0ubuntu2_amd64.deb
indicator-bluetooth_0.0.6+17.04.20170322-0ubuntu1_amd64.deb
indicator-datetime_15.10+17.04.20170322-0ubuntu2_amd64.deb
libertine-xmir-tools_1.7.1+17.04.20170331-0ubuntu1_amd64.deb
libubuntu-app-launch4_0.12+17.04.20170404.2-0ubuntu2_amd64.deb
libunity-scopes1.0_1.0.8+17.04.20170116-0ubuntu1_amd64.deb
lock
partial
qtdeclarative5-ubuntu-content1_0.3+17.04.20170403-0ubuntu2_amd64.deb
ubuntu-app-launch-tools_0.12+17.04.20170404.2-0ubuntu2_amd64.deb
ubuntu-desktop_1.379_amd64.deb
ubuntu-system-settings_0.4+17.04.20170324-0ubuntu1_amd64.deb
ubuntu-system-settings-online-accounts_0.7+17.04.20170308.2-0ubuntu3_amd64.deb
unity-control-center_15.04.0+17.04.20170402.6-0ubuntu1_amd64.deb
unity-greeter-session-broadcast_0.1+14.10.20140601-0ubuntu5_amd64.deb
url-dispatcher-tools_0.1+17.04.20170328-0ubuntu2_amd64.deb
webapp-container_0.23+17.04.20170321-0ubuntu1_amd64.deb
webbrowser-app_0.23+17.04.20170321-0ubuntu1_amd64.deb
```

Then trying to fix the install:

```
[COLOR=#111111][FONT=Ubuntu]marcelt@marcelt-HP-EliteBook-840-G3:/var/cache/apt/archives$ sudo apt --fix-broken install[/FONT][/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-tools cgmanager dns-root-data dnsmasq-base espeak-data
  fonts-stix gdebi-core hwdata imagemagick-common iproute libavcodec-ffmpeg56
  libavfilter-ffmpeg5 libavformat-ffmpeg56 libavresample-ffmpeg2
  libavutil-ffmpeg54 libbluray1 libboost-date-time1.61.0
  libboost-filesystem1.61.0 libboost-iostreams1.61.0 libboost-log1.61.0
  libboost-program-options1.61.0 libboost-regex1.61.0 libboost-system1.61.0
  libboost-thread1.61.0 libcgmanager0 libchromaprint0 libcolamd2 libespeak1
  libglew1.13 libgnome2-0 libgnome2-bin liblircclient0 libllvm3.8 liblouis10
  libmimic0 libmircommon6 libopencv-contrib2.4v5 libopencv-legacy2.4v5
  libopencv-ml2.4v5 libopenjpeg5 liborcus-0.11-0 libpam-cgfs libperl5.22
  libpoppler61 libpostproc-ffmpeg53 libraw15 libschroedinger-1.0-0
  libsuitesparseconfig4 libswresample-ffmpeg1 libswscale-ffmpeg3
  libubuntu-app-launch3 libubuntuoneauth-2.0-0 libvpx3 libwebp5 libx265-79
  libx86-1 libxapian22v5 linux-headers-4.8.0-45 linux-headers-4.8.0-45-generic
  linux-image-4.8.0-45-generic linux-image-extra-4.8.0-45-generic lp-solve
  perl-modules-5.22 pm-utils pyotherside signon-plugin-password snap-confine
  ubuntuone-client-data ubuntuone-credentials-common upstart vbetool
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  click-apparmor ubuntu-app-launch url-dispatcher
The following packages will be upgraded:
  click-apparmor ubuntu-app-launch url-dispatcher
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 71,9 kB of archives.
After this operation, 80,9 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) zesty/main amd64 ubuntu-app-launch amd64 0.12+17.04.20170404.2-0ubuntu2 [14,1 kB]
Get:2 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) zesty/main amd64 url-dispatcher amd64 0.1+17.04.20170328-0ubuntu2 [47,1 kB]
Get:3 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) zesty/main amd64 click-apparmor amd64 0.3.18 [10,7 kB]
Fetched 71,9 kB in 0s (233 kB/s)           
dpkg: warning: files list file for package 'unity-control-center' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'indicator-datetime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'webapp-container' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'qtdeclarative5-ubuntu-content1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcontent-hub0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'content-hub' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unity-greeter-session-broadcast' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'webbrowser-app' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-desktop' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-system-settings' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'account-plugin-facebook' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'url-dispatcher-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-app-launch-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'indicator-bluetooth' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-apparmor-click' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-system-settings-online-accounts' missing; assuming package has no files currently installed
(Reading database ... 262046 files and directories currently installed.)
Preparing to unpack .../ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../click-apparmor_0.3.18_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: error processing archive /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb
 /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb
 /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Maybe getting click back from where it was in 16.10 would work?

```
marcelt@marcelt-HP-EliteBook-840-G3:/var/cache/apt/archives$ sudo -H pip2 install click
Collecting click
  Using cached click-6.7-py2.py3-none-any.whl
Installing collected packages: click
Successfully installed click-6.7
marcelt@marcelt-HP-EliteBook-840-G3:/var/cache/apt/archives$ sudo -H pip3 install click
BUG: Is it bad if orig_path is not sorted correctly?
Collecting click
  Using cached click-6.7-py2.py3-none-any.whl
Installing collected packages: click
Successfully installed click-6.7
```

Retry:
```
marcelt@marcelt-HP-EliteBook-840-G3:/var/cache/apt/archives$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-tools cgmanager dns-root-data dnsmasq-base espeak-data fonts-stix gdebi-core hwdata imagemagick-common iproute
  libavcodec-ffmpeg56 libavfilter-ffmpeg5 libavformat-ffmpeg56 libavresample-ffmpeg2 libavutil-ffmpeg54 libbluray1 libboost-date-time1.61.0
  libboost-filesystem1.61.0 libboost-iostreams1.61.0 libboost-log1.61.0 libboost-program-options1.61.0 libboost-regex1.61.0
  libboost-system1.61.0 libboost-thread1.61.0 libcgmanager0 libchromaprint0 libcolamd2 libespeak1 libglew1.13 libgnome2-0 libgnome2-bin
  liblircclient0 libllvm3.8 liblouis10 libmimic0 libmircommon6 libopencv-contrib2.4v5 libopencv-legacy2.4v5 libopencv-ml2.4v5 libopenjpeg5
  liborcus-0.11-0 libpam-cgfs libperl5.22 libpoppler61 libpostproc-ffmpeg53 libraw15 libschroedinger-1.0-0 libsuitesparseconfig4
  libswresample-ffmpeg1 libswscale-ffmpeg3 libubuntu-app-launch3 libubuntuoneauth-2.0-0 libvpx3 libwebp5 libx265-79 libx86-1 libxapian22v5
  linux-headers-4.8.0-45 linux-headers-4.8.0-45-generic linux-image-4.8.0-45-generic linux-image-extra-4.8.0-45-generic lp-solve
  perl-modules-5.22 pm-utils pyotherside signon-plugin-password snap-confine ubuntuone-client-data ubuntuone-credentials-common upstart vbetool
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  click-apparmor ubuntu-app-launch url-dispatcher
The following packages will be upgraded:
  click-apparmor ubuntu-app-launch url-dispatcher
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0 B/71,9 kB of archives.
After this operation, 80,9 kB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'unity-control-center' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'indicator-datetime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'webapp-container' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'qtdeclarative5-ubuntu-content1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcontent-hub0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'content-hub' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unity-greeter-session-broadcast' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'webbrowser-app' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-desktop' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-system-settings' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'account-plugin-facebook' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'url-dispatcher-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-app-launch-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'indicator-bluetooth' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-apparmor-click' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-system-settings-online-accounts' missing; assuming package has no files currently installed
(Reading database ... 262046 files and directories currently installed.)
Preparing to unpack .../ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to unpack .../click-apparmor_0.3.18_amd64.deb ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: error processing archive /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb
 /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb
 /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How about that beautiful crap circle, yes I'm mad.

---

### Post by marcelton on 2017-04-19
Last try:

```

sudo dpkg -i Downloads/click_0.4.45.1+16.10.20160916-0ubuntu1_amd64.deb 
[sudo] password for marcelt: 
dpkg: warning: files list file for package 'unity-control-center' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'indicator-datetime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'webapp-container' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'qtdeclarative5-ubuntu-content1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcontent-hub0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'content-hub' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unity-greeter-session-broadcast' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'webbrowser-app' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-desktop' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-system-settings' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'account-plugin-facebook' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'url-dispatcher-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-app-launch-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'indicator-bluetooth' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-apparmor-click' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-system-settings-online-accounts' missing; assuming package has no files currently installed
(Reading database ... 262046 files and directories currently installed.)
Preparing to unpack .../click_0.4.45.1+16.10.20160916-0ubuntu1_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/click", line 37, in <module>
    import click
ImportError: No module named 'click'
dpkg: error processing archive Downloads/click_0.4.45.1+16.10.20160916-0ubuntu1_amd64.deb (--install):
 subprocess new pre-removal script returned error exit status 1
Job for click-system-hooks.service failed because the control process exited with error code.
See "systemctl status click-system-hooks.service" and "journalctl -xe" for details.
click-system-hooks.service couldn't start.
Errors were encountered while processing:
 Downloads/click_0.4.45.1+16.10.20160916-0ubuntu1_amd64.deb
```

So it looks like the tips in [https://askubuntu.com/questions/904952/the-package-system-is-broken-after-upgraded-to-ubuntu-17-04](https://askubuntu.com/questions/904952/the-package-system-is-broken-after-upgraded-to-ubuntu-17-04) and [https://askubuntu.com/questions/688338/e-sub-process-usr-bin-dpkg-returned-an-error-code-1-related-to-google-chrom](https://askubuntu.com/questions/688338/e-sub-process-usr-bin-dpkg-returned-an-error-code-1-related-to-google-chrom) sooner pushed me away from a solution than got me closer to a fix. I can't find any productive starting point that helps my system towards a total fix, all of them err out in some way or another and reason in circles. "Don't assume you tested better than we did" is what I read somewhere in the 17.04 upgrade. Well, I'll skip this well tested upgrade tyvm.

---

### Post by marcelton on 2017-04-19
Solved; reinstalling different OS ):P .

---

### Post by skamphax0r on 2017-04-25
was able to get past this by doing the following: 

```

dpkg -P --force-all python3-click-package
apt --fix-broken install

```

in case anyone else has the same problem....

---

