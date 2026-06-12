---
title: "Unable to install package-&quot;unable to stat config file&quot;???"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by az_s_za on 2006-11-04
Sorry if this is obvious... I'm new.
When trying to install the bpalogin package I get the following:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  dhcp-client
The following NEW packages will be installed:
  bpalogin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/22.1kB of archives.
After unpacking 131kB of additional disk space will be used.
(Reading database ... 88722 files and directories currently installed.)
Unpacking bpalogin (from .../bpalogin_2.0.2-9ubuntu1_i386.deb) ...
dpkg: bpalogin: warning - unable to stat config file `etc/init.d/bpalogin'
 (= `/etc/init.d/bpalogin'): Input/output error
dpkg: error processing /var/cache/apt/archives/bpalogin_2.0.2-9ubuntu1_i386.deb (--unpack):
 unable to stat `./etc/init.d/bpalogin' (which I was about to install): Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/bpalogin_2.0.2-9ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
This happens whether I use the Synaptic Manager or apt-get. 

How can I install this package?

---

