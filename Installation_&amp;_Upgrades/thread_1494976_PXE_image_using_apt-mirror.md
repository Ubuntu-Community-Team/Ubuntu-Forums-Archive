---
title: "PXE image using apt-mirror"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by Hypnoz on 2010-05-27
I have always been able to pxe image using an extracted .iso, however now I am trying to point the imaging process towards an apt-mirror archive I have set up.

The system boots into the kickstart file, grabs a dhcp IP, then dumps this error message.

```
No kernel modules were found. This probably is due to a mismatch 
between the kernel version used by this version of the installer and the
kernel version available in the archive.

If you're installing from a mirror, you can work around this problem
by choosing to install a different version of Ubuntu. The install
will probably fail to work if you continue without kernel modules.

Continue the install without kernel modules?

<Go Back>   <Yes>  <No>
```

I have tried the netboot files from both the server iso and the alternative iso. I even tried the netboot files from 
[http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/)

Everything dumps me to this error message. Does anyone have an idea of what files are not matching?

Thanks

---

### Post by Hypnoz on 2010-06-01
I was able to solve this issue. I originally was only mirroring debian-installer for the "hardy" section, but from my apache logs during imaging process, I realized the pxe installer was looking for debian-installer in hardy-updates and hardy-security. 

```
deb-amd64 http://mirror.anl.gov/pub/ubuntu hardy main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-amd64 http://mirror.anl.gov/pub/ubuntu hardy-updates main/debian-installer restricted/debian-installer universe/debian-installer
deb-amd64 http://mirror.anl.gov/pub/ubuntu hardy-security main/debian-installer restricted/debian-installer universe/debian-installer
```

I had the first line. I had to add the two lines after and resync the mirror. Then it worked.

NOTE: My mirror is using mirror.anl.gov because they have a fast connection. Yours probably says archive.ubuntu.com or something.

---

