---
title: "Question about Alsa Equalizer."
date: 2013-08-26
forum: Installation &amp; Upgrades
---

### Post by robgeek on 2013-08-26
Hello, guys.
I'm trying to install alsaequal in my Ubuntu 13 and i'm having the following error message:
> /opt/alsaequal# make install
Installing...
install: target `/usr/lib/alsa-lib/' is not a directory: No such file or directory
make: *** [install] Error 1

So, here is what i did:
> 
apt-file search alsa-lib
libasound2-plugin-equal: /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_ctl_equal.so
libasound2-plugin-equal: /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_equal.so
libasound2-plugins: /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_conf_pulse.so
libasound2-plugins: /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_ctl_arcam_av.so
libasound2-plugins: /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_ctl_oss.so
libasound2-plugins: /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_ctl_pulse.so
I'm trying to install libasound2-plugins:
> aptitude install libasound2-plugins
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

I tried to download from the pool:
> 
dpkg -i libasound2-plugins_1.0.27-2_i386.deb 
(Reading database ... 138434 files and directories currently installed.)
Preparing to replace libasound2-plugins:i386 1.0.25-2 (using libasound2-plugins_1.0.27-2_i386.deb) ...
Unpacking replacement libasound2-plugins:i386 ...
dpkg: dependency problems prevent configuration of libasound2-plugins:i386:
 libasound2-plugins:i386 depends on libc6 (>= 2.15); however:
  Version of libc6:i386 on system is 2.13-38.

dpkg: error processing libasound2-plugins:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libasound2-plugins:i386


The version of libc6 in the pool is avaliable only in amd64 but my system is i386!
I don't know what to do. 
How can i solve this problem?

---

