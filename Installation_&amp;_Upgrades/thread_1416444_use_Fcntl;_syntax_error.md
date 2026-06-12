---
title: "use Fcntl; syntax error"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2010-02-26
I run a perl-based program called PerlFect. It is a web site search index. I went to reindex it tonight, but I got this error:

```

File "indexer.pl", line 24
  use Fcntl;
          ^

SyntaxError: invalid syntax

```

I've used this before, so I know it used to work. I can't find anything about this through Google, so can someone tell me how to fix this? Thanks...

BTW - if this help: 

```

dpkg -l | grep perl

ii  libarchive-zip-perl                   1.18-1                     Module for manipulation of ZIP archives
ii  libcompress-raw-zlib-perl             2.005-1                    low-level interface to zlib compression libr
ii  libcompress-zlib-perl                 2.005-1ubuntu0.2           Perl module for creation and manipulation of
ii  libdb-file-lock-perl                  0.05-2                     Provides a wrapper for the DB_File module, a
ii  libdbd-mysql-perl                     4.004-2                    A Perl5 database interface to the MySQL data
ii  libdbi-perl                           1.57-1                     Perl5 database interface by Tim Bunce
ii  libdigest-hmac-perl                   1.01-5                     create standard message integrity checks
ii  libdigest-sha1-perl                   2.11-2                     NIST SHA-1 message digest algorithm
ii  libhtml-parser-perl                   3.56-1                     A collection of modules that parse HTML text
ii  libhtml-tagset-perl                   3.10-2                     Data tables pertaining to HTML
ii  libhtml-tree-perl                     3.23-1                     represent and create HTML syntax trees
ii  libio-compress-base-perl              2.005-1                    Base Class for IO::Compress modules
ii  libio-compress-zlib-perl              2.005-1                    Perl interface to zlib
ii  liblocale-gettext-perl                1.05-1build1               Using libc functions for internationalizatio
ii  libnet-daemon-perl                    0.38-1.1                   Perl module for building portable Perl daemo
ii  libnet-dns-perl                       0.60-1ubuntu0.1            Perform DNS queries from a Perl script
ii  libnet-ip-perl                        1.25-2                     Perl extension for manipulating IPv4/IPv6 ad
ii  libperl5.8                            5.8.8-7ubuntu3.4           Shared Perl library
ii  libplrpc-perl                         0.2017-1.1                 Perl extensions for writing PlRPC servers an
ii  librpc-xml-perl                       0.59-1                     Perl module implementation of XML-RPC
ii  libterm-readkey-perl                  2.30-3ubuntu1              A perl module for simple terminal control
ii  libtext-charwidth-perl                0.04-4build1               get display widths of characters on the term
ii  libtext-iconv-perl                    1.4-3                      converts between character sets in Perl
ii  libtext-wrapi18n-perl                 0.06-5                     internationalized substitute of Text::Wrap
ii  liburi-perl                           1.35.dfsg.1-1              Manipulates and accesses URI strings
ii  libwww-perl                           5.805-1                    WWW client/server library for Perl (aka LWP)
ii  libxml-parser-perl                    2.34-4.3                   Perl module for parsing XML files
ii  perl                                  5.8.8-7ubuntu3.4           Larry Wall's Practical Extraction and Report
ii  perl-base                             5.8.8-7ubuntu3.4           The Pathologically Eclectic Rubbish Lister
ii  perl-modules                          5.8.8-7ubuntu3.4           Core Perl modules

```


and this is on Ubuntu 7.10 Server. 

[edit] 
I just tried running it on my Karmic 9.10 system and I get the same error. So it doesn't appear to be related to the Ubuntu version... I really need some help here!

---

