---
title: "Upgrade to 11.04 fails"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by wurlyfan on 2011-09-02
Having upgraded my graphics card, I am trying to upgrade from 10.10 to 11.04 (after backing up my working system)! The upgrade process fails at the point of beginning the actual upgrade (after setting software channels), with the following messages:

Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb) 404  Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-js-common/gnome-js-common_0.1.2-1_all.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-js-common/gnome-js-common_0.1.2-1_all.deb) 404  Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/h/hal/libhal1_0.5.14-5+svn1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/h/hal/libhal1_0.5.14-5+svn1_i386.deb) 404  Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/h/hal/libhal-storage1_0.5.14-5+svn1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/h/hal/libhal-storage1_0.5.14-5+svn1_i386.deb) 404  Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/h/hal/hal_0.5.14-5+svn1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/h/hal/hal_0.5.14-5+svn1_i386.deb) 404  Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/i/ibus-pinyin/ibus-pinyin-db-open-phrase_1.3.11-1_all.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/i/ibus-pinyin/ibus-pinyin-db-open-phrase_1.3.11-1_all.deb) 404  Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb) 404  Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/n/nvclock/smartdimmer_0.8b4-1ubuntu6_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/n/nvclock/smartdimmer_0.8b4-1ubuntu6_i386.deb) 404  Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb) 404  Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb) 404  Not Found

The problem may be that the files in the NZ repository have slightly different names to the files the upgrader is looking for, for example:
Upgrader wants libnspr4-0d_4.8.7-0ubuntu1_i386.deb
Repository has libnspr4-0d_4.8.7-0ubuntu3_i386.deb.

I have tried using the alternate upgrade process described in [http://gerardmcgarry.com/blog/quickly-upgrade-ubuntu-1104-natty-narwhal](http://gerardmcgarry.com/blog/quickly-upgrade-ubuntu-1104-natty-narwhal), but the same thing happens, even when I choose the option not to update the installation files from the repository.

I currently have 10.10 running beautifully (well, almost!) on a fairly old i386 box (3 GHz Intel P4/3GB RAM) and have just installed an ASUS 256M GeForce 7600 GS card.

Can anyone help?

---

### Post by coffeecat on 2011-09-02
The GB repository has the libnspr4-0d_4.8.7-0ubuntu1_i386.deb package.

It could be that the NZ repository is (temporarily) inconsistent. Try changing your download server to the main server or to another country's.

**EDIT**: I've tried the main, US and Australian servers as well as the GB one for libnspr4-0d_4.8.7-0ubuntu1_i386.deb and they all offered the download. Changing the server should do the trick.

---

### Post by wurlyfan on 2011-09-02
> **coffeecat said:**
> The GB repository has the libnspr4-0d_4.8.7-0ubuntu1_i386.deb package.

It could be that the NZ repository is (temporarily) inconsistent. Try changing your download server to the main server or to another country's.

**EDIT**: I've tried the main, US and Australian servers as well as the GB one for libnspr4-0d_4.8.7-0ubuntu1_i386.deb and they all offered the download. Changing the server should do the trick.

Yep - my upgrade is now under way. Many thanks!!!!:P

---

