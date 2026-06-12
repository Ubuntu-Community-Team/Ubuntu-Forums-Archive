---
title: "Dependencies while installing audacious"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by indrajit_1 on 2011-05-18
I get the following error

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 audacious : Depends: libaudclient2 (= 2.4.4-1) but it is not going to be installed
             Depends: libaudcore1 (= 2.4.4-1) but it is not going to be installed
             Depends: libmcs1 but it is not going to be installed
             Depends: libmowgli2 (>= 0.7.0) but it is not going to be installed
 audacious-plugins : Depends: libaudcore1 (>= 2.4.3) but it is not going to be installed
                     Depends: libavcodec52 (>= 4:0.6-1~) but it is not going to be installed or
                              libavcodec-extra-52 (>= 4:0.6-1~) but it is not going to be installed
                     Depends: libavformat52 (>= 4:0.6-1~) but it is not going to be installed or
                              libavformat-extra-52 (>= 4:0.6-1~) but it is not going to be installed
                     Depends: libavutil50 (>= 4:0.6-1~) but it is not going to be installed or
                              libavutil-extra-50 (>= 4:0.6-1~) but it is not going to be installed
                     Depends: libbinio1ldbl but it is not going to be installed
                     Depends: libcddb2 but it is not going to be installed
                     Depends: libcue1 but it is not going to be installed
                     Depends: libfaad2 but it is not going to be installed
                     Depends: libfluidsynth1 but it is not going to be installed
                     Depends: libmcs1 but it is not going to be installed
                     Depends: libmms0 (>= 0.4) but it is not going to be installed
                     Depends: libmowgli2 (>= 0.7.0) but it is not going to be installed
                     Depends: libresid-builder0c2a but it is not going to be installed
                     Depends: libsidplay2 but it is not going to be installed
 google-chrome-stable : Depends: libcurl3 but it is not going to be installed
                        Depends: libnspr4-0d (>= 4.7.1) but it is not going to be installed
                        Depends: libnss3-1d (>= 3.12.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Help will be appreciated.
Indrajit Paul

---

### Post by Joe of loath on 2011-05-18
Post the output of ```
cat /etc/apt/sources.list
``` please?

---

### Post by indrajit_1 on 2011-05-18
/etc/apt/sources.list

```

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe 
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

```

I have the original problem solved. Just installed Audacious using Ubuntu Software Center.

Thanks!
Indrajit

---

