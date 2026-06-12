---
title: "Reinstalling  2.6.35-27 not working"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by NuttinButNet on 2011-03-06
I had a driver problem and am trying to reinstall 2.6.35-27 in
10.10

When I execute 
sudo apt-get install 2.6.35-27

I get the following error which I don't understand.
There aren't any wireless cards on this computer even.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-backports-modules-alsa-2.6.35-27-generic' for regex '2.6.35-27'
Note, selecting 'linux-image-2.6.35-27-generic' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-alsa-2.6.35-27-server' for regex '2.6.35-27'
Note, selecting 'linux-image-2.6.35-27-server' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-compat-wireless-2.6.36-2.6.35-27-generic' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-compat-wireless-2.6.37-2.6.35-27-generic' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-compat-wireless-2.6.36-2.6.35-27-server' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-compat-wireless-2.6.37-2.6.35-27-server' for regex '2.6.35-27'
Note, selecting 'linux-headers-lbm-2.6.35-27-generic' for regex '2.6.35-27'
Note, selecting 'linux-headers-lbm-2.6.35-27-server' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-input-2.6.35-27-generic' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-input-2.6.35-27-server' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-media-2.6.35-27-generic' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-media-2.6.35-27-server' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-net-2.6.35-27-generic' for regex '2.6.35-27'
Note, selecting 'linux-backports-modules-net-2.6.35-27-server' for regex '2.6.35-27'
Note, selecting 'linux-headers-2.6.35-27' for regex '2.6.35-27'
Note, selecting 'linux-headers-2.6.35-27-generic' for regex '2.6.35-27'
Note, selecting 'linux-headers-2.6.35-27-server' for regex '2.6.35-27'
Note, selecting 'linux-headers-2.6.35-27-virtual' for regex '2.6.35-27'
Note, selecting 'linux-image-2.6.35-27-virtual' for regex '2.6.35-27'
Note, selecting 'linux-tools-2.6.35-27' for regex '2.6.35-27'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-backports-modules-compat-wireless-2.6.36-2.6.35-27-generic : Conflicts: linux-backports-modules-compat-wireless-2.6.37-2.6.35-27-generic but 2.6.35-27.18 is to be installed
 linux-backports-modules-compat-wireless-2.6.36-2.6.35-27-server : Conflicts: linux-backports-modules-compat-wireless-2.6.37-2.6.35-27-server but 2.6.35-27.18 is to be installed
 linux-backports-modules-compat-wireless-2.6.37-2.6.35-27-generic : Conflicts: linux-backports-modules-compat-wireless-2.6.36-2.6.35-27-generic but 2.6.35-27.18 is to be installed
 linux-backports-modules-compat-wireless-2.6.37-2.6.35-27-server : Conflicts: linux-backports-modules-compat-wireless-2.6.36-2.6.35-27-server but 2.6.35-27.18 is to be installed
E: Broken packages

---

### Post by NuttinButNet on 2011-03-06
Never mind. Now that I look at this again, it is silly.

---

