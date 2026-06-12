---
title: "faisty latest upgrade broken"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by marekm on 2007-04-14
after faisty latest upgrade:

ld_static: fcpci/fcpci-lib.o: invalid string offset 174613362 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1852795252 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1986621045 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1635021678 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 171323703 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1853186645 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1701867372 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1081439343 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1836016430 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1953392993 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 544106861 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1818845549 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1953065059 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1919243786 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1684826485 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 673215600 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1701060652 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 691088950 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1651076141 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1651076128 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1853186677 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1042817073 >= 31509 for section `.strtab'
ld_static: fcpci/fcpci-lib.o: invalid string offset 1902274924 >= 31509 for section `.strtab'
fcpci/fcpci-lib.o: In function `no symbol':
(*ABS*+0x7265766f): multiple definition of `no symbol'
ld_static: ld_static: BFD 2.17.50 20070103 Ubuntu internal error, aborting at ../../bfd/bfd.c line 533 in _bfd_default_error_handler

ld_static: Please report this bug.

fglrx/fglrx.mod.o: file not recognized: File format not recognized
nvidia/nv-i2c.o: file not recognized: File format not recognized
WARNING: Can't read module /lib/modules/2.6.20-15-generic/volatile/fcpci.ko: Invalid argument
WARNING: Can't read module /lib/modules/2.6.20-15-generic/volatile/fcdslusb.ko: Invalid argument
Segmentation fault
dpkg: b&#322;&#261;d przetwarzania linux-restricted-modules-2.6.20-15-generic (--configure):
 podproces post-installation script zwróci&#322; kod b&#322;&#281;du 139
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie linux-restricted-modules-generic:
 linux-restricted-modules-generic zale&#380;y od linux-restricted-modules-2.6.20-15-generic; jednak&#380;e:
  Pakiet linux-restricted-modules-2.6.20-15-generic nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania linux-restricted-modules-generic (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie linux-generic:
 linux-generic zale&#380;y od linux-restricted-modules-generic; jednak&#380;e:
  Pakiet linux-restricted-modules-generic nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania linux-generic (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Konfigurowanie linux-headers-2.6.20-15 (2.6.20-15.25) ...
dpkg (podproces): nie mo&#380;na wykona&#263; post-installation script: Exec format error
dpkg: b&#322;&#261;d przetwarzania linux-headers-2.6.20-15 (--configure):
 podproces post-installation script zwróci&#322; kod b&#322;&#281;du 2
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie linux-headers-2.6.20-15-generic:
 linux-headers-2.6.20-15-generic zale&#380;y od linux-headers-2.6.20-15; jednak&#380;e:
  Pakiet linux-headers-2.6.20-15 nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania linux-headers-2.6.20-15-generic (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie linux-headers-generic:
 linux-headers-generic zale&#380;y od linux-headers-2.6.20-15-generic; jednak&#380;e:
  Pakiet linux-headers-2.6.20-15-generic nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania linux-headers-generic (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 linux-restricted-modules-2.6.20-15-generic
 linux-restricted-modules-generic
 linux-generic
 linux-headers-2.6.20-15
 linux-headers-2.6.20-15-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

what is going on? 
help needed :)

---

