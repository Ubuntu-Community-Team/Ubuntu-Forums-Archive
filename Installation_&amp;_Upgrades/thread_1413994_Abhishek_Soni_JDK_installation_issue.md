---
title: "Abhishek Soni JDK installation issue"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by abhisheksoni on 2010-02-23
Hi,

I had downloded Sun Java EE + Sun java 6 U18 SDK from the Sun web site. While I tried to install this pacakage, it gave an error, as given below. I even tried to give
"export MALLOC_CHECK_=0" before executing the bin file but this too is not working, anybody who knows the solution please help me in installing this. I am using Ubuntu Linux Alternate 9.04 on PIII 256 MB + 64 MB RAM and 20GB Hdisk.

soni@soni:~/JDK6$ sudo ./java_ee_sdk-5_08-jdk-6u18-linux.bin 
[sudo] password for soni: 
Checking available disk space...
Checking Java(TM) 2 Runtime Environment...
Extracting Java(TM) 2 Runtime Environment files...
*** glibc detected *** ./java_ee_sdk-5_08-jdk-6u18-linux.bin: double free or corruption (!prev): 0x082c72c0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e66604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7e685b6]
./java_ee_sdk-5_08-jdk-6u18-linux.bin(GetPublicJREPath+0x6df)[0x8054269]
./java_ee_sdk-5_08-jdk-6u18-linux.bin(main+0x8f:cool:[0x804e37c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7e0d775]
./java_ee_sdk-5_08-jdk-6u18-linux.bin(dlopen+0x41)[0x804c9f5]
======= Memory map: ========
08048000-08061000 r-xp 00000000 08:06 12359      /home/soni/JDK6/java_ee_sdk-5_08-jdk-6u18-linux.bin
.
.
.
(memory map/dump not given fully by me)

Thanks and Regards,
Abhishek Soni.

---

