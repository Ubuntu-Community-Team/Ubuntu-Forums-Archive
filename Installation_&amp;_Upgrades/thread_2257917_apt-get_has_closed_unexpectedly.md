---
title: "apt-get has closed unexpectedly"
date: 2014-12-23
forum: Installation &amp; Upgrades
---

### Post by maclenin on 2014-12-23
I am not usually one to dump (or for dumping) loads of potentially meaningless detailia into a forum post - however, others have been asked to produce similar for seemingly similar errors, so, here we go!

When my 12.04 xubuntu system tries to run update-manager at boot-up (and at the other times update-manager attempts to run while the computer is on), the "do not enter" red circle of error icon appears, with the message "An error occurred when checking for updates" just next to the "!" crash report detected splash icon, which, perhaps, more substantively, reveals the following:

```
ProblemType: Crash
Architecture: i386
CrashCounter: 1
Date: Mon Dec 15 07:35:04 2014
DistroRelease: Ubuntu 12.04
ExecutablePath: /usr/bin/apt-get
ExecutableTimestamp: 1414703908
ProcCmdline: apt-get check -f -qq
ProcCwd: /var/backups
ProcEnviron:
 TERM=linux
 PATH=(custom, no user)
 SHELL=/bin/sh
ProcMaps:
 00110000-0012c000 r-xp 00000000 fc:00 393261     /lib/i386-linux-gnu/libgcc_s.so.1
 0012c000-0012d000 r--p 0001b000 fc:00 393261     /lib/i386-linux-gnu/libgcc_s.so.1
 0012d000-0012e000 rw-p 0001c000 fc:00 393261     /lib/i386-linux-gnu/libgcc_s.so.1
 00260000-00261000 r-xp 00000000 00:00 0          [vdso]
 00365000-00368000 r-xp 00000000 fc:00 393317     /lib/i386-linux-gnu/libdl-2.15.so
 00368000-00369000 r--p 00002000 fc:00 393317     /lib/i386-linux-gnu/libdl-2.15.so
 00369000-0036a000 rw-p 00003000 fc:00 393317     /lib/i386-linux-gnu/libdl-2.15.so
 00375000-00395000 r-xp 00000000 fc:00 393311     /lib/i386-linux-gnu/ld-2.15.so
 00395000-00396000 r--p 0001f000 fc:00 393311     /lib/i386-linux-gnu/ld-2.15.so
 00396000-00397000 rw-p 00020000 fc:00 393311     /lib/i386-linux-gnu/ld-2.15.so
 003f0000-00404000 r-xp 00000000 fc:00 393448     /lib/i386-linux-gnu/libz.so.1.2.3.4
 00404000-00405000 r--p 00013000 fc:00 393448     /lib/i386-linux-gnu/libz.so.1.2.3.4
 00405000-00406000 rw-p 00014000 fc:00 393448     /lib/i386-linux-gnu/libz.so.1.2.3.4
 00412000-0043c000 r-xp 00000000 fc:00 396844     /lib/i386-linux-gnu/libm-2.15.so
 0043c000-0043d000 r--p 00029000 fc:00 396844     /lib/i386-linux-gnu/libm-2.15.so
 0043d000-0043e000 rw-p 0002a000 fc:00 396844     /lib/i386-linux-gnu/libm-2.15.so
 006e1000-006e3000 r-xp 00000000 fc:00 396850     /lib/i386-linux-gnu/libutil-2.15.so
 006e3000-006e4000 r--p 00001000 fc:00 396850     /lib/i386-linux-gnu/libutil-2.15.so
 006e4000-006e5000 rw-p 00002000 fc:00 396850     /lib/i386-linux-gnu/libutil-2.15.so
 00853000-0092b000 r-xp 00000000 fc:00 791485     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
 0092b000-0092c000 ---p 000d8000 fc:00 791485     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
 0092c000-00930000 r--p 000d8000 fc:00 791485     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
 00930000-00931000 rw-p 000dc000 fc:00 791485     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
 00931000-00938000 rw-p 00000000 00:00 0 
 00c3f000-00de3000 r-xp 00000000 fc:00 396855     /lib/i386-linux-gnu/libc-2.15.so
 00de3000-00de5000 r--p 001a4000 fc:00 396855     /lib/i386-linux-gnu/libc-2.15.so
 00de5000-00de6000 rw-p 001a6000 fc:00 396855     /lib/i386-linux-gnu/libc-2.15.so
 00de6000-00de9000 rw-p 00000000 00:00 0 
 00ec2000-00fe7000 r-xp 00000000 fc:00 788400     /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 00fe7000-00fe8000 ---p 00125000 fc:00 788400     /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 00fe8000-00fea000 r--p 00125000 fc:00 788400     /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 00fea000-00feb000 rw-p 00127000 fc:00 788400     /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 08048000-08073000 r-xp 00000000 fc:00 793847     /usr/bin/apt-get
 08073000-08074000 r--p 0002b000 fc:00 793847     /usr/bin/apt-get
 08074000-08075000 rw-p 0002c000 fc:00 793847     /usr/bin/apt-get
 0937a000-093af000 rw-p 00000000 00:00 0          [heap]
 b46bf000-b5fbf000 rw-s 00000000 fc:03 260678     /var/cache/apt/pkgcache.bin.g32R6o
 b77bf000-b77c3000 rw-p 00000000 00:00 0 
 b77d8000-b77db000 rw-p 00000000 00:00 0 
 bfbd3000-bfbf4000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:	apt-get
 State:	S (sleeping)
 Tgid:	23582
 Pid:	23582
 PPid:	23571
 TracerPid:	0
 Uid:	0	0	0	0
 Gid:	0	0	0	0
 FDSize:	32
 Groups:	
 VmPeak:	   54316 kB
 VmSize:	   30524 kB
 VmLck:	       0 kB
 VmPin:	       0 kB
 VmHWM:	   26612 kB
 VmRSS:	   26612 kB
 VmData:	     284 kB
 VmStk:	     136 kB
 VmExe:	     172 kB
 VmLib:	    4224 kB
 VmPTE:	      60 kB
 VmSwap:	       0 kB
 Threads:	1
 SigQ:	0/24001
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	0000000000000000
 SigIgn:	0000000000001000
 SigCgt:	0000000008000000
 CapInh:	0000000000000000
 CapPrm:	ffffffffffffffff
 CapEff:	ffffffffffffffff
 CapBnd:	ffffffffffffffff
 Cpus_allowed:	f
 Cpus_allowed_list:	0-3
 Mems_allowed:	1
 Mems_allowed_list:	0
 voluntary_ctxt_switches:	69
 nonvoluntary_ctxt_switches:	187
Signal: 11
Uname: Linux 3.2.0-64-generic i686
UserGroups: 
CoreDump: base64
H4sICAAAAAAC/0NvcmVEdW1wAA==
[...TRUNCATED...] 
SSEG69Mtdx0g+3qOv9ADAIAA==
ApportVersion: 2.0.1-0ubuntu17.8
Dependencies:
 coreutils 8.13-3ubuntu3.2
 debconf 1.5.42ubuntu1
 dpkg 1.16.1.2ubuntu7.5
 gcc-4.6-base 4.6.3-1ubuntu5
 gnupg 1.4.11-3ubuntu2.7
 gpgv 1.4.11-3ubuntu2.7
 libacl1 2.2.51-5ubuntu1
 libapt-pkg4.12 0.8.16~exp12ubuntu10.22
 libattr1 1:2.4.46-5ubuntu1
 libbz2-1.0 1.0.6-1
 libc-bin 2.15-0ubuntu10.9
 libc6 2.15-0ubuntu10.9
 libgcc1 1:4.6.3-1ubuntu5
 liblzma5 5.1.1alpha+20110809-3
 libreadline6 6.2-8
 libselinux1 2.1.0-4.1ubuntu1
 libstdc++6 4.6.3-1ubuntu5
 libtinfo5 5.9-4
 libusb-0.1-4 2:0.1.12-20
 multiarch-support 2.15-0ubuntu10.9
 perl-base 5.14.2-6ubuntu2.4
 readline-common 6.2-8
 tar 1.26-4ubuntu1
 tzdata 2014i-0ubuntu0.12.04
 ubuntu-keyring 2011.11.21.1
 xz-utils 5.1.1alpha+20110809-3
 zlib1g 1:1.2.3.4.dfsg-3ubuntu4
Disassembly:
 => 0xf98281 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1425>:	mov    %eax,0x8(%ebp)
    0xf98284 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1428>:	mov    0x64(%esp),%eax
    0xf98288 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1432>:	lea    -0xc(%eax),%ecx
    0xf9828b <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1435>:	cmp    -0xb4(%ebx),%ecx
    0xf98291 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1441>:	je     0xf97fd0 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+736>
    0xf98297 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1447>:	mov    -0xe4(%ebx),%ebp
    0xf9829d <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1453>:	test   %ebp,%ebp
    0xf9829f <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1455>:	je     0xf9860e <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+2334>
    0xf982a5 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1461>:	mov    $0xffffffff,%edx
    0xf982aa <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1466>:	lock xadd %edx,-0x4(%eax)
    0xf982af <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1471>:	test   %edx,%edx
    0xf982b1 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1473>:	jg     0xf97fd0 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+736>
    0xf982b7 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1479>:	lea    0x74(%esp),%eax
    0xf982bb <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1483>:	mov    %eax,0x4(%esp)
    0xf982bf <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1487>:	mov    %ecx,(%esp)
    0xf982c2 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1490>:	call   0xee72d0 <_ZNSs4_Rep10_M_destroyERKSaIcE@plt>
InstallationMedia: Xubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423.1)
MarkForUpload: True
Package: apt 0.8.16~exp12ubuntu10.22
PackageArchitecture: i386
ProcVersionSignature: Ubuntu 3.2.0-64.97-generic 3.2.59
Registers:
 eax            0x17ffff1	25165809
 ecx            0xb46bf000	-1267994624
 edx            0x18	24
 ebx            0xfe9ff4	16687092
 esp            0xbfbf1a90	0xbfbf1a90
 ebp            0xb5fc3b00	0xb5fc3b00
 esi            0xbfbf1af4	-1077994764
 edi            0xbfbf1ae0	-1077994784
 eip            0xf98281	0xf98281 <debListParser::LoadReleaseInfo(pkgCache::PkgFileIterator&, FileFd&, std::string)+1425>
 eflags         0x10282	[ SF IF RF ]
 cs             0x73	115
 ss             0x7b	123
 ds             0x7b	123
 es             0x7b	123
 fs             0x0	0
 gs             0x33	51
SegvAnalysis:
 Segfault happened at: 0xf98281 <_ZN13debListParser15LoadReleaseInfoERN8pkgCache15PkgFileIteratorER6FileFdSs+1425>:	mov    %eax,0x8(%ebp)
 PC (0x00f98281) ok
 source "%eax" ok
 destination "0x8(%ebp)" (0xb5fc3b08) not located in a known VMA region (needed writable region)!
SegvReason: writing unknown VMA
SourcePackage: apt
Stacktrace:
 #0  0x00f98281 in debListParser::LoadReleaseInfo(pkgCache::PkgFileIterator&, FileFd&, std::string) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #1  0x00fb402a in debPackagesIndex::Merge(pkgCacheGenerator&, OpProgress*) const () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #2  0x00f4d66c in ?? () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #3  0x00f506b8 in pkgCacheGenerator::MakeStatusCache(pkgSourceList&, OpProgress*, MMap**, bool) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #4  0x00f45ce0 in pkgCacheFile::BuildCaches(OpProgress*, bool) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #5  0x00f4617d in pkgCacheFile::Open(OpProgress*, bool) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #6  0x08055726 in ?? ()
 No symbol table info available.
 #7  0x00ef705e in CommandLine::DispatchArg(CommandLine::Dispatch*, bool) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #8  0x0804fd98 in ?? ()
 No symbol table info available.
 #9  0x00c584d3 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
 No symbol table info available.
 #10 0x08050141 in ?? ()
 No symbol table info available.
StacktraceAddressSignature: /usr/bin/apt-get:11:i686:/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0+d6281:/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0+f202a:/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0+8b66c:/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0+8e6b8:/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0+83ce0:/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0+8417d:/usr/bin/apt-get+d726:/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0+3505e:/usr/bin/apt-get+7d98:/lib/i386-linux-gnu/libc-2.15.so+194d3:/usr/bin/apt-get+8141
StacktraceTop:
 debListParser::LoadReleaseInfo(pkgCache::PkgFileIterator&, FileFd&, std::string) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 debPackagesIndex::Merge(pkgCacheGenerator&, OpProgress*) const () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 ?? () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 pkgCacheGenerator::MakeStatusCache(pkgSourceList&, OpProgress*, MMap**, bool) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 pkgCacheFile::BuildCaches(OpProgress*, bool) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
Tags:  precise
ThreadStacktrace:
 .
 Thread 1 (LWP 23582):
 #0  0x00f98281 in debListParser::LoadReleaseInfo(pkgCache::PkgFileIterator&, FileFd&, std::string) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #1  0x00fb402a in debPackagesIndex::Merge(pkgCacheGenerator&, OpProgress*) const () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #2  0x00f4d66c in ?? () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #3  0x00f506b8 in pkgCacheGenerator::MakeStatusCache(pkgSourceList&, OpProgress*, MMap**, bool) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #4  0x00f45ce0 in pkgCacheFile::BuildCaches(OpProgress*, bool) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #5  0x00f4617d in pkgCacheFile::Open(OpProgress*, bool) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #6  0x08055726 in ?? ()
 No symbol table info available.
 #7  0x00ef705e in CommandLine::DispatchArg(CommandLine::Dispatch*, bool) () from /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
 No symbol table info available.
 #8  0x0804fd98 in ?? ()
 No symbol table info available.
 #9  0x00c584d3 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
 No symbol table info available.
 #10 0x08050141 in ?? ()
 No symbol table info available.
Title: apt-get crashed with SIGSEGV in debListParser::LoadReleaseInfo()
UpgradeStatus: No upgrade log present (probably fresh install)
```

Thanks for any insight!

---

### Post by -Marco on 2014-12-23
Try to re-install Synaptic or App Center. This problem displayied to me last night and I resolved with this.

---

### Post by slickymaster on 2014-12-23
@maclenin:
That's a known and reported bug in Precise: [Bug #957231]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/957231")

---

### Post by maclenin on 2014-12-31
@all!

In the wake of a recent "aptitude safe-upgrade", the bug seems to have flown (no more scary icons and related).

Will report back if the situation changes (not quite "Solved", in my view).

Thanks for the comments.

---

