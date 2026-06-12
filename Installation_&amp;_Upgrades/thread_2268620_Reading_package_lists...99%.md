---
title: "Reading package lists...99%"
date: 2015-03-10
forum: Installation &amp; Upgrades
---

### Post by albert29 on 2015-03-10
Hello everyone,
I'm having a problem when executing apt-get update on a virtual machine using Virtualbox. My host is Ubuntu Server 14.04LTS 64 bits and I'm running a Ubuntu 12.04LTS 64 bits VM. I don't get any error message, but the command gets stuck at "Reading package lists...99%". It can stay like this for more than a minute before it ends. 

If I execute "time -p apt-get update", I get this output: 

```
Ign http://security.ubuntu.com precise-security InRelease
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://security.ubuntu.com precise-security Release [53.0 kB]
Ign http://us.archive.ubuntu.com precise InRelease 
Ign http://us.archive.ubuntu.com precise-updates InRelease
Ign http://us.archive.ubuntu.com precise-backports InRelease
Get:3 http://us.archive.ubuntu.com precise Release.gpg [198 B]
Get:4 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:5 http://security.ubuntu.com precise-security/main Sources [124 kB]
Get:6 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]
Get:7 http://us.archive.ubuntu.com precise Release [49.6 kB]
Get:8 http://security.ubuntu.com precise-security/restricted Sources [3,759 B] 
Get:9 http://security.ubuntu.com precise-security/universe Sources [33.8 kB]        
Get:10 http://security.ubuntu.com precise-security/multiverse Sources [1,819 B]     
Get:11 http://security.ubuntu.com precise-security/main amd64 Packages [487 kB]
Get:12 http://us.archive.ubuntu.com precise-updates Release [194 kB]                       
Get:13 http://security.ubuntu.com precise-security/restricted amd64 Packages [8,943 B]                        
Get:14 http://security.ubuntu.com precise-security/universe amd64 Packages [107 kB]     
Get:15 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,460 B] 
Get:16 http://security.ubuntu.com precise-security/main i386 Packages [527 kB]         
Get:17 http://us.archive.ubuntu.com precise-backports Release [53.1 kB]               
Get:18 http://security.ubuntu.com precise-security/restricted i386 Packages [8,939 B]                               
Get:19 http://security.ubuntu.com precise-security/universe i386 Packages [114 kB]                                
Get:20 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,651 B]                            
Get:21 http://security.ubuntu.com precise-security/main TranslationIndex [208 B]
Get:22 http://security.ubuntu.com precise-security/multiverse TranslationIndex [199 B]
Get:23 http://security.ubuntu.com precise-security/restricted TranslationIndex [202 B]          
Get:24 http://security.ubuntu.com precise-security/universe TranslationIndex [205 B]            
Get:25 http://us.archive.ubuntu.com precise/main Sources [934 kB]                               
Get:26 http://security.ubuntu.com precise-security/main Translation-en [216 kB]                         
Get:27 http://security.ubuntu.com precise-security/multiverse Translation-en [1,299 B]          
Get:28 http://security.ubuntu.com precise-security/restricted Translation-en [2,066 B]
Get:29 http://security.ubuntu.com precise-security/universe Translation-en [65.3 kB]
Get:30 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]                     
Get:31 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]
Get:32 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]                                                                                                                                                                                                      
Get:33 http://us.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]                                                                                                                                                                                                   
Get:34 http://us.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]                                                                                                                                                                                              
Get:35 http://us.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]                                                                                                                                                                                               
Get:36 http://us.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]                                                                                                                                                                                               
Get:37 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]                                                                                                                                                                                                    
Get:38 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]                                                                                                                                                                                               
Get:39 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]                                                                                                                                                                                                
Get:40 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                                                                                                                                                                                
Get:41 http://us.archive.ubuntu.com precise/main TranslationIndex [3,706 B]                                                                                                                                                                                                  
Get:42 http://us.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]                                                                                                                                                                                            
Get:43 http://us.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]                                                                                                                                                                                            
Get:44 http://us.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]                                                                                                                                                                                              
Get:45 http://us.archive.ubuntu.com precise-updates/main Sources [486 kB]                                                                                                                                                                                                    
Get:46 http://us.archive.ubuntu.com precise-updates/restricted Sources [7,981 B]                                                                                                                                                                                             
Get:47 http://us.archive.ubuntu.com precise-updates/universe Sources [112 kB]                                                                                                                                                                                                
Get:48 http://us.archive.ubuntu.com precise-updates/multiverse Sources [9,390 B]                                                                                                                                                                                             
Get:49 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [879 kB]                                                                                                                                                                                             
Get:50 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.6 kB]                                                                                                                                                                                      
Get:51 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [254 kB]                                                                                                                                                                                         
Get:52 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [16.4 kB]                                                                                                                                                                                      
Get:53 http://us.archive.ubuntu.com precise-updates/main i386 Packages [915 kB]                                                                                                                                                                                              
Get:54 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.6 kB]                                                                                                                                                                                       
Get:55 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [262 kB]                                                                                                                                                                                          
Get:56 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [16.6 kB]                                                                                                                                                                                       
Get:57 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [10.6 kB]                                                                                                                                                                                          
Get:58 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [7,613 B]                                                                                                                                                                                    
Get:59 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [7,297 B]                                                                                                                                                                                    
Get:60 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [8,333 B]                                                                                                                                                                                      
Get:61 http://us.archive.ubuntu.com precise-backports/main Sources [5,411 B]                                                                                                                                                                                                 
Get:62 http://us.archive.ubuntu.com precise-backports/restricted Sources [28 B]                                                                                                                                                                                              
Get:63 http://us.archive.ubuntu.com precise-backports/universe Sources [41.3 kB]                                                                                                                                                                                             
Get:64 http://us.archive.ubuntu.com precise-backports/multiverse Sources [5,750 B]                                                                                                                                                                                           
Get:65 http://us.archive.ubuntu.com precise-backports/main amd64 Packages [5,491 B]                                                                                                                                                                                          
Get:66 http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages [28 B]                                                                                                                                                                                       
Get:67 http://us.archive.ubuntu.com precise-backports/universe amd64 Packages [43.4 kB]                                                                                                                                                                                      
Get:68 http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages [5,419 B]                                                                                                                                                                                    
Get:69 http://us.archive.ubuntu.com precise-backports/main i386 Packages [5,484 B]                                                                                                                                                                                           
Get:70 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [28 B]                                                                                                                                                                                        
Get:71 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [43.2 kB]                                                                                                                                                                                       
Get:72 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,413 B]                                                                                                                                                                                     
Get:73 http://us.archive.ubuntu.com precise-backports/main TranslationIndex [202 B]                                                                                                                                                                                          
Get:74 http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex [202 B]                                                                                                                                                                                    
Get:75 http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex [193 B]                                                                                                                                                                                    
Get:76 http://us.archive.ubuntu.com precise-backports/universe TranslationIndex [205 B]                                                                                                                                                                                      
Get:77 http://us.archive.ubuntu.com precise/main Translation-en [726 kB]                                                                                                                                                                                                     
Get:78 http://us.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]                                                                                                                                                                                              
Get:79 http://us.archive.ubuntu.com precise/restricted Translation-en [2,395 B]                                                                                                                                                                                              
Get:80 http://us.archive.ubuntu.com precise/universe Translation-en [3,341 kB]                                                                                                                                                                                               
Get:81 http://us.archive.ubuntu.com precise-updates/main Translation-en [386 kB]                                                                                                                                                                                             
Get:82 http://us.archive.ubuntu.com precise-updates/multiverse Translation-en [9,533 B]                                                                                                                                                                                      
Get:83 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [2,982 B]                                                                                                                                                                                      
Get:84 http://us.archive.ubuntu.com precise-updates/universe Translation-en [148 kB]                                                                                                                                                                                         
Get:85 http://us.archive.ubuntu.com precise-backports/main Translation-en [4,911 B]                                                                                                                                                                                          
Get:86 http://us.archive.ubuntu.com precise-backports/multiverse Translation-en [4,838 B]                                                                                                                                                                                    
Get:87 http://us.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]                                                                                                                                                                                       
Get:88 http://us.archive.ubuntu.com precise-backports/universe Translation-en [34.4 kB]                                                                                                                                                                                      
Fetched 28.5 MB in 18s (1,558 kB/s)                                                                                                                                                                                                                                          
Reading package lists... Done


real    1m37.418s
user    0m6.416s
sys    0m11.349s


```



