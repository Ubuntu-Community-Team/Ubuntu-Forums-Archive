---
title: "Dependency mess on Jammy"
date: 2022-12-19
forum: Installation &amp; Upgrades
---

### Post by Tadaen_Sylvermane on 2022-12-19
Just did a new install via chroot. Everything is working fine save the apt packages of steam and evolution. I'm not opposed to flatpaks or snaps but it just seems odd. This is Jammy. I did add the i386 architecture to it. apt-mark showhold shows zero packages on hold.

```
apt install steam evolution

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libbsd0:i386 : Depends: libc6:i386 (>= 2.33) but it is not installable
 libgail-3-0 : Depends: libgtk-3-0 (= 3.24.33-1ubuntu1) but 3.24.33-1ubuntu2 is to be installed
 libgcc-s1:i386 : Depends: libc6:i386 (>= 2.35) but it is not installable
 libgl1:i386 : Depends: libc6:i386 (>= 2.1.3) but it is not installable
 libglvnd0:i386 : Depends: libc6:i386 (>= 2.34) but it is not installable
 libglx0:i386 : Depends: libc6:i386 (>= 2.34) but it is not installable
                Depends: libglx-mesa0:i386 but it is not installable
 libgpg-error0:i386 : Depends: libc6:i386 (>= 2.34) but it is not installable
 libmd0:i386 : Depends: libc6:i386 (>= 2.33) but it is not installable
 libstdc++6:i386 : Depends: libc6:i386 (>= 2.34) but it is not installable
 libx11-6:i386 : Depends: libc6:i386 (>= 2.34) but it is not installable
 libxau6:i386 : Depends: libc6:i386 (>= 2.33) but it is not installable
 libxcb-dri3-0:i386 : Depends: libc6:i386 (>= 2.4) but it is not installable
 libxcb1:i386 : Depends: libc6:i386 (>= 2.28) but it is not installable
 libxdmcp6:i386 : Depends: libc6:i386 (>= 2.4) but it is not installable
 libxext6:i386 : Depends: libc6:i386 (>= 2.4) but it is not installable
 libxi6:i386 : Depends: libc6:i386 (>= 2.4) but it is not installable
 libxinerama1:i386 : Depends: libc6:i386 (>= 2.4) but it is not installable
 steam:i386 : Depends: libgl1-mesa-dri:i386 (>= 17.3) but it is not installable
              Depends: libudev1:i386 but it is not installable
              Depends: libc6:i386 (>= 2.15) but it is not installable
              Recommends: libasound2-plugins:i386 but it is not installable
              Recommends: libegl1:i386 but it is not installable
              Recommends: libgbm1:i386 but it is not installable
              Recommends: libsdl2-2.0-0:i386 but it is not installable
              Recommends: libva2:i386 but it is not installable
              Recommends: libxss1:i386 but it is not installable
              Recommends: mesa-vulkan-drivers:i386 but it is not installable
              Recommends: va-driver-all:i386 but it is not installable or
                          va-driver:i386
```

No ppa's, no backports to my knowledge. Straight repository packages up to now.

