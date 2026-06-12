---
title: "Pidgin 2.0"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by teejay17 on 2007-05-07
Now that Pidgin is finally out of beta, is it going to be available in the repositories, or do I have to install it myself? 
If I do have to install it myself, how does one go about this?

---

### Post by tkjacobsen on 2007-05-07
you can get it from getdeb.net:
[http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

---

### Post by teejay17 on 2007-05-07
> **tkjacobsen said:**
> you can get it from getdeb.net:
[http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)
Cool. Thanks. 
I guess we have to wait for 7.10 to be released before we will see Pidgin in Synaptic, etcetera?

---

### Post by Wiebelhaus on 2007-05-07
that little icon.....jesus that thing is messed up

---

### Post by teejay17 on 2007-05-07
> **tkjacobsen said:**
> you can get it from getdeb.net:
[http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)
Okay, now that I get it from this site, what do I do with it? 
I was hoping there was something already compiled, something easy to install.

---

### Post by total wormage on 2007-05-07
you can double click the .deb file :]
if that doesn't work you'll need to install 'gdebi'

---

### Post by tkjacobsen on 2007-05-08
I dont know if double click works in xubuntu..

Else
Open a terminal
Go to the location of the package
write: "sudo dpkg -i pidgin????.deb"  where pidgin????.deb is the correct name of the package.
write: "sudo apt-get --fix-missing" to install missing dependencies (if any)

---

### Post by teejay17 on 2007-05-08
> **tkjacobsen said:**
> I dont know if double click works in xubuntu..

Else
Open a terminal
Go to the location of the package
write: "sudo dpkg -i pidgin????.deb"  where pidgin????.deb is the correct name of the package.
write: "sudo apt-get --fix-missing" to install missing dependencies (if any)
Okay, thanks. I'll give that a try. It doesn't look like double clicking works in Xubuntu.
I'll let you know if it's successful or not. 
Cheers.

---

### Post by motang on 2007-05-08
> **tkjacobsen said:**
> you can get it from getdeb.net:
[http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

Wow cool thanks, I am going to be trying this out.  Has anyone tried installed Pidgin, if so does it create any problmes as to the name chanage from Gaim to Pidgin?

---

### Post by total wormage on 2007-05-09
i installed pidgin on my system that had gaim already on it and as far as i know there are no problems.
pidgin copied my gaim accounts and settings, but the install doesn't remove gaim from your system :]

so i think you can fairly safe install it :p

---

### Post by maddbaron on 2007-05-09
can someone upload the deb from getdeb please? its no longer on the site. i need a deb for edgy please.

---

### Post by teejay17 on 2007-06-04
> **tkjacobsen said:**
> you can get it from getdeb.net:
[http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)
Okay, now I see that version 2.0.1 is out, so how do I update to the newest version without breaking something. It's not in the repositories yet, so it won't get updated there. 
I don't want to have two different versions of the same program installed either.

---

### Post by tkjacobsen on 2007-06-04
If you install the new version from getdeb.net it will automatically replace the old one..

---

### Post by teejay17 on 2007-06-04
> **tkjacobsen said:**
> If you install the new version from getdeb.net it will automatically replace the old one..
Cool. Thanks.

---

### Post by th3gh05t on 2007-06-04
That deb didn't work for me. I am on Dapper.

```
derek@ghost:~/downloads$ sudo dpkg -i pidgin_2.0.1-1~getdeb2_i386.deb
Selecting previously deselected package pidgin.
(Reading database ... 167450 files and directories currently installed.)
Unpacking pidgin (from pidgin_2.0.1-1~getdeb2_i386.deb) ...
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libatk1.0-0 (>= 1.13.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 pidgin depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 pidgin depends on libcairo2 (>= 1.4.2); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.
 pidgin depends on libdbus-1-3 (>= 0.94); however:
  Package libdbus-1-3 is not installed.
 pidgin depends on libdbus-glib-1-2 (>= 0.73); however:
  Version of libdbus-glib-1-2 on system is 0.60-6ubuntu8.1.
 pidgin depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-1.1ubuntu12.
 pidgin depends on libfreetype6 (>= 2.2); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.4.
 pidgin depends on libgadu3 (>= 1:1.7~rc2); however:
  Version of libgadu3 on system is 1:1.6+20051103-1ubuntu1.
 pidgin depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 pidgin depends on libgnutls13 (>= 1.4.0-0); however:
  Package libgnutls13 is not installed.
 pidgin depends on libgstreamer0.10-0 (>= 0.10.12); however:
  Version of libgstreamer0.10-0 on system is 0.10.6-0ubuntu2.
 pidgin depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
 pidgin depends on libpango1.0-0 (>= 1.16.2); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
 pidgin depends on libperl5.8 (>= 5.8.8); however:
  Version of libperl5.8 on system is 5.8.7-10ubuntu1.
 pidgin depends on libpng12-0 (>= 1.2.13-4); however:
  Version of libpng12-0 on system is 1.2.8rel-5ubuntu0.1.
 pidgin depends on libsqlite3-0 (>= 3.3.13); however:
  Version of libsqlite3-0 on system is 3.2.8-1ubuntu1.
 pidgin depends on libxfixes3 (>= 1:4.0.1); however:
  Version of libxfixes3 on system is 1:3.0.1.2-0ubuntu3.
 pidgin depends on libxml2 (>= 2.6.27); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
 pidgin depends on libxrandr2 (>= 2:1.2.0); however:
  Version of libxrandr2 on system is 1:1.1.0.2-0ubuntu4.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin
derek@ghost:~/downloads$ sudo apt-get --fix-missing
apt 0.6.43.3ubuntu2 for linux i386 compiled on Apr 18 2006 19:46:38
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
derek@ghost:~/downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  pidgin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 24.7MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 168253 files and directories currently installed.)
Removing pidgin ...
derek@ghost:~/downloads$

```

Please help me out because I want to get this installed.

Thanks, th3ghj05t

---

### Post by steveneddy on 2007-06-04
> **motang said:**
> Has anyone tried installed Pidgin......

I only recently installed it on a Windows XP machine and it works fine.

BTW - the only reason I have a WinXP machine is to give remote help to those not in the wonderful world of Ubuntu.

---

### Post by teejay17 on 2007-06-05
> **tkjacobsen said:**
> If you install the new version from getdeb.net it will automatically replace the old one..
It worked like a charm. Is that ever awesome! That's by far the easiest way to install a program!

---

### Post by total wormage on 2007-06-05
> **th3gh05t said:**
> That deb didn't work for me. I am on Dapper. [...]

have you downloaded the actual dapper .deb? you can select your version of ubuntu on the main screen of getdeb
or go to [http://www.getdeb.net/distro_select.php]("http://www.getdeb.net/distro_select.php")

:]

---

### Post by th3gh05t on 2007-06-05
> **total wormage said:**
> have you downloaded the actual dapper .deb? you can select your version of ubuntu on the main screen of getdeb
or go to [http://www.getdeb.net/distro_select.php]("http://www.getdeb.net/distro_select.php")

:]

There is no .deb for Dapper 32 bit!!

---

### Post by paguilera on 2007-06-07
I'm not finding the package for edgy (32 bit) there either.  Have the packages been removed?

---

### Post by Elrohir on 2007-06-07
in case any deb fails, there's always the source code (as is my case, not sure why exactly)...

Here's [my tutorial (post anyway) on how to install pidgin from source]("http://ubuntuforums.org/showpost.php?p=2646809&postcount=121")... have fun!

---