And this is the output of strace -c:
```

% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 47.55    0.104006       26002         4           msync
 20.91    0.045730         159       287           write
 14.63    0.032002       16001         2           fsync
  8.26    0.018070           4      4719           read
  3.66    0.008001        1143         7         5 unlink
  1.83    0.004001          48        84           select
  1.42    0.003099          76        41           munmap
  1.22    0.002666         333         8           wait4
  0.46    0.001001          59        17           mremap
  0.04    0.000097           5        20           mprotect
  0.01    0.000030           0       799       156 stat
  0.01    0.000022          22         1           getuid
  0.00    0.000003           0       284        12 open
  0.00    0.000000           0       336           close
  0.00    0.000000           0       316           fstat
  0.00    0.000000           0         2         2 lstat
  0.00    0.000000           0        55         3 lseek
  0.00    0.000000           0        72           mmap
  0.00    0.000000           0         9           brk
  0.00    0.000000           0         2           rt_sigaction
  0.00    0.000000           0        76           rt_sigprocmask
  0.00    0.000000           0         2           ioctl
  0.00    0.000000           0        11        10 access
  0.00    0.000000           0        13           pipe
  0.00    0.000000           0        32           dup
  0.00    0.000000           0         1           getpid
  0.00    0.000000           0         8           clone
  0.00    0.000000           0         1           execve
  0.00    0.000000           0         5           kill
  0.00    0.000000           0       326           fcntl
  0.00    0.000000           0         1           ftruncate
  0.00    0.000000           0        12           getdents
  0.00    0.000000           0         2           getcwd
  0.00    0.000000           0         4           chdir
  0.00    0.000000           0        34        16 rename
  0.00    0.000000           0        24           chmod
  0.00    0.000000           0         2           fchmod
  0.00    0.000000           0         1           arch_prctl
  0.00    0.000000           0         6           openat
------ ----------- ----------- --------- --------- ----------------
100.00    0.218728                  7626       204 total

```

