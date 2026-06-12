---
title: "Missing Perl Mod Table.pm"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by BeartoothTech on 2011-05-10
I am not sure this is the correct forum but please bear with me.
 
I have converted from an ancient release of Red Hat to Ubuntu 11.04.  I have resolved most of the conversion problems except for one.  A number of my CGI Scipts require the Perl Module Table.pm.  It has not been installed.  Where do I find that module and how can I install it?
 
:confused:

---

### Post by Lars Noodén on 2011-05-10
> **BeartoothTech said:**
>  A number of my CGI Scipts require the Perl Module Table.pm.  It has not been installed.  Where do I find that module and how can I install it?
 
:confused:

There should be a longer name, because there are many [table.pm](http://packages.ubuntu.com/search?searchon=contents&keywords=Table.pm&mode=exactfilename&suite=natty&arch=any) files.

What do the require, use or include statements at the beginning of the program tell you?  Those are the modules you need.

---

### Post by BeartoothTech on 2011-05-10
> **Lars Noodén said:**
> There should be a longer name, because there are many [table.pm]("http://packages.ubuntu.com/search?searchon=contents&keywords=Table.pm&mode=exactfilename&suite=natty&arch=any") files.
 
What do the require, use or include statements at the beginning of the program tell you? Those are the modules you need.
 
 
The use modules are:
 
use strict;
use DBI;
use CGI qw(fatalsToBrowser); 
use HTML::Table;
 
 
The message in the error.log is:
 
[Sun May 08 19:32:06 2011] [error] [client xxx.xxx.xxx.xxx] Can't locate HTML/Table.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /www/cgi/yellowstoneloon/cgi-bin/addlooninfo.cgi line 36.
 
[Sun May 08 19:32:06 2011] [error] [client xxx.xxx.xxx.xxx] BEGIN failed--compilation aborted at /www/cgi/yellowstoneloon/cgi-bin/addlooninfo.cgi line 36.
 
 
Thanks for the response.

---

### Post by Lars Noodén on 2011-05-10
> **BeartoothTech said:**
> 
use DBI;
use CGI qw(fatalsToBrowser); 
use HTML::Table;
 

[s]It's probably DBI you're missing.  It should be in [libdbi-perl](http://packages.ubuntu.com/natty/libdbi-perl).  See if it's installed.[/s]

Edit: Scratch that.

It's probably HTML::Table.  That will be in **libhtml-table-perl**

---

### Post by BeartoothTech on 2011-05-10
> **Lars Noodén said:**
> [s]It's probably DBI you're missing. It should be in [libdbi-perl]("http://packages.ubuntu.com/natty/libdbi-perl"). See if it's installed.[/s]
 
Edit: Scratch that.
 
It's probably HTML::Table. That will be in **libhtml-table-perl**
 
 
How can I get a list of packages that are installed?  I am just starting with Ubuntu.  I did a scan (find) of the system and Table.pm does not exist.
 
Also, how would I install the package?
 
Would I use "sudo apt-get libhtml-table-perl install"?

---

### Post by Lars Noodén on 2011-05-10
> **BeartoothTech said:**
> Would I use "sudo apt-get libhtml-table-perl install"?

```

sudo apt-get install libhtml-table-perl libdbi-perl

```

---

### Post by Lars Noodén on 2011-05-10
> **BeartoothTech said:**
> How can I get a list of packages that are installed? 
```

dpkg -l |awk '/^ii/ { print $2 }'

```
or
```

dpkg -l |awk '/^ii.*-perl/ { print $2 }'

```

---

### Post by BeartoothTech on 2011-05-10
> **Lars Noodén said:**
> ```

dpkg -l |awk '/^ii/ { print $2 }'

```
or
```

dpkg -l |awk '/^ii.*-perl/ { print $2 }'

```
 
 
Thanks for your help.  I added those two packages and everything worked.
 
:)

---

