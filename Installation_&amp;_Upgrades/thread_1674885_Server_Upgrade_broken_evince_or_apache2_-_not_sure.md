---
title: "Server Upgrade broken evince or apache2 - not sure"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by delbydev on 2011-01-24
apache2: Syntax error on line 204 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/libxml2.so.2: undefined symbol: gzopen64

Hi 
Have been running ubuntu server for about 6 months on a rickety but reliable AMD1.2GHz laptop (hp compaq nx9005) Had successfully deployed a UPS and various CGI scripts.  Familiar with the basics of apache tomcat and even dabbled with some mods.  All was running sweetly until I performed an upgraded yesterday which took me to Kernel (from uname -a) 2.6.31-22-generic-pae #70-Ubuntu SMP Thu Dec 2 00:54:52 UTC 2010 i686 GNU/Linux

During the upgrade there were libraries which apache2 depended upon and the process halted.  Have brute forced some other libraries - given there were 87 packages in the upgrade and it had got to 78 - I did not dare roll back - so pursued further until I finally noticed the message above

If I just break the message up a moment:

0 apache2: 
1 Syntax error on line 204 of /etc/apache2/apache2.conf: 
2 Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: 
3 Cannot load /usr/lib/apache2/modules/libphp5.so into server: 
4 /usr/lib/libxml2.so.2: undefined symbol: 
5 gzopen64

All failed attempts to apache2ctl start (and configtest etc) have consistently shown the same messages for lines 0,1,2,4 and 5 (i.e. not 3 - always something new falls over there when I reinstall the new set of libraries

( I have learned not to use apt-get and go for aptitude - (painfully) - I have attempted to rollback and roll forward and each time evince aborts the whole process.

I seemed to go into a dark road when started installing php5-pear because dpkg reported yet another suggestion (friendly dpkg)
Same message came back : as it seems to for all installs 

0 Creating config file /etc/php5/cli/php.ini with new version
1 update-alternatives: using /usr/bin/php5 to provide /usr/bin/php (php) in auto mode.

2 Setting up php-pear (5.2.10.dfsg.1-2ubuntu6.7) ...
3 Errors were encountered while processing:
4 evince
5 E: Sub-process /usr/bin/dpkg returned an error code (1)

Darned evince - I am not even using the desktop making it a headless installation - Have done okay with ssh - like I say this machine was running for at least 6 months without hitch until this upgrade yesterday

I have hopped around various threads anonymously and tried various methods to little or no avail and I respectfully call on the forum to see if they might have a clear path out of this .  As I said this occurred during an apt-get upgrade and now it seems I might be in a spot of treacle


______________________________________________________________________


Anyway - I shall add some files here to demonstrate the configurations of my apache configuration - because I have also sene notes of apache2.conf no longer being correct all of a sudden - though I believe it is something more low level

Help very appreciated -- the server is still operating for core file management.  Just would like to get the small HTML / PHP / Perl apps back up and running - specifically to keep an eye on my UPS as power supply in my neighbourhood is sporadic
______________________________________________________________________

# File reporting problems Last message when attempting to start apache2
md5sum /usr/lib/apache2/modules/libphp5.so
924c43b9c7896386f5009c79e737f31d  /usr/lib/apache2/modules/libphp5.so

______________________________________________________________________

cat /etc/apache2/mods-enabled/php5.load 
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

Have attached http.conf, ports.conf and apache2.conf in the file apache_break20110124.txt

---

### Post by delbydev on 2011-01-26
Has anybody had chance to view or think about this yet?

Tried another upgrade - hit same issue


Setting up evince (2.28.1-0ubuntu1.3) ...
/usr/bin/python: /usr/local/lib/libz.so.1: no version information available (required by /usr/bin/python)
gconftool-2: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing evince (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up hplip-data (3.9.8-1ubuntu2.1) ...
/usr/bin/python: /usr/local/lib/libz.so.1: no version information available (required by /usr/bin/python)

Thanks

---

