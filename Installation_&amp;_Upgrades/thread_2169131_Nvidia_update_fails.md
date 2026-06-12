---
title: "Nvidia update fails"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by Bill Roberts on 2013-08-20
I receive the floowing messages executing Upgrade.  Any suggestions on resolving this issue would be most welcome.

 error in Config-Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 60092 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 60093 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 57941 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 57942 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 60092 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 60093 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 57941 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 57942 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 60092 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 60093 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 57941 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 57942 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 60092 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 60093 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 57941 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 57942 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 60092 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 60093 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/nvidia-304-updates_304.88-0ubuntu0.0.3_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
         Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-304-updates_304.88-0ubuntu0.0.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 57941 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 57942 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60092 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60093 package 'virtualbox-2.2':
 error in Config-Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
dpkg: dependency problems prevent configuration of nvidia-current-updates:
 nvidia-current-updates depends on nvidia-304-updates; however:
  Package nvidia-304-updates is not installed.
dpkg: error processing nvidia-current-updates (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-current-updates

---

### Post by papibe on 2013-08-20
Hi Bill Roberts.

It seems that you are trying to update a Karmic (9.10) system. That version is no longer supported and there's little support we can offer.

I recommend you to both backing up your data, and to either upgrade, or do a clean install.

Hope it helps.
Regards.

P.S.: Here's a couple of old tricks related to that version: [How do I rebuild a corrupt dpkg status file]("http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file").

---

### Post by Bill Roberts on 2013-08-21
Wierd...

It's a 10.04 LTS installation and the problem began with a recent Nvidia file provided by the Update Manager.

Any other suggestions?

---

