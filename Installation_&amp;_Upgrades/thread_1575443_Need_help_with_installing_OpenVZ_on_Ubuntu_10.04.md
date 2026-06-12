---
title: "Need help with installing OpenVZ on Ubuntu 10.04"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by M4r5h4ll on 2010-09-15
Hello,

i was trying to install that OpenVZ on my Ubuntu 10.04
i found this link on [https://help.ubuntu.com/community/OpenVZ](https://help.ubuntu.com/community/OpenVZ) & was doing exactly what it said.


till i came to this part:

Build the Kernel
sudo fakeroot make-kpkg --initrd --append-to-version=-ovz32 --revision=1.0 kernel_image kernel_headers

& i got this error


test -f debian/control || sed         -e 's/=V/2.6.32.14-ovz32/g'  \
                -e 's/=D/1.0/g'         -e 's/=A/amd64/g'  \
        -e 's/=SA//g'  \
        -e 's/=I//g'                    \
        -e 's/=CV/2.6/g'                \
        -e 's/=M/echo "CONCURRENCY_LEVEL := 2" >> /etc/kernel-pkg.conf <xxxx>/g'                \
        -e 's/=ST/linux/g'      -e 's/=B/x86_64/g'    \
                  /usr/share/kernel-package/Control > debian/control
sed: -e expression #7, char 41: unknown option to `s'
make: *** [debian/stamp/conf/minimal_debian] Error 1
Failed to create a ./debian directory: Bad file descriptor at /usr/bin/make-kpkg line 971.
root@St0rm:/usr/src/linux# 

i don't know what to do
i really need OpenVZ installed & i can't fix this error.

btw i am using a Acer Aspire 5741G laptop with inter i5 processor 430M & 4G DDR3 rams.


Thanks all

---

### Post by M4r5h4ll on 2010-09-16
Hello ? sorry guys but i need to fix this ASAP please.

Regards

---

