---
title: "apt installation from pool"
date: 2012-04-12
forum: Installation &amp; Upgrades
---

### Post by Tolstoi on 2012-04-12
I need to install some perl-packets in a lucid environment, which are distribution independent and available below the base/pool/universe directory.

Now I receive for some packets the message, that they cannot be found, when I search manually the ubuntu repository, I see, that they are there.

Example given:  **libmath-base64-perl**

Available at:
***http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmath-base36-perl/***

When I search for it on the lucid-system, i can't find the package:
[INDENT][I]**# lsb_release -a ; apt-cache show libmath-base64-perl **
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid
[COLOR="Red"]W: Paket libmath-base64-perl kann nicht gefunden werden
E: Keine Pakete gefunden[/COLOR][/I][/INDENT]

When I search for it from an oneiric and lucid system I am able to find it:

[I][INDENT]**# lsb_release -a ;apt-cache show libmath-base36-perl **
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
Package: libmath-base36-perl
Priority: optional
Section: universe/perl
Installed-Size: 56
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Perl Group <pkg-perl-maintainers@lists.alioth.debian.org>
Architecture: all
Version: 0.09-1
Depends: perl
Filename: [COLOR="Red"]pool/universe/libm/libmath-base36-perl/libmath-base36-perl_0.09-1_all.deb[/COLOR]
Size: 5548
MD5sum: 3441b9078cea1c92bc3d7a36d7a5594a
SHA1: 5878f31fd5a3513994485b1c08368bed61fed629
SHA256: 71b350d5bf48f7d4d71a299f53fa6be4f5af68a3737ddc51baf5bfd1b7f3ced1
Description-en: Perl module for encoding and decoding of base36 strings
 Math::Base36 converts to and from Base36 numbers (0..9 - A..Z).
Homepage: [http://search.cpan.org/dist/Math-Base36/](http://search.cpan.org/dist/Math-Base36/)
Description-md5: c5d2582f230791a233c310bfce911a81
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
[/INDENT][/I]

When I however search in the lucid-based system for another package from the very same directory, e.g. **libmath-basecnv-perl** I am able to find it.


[I][INDENT]# **lsb_release -a ; apt-cache show libmath-basecnv-perl  ** 
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid
Package: libmath-basecnv-perl
Priority: optional
Section: universe/perl
Installed-Size: 80
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian Perl Group <pkg-perl-maintainers@lists.alioth.debian.org>
Architecture: all
Version: 1.4.75O6Pbr-1
Depends: perl (>= 5.6.0-16)
Filename:[COLOR="Red"] pool/universe/libm/libmath-basecnv-perl/libmath-basecnv-perl_1.4.75O6Pbr-1_all.deb[/COLOR]
Size: 17750
MD5sum: 89f50150ccd9fb098b5c077dd6b5943a
SHA1: cdc7dc3d490fe0ee824b8effb3109e3e290b9c26
SHA256: 68ae71ac52a0baa9c93b7efd73e745a58348bfe4a1a16ff694e0a61b0493d654
Description: set of fast functions to convert between number bases
 Math::BaseCnv provides a few simple functions for converting between
 arbitrary number bases. It is as fast as the author currently knows
 how to make it (of course relying only on the lovely Perl).
Homepage: [http://search.cpan.org/dist/Math-BaseCnv/](http://search.cpan.org/dist/Math-BaseCnv/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu[/INDENT][/I]

/etc/apt/sources.list on all systems are similar, the only difference is the distribution name.

Why I cant find certain packets from the lucid system?

Any hints??

---

