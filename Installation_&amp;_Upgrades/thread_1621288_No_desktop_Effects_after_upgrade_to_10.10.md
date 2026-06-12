---
title: "No desktop Effects after upgrade to 10.10"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by stuartlea on 2010-11-14
Hi,

I have a problem that I am struggling to fix following an upgrade to 10.10.

I am fairly sure it is something to do with the ATI driver but dont quite know enough about it to get beyond the point I am at.

Summary:
I have 64bit Ubuntu with an ATI Radeon 4350 Card and 2 monitors. During the upgrade there was a error which flew by and I missed. Upon restart I had an error something like /proc/usb which turned out to be an issue with Virtualbox that I easily fixed.

I now am unable to get the desktop effects to work and have really slow window performance. I get an error message saying the desktop effects cannot be enabled. 

I now seem to be caught between the ATI Open Source and the ATI Propriety drivers.

I thought it would be a good idea to try and remove drivers and start again but to no avail. I found this post [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) which I followed but looks like I cannot remove some of the drivers as suggested.

I have pasted below a some of the output where it seems to be getting stuck - I am afraid I dont understand it enough to interpret what it means.

```
lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV710 [Radeon HD 4350] [1002:954f]
```

```
sudo apt-get remove --purge xorg-driver-fglrx

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libyaml-syck-perl libdate-manip-perl libfile-slurp-perl kdesudo
  python-soappy python-fpconst hddtemp libcarp-clan-perl libwww-search-perl
  update-manager-kde libuser-perl libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  fglrx xorg-driver-fglrx*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 108MB disk space will be freed.
Do you want to continue [Y/n]? y
warning, in file '/var/lib/dpkg/status' near line 39991 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 39992 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 40568 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
(Reading database ... 187737 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks (in anticipation).

Stu

---