Finally, this is the output I get when executing ltrace -c:
```

% time     seconds  usecs/call     calls      function
------ ----------- ----------- --------- --------------------
 47.63   22.042292    22042292         1 _ZN11CommandLine11DispatchArgEPNS_8DispatchEb
 46.96   21.733141    21733141         1 _ZN12pkgCacheFile11BuildCachesEP10OpProgressb
  4.87    2.255914     2255914         1 _Z10ListUpdateR16pkgAcquireStatusR13pkgSourceListi
  0.14    0.065913         716        92 _ZNSo3putEc
  0.07    0.033793       16896         2 _ZN12pkgCacheFile15BuildSourceListEP10OpProgress
  0.07    0.032048          56       567 _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_l
  0.04    0.019882          56       351 strlen
  0.04    0.019562         155       126 _ZNSo5flushEv
  0.03    0.015519       15519         1 _ZN12pkgCacheFile12RemoveCachesEv
  0.02    0.007890         239        33 memset
  0.01    0.006643        6643         1 _Z13pkgInitConfigR13Configuration
  0.01    0.006633         100        66 sigprocmask
  0.01    0.006533          68        96 gettext
  0.01    0.005278          56        94 _ZN10pkgAcquire10WorkerStepEPNS_6WorkerE
  0.01    0.005103          57        88 _ZN16pkgAcquireStatus7FetchedEyy
  0.01    0.003564          62        57 _ZNSt8ios_base4InitD1Ev
  0.01    0.003225          56        57 __snprintf_chk
  0.01    0.002471          74        33 _ZN16pkgAcquireStatus5PulseEP10pkgAcquire
  0.01    0.002337          70        33 __sprintf_chk
  0.00    0.002156          65        33 sigemptyset
  0.00    0.002094          63        33 sigaddset
  0.00    0.001030        1030         1 _ZN12pkgCacheFileD2Ev
  0.00    0.000994         994         1 setlocale
  0.00    0.000617         617         1 _ZNSt14basic_ofstreamIcSt11char_traitsIcEEC1EPKcSt13_Ios_Openmode
  0.00    0.000351          58         6 __cxa_atexit
  0.00    0.000350          70         5 _Z9SizeToStrd
  0.00    0.000339          67         5 snprintf
  0.00    0.000333          66         5 _ZNSsD1Ev
  0.00    0.000331         331         1 _ZN14OpTextProgressC1ER13Configuration
  0.00    0.000311         311         1 _Z13pkgInitSystemR13ConfigurationRP9pkgSystem
  0.00    0.000284          56         5 _ZNSs4_Rep10_M_destroyERKSaIcE
  0.00    0.000238          59         4 _ZNK13Configuration5FindIEPKcRKi
  0.00    0.000233          58         4 _ZNK13Configuration5FindBEPKcRKb
  0.00    0.000227         227         1 _ZNSt14basic_ofstreamIcSt11char_traitsIcEED1Ev
  0.00    0.000217         108         2 signal
  0.00    0.000214          71         3 _ZNSoC1EPSt15basic_streambufIcSt11char_traitsIcEE
  0.00    0.000214         107         2 _ZNSt8ios_base4InitC1Ev
  0.00    0.000173          57         3 _ZNSt9basic_iosIcSt11char_traitsIcEE5rdbufEPSt15basic_streambufIcS1_E
  0.00    0.000173          57         3 _ZNSoD1Ev
  0.00    0.000151         151         1 _ZN16pkgAcquireStatusC2Ev
  0.00    0.000146         146         1 isatty
  0.00    0.000143         143         1 getuid
  0.00    0.000131          65         2 _ZNK11CommandLine8FileSizeEv
  0.00    0.000131         131         1 _ZN14OpTextProgress4DoneEv
  0.00    0.000117         117         1 textdomain
  0.00    0.000116          58         2 _Z12_GetErrorObjv
  0.00    0.000107         107         1 ioctl
  0.00    0.000101         101         1 _ZN11CommandLine5ParseEiPPKc
  0.00    0.000093          93         1 _ZN12pkgCacheFileC2Ev
  0.00    0.000092          92         1 _ZN11CommandLineC1EPNS_4ArgsEP13Configuration
  0.00    0.000082          82         1 _ZN11GlobalError10DumpErrorsERSoRKNS_7MsgTypeERKb
  0.00    0.000060          60         1 _ZN11CommandLineD1Ev
  0.00    0.000057          57         1 _ZN16pkgAcquireStatus4StopEv
  0.00    0.000000           0         1 _ZN16pkgAcquireStatus5StartEv
------ ----------- ----------- --------- --------------------
100.00   46.280147                  1836 total

```

Maybe it's a problem with the cache?
I hope you can help me.
Thanks!

---

### Post by dino99 on 2015-03-10
maybe you need to allow a bit more ram to the vdi config

---

### Post by albert29 on 2015-03-10
That didn't seem to work. I tried with 3GB of ram, and this is the output of free while it's stuck at "Reading package lists...99%"

```
             total       used       free     shared    buffers     cached
Mem:       3083864     353552    2730312          0      10320     246908
-/+ buffers/cache:      96324    2987540
Swap:       786428          0     786428

```

---

### Post by nerdtron on 2015-03-10
> "Reading package lists...99%". It can stay like this for more than a minute before it ends. 
Every time? even if you "sudo apt-get update" twice in a row?

Also did you install any PPA?

---

