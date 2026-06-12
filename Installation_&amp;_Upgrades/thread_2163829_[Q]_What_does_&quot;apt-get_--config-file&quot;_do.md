---
title: "[Q] What does &quot;apt-get --config-file&quot; do?"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by heWhoWearsAshes on 2013-07-19
I was looking through the man page. Is this option for providing an alternate configuration for compiling? Is is this only used when apt-get'ing source?

---

### Post by grahammechanical on 2013-07-19
I do not see the information in the man page the same way as you.

>  -c, --config-file
           Configuration File; Specify a configuration file to use. The program will read the default configuration file and then this configuration file. If configuration settings need to be set before the default configuration files are parsed specify a file with the APT_CONFIG environment variable. See apt.conf(5) for syntax information.


I see it as talking about an alternative configuration file for apt-get. Then there are these two options

>        source
           source causes apt-get to fetch source packages. APT will examine the available packages to decide which source package to fetch. It will then find and download into the current directory the newest available version of that source package while respecting the default release, set with the option APT : : default-Release, the -t
           option or per package with the pkg/release syntax, if possible.

If the --compile option is specified then the package will be compiled to a binary .deb using dpkg-buildpackage for the architecture as defined by the --host-architecture option. If --download-only is specified then the source package will not be unpacked.


So, --compile not --config-file

Regards.

---

