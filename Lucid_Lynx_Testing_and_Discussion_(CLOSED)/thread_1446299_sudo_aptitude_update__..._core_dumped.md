---
title: "sudo aptitude update  ... core dumped"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by boondocks on 2010-04-03
I got "ubuntu-10.04-beta1-[COLOR="Red"]server[/COLOR]-amd64.iso" up and running.

After the installation, I did:
[COLOR="Blue"]sudo aptitude clean 
sudo aptitude update 
sudo aptitude safe-upgrade[/COLOR]  

Everything was fine.
So I thought I would install atop.

A few hours later:
[COLOR="Blue"]sudo aptitude clean[/COLOR] 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```
[COLOR="Blue"]sudo aptitude update[/COLOR] 
```
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,370kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,229B]                                                   
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [648kB]                                                           
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,763B]                                                    
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,454kB]                                                    
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,188kB]                                                     
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [175kB]                                                    
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [117kB]              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources                                                       
Fetched 11.0MB in 1min 18s (140kB/s)                                                                                    
*** glibc detected *** aptitude: free(): invalid next size (fast): 0x00000000021c1360 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f39c2c2a5b6]
/lib/libc.so.6(cfree+0x73)[0x7f39c2c30e53]
aptitude[0x526aa9]
aptitude[0x5459ed]
aptitude[0x542fb7]
aptitude[0x506297]
aptitude[0x501f1d]
aptitude[0x41bb76]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f39c2bd1c4d]
aptitude[0x419619]
======= Memory map: ========
00400000-00626000 r-xp 00000000 08:01 266704                             /usr/bin/aptitude
00825000-00826000 r--p 00225000 08:01 266704                             /usr/bin/aptitude
00826000-00828000 rw-p 00226000 08:01 266704                             /usr/bin/aptitude
00828000-0082c000 rw-p 00000000 00:00 0 
01f2c000-02220000 rw-p 00000000 00:00 0                                  [heap]
7f39b8000000-7f39b8021000 rw-p 00000000 00:00 0 
7f39b8021000-7f39bc000000 ---p 00000000 00:00 0 
7f39bfc24000-7f39bfc25000 ---p 00000000 00:00 0 
7f39bfc25000-7f39c05f2000 rw-p 00000000 00:00 0 
7f39c07b5000-7f39c1265000 rw-p 00000000 00:00 0 
7f39c1265000-7f39c1f71000 rw-p 00000000 08:01 7602188                    /var/cache/apt/pkgcache.bin
7f39c1f71000-7f39c1f7d000 r-xp 00000000 08:01 1314840                    /lib/libnss_files-2.11.1.so
7f39c1f7d000-7f39c217c000 ---p 0000c000 08:01 1314840                    /lib/libnss_files-2.11.1.so
7f39c217c000-7f39c217d000 r--p 0000b000 08:01 1314840                    /lib/libnss_files-2.11.1.so
7f39c217d000-7f39c217e000 rw-p 0000c000 08:01 1314840                    /lib/libnss_files-2.11.1.so
7f39c217e000-7f39c2188000 r-xp 00000000 08:01 1314842                    /lib/libnss_nis-2.11.1.so
7f39c2188000-7f39c2387000 ---p 0000a000 08:01 1314842                    /lib/libnss_nis-2.11.1.so
7f39c2387000-7f39c2388000 r--p 00009000 08:01 1314842                    /lib/libnss_nis-2.11.1.so
7f39c2388000-7f39c2389000 rw-p 0000a000 08:01 1314842                    /lib/libnss_nis-2.11.1.so
7f39c2389000-7f39c23a0000 r-xp 00000000 08:01 1314837                    /lib/libnsl-2.11.1.so
7f39c23a0000-7f39c259f000 ---p 00017000 08:01 1314837                    /lib/libnsl-2.11.1.so
7f39c259f000-7f39c25a0000 r--p 00016000 08:01 1314837                    /lib/libnsl-2.11.1.so
7f39c25a0000-7f39c25a1000 rw-p 00017000 08:01 1314837                    /lib/libnsl-2.11.1.so
7f39c25a1000-7f39c25a3000 rw-p 00000000 00:00 0 
7f39c25a3000-7f39c25ab000 r-xp 00000000 08:01 1314838                    /lib/libnss_compat-2.11.1.so
7f39c25ab000-7f39c27aa000 ---p 00008000 08:01 1314838                    /lib/libnss_compat-2.11.1.so
7f39c27aa000-7f39c27ab000 r--p 00007000 08:01 1314838                    /lib/libnss_compat-2.11.1.so
7f39c27ab000-7f39c27ac000 rw-p 00008000 08:01 1314838                    /lib/libnss_compat-2.11.1.so
7f39c27ac000-7f39c27ae000 r-xp 00000000 08:01 1314834                    /lib/libdl-2.11.1.so
7f39c27ae000-7f39c29ae000 ---p 00002000 08:01 1314834                    /lib/libdl-2.11.1.so
7f39c29ae000-7f39c29af000 r--p 00002000 08:01 1314834                    /lib/libdl-2.11.1.so
7f39c29af000-7f39c29b0000 rw-p 00003000 08:01 1314834                    /lib/libdl-2.11.1.so
7f39c29b0000-7f39c29b2000 r-xp 00000000 08:01 1314850                    /lib/libutil-2.11.1.so
7f39c29b2000-7f39c2bb1000 ---p 00002000 08:01 1314850                    /lib/libutil-2.11.1.so
7f39c2bb1000-7f39c2bb2000 r--p 00001000 08:01 1314850                    /lib/libutil-2.11.1.so
7f39c2bb2000-7f39c2bb3000 rw-p 00002000 08:01 1314850                    /lib/libutil-2.11.1.so
7f39c2bb3000-7f39c2d2b000 r-xp 00000000 08:01 1314831                    /lib/libc-2.11.1.so
7f39c2d2b000-7f39c2f2b000 ---p 00178000 08:01 1314831                    /lib/libc-2.11.1.so
7f39c2f2b000-7f39c2f2f000 r--p 00178000 08:01 1314831                    /lib/libc-2.11.1.so
7f39c2f2f000-7f39c2f30000 rw-p 0017c000 08:01 1314831                    /lib/libc-2.11.1.so
7f39c2f30000-7f39c2f35000 rw-p 00000000 00:00 0 
7f39c2f35000-7f39c2f4b000 r-xp 00000000 08:01 1310732                    /lib/libgcc_s.so.1
7f39c2f4b000-7f39c314a000 ---p 00016000 08:01 1310732                    /lib/libgcc_s.so.1
7f39c314a000-7f39c314b000 r--p 00015000 08:01 1310732                    /lib/libgcc_s.so.1
7f39c314b000-7f39c314c000 rw-p 00016000 08:01 1310732                    /lib/libgcc_s.so.1
7f39c314c000-7f39c31ce000 r-xp 00000000 08:01 1314835                    /lib/libm-2.11.1.so
7f39c31ce000-7f39c33cd000 ---p 00082000 08:01 1314835                    /lib/libm-2.11.1.so
7f39c33cd000-7f39c33ce000 r--p 00081000 08:01 1314835                    /lib/libm-2.11.1.so
7f39c33ce000-7f39c33cf000 rw-p 00082000 08:01 1314835                    /lib/libm-2.11.1.so
7f39c33cf000-7f39c34c5000 r-xp 00000000 08:01 263079                     /usr/lib/libstdc++.so.6.0.13
7f39c34c5000-7f39c36c5000 ---p 000f6000 08:01 263079                     /usr/lib/libstdc++.so.6.0.13
7f39c36c5000-7f39c36cc000 r--p 000f6000 08:01 263079                     /usr/lib/libstdc++.so.6.0.13
7f39c36cc000-7f39c36ce000 rw-p 000fd000 08:01 263079                     /usr/lib/libstdc++.so.6.0.13
7f39c36ce000-7f39c36e3000 rw-p 00000000 00:00 0 
7f39c36e3000-7f39c36fb000 r-xp 00000000 08:01 1314845                    /lib/libpthread-2.11.1.so
7f39c36fb000-7f39c38fa000 ---p 00018000 08:01 1314845                    /lib/libpthread-2.11.1.so
7f39c38fa000-7f39c38fb000 r--p 00017000 08:01 1314845                    /lib/libpthread-2.11.1.so
7f39c38fb000-7f39c38fc000 rw-p 00018000 08:01 1314845                    /lib/libpthread-2.11.1.so
7f39c38fc000-7f39c3900000 rw-p 00000000 00:00 0 
7f39c3900000-7f39c3916000 r-xp 00000000 08:01 1310937                    /lib/libz.so.1.2.3.3
7f39c3916000-7f39c3b15000 ---p 00016000 08:01 1310937                    /lib/libz.so.1.2.3.3
7f39c3b15000-7f39c3b16000 r--p 00015000 08:01 1310937                    /lib/libz.so.1.2.3.3
7f39c3b16000-7f39c3b17000 rw-p 00016000 08:01 1310937                    /lib/libz.so.1.2.3.3
7f39c3b17000-7f39c3c5d000 r-xp 00000000 08:01 271705                     /usr/lib/libxapian.so.15.6.9
7f39c3c5d000-7f39c3e5c000 ---p 00146000 08:01 271705                     /usr/lib/libxapian.so.15.6.9
7f39c3e5c000-7f39c3e62000 r--p 00145000 08:01 271705                     /usr/lib/libxapian.so.15.6.9
7f39c3e62000-7f39c3e63000 rw-p 0014b000 08:01 271705                     /usr/lib/libxapian.so.15.6.9
7f39c3e63000-7f39c3ed4000 r-xp 00000000 08:01 267617                     /usr/lib/libept.so.0.5.30
Aborted (core dumped)
```

Is there anything I should do here?

---

### Post by VMC on 2010-04-03
This bug has been around with a log of comments. Add a "-q" to aptitude. Apparently size matters, when it comes to aptitude. Odd size terminal screens causes aptitude to create core dumps.

There's several bugs open on aptitude crashing. Here's one about "glibc detected" . [[COLOR="Blue"]**_Bug#515525_**[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/515525")

Edit: Changed bug report number. There is a lot of duplicates!

---

### Post by boondocks on 2010-04-03
> **VMC said:**
> This bug has been around with a log of comments. Add a "-q" to aptitude. Apparently size matters, when it comes to aptitude. Odd size terminal screens causes aptitude to create core dumps.

There's several bugs open on aptitude crashing. Here's one about "glibc detected" . [**_Bug#423074_**]("https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/423074")

Thank you.
The "-q" took care of it.

Does this impact the installation of a package?

Before trying the "-q", I got a core dump when I did:
 [COLOR="Blue"]sudo  aptitude install atop[/COLOR]
It looks like the atop command is working fine.
But I am wondering - was the package was installed properly?

---

### Post by VMC on 2010-04-03
> **boondocks said:**
> Thank you.
The "-q" took care of it.

Does this impact the installation of a package?

Before trying the "-q", I got a core dump when I did:
 [COLOR="Blue"]sudo  aptitude install atop[/COLOR]
It looks like the atop command is working fine.
But I am wondering - was the package was installed properly?
You could try a *reinstall* to be safe, but those crashes usually occur after the install is completed.

---

### Post by Regenweald on 2010-04-03
Thanks for the info VMC, in the meanwhile I use apt-get. Although as you said and in my case, the crash does not affect package install.

---

