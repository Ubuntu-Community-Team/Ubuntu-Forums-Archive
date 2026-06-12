---
title: "i Couldn't downlaod software from software center or package manager"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by hosseini on 2012-05-10
hi
i Could download software 4 day ago but now i couldn't
i change download server in software center but don't fix
when i type 
sudo apt-get update
The answer is given
```
 associated with hostname)
Err http://archive.ubuntu.com precise-security/multiverse Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-security/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-security/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-security/universe Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-security/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/multiverse amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/restricted i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/main i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/multiverse i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/universe i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/main Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/multiverse Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/multiverse Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/universe Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com precise-proposed/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Fetched 270 B in 51s (5 B/s)          
W: GPG error: http://archive.canonical.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://extras.ubuntu.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/multiverse/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```
but I am conecct to Internet
and i can Surf
Please help me

---

### Post by codemaniac on 2012-05-10
You can try recreating your surces.lst from the below link .
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Enigmapond on 2012-05-10
Very odd as all your sources are missing .gz at the end. In other words yours read like this:
```
http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources
```

when they should read:

```
http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources.gz
```

I would use that link provided and re-build your sources.

---

### Post by hosseini on 2012-05-10
> **codemaniac said:**
> You can try recreating your surces.lst from the below link .
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
my problem didn,t solve the package manager show this errore to me
```
Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.
```

---

### Post by codemaniac on 2012-05-10
You are getting some alarms because of restricted repositories you have checked while creating your sources.lst i believe.
It should not be an issue .What happens when you do an update ?

---

### Post by hosseini on 2012-05-10
> **codemaniac said:**
> You are getting some alarms because of restricted repositories you have checked while creating your sources.lst i believe.
It should not be an issue .What happens when you do an update ?
the software become failed for download and The above error occurs

---

