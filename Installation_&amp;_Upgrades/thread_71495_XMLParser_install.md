---
title: "XML::Parser install"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by Sosia on 2005-10-03
I've been trying to install gnomeppp and discovered I needed XML::Parser before I could do that. So I tried perl -MCPAN -e "install XML::Parser" and got this> CPAN: Storable loaded ok
Going to read /home/ubuntu/.cpan/Metadata
Warning: Found only 0 objects in /home/ubuntu/.cpan/Metadata
Warning: You are not allowed to write into directory "/home/ubuntu/.cpan/sources/authors".
    I'll continue, but if you encounter problems, they may be due
    to insufficient permissions.
LWP not available
CPAN: Net::FTP loaded ok
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz](ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz)
Cannot open Local file /home/ubuntu/.cpan/sources/authors/01mailrc.txt.gz: Permission denied
 at /usr/share/perl/5.8/CPAN.pm line 2265
Couldn't fetch 01mailrc.txt.gz from ftp.perl.org

Trying with "/usr/bin/wget -O -" to get
    [ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz](ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz)
sh: /home/ubuntu/.cpan/sources/authors/01mailrc.txt: Permission denied

System call "/usr/bin/wget -O - "ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz"  > /home/ubuntu/.cpan/sources/authors/01mailrc.txt"
returned status 1 (wstat 256)
Warning: expected file [/home/ubuntu/.cpan/sources/authors/01mailrc.txt.gz] doesn't exist
Issuing "/usr/bin/ftp -n"
Local directory now /home/ubuntu/.cpan/sources/authors
local: 01mailrc.txt.gz: Permission denied
Bad luck... Still failed!
Can't access URL [ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz](ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz).

Please check, if the URLs I found in your configuration file () are valid.
The urllist can be edited. E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch authors/01mailrc.txt.gz
Warning: You are not allowed to write into directory "/home/ubuntu/.cpan/sources/modules".
    I'll continue, but if you encounter problems, they may be due
    to insufficient permissions.
LWP not available
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz](ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz)
Cannot open Local file /home/ubuntu/.cpan/sources/modules/02packages.details.txt.gz: Permission denied
 at /usr/share/perl/5.8/CPAN.pm line 2265
Couldn't fetch 02packages.details.txt.gz from ftp.perl.org

Trying with "/usr/bin/wget -O -" to get
    [ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz](ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz)
sh: /home/ubuntu/.cpan/sources/modules/02packages.details.txt: Permission denied
System call "/usr/bin/wget -O - "ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz"  > /home/ubuntu/.cpan/sources/modules/02packages.details.txt"
returned status 1 (wstat 256)
Warning: expected file [/home/ubuntu/.cpan/sources/modules/02packages.details.txt.gz] doesn't exist
Issuing "/usr/bin/ftp -n"
Local directory now /home/ubuntu/.cpan/sources/modules
local: 02packages.details.txt.gz: Permission denied
Bad luck... Still failed!
Can't access URL [ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz](ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz).

Please check, if the URLs I found in your configuration file () are valid.
The urllist can be edited. E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch modules/02packages.details.txt.gz
Warning: You are not allowed to write into directory "/home/ubuntu/.cpan/sources/modules".
    I'll continue, but if you encounter problems, they may be due
    to insufficient permissions.
LWP not available
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz](ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz)
Cannot open Local file /home/ubuntu/.cpan/sources/modules/03modlist.data.gz: Permission denied
 at /usr/share/perl/5.8/CPAN.pm line 2265
Couldn't fetch 03modlist.data.gz from ftp.perl.org

Trying with "/usr/bin/wget -O -" to get
    [ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz](ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz)
sh: /home/ubuntu/.cpan/sources/modules/03modlist.data: Permission denied

System call "/usr/bin/wget -O - "ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz"  > /home/ubuntu/.cpan/sources/modules/03modlist.data"
returned status 1 (wstat 256)
Warning: expected file [/home/ubuntu/.cpan/sources/modules/03modlist.data.gz] doesn't exist
Issuing "/usr/bin/ftp -n"
Local directory now /home/ubuntu/.cpan/sources/modules
local: 03modlist.data.gz: Permission denied
Bad luck... Still failed!
Can't access URL [ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz](ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz).

Please check, if the URLs I found in your configuration file () are valid.
The urllist can be edited. E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch modules/03modlist.data.gz
Going to write /home/ubuntu/.cpan/Metadata
can't create /home/ubuntu/.cpan/Metadata: Permission denied at /usr/share/perl/5.8/CPAN.pm line 3432
Warning: Cannot install XML::Parser, don't know what it is.
Try the command

    i /XML::Parser/

to find objects with matching identifiers.

I'm really out of my depth, as I haven't got a clue what this means, or how to fix it.

Can someone help??

---

