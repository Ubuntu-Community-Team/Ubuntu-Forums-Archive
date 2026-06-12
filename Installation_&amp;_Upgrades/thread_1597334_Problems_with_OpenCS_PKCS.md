---
title: "Problems with OpenCS PKCS"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by dejansoftware on 2010-10-15
Hi,

Can you help me to install OpenCS PKCS on Ubuntu 10.10  with Firefox 3.6.
I have smard card reader Gemplus

Here is error:
[HTML]dejansoftware@ubuntu:~$ pkcs11-tool --show-info
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
[opensc-pkcs11] reader-pcsc.c:906:pcsc_detect_readers: SCardEstablishContext failed: 0x8010001d
[opensc-pkcs11] reader-pcsc.c:1015:pcsc_detect_readers: returning with: No readers found
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Cryptoki version 2.20
Manufacturer     OpenSC (www.opensc-project.org)
Library          smart card PKCS#11 API (ver 0.0)
[opensc-pkcs11] reader-pcsc.c:906:pcsc_detect_readers: SCardEstablishContext failed: 0x8010001d
[opensc-pkcs11] reader-pcsc.c:1015:pcsc_detect_readers: returning with: No readers found
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
dejansoftware@ubuntu:~$ 
[/HTML]Result is the same for commands:
opensc-tool --atr
opensc-tool --name

Can you help me to set up this, I am Linux beginner.

Thanks

---

### Post by dejansoftware on 2010-10-16
Anyone, it's very important

---

