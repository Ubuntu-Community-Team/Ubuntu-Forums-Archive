---
title: "Likewise and Lucid Lynx 10.04 - unsupported version of Likewise open in repositories"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mbw on 2010-04-08
Hey Folks,

I just installed Likewise on Lucid Lynx 10.04 Beta 2.

Some notes from the effort:


Lucid Lynx contains a weirdish version of Likewise open - its version 5.4

According to my contact at Likewise, version 5.3 is supported, and the upcoming 6.0 is supported, but Likewise 5.4 is not and will not ever be supported.

What does this mean?

You may want to skip 5.4 and go get the ubuntu package for 5.3 from the Likewise site and use that instead.

If you really want to use 5.4,  my preliminary tests show it working reasonably well, but changing settings has become more complicated - now you must change a registry file and re-import those registry settings & restart the likewise service daemons in order to activate the change.

There are some good docs for likewise 5.4, but they are only  provided to OEMS and stashed away on a hidden URL at the Likewise web site. 

Those docs are here:


LWIS and Likewise-CIFS 5.4: 

[http://www.likewise.com/resources/documentation_library/manuals/oem/likewise-lwis-cifs-guide.html](http://www.likewise.com/resources/documentation_library/manuals/oem/likewise-lwis-cifs-guide.html)



To change my Likewise 5.4 install to Assume the default domain, so I can log in as "username" rather than "domain\username"

I had to edit the /etc/likewise-open/lsassd.reg file and
change the AssumeDefDom line to:

"AssumeDefaultDomain"=dword:00000001

then I ran:

lwregshell import lsassd.reg

to load the change, and lastly:

/etc/init.d/lwregd restart
/etc/init.d/lwiod restart


The following command was also helpful in debugging whether the setting change happened or not:

lw-eventlog-cli -s - 127.0.0.1 | more


also useful in testing the domain connection:

lw-enum-users | more


In the end, I still couldnt log in without the domain prefix on the username, so I removed the lucid package (5.4) and rolled back to:

# cat /opt/likewise/data/VERSION 
VERSION=5.3.0
BUILD=7724
REVISION=41177

Which I just downloaded from the likewise site... this version
has been working well for me on multiple platforms and I can
actually get support for it from likewise.


Get the latest supported, stable version of 5.3 here:

[http://www.likewise.com/community/index.php/download/](http://www.likewise.com/community/index.php/download/)


Hope this helps someone

Matt Weatherford
University of Washington
Seattle, WA

---

