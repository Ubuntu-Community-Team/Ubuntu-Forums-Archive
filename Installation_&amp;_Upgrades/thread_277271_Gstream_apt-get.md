---
title: "Gstream apt-get"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2006-10-14
Heya
I have today problem with installation of gstream
Any idea whats the problem can be ?

Thanks



dmsn@lappen:~$ sudo apt-get install gstreamer* Reading package lists... Done Building dependency tree... Done
Note, selecting gstreamer0.10-alsa for regex 'gstreamer*'
Note, selecting totem-gstreamer-firefox-plugin for regex 'gstreamer*'
Note, selecting gstreamer0.10-audiosink for regex 'gstreamer*'
Note, selecting gstreamer0.10-x for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base-dbg for regex 'gstreamer*'
Note, selecting libgstreamer0.10-0 for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly for regex 'gstreamer*'
Note, selecting gstreamer0.10-colorspace for regex 'gstreamer*'
Note, selecting gstreamer0.8-misc for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-multiverse for regex 'gstreamer*'
Note, selecting libgstreamer-plugins-base0.10-dev for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-bad-multiverse for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-good for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins for regex 'gstreamer*'
Note, selecting gstreamer0.10-ffmpeg for regex 'gstreamer*'
Note, selecting gstreamer0.10-pitfdll for regex 'gstreamer*'
Note, selecting gstreamer0.10-videosink for regex 'gstreamer*'
Note, selecting gstreamer0.10-lame for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-multiverse instead of gstreamer0.10-lame
Note, selecting gstreamer0.10-plugins-good-dbg for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-good-doc for regex 'gstreamer*'
Note, selecting totem-gstreamer for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-bad for regex 'gstreamer*'
Note, selecting gstreamer0.10-doc for regex 'gstreamer*'
Note, selecting gstreamer0.10-esd for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base-apps for regex 'gstreamer*'
Note, selecting libgstreamer0.10-dev for regex 'gstreamer*'
Note, selecting gstreamer0.10-gnomevfs for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base for regex 'gstreamer*'
Note, selecting libgstreamer-plugins-base0.10-0 for regex 'gstreamer*'
Note, selecting gstreamer0.10-tools for regex 'gstreamer*'
Note, selecting libgstreamer0.10-0-dbg for regex 'gstreamer*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.10-plugins-base-dbg: Depends: gstreamer0.10-alsa (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
                                  Depends: gstreamer0.10-gnomevfs (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
                                  Depends: gstreamer0.10-plugins-base (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
                                  Depends: gstreamer0.10-x (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
                                  Depends: libgstreamer-plugins-base0.10-0 (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
  libgstreamer-plugins-base0.10-dev: Depends: libgstreamer-plugins-base0.10-0 (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
                                     Depends: libglib2.0-dev but it is not going to be installed
  libgstreamer0.10-dev: Depends: libglib2.0-dev but it is not going to be installed
E: Broken packages
dmsn@lappen:~$










dmsn@lappen:~$ sudo apt-get install libglib2.0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed
E: Broken packages
dmsn@lappen:~$

---

