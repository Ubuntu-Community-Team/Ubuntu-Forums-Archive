---
title: "kodi installation on fresh Ubuntu Server has unmet dependencies"
date: 2018-08-20
forum: Installation &amp; Upgrades
---

### Post by pdxkodi on 2018-08-20
Trying to install Kodi on a fresh install of Ubuntu Server.

following this: [https://github.com/OnceUponALoop/mini-kodi](https://github.com/OnceUponALoop/mini-kodi)

After running sudo apt-get update and adding the Kodi PPA Repository, i get the following errors after installing:

```
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages may have unmet dependencies:


 Kodi : Depends: kodi-bin (>=.....final.obionic) but it is not going to be installed
Depends: kodi-bin (>=.....final.obionic.1) but it is not going to be installed
Depends: mesa-utils but it is not installable
Depends: python-bluez but it is not installable or
python-lightblue but it is not installable

Depends: libmad0 but it is not installable
libass9,5,4 but it is not installable
libnfs11,8,4,1 but it is not installable
libbluray1 but it is not installable
libblueray2 but it is not installable
libaacs0 but it is not installable
libcec4 but it is not installable

Recommends: libvdpau1 but it is not going to be installed
i965-va-driver but it is not installable
libva-intel-vaapi-driver but it is not installable
libva1 but it is not installable

E: Unable to correct problems, you have held broken packages
```

---

