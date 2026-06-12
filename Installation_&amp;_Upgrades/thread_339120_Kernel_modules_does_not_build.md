---
title: "Kernel modules does not build?"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by Rizado on 2007-01-15
I have a abit motherboard with uguru and as some of you probably know, lmsensors is not able to read anything from the uguru chip up until recently. In 2.6.19 there's a module called abituguru and that's why I decided to compile a new kernel. This is something I've always done before until edgy came and I was too lazy. I've done all the steps I usually do but when I run ```
sudo make-kpkg modules_image
``` it doesn't work and all I get is: ```
exec debian/rules  DEBIAN_REVISION=686  modules_image
for module in  ; do                       \
          if test -d  $module; then                                \
            (cd $module;                                          \
              if ./debian/rules KVERS="2.6.19-ck2" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="i386"                  \
                             KDREV="686" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
                 read ans;                                        \
              fi;                                                   \
             );                                                    \
          else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
          fi;                                                       \
        done
```I don't get it, why doesn't it work anymore!?

---

### Post by Rizado on 2007-06-25
Well the damn problem still exist on feisty. Does no one have any idea?

---

### Post by Rizado on 2007-11-18
I feel ashamed :oops:
What's been bugging me this last year or so wasn't really a problem because I just realized modules_image is for extra modules! Not the ones in the  kernel. I've always had extra modules like nvidia and stuff before but have gone over to the official ones.

Anyway, if anyone have the same problem, just don't use modules_image...

---

