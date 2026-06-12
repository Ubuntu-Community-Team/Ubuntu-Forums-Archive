---
title: "hardy kernel compiled too big, also git way not work"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by iappia on 2008-08-18
Following [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) guide,
I succeded using the "The Old-Fashioned Debian Way",
but the kernel, in /boot dir, is very big, about 50MB.
The other versions of kernel, installed with apt-get, are about 7.5MB.
I have used the same .config.
My /boot partition is only 100MB, and so the dpkg command run out the space.
What I can do?

Then I try the git way.
I download the kernel, but I can't compile.

Here the logs:
recalcati@BT19207:~/DEVEL_BT19207/KERNEL/ubuntu-hardy$ AUTOBUILD=1 fakeroot debian/rules binary-debs
Preparing 386...
install -d /home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy/debian/build/build-386
touch /home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy/debian/build/build-386/ubuntu-build
cat /home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy/debian/config/i386/config /home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy/debian/config/i386/config.386 | sed -e 's/.*CONFIG_VERSION_SIGNATURE.*/CONFIG_VERSION_SIGNATURE="Ubuntu 2.6.24-22.41-386"/' > /home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy/debian/build/build-386/.config
find /home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy/debian/build/build-386 -name "*.ko" | xargs rm -f
make ARCH=i386 EXTRAVERSION=-22-386 SUBLEVEL=24 O=/home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy/debian/build/build-386 silentoldconfig prepare scripts
make[1]: Entering directory `/home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy'
make[3]: Nothing to be done for `/home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy/Makefile'.
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  GEN     /home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy/debian/build/build-386/Makefile
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
  Using /home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy as source for kernel
  /home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy is not clean, please run 'make mrproper'
  in the '/home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy' directory.
make[4]: *** [prepare3] Error 1
make[3]: *** [sub-make] Error 2
make[2]: *** [prepare] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy'
make: *** [/home/recalcati/DEVEL_BT19207/KERNEL/ubuntu-hardy/debian/stamps/stamp-prepare-386] Error 2

If I do mrproper the debian directory disappear and I have to download it again with git.

Again, what I can do?

---

