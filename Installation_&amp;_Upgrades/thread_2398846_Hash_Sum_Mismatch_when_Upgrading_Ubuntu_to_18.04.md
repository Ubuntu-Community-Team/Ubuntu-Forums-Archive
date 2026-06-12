---
title: "Hash Sum Mismatch when Upgrading Ubuntu to 18.04"
date: 2018-08-18
forum: Installation &amp; Upgrades
---

### Post by arorashwetankkdm on 2018-08-18
While upgrading ubuntu 16.04 to 18.04, it shows "hash sum mismatch" when fetching a package **libgcc-5-dev** from [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu).

After some digging, I found out that those hashes are actually different.

From package.xz from [http://in.archive.ubuntu.com/ubuntu/dists/bionic/universe/binary-amd64/](http://in.archive.ubuntu.com/ubuntu/dists/bionic/universe/binary-amd64/) :

[COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Package: libgcc-5-dev
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Architecture: amd64
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Version: 5.5.0-12ubuntu1
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Multi-Arch: same
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Priority: optional
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Section: universe/libdevel
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Source: gcc-5
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Origin: Ubuntu
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Installed-Size: 12196
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Depends: gcc-5-base (= 5.5.0-12ubuntu1), libgcc1 (>= 1:5.5.0-12ubuntu1), libgomp1 (>= 5.5.0-12ubuntu1), libitm1 (>= 5.5.0-12ubuntu1), libatomic1 (>= 5.5.0-12ubuntu1), libasan2 (>= 5.5.0-12ubuntu1), liblsan0 (>= 5.5.0-12ubuntu1), libtsan0 (>= 5.5.0-12ubuntu1), libubsan0 (>= 5.5.0-12ubuntu1), libcilkrts5 (>= 5.5.0-12ubuntu1), libmpx0 (>= 5.5.0-12ubuntu1), libquadmath0 (>= 5.5.0-12ubuntu1)
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Recommends: libc6-dev (>= 2.13-0ubuntu6)
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Replaces: gccgo-5 (<< 5.5.0-12ubuntu1)
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Filename: pool/universe/g/gcc-5/libgcc-5-dev_5.5.0-12ubuntu1_amd64.deb
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Size: 2224336
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]MD5sum: b231699e74ba0313471f0eb8165a2670
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]SHA1: eef0933dbc4ff3cfdf8480cc3b608cd3aefb4e7b
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]SHA256: 82881d0950cecf10639208563084b7f3dbc903be53e8ce8fa0f948d12bc875cf
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Homepage: [http://gcc.gnu.org/](http://gcc.gnu.org/)
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Description: GCC support library (development files)
[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][INDENT][SIZE=2]Description-md5: 4ab7cb439b47e1d0796fbaf8447229ac

[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][FONT=Verdana]By calculating the hashes of file **libgcc-5-dev_5.5.0-12ubuntu1_amd54.deb** from [/FONT][COLOR=#222222][FONT=Verdana][http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-5/libgcc-5-dev_5.5.0-12ubuntu1_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-5/libgcc-5-dev_5.5.0-12ubuntu1_amd64.deb):
[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][INDENT][SIZE=2]MD5sum: 8347688945d5b4023ab71afb73093e95
SHA1: 2f98903386b5e527708e385b7b3ff4831475628f
SHA256: 98a6142ecc005ed954a472bd84712430e01e03b08d0fccb50cd0d611f961ab0f

[/SIZE][/INDENT]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp][FONT=Verdana]I could upgrade it by manually downloading the package but I didn't for security reasons and there may be other packages having this problem as well. I couldn't wait to check out this new version, so please could anyone fix this ASAP.[/FONT][/FONT][/COLOR]

---

