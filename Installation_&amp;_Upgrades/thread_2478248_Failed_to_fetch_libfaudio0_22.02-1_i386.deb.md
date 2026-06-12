---
title: "Failed to fetch libfaudio0_22.02-1_i386.deb"
date: 2022-08-21
forum: Installation &amp; Upgrades
---

### Post by wy7305e on 2022-08-21
```
dpkg --add-architecture i386
apt-get update --fix-missing
apt-get install -y libfaudio0:i386

```

```
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 gcc-12-base i386 12-20220319-1ubuntu1 [18.9 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libgcc-s1 i386 12-20220319-1ubuntu1 [64.7 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libcrypt1 i386 1:4.4.27-1 [97.2 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libc6 amd64 2.35-0ubuntu3.1 [3235 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libc6 i386 2.35-0ubuntu3.1 [3013 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libcap2 i386 1:2.44-1build3 [19.0 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libgpg-error0 i386 1.43-3 [78.0 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libgcrypt20 i386 1.9.4-3ubuntu3 [493 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 liblz4-1 i386 1.9.3-2build2 [62.8 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 liblzma5 i386 5.2.5-2ubuntu1 [105 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libzstd1 i386 1.4.8+dfsg-3build1 [317 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libsystemd0 i386 249.11-0ubuntu3.4 [339 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 uuid-runtime amd64 2.37.2-4ubuntu3 [32.2 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libcom-err2 amd64 1.46.5-2ubuntu1.1 [9158 B]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libssl3 amd64 3.0.2-0ubuntu1.6 [1900 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libtirpc-common all 1.3.2-2ubuntu0.1 [7766 B]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libtirpc3 amd64 1.3.2-2ubuntu0.1 [82.3 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libblkid1 i386 2.37.2-4ubuntu3 [166 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libcom-err2 i386 1.46.5-2ubuntu1.1 [9614 B]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libkrb5support0 i386 1.19.2-2 [37.0 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libk5crypto3 i386 1.19.2-2 [91.1 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libkeyutils1 i386 1.6.1-2ubuntu3 [10.7 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libssl3 i386 3.0.2-0ubuntu1.6 [1941 kB]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libkrb5-3 i386 1.19.2-2 [403 kB]
Get:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libgssapi-krb5-2 i386 1.19.2-2 [154 kB]
Get:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libpcre2-8-0 i386 10.39-3build1 [221 kB]
Get:27 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libselinux1 i386 3.3-1build2 [80.2 kB]
Get:28 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libmount1 i386 2.37.2-4ubuntu3 [179 kB]
Get:29 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libtirpc3 i386 1.3.2-2ubuntu0.1 [92.8 kB]
Get:30 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libnsl2 i386 1.3.0-2build2 [46.2 kB]
Get:31 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libpcre3 i386 2:8.39-13ubuntu0.22.04.1 [245 kB]
Get:32 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libuuid1 i386 2.37.2-4ubuntu3 [25.8 kB]
Get:33 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 zlib1g i386 1:1.2.11.dfsg-2ubuntu9 [60.5 kB]
Get:34 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libapparmor1 i386 3.0.4-2ubuntu2.1 [40.6 kB]
Get:35 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libmd0 i386 1.0.4-1build1 [23.8 kB]
Get:36 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libbsd0 i386 0.11.5-1 [48.3 kB]
Get:37 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libdbus-1-3 i386 1.12.20-2ubuntu4 [206 kB]
Get:38 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libexpat1 i386 2.4.7-1 [92.2 kB]
Get:39 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libffi8 i386 3.4.2-4 [20.7 kB]
Get:40 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libfribidi0 i386 1.0.8-2ubuntu3.1 [26.6 kB]
Get:41 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libglib2.0-0 i386 2.72.1-1 [1565 kB]
Get:42 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libunistring2 i386 1.0-1 [554 kB]
Get:43 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libidn2-0 i386 2.3.2-2build1 [71.1 kB]
Get:44 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libstdc++6 i386 12-20220319-1ubuntu1 [757 kB]
Get:45 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libdrm2 i386 2.4.110-1ubuntu1 [41.5 kB]
Get:46 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libpng16-16 i386 1.6.37-3build5 [196 kB]
Get:47 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxau6 i386 1:1.0.9-1build5 [7924 B]
Get:48 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxdmcp6 i386 1:1.1.3-0ubuntu5 [11.4 kB]
Get:49 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxcb1 i386 1.14-3ubuntu3 [55.4 kB]
Get:50 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libx11-6 i386 2:1.7.5-1 [692 kB]
Get:51 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxext6 i386 2:1.3.4-1build1 [34.8 kB]
Get:52 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 krb5-locales all 1.19.2-2 [11.8 kB]
Get:53 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libasound2 i386 1.2.6.1-1ubuntu1 [420 kB]
Get:54 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libasyncns0 i386 0.8-6build2 [13.3 kB]
Get:55 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libbrotli1 i386 1.0.9-2build6 [321 kB]
Get:56 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libfreetype6 i386 2.11.1+dfsg-1ubuntu0.1 [403 kB]
Get:57 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libfontconfig1 i386 2.13.1-4.2ubuntu5 [140 kB]
Get:58 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libpixman-1-0 i386 0.40.0-1build4 [265 kB]
Get:59 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxcb-render0 i386 1.14-3ubuntu3 [17.5 kB]
Get:60 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxcb-shm0 i386 1.14-3ubuntu3 [5958 B]
Get:61 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxrender1 i386 1:0.9.10-1build4 [21.0 kB]
Get:62 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libcairo2 i386 1.16.0-5ubuntu2 [689 kB]
Get:63 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libdatrie1 i386 0.2.13-2 [22.5 kB]
Get:64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libwayland-client0 i386 1.20.0-1 [28.1 kB]
Get:65 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libdecor-0-0 i386 0.1.0-3build1 [15.6 kB]
Get:66 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libgraphite2-3 i386 1.3.14-1build2 [80.2 kB]
Get:67 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libharfbuzz0b i386 2.7.4-1ubuntu3.1 [397 kB]
Get:68 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libthai0 i386 0.1.29-1build1 [20.6 kB]
Get:69 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libpango-1.0-0 i386 1.50.6+ds-2 [240 kB]
Get:70 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libpangoft2-1.0-0 i386 1.50.6+ds-2 [58.0 kB]
Get:71 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libpangocairo-1.0-0 i386 1.50.6+ds-2 [41.5 kB]
Get:72 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libwayland-cursor0 i386 1.20.0-1 [12.3 kB]
Get:73 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libdecor-0-plugin-1-cairo i386 0.1.0-3build1 [21.9 kB]
Get:74 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libwayland-server0 i386 1.20.0-1 [37.3 kB]
Get:75 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libgbm1 i386 22.0.5-0ubuntu0.1 [34.2 kB]
Get:76 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libogg0 i386 1.3.5-0ubuntu3 [23.6 kB]
Get:77 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libflac8 i386 1.3.3-2build2 [109 kB]
Get:78 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libopus0 i386 1.3.1-0.1build2 [204 kB]
Get:79 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libvorbis0a i386 1.3.7-1build2 [97.6 kB]
Get:80 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libvorbisenc2 i386 1.3.7-1build2 [76.3 kB]
Get:81 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libsndfile1 i386 1.0.31-2build1 [227 kB]
Get:82 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libx11-xcb1 i386 2:1.7.5-1 [7818 B]
Get:83 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libpulse0 i386 1:15.99.1+dfsg1-1ubuntu1 [296 kB]
Get:84 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libwayland-egl1 i386 1.20.0-1 [5704 B]
Get:85 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxfixes3 i386 1:6.0.0-1 [12.4 kB]
Get:86 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxcursor1 i386 1:1.2.0-2build4 [22.8 kB]
Get:87 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxi6 i386 2:1.8-1build1 [35.6 kB]
Get:88 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxinerama1 i386 2:1.1.4-3 [7606 B]
Get:89 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxkbcommon0 i386 1.4.0-1 [128 kB]
Get:90 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxrandr2 i386 2:1.5.2-1build1 [21.9 kB]
Get:91 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxss1 i386 1:1.2.3-1build2 [8838 B]
Get:92 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libxxf86vm1 i386 1:1.1.4-1build3 [11.3 kB]
Get:93 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libsdl2-2.0-0 i386 2.0.20+dfsg-2ubuntu1.22.04.1 [607 kB]
Ign:93 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libsdl2-2.0-0 i386 2.0.20+dfsg-2ubuntu1.22.04.1
Get:94 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/universe i386 libstb0 i386 0.0~git20210910.af1a5bc+ds-1 [229 kB]
Ign:95 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/universe i386 libfaudio0 i386 22.02-1
Get:96 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 libgpg-error-l10n all 1.43-3 [7134 B]
Get:97 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libnss-nis i386 3.1-0ubuntu6 [28.2 kB]
Get:98 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 libnss-nisplus i386 1.3-0ubuntu6 [23.7 kB]
Get:93 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libsdl2-2.0-0 i386 2.0.20+dfsg-2ubuntu1.22.04.1 [607 kB]
Ign:95 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/universe i386 libfaudio0 i386 22.02-1
Ign:95 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/universe i386 libfaudio0 i386 22.02-1
Err:95 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/universe i386 libfaudio0 i386 22.02-1
  Connection failed [IP: 91.189.91.38 80]
Fetched 23.5 MB in 55s (429 kB/s)                                              
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/f/faudio/libfaudio0_22.02-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/f/faudio/libfaudio0_22.02-1_i386.deb)  Connection failed [IP: 91.189.91.38 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
The command '/bin/sh -c apt-get install -y libfaudio0:i386' returned a non-zero code: 100
```

---

