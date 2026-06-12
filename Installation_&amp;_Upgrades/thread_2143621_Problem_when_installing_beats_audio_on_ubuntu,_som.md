---
title: "Problem when installing beats audio on ubuntu, somebody knows how to fix it."
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by ajsalmeida17 on 2013-05-09
Hello everyone, I was trying to install teh beats audio on ubuntu 13.04 by this post:
[http://droid-hive.com/index.php?/topic/919-how-to-beats-audio-with-alsa-dv7-eoslubuntu/](http://droid-hive.com/index.php?/topic/919-how-to-beats-audio-with-alsa-dv7-eoslubuntu/)

So...when i was installing, apears to me this little problem, but until this moment, i can't find a way to fix it . So the error is the following:
[COLOR=#ff0000]
*Please install the package with full kernel sources for your distribution*[/COLOR]
More details:
> 
checking for kernel linux/version.h ... no
The file /usr/src/linux-headers-3.8.0-19-generic/include/INCLUDE_VERSION_H does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/3.8.0-19-generic/build).

If somebody knows how to solve this problem...
thank's:)

---

### Post by WTF_Shelley on 2013-05-09
try

sudo apt-get install kernel-headers-generic

then try installing the package again

---

### Post by ajsalmeida17 on 2013-05-09
Ok, but, it does'nt worked, i think that is another problem, when i try it, this mesage apears:
> 
ajsalmeida @ anubis: ~ / Downloads $ sudo apt-get install kernel-headers-generic
Reading package lists ... ready
Building dependency tree
Reading state information ... ready
E: Could not find package kernel-headers-generic


---

### Post by WTF_Shelley on 2013-05-09
thats odd, try

sudo apt-get update

first.  maybe you need to update apts package catalogue.

Also installing a new version of alsa, is serious business which can cause all kinds of problems.  i would report the missing support for your hardware as a bug and see if ubuntu can patch it in instead of installing random versios of deep level code.

---

### Post by Cheesemill on 2013-05-09
Try this command to install the kernel headers...
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by ajsalmeida17 on 2013-05-09
After run sudo apt-get update :
I did:

> 
ajsalmeida @ anubis: ~ / Downloads $ sudo apt-get install linux-headers-$ (uname-r)
Reading package lists ... ready
Building dependency tree
Reading state information ... ready
linux-headers-3.8.0-19-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


 sudo ./AlsaUpgrade-1.0.25-3.sh -c   :




And try another time to install
> 
The file /usr/src/linux-headers-3.8.0-19-generic/include/INCLUDE_VERSION_H does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/3.8.0-19-generic/build).

***************************************************************************
*  alsa-driver-1.0.25 configure failed
***************************************************************************





---

### Post by ajsalmeida17 on 2013-05-10
Realy? Nobody knows? i realy don't know what's hapenning... i doing everything right but it does'nt work.
Somebody think that if i reconpile the kernel, it will work?

---

### Post by preetammn on 2014-04-18
I fixed with the below hack in "configure" of the "alsa-driver-1.0.25+dfsgalsa-driver-1.0.25+dfsg"



#  INCLUDE_VERSION_H="linux/version.h"
  INCLUDE_VERSION_H="generated/uapi/linux/version.h"
  { $as_echo "$as_me:${as_lineno-$LINENO}: checking for kernel ${INCLUDE_VERSION_H} " >&5
$as_echo_n "checking for kernel ${INCLUDE_VERSION_H} ... " >&6; }
  if ! test -s $CONFIG_SND_KERNELDIR/include/$INCLUDE_VERSION_H; then
    if test -z "$kernelbuild" -o ! -s $kernelbuild/include/$INCLUDE_VERSION_H; then
      if test -n ""; then
    INCLUDE_VERSION_H=""
    if ! test -s $CONFIG_SND_KERNELDIR/include/; then
      if test -z "$kernelbuild" -o ! -s $kernelbuild/include/; then
        { $as_echo "$as_me:${as_lineno-$LINENO}: result: no" >&5
$as_echo "no" >&6; }
        cat << EOF
The file $CONFIG_SND_KERNELDIR/include/$INCLUDE_VERSION_H does not exist.
The file $CONFIG_SND_KERNELDIR/include/ does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is $DEFAULT_KERNEL_DIR).
EOF
        exit 1
      fi
    fi
      else
        { $as_echo "$as_me:${as_lineno-$LINENO}: result: no" >&5
$as_echo "no" >&6; }
        cat << EOF
The file $CONFIG_SND_KERNELDIR/include/$INCLUDE_VERSION_H does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is $DEFAULT_KERNEL_DIR).
EOF
        exit 1
      fi
    fi
  fi
  { $as_echo "$as_me:${as_lineno-$LINENO}: result: $INCLUDE_VERSION_H" >&5
$as_echo "$INCLUDE_VERSION_H" >&6; }

---

