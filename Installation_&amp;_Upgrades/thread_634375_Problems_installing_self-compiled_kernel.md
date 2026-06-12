---
title: "Problems installing self-compiled kernel"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by SveinT on 2007-12-07
Because of some SATA issues I had to compile my own kernel including a fix. The kernel is 2.6.24rc4 and it compiles as it should. However, the deb that is created won't install. I keep getting an error message:

broken filesystem / tar-archive
and then
dpkg-deb: subprocess paste killed by signal

I have tried compiling it twice, but it didn't work the second time either. Method I use is posted below.

sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
wget [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2)
wget [http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.24-rc4.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.24-rc4.bz2)
bzip2 -cd linux-2.6.23.tar.bz2 | tar xf -
cd linux-2.6.23
bzip2 -cd ../patch-2.6.24-rc4.bz2 | patch -p1
cat /home/lex/Desktop/sata_sil-irq-fix.patch | patch -p1
copy attached config file to your linux-2.6.23 folder and rename this file to .config !!! point is important !!! )
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-patched kernel_image kernel_headers
cd ..
sudo dpkg -i linux-image-2.6.24-rc4-patched_2.6.24-rc4-patched-10.00.Custom_i386.deb

---