```
apt install libc6:i386

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apt : Depends: adduser but it is not going to be installed
       Depends: gpgv or
                gpgv2 but it is not going to be installed or
                gpgv1 but it is not going to be installed
       Depends: libapt-pkg6.0 (>= 2.4.8) but it is not going to be installed
       Depends: libc6 (>= 2.34) but it is not installable
       Depends: libgcc-s1 (>= 3.3.1) but it is not going to be installed
       Depends: libgnutls30 (>= 3.7.0) but it is not going to be installed
       Depends: libseccomp2 (>= 2.4.2) but it is not going to be installed
       Depends: libstdc++6 (>= 11) but it is not going to be installed
       Depends: libsystemd0 but it is not going to be installed
       Recommends: ca-certificates but it is not going to be installed
 base-files : PreDepends: awk
              Depends: libc6 (>= 2.34) but it is not installable
 base-passwd : Depends: libc6 (>= 2.34) but it is not installable
               Depends: libdebconfclient0 (>= 0.145) but it is not going to be installed
 bash : PreDepends: libc6 (>= 2.34) but it is not installable
        PreDepends: libtinfo6 (>= 6) but it is not going to be installed
        Recommends: bash-completion (>= 20060301-0) but it is not going to be installed
 bsdutils : PreDepends: libc6 (>= 2.34) but it is not installable
            PreDepends: libsystemd0 but it is not going to be installed
            Recommends: bsdextrautils
 coreutils : PreDepends: libacl1 (>= 2.2.23) but it is not going to be installed
             PreDepends: libattr1 (>= 1:2.4.44) but it is not going to be installed
             PreDepends: libc6 (>= 2.34) but it is not installable
             PreDepends: libgmp10 (>= 2:6.2.1+dfsg) but it is not going to be installed
             PreDepends: libselinux1 (>= 3.1~) but it is not going to be installed
 dash : PreDepends: libc6 (>= 2.34) but it is not installable
 debianutils : PreDepends: libc6 (>= 2.34) but it is not installable
 diffutils : PreDepends: libc6 (>= 2.34) but it is not installable
 dpkg : PreDepends: libbz2-1.0 but it is not going to be installed
        PreDepends: libc6 (>= 2.34) but it is not installable
        PreDepends: liblzma5 (>= 5.2.2) but it is not going to be installed
        PreDepends: libselinux1 (>= 3.1~) but it is not going to be installed
        PreDepends: libzstd1 (>= 1.4.0) but it is not going to be installed
        PreDepends: zlib1g (>= 1:1.1.4) but it is not going to be installed
 e2fsprogs : PreDepends: libblkid1 (>= 2.36) but it is not going to be installed
             PreDepends: libc6 (>= 2.34) but it is not installable
             PreDepends: libcom-err2 (>= 1.43.9) but it is not going to be installed
             PreDepends: libext2fs2 (= 1.46.5-2ubuntu1.1) but it is not going to be installed
             PreDepends: libss2 (>= 1.38) but it is not going to be installed
             PreDepends: libuuid1 (>= 2.16) but it is not going to be installed
             Depends: logsave
             Recommends: e2fsprogs-l10n but it is not going to be installed
 findutils : PreDepends: libc6 (>= 2.34) but it is not installable
             PreDepends: libselinux1 (>= 3.1~) but it is not going to be installed
 grep : PreDepends: libc6 (>= 2.34) but it is not installable
        PreDepends: libpcre3 but it is not going to be installed
 gzip : PreDepends: libc6 (>= 2.34) but it is not installable
 hostname : PreDepends: libc6 (>= 2.34) but it is not installable
 init : PreDepends: systemd-sysv
 libc-bin : Depends: libc6 (> 2.35) but it is not installable
            Depends: libc6 (< 2.36) but it is not installable
 libcrypt1 : Depends: libc6 (>= 2.25) but it is not installable
 login : PreDepends: libaudit1 (>= 1:2.2.1) but it is not going to be installed
         PreDepends: libc6 (>= 2.34) but it is not installable
         PreDepends: libpam0g (>= 0.99.7.1) but it is not going to be installed
         PreDepends: libpam-runtime but it is not going to be installed
         PreDepends: libpam-modules but it is not going to be installed
 ncurses-bin : PreDepends: libc6 (>= 2.34) but it is not installable
               PreDepends: libtinfo6 (>= 6.3) but it is not going to be installed
 perl-base : PreDepends: libc6 (>= 2.35) but it is not installable
 sed : PreDepends: libacl1 (>= 2.2.23) but it is not going to be installed
       PreDepends: libc6 (>= 2.34) but it is not installable
       PreDepends: libselinux1 (>= 3.1~) but it is not going to be installed
 sysvinit-utils : Depends: libc6 (>= 2.34) but it is not installable
 tar : PreDepends: libacl1 (>= 2.2.23) but it is not going to be installed
       PreDepends: libc6 (>= 2.34) but it is not installable
       PreDepends: libselinux1 (>= 3.1~) but it is not going to be installed
 util-linux : PreDepends: libaudit1 (>= 1:2.2.1) but it is not going to be installed
              PreDepends: libblkid1 (>= 2.37.2) but it is not going to be installed
              PreDepends: libc6 (>= 2.34) but it is not installable
              PreDepends: libcap-ng0 (>= 0.7.9) but it is not going to be installed
              PreDepends: libmount1 (>= 2.37.2) but it is not going to be installed
              PreDepends: libpam0g (>= 0.99.7.1) but it is not going to be installed
              PreDepends: libselinux1 (>= 3.1~) but it is not going to be installed
              PreDepends: libsmartcols1 (>= 2.34) but it is not going to be installed
              PreDepends: libsystemd0 but it is not going to be installed
              PreDepends: libtinfo6 (>= 6) but it is not going to be installed
              PreDepends: libudev1 (>= 183) but it is not going to be installed
              PreDepends: libuuid1 (>= 2.16) but it is not going to be installed
              PreDepends: zlib1g (>= 1:1.1.4) but it is not going to be installed
```

---

### Post by ian-weisser on 2022-12-19
Let's see the complete output of "sudo apt update", please.

---

### Post by Tadaen_Sylvermane on 2022-12-19
```
Hit:1 http://us.archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Get:4 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [13.3 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [20.0 kB]
Get:6 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [20.0 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [13.3 kB]
Fetched 287 kB in 1s (255 kB/s)             
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
```

```
deb http://us.archive.ubuntu.com/ubuntu jammy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu jammy-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse
```

Consolidated my sources list to something easier to deal with from the default.

*EDIT*
 
Installed packages - [https://paste.ubuntu.com/p/bzf9DFHDff/](https://paste.ubuntu.com/p/bzf9DFHDff/)

---

### Post by ian-weisser on 2022-12-19
Looks like you have disabled jammy-updates. Try re-enabling it.

---

### Post by Tadaen_Sylvermane on 2022-12-19
Thought I had only removed backports. Well then solved. Thank you much. It's installing as I type this.

---

