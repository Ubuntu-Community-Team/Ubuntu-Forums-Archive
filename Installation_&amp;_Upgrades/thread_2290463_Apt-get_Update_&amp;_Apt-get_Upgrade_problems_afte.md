---
title: "Apt-get Update &amp; Apt-get Upgrade problems after switching to Hyper-V (Windows 10)"
date: 2015-08-12
forum: Installation &amp; Upgrades
---

### Post by sam145 on 2015-08-12
I have not used Ubuntu in a while but ever since upgrading to Windows 10, VirtualBox in no longer supported so i have been using Hyper-V which seems to be a little more complicated, Im a Kali Linux user which is not fully supported by Hyper-V, so i have been refreshing my skills on Ubuntu.. although i seem to have a very annoying problem both apt-get update and apt-get upgrade fail to fetch anything from the servers.. I just recently got Apt-get update to work but when i do apt-get upgrade i get nothing but err, what is really annoying is that it will work for about 25 min before it gives me all these errors.. im fully connected to the internet with no problems so im not sure if its something in Hyper-V that's causing the problem because apt-get update is working fine now, but nothing will upgrade.. Also I am using Ubuntu 12.04 because 14.04 failed to install and i am trying to upgrade but it will not let me do that either.. Please Help!

---

### Post by v3.xx on 2015-08-12
Can you post the errors?

---

### Post by sam145 on 2015-08-12
Yea sorry... this list was really long so i just copied parts of each error but this is mainly what i get when i try apt-get updrade

Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main bash amd64 4.2-2ubuntu2.6
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main bash amd64 4.2-2ubuntu2.6
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libreoffice-writer amd64 1:3.5.7-0ubuntu8
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libreoffice-calc amd64 1:3.5.7-0ubuntu8
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

--------------------------------------------------------------

Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgnome-control-center1 amd64 1:3.4.2-0ubuntu0.13.3
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libnm-gtk-common all 0.9.4.1-0ubuntu2.5
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libnm-gtk0 amd64 0.9.4.1-0ubuntu2.5
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main gnome-control-center-data all 1:3.4.2-0ubuntu0.13.3
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main gnome-control-center amd64 1:3.4.2-0ubuntu0.13.3
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main grub-pc amd64 1.99-21ubuntu3.18
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main grub-pc-bin amd64 1.99-21ubuntu3.18
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main grub2-common amd64 1.99-21ubuntu3.18
  Could not resolve 'us.archive.ubuntu.com'

-------------------------------------------------------------------

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.10.3-0ubuntu1.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.10.3-0ubuntu1.6_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.10.3-0ubuntu1.6_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.10.3-0ubuntu1.6_amd64.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-emailmerge_3.5.7-0ubuntu8_all.deb](http://security.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-emailmerge_3.5.7-0ubuntu8_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-help-en-us_3.5.7-0ubuntu8_all.deb](http://security.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-help-en-us_3.5.7-0ubuntu8_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libv/libvncserver/libvncserver0_0.9.8.2-2ubuntu1.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libv/libvncserver/libvncserver0_0.9.8.2-2ubuntu1.1_amd64.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.79.18_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.79.18_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-trusty/linux-image-generic-lts-trusty_3.13.0.61.52_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-trusty/linux-image-generic-lts-trusty_3.13.0.61.52_amd64.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-trusty/linux-headers-3.13.0-61_3.13.0-61.100~precise1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-trusty/linux-headers-3.13.0-61_3.13.0-61.100~precise1_all.deb)  Could not resolve 'security.ubuntu.com'

---

### Post by v3.xx on 2015-08-13
Hay sam

I know nothing about hyper-v as I use vBox, but it looks like you have a mix of 14.04 and 12.04.  So I'm thinking that you may have a software source problem and not a virtual one.

I would like to see your sources list, can you post the output of ..

```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

Thanks

---

