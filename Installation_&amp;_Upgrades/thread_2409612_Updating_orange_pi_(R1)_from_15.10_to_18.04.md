---
title: "Updating orange pi (R1) from 15.10 to 18.04"
date: 2019-01-04
forum: Installation &amp; Upgrades
---

### Post by sven20000 on 2019-01-04
Hello,

i want to use a orange pi (R1) for some home automation, but before i want to do this i want first update the availebel software. I have download the ubuntu server image from the orange site but the version is not supported.

After a day i have update it to 15.10, but i got many error's when i try to update it further.

Can someone explane me how i can update to 18.04 LTS?

Ps. I use the armhf architecture.

```


root@OrangePizero:~# sudo apt-get update
Ign http://security.ubuntu.com wily-security InRelease
Ign http://ports.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com wily-security Release.gpg
Hit http://ports.ubuntu.com trusty Release.gpg
Ign http://security.ubuntu.com wily-security Release
Hit http://ports.ubuntu.com trusty Release
Ign http://no.archive.ubuntu.com wily InRelease
Ign http://no.archive.ubuntu.com wily-updates InRelease
Hit http://ports.ubuntu.com trusty/main Sources
Ign http://no.archive.ubuntu.com wily-backports InRelease
Hit http://ports.ubuntu.com trusty/universe Sources
Ign http://no.archive.ubuntu.com wily Release.gpg
Ign http://no.archive.ubuntu.com wily-updates Release.gpg
Ign http://no.archive.ubuntu.com wily-backports Release.gpg
Ign http://no.archive.ubuntu.com wily Release
Ign http://no.archive.ubuntu.com wily-updates Release
Ign http://no.archive.ubuntu.com wily-backports Release
Err http://security.ubuntu.com wily-security/main Sources
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/restricted Sources
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/universe Sources
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/multiverse Sources
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/main amd64 Packages
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/restricted amd64 Packages
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/universe amd64 Packages
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/multiverse amd64 Packages
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/main i386 Packages
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/restricted i386 Packages
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/universe i386 Packages
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err http://security.ubuntu.com wily-security/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Ign http://security.ubuntu.com wily-security/main Translation-en_US
Ign http://security.ubuntu.com wily-security/main Translation-en
Ign http://security.ubuntu.com wily-security/multiverse Translation-en_US
Ign http://security.ubuntu.com wily-security/multiverse Translation-en
Ign http://security.ubuntu.com wily-security/restricted Translation-en_US
Ign http://security.ubuntu.com wily-security/restricted Translation-en
Ign http://security.ubuntu.com wily-security/universe Translation-en_US
Ign http://security.ubuntu.com wily-security/universe Translation-en
Err http://no.archive.ubuntu.com wily/main Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/restricted Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/universe Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/multiverse Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/main amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/restricted amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/universe amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/multiverse amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/main i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/restricted i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/universe i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Ign http://no.archive.ubuntu.com wily/main Translation-en_US
Ign http://no.archive.ubuntu.com wily/main Translation-en
Ign http://no.archive.ubuntu.com wily/multiverse Translation-en_US
Ign http://no.archive.ubuntu.com wily/multiverse Translation-en
Ign http://no.archive.ubuntu.com wily/restricted Translation-en_US
Ign http://no.archive.ubuntu.com wily/restricted Translation-en
Ign http://no.archive.ubuntu.com wily/universe Translation-en_US
Ign http://no.archive.ubuntu.com wily/universe Translation-en
Err http://no.archive.ubuntu.com wily-updates/main Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/restricted Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/universe Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/multiverse Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/main amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/restricted amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/universe amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/multiverse amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/main i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/restricted i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/universe i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-updates/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Ign http://no.archive.ubuntu.com wily-updates/main Translation-en_US
Ign http://no.archive.ubuntu.com wily-updates/main Translation-en
Ign http://no.archive.ubuntu.com wily-updates/multiverse Translation-en_US
Ign http://no.archive.ubuntu.com wily-updates/multiverse Translation-en
Ign http://no.archive.ubuntu.com wily-updates/restricted Translation-en_US
Ign http://no.archive.ubuntu.com wily-updates/restricted Translation-en
Ign http://no.archive.ubuntu.com wily-updates/universe Translation-en_US
Ign http://no.archive.ubuntu.com wily-updates/universe Translation-en
Err http://no.archive.ubuntu.com wily-backports/main Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/restricted Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/universe Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/multiverse Sources
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/main amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/restricted amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/universe amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/multiverse amd64 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/main i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/restricted i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/universe i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Err http://no.archive.ubuntu.com wily-backports/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:29f4::51 80]
Ign http://no.archive.ubuntu.com wily-backports/main Translation-en_US
Ign http://no.archive.ubuntu.com wily-backports/main Translation-en
Ign http://no.archive.ubuntu.com wily-backports/multiverse Translation-en_US
Ign http://no.archive.ubuntu.com wily-backports/multiverse Translation-en
Ign http://no.archive.ubuntu.com wily-backports/restricted Translation-en_US
Ign http://no.archive.ubuntu.com wily-backports/restricted Translation-en
Ign http://no.archive.ubuntu.com wily-backports/universe Translation-en_US
Ign http://no.archive.ubuntu.com wily-backports/universe Translation-en
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/main/source/Sources  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/source/Sources  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/universe/source/Sources  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/source/Sources  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/main/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/universe/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/main/binary-i386/Packages  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/binary-i386/Packages  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/universe/binary-i386/Packages  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/binary-i386/Packages  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/main/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/restricted/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/universe/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/multiverse/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/restricted/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/universe/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/multiverse/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/restricted/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/universe/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily/multiverse/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/main/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/universe/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/universe/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/universe/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/main/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/source/Sources  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/main/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/main/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 2001:67c:29f4::51 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
root@OrangePizero:~#



```

---

### Post by QIII on 2019-01-04
Hello!

Ubuntu 15.10 has long since passed its End of Life (EOL) and the repositories have been archived.  You won't be able to update it.

Instead, you will have to do a fresh install of 18.04.  I would suggest downloading and installing the [ARM server image of 18.04]("https://www.ubuntu.com/download/server/arm"), but beware that each producer of ARM SBCs may have their own specialized port and the official version from Canonical may not work on specialized hardware.

Best wishes!

---

### Post by sven20000 on 2019-01-04
Hi,

i have read some information about the EOL, but whith some changes in the sources.list i have update it to 15.10.

I want to update (instead of fresh install) so i can keep the specialized parts for my device.

Thanks

[IMG]http://www.orangepi.org/images/Pi_R1_en.jpg[/IMG]

---

### Post by CatKiller on 2019-01-04
It is possible.

You can change your sources.list to point to the graveyard that they put the old repositories. Then you should be able to upgrade to 16.04, which *is* still supported. Then upgrade from there to 18.04.

You will likely experience breakage.

Much better to do a fresh install. The Orange Pi site has images of Ubuntu 16.04 available. If you downloaded one of the x86 versions from the Ubuntu site they won't work, since you don't have an x86 processor.

---

### Post by sven20000 on 2019-01-04
> **CatKiller said:**
> 
Much better to do a fresh install. The Orange Pi site has images of Ubuntu 16.04 available.


Will that image work for the orange pi R1?

---

### Post by CatKiller on 2019-01-04
> **sven20000 said:**
> Will that image work for the orange pi R1?

I've never heard of them before today, but their website says it will.

---

### Post by fabio-oleari on 2019-06-03
Hi Sven20000,
can you please share the solution you found, to update Orange Pi R1 at least to 15.10?

Many thanks!

---

