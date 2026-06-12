---
title: "libatlas-cpp won't install, can't continue with dist-upgrade"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by MetalHannes on 2006-06-02
Hello, I've started the dist-upgrade this morning as said in [https://wiki.ubuntu.com/DapperUpgrades]("https://wiki.ubuntu.com/DapperUpgrades") it installes fine until this message came: (I've translated it from German so the msg might not be the same as in english) > Choose not chosen package libatlas-cpp-0.6-0c2a. Unpacking libatlas-cpp-0.6-0c2a (aus .../libatlas-cpp-0.6-0c2a_0.5.98-3ubuntu1_i386.deb) ... dpkg: An error occured while editing: /var/cache/apt/archives/libatlas-cpp-0.6-0c2a_0.5.98-3ubuntu1_i386.deb (--unpack): trying to overwrite »/usr/lib/libAtlas-0.6.la« which is also in the package libatlas-cpp-0.6-0 dpkg-deb: Underprocess paste killed with the Signal (Broken pipe) Choose not chosen package libwfmath-0.3-3c2a. Unpacking libwfmath-0.3-3c2a (aus .../libwfmath-0.3-3c2a_0.3.4-4_i386.deb) ... dpkg: An error occured while editing: /var/cache/apt/archives/libwfmath-0.3-3c2a_0.3.4-4_i386.deb (--unpack): trying to overwrite »/usr/lib/libwfmath-0.3.so.3.0.3« which is also in the package Paket libwfmath-0.3c2 Preparing to replace cyphesis-cpp 0.5.1-1ubuntu1 (with .../cyphesis-cpp_0.5.5-2_i386.deb) ... Stopping cyphesis games server:/etc/init.d/cyphesis-cpp: line 27: kill: SIGTERM: invalid signal specification failed. Unpacking replacement for cyphesis-cpp ... Preparing to replace cyphesis-cpp-clients 0.5.1-1ubuntu1 (with .../cyphesis-cpp-clients_0.5.5-2_i386.deb) ... Unpacking replacement for cyphesis-cpp-clients ... An error occured while editing: /var/cache/apt/archives/libatlas-cpp-0.6-0c2a_0.5.98-3ubuntu1_i386.deb /var/cache/apt/archives/libwfmath-0.3-3c2a_0.3.4-4_i386.deb E: Sub-process /usr/bin/dpkg returned an error code (1)  After that i tried sudo apt-get -f install and that ended up with the error: > dpkg: An error occured while editing: /var/cache/apt/archives/libatlas-cpp-0.6-0c2a_0.5.98-3ubuntu1_i386.deb (--unpack): trying to overwrite »/usr/lib/libAtlas-0.6.la« which is also in the package libatlas-cpp-0.6-0 dpkg-deb: Underprocess paste killed with the Signal (Broken pipe) An error occured while editing: /var/cache/apt/archives/libatlas-cpp-0.6-0c2a_0.5.98-3ubuntu1_i386.deb E: Sub-process /usr/bin/dpkg returned an error code (1)  I can't continue with apt and my dist-upgrade. I hope i haven't pasted to much error-things(sry for my english ;) ). Thx in advance Hannes

/edit: I've tried a reboot now and now gdm won't start anymore..

Ok fixed but please don't ask how...

---

