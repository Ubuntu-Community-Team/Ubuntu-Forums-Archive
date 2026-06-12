---
title: "how to install Curses.pm on ubuntu 6.06"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by tomjennings on 2007-07-26
I backed down to ubuntu 6.06 LTS (because 7.04 has a fatal-to-me "connect-debounce" USB bug) and I am unable to get Curses.PM to install via cpan. Or anything to install via cpan, for that matter.

All attempts fail with "make had returned bad status, install seems impossible". For example, from install Bundle::CPAN:

... download junk....
  CPAN.pm: Going to build K/KW/KWILLIAMS/ExtUtils-CBuilder-0.19.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for ExtUtils::CBuilder
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module ExtUtils::MakeMaker
Running make for M/MS/MSCHWERN/ExtUtils-MakeMaker-6.36.tar.gz
Checksum for /root/.cpan/sources/authors/id/M/MS/MSCHWERN/ExtUtils-MakeMaker-6.36.tar.gz ok
(((tar unpacks files)))
Writing Makefile for ExtUtils::MakeMaker
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module Module::Build

....more follows....


Why does it procede if it can't write the Makefile? Where do makefiles get written?

I'm sudo'd. Looked for these packages  in the repositories (such as later versions have) rather than cpan. No go.

I recall from other ubuntu 6.x versions that there's some bug that requires moving some c-config.h file or something but I lost my notes there.

All of the following have failed, even with force:

install Bundle::CPAN
install Curses
install Term::ReadKey
install force Device::SerialPort


Anyone have any hints? I thought the LTS packages were more usable!

---

### Post by tbroderick on 2007-07-26
Try the libcurses-perl package.

---

### Post by tomjennings on 2007-07-26
> **tbroderick said:**
> Try the libcurses-perl package.

There isn't one for 6.06 like there is for 7.04.

---

### Post by tbroderick on 2007-07-26
> **tomjennings said:**
> There isn't one for 6.06 like there is for 7.04.
[libcurses-perl]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libcurses-perl&searchon=names&subword=1&version=all&release=all")
```

Package libcurses-perl
warty (perl): Curses interface for Perl [universe] 
1.06-10: amd64 i386 powerpc 
hoary (perl): Curses interface for Perl [universe] 
1.08b-1: amd64 i386 powerpc 
breezy (perl): Curses interface for Perl [universe] 
1.12-1ubuntu1: amd64 i386 powerpc 
[B]dapper (perl): Curses interface for Perl [universe] 
1.13-1: amd64 i386 powerpc [/B]
edgy (perl): Curses interface for Perl [universe] 
1.13-1: amd64 i386 powerpc 
feisty (perl): Curses interface for Perl [universe] 
1.13-1: amd64 i386 powerpc 
gutsy (perl): Curses interface for Perl [universe] 
1.13-1: amd64 i386 powerpc

```

---

### Post by tomjennings on 2007-07-26
> **tbroderick said:**
> [libcurses-perl]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libcurses-perl&searchon=names&subword=1&version=all&release=all")
```

Package libcurses-perl
warty (perl): Curses interface for Perl [universe] 
blah blah blah...
1.13-1: amd64 i386 powerpc

```


Well hells bells.

I'd earlier done apt-cache search for libcurses-perl, and for 'curses' 'perl' etc w/egrep. No match. I swear. Universe repositories in sources.txt uncommented.  

But I also found I didn't have make installed. Installed that plus a bunch of package groups in aptitude (umm hard for CPAN to make w/o make...). Still no work. I did cpan o make /usr/bin/make, lo! compilation there. OK.

Then this AM I read your post. 'sigh, did that' but I like to repeat suggestions before replying so that I can tell you that it didn't...

... but it worked. So I don't know what to think.  Something came along with group apt-gets? Late night? Bright sunlight?

I must have broken something, obviously. It's a PITA to get a low overhead non-graphical ubuntu installed I must have removed something stupid. 

Thanks for the "obvious" (sic) suggestion!

---

### Post by tr333 on 2007-07-31
To install make and related utilities, install the "build-essential" meta-package.  This will install gcc/make/autoconf/etc.

---

