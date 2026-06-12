---
title: "Installing Xampp, snort and the mysql problem!"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by _sleeper on 2008-09-11
hi guys! i hope all the great minds here will give me a hand on this. here's what's going on..

i have a kubuntu 8.04 distro and i want to work on an IDS, snort  in this case. i knew it could log into a database, so i chose xampp, which apart from mysql gives a full package of an apache server, php, etc, which comes pretty handy with what i want to do. BUT, the problem is that although i think i have configured everything perfectly, i cannot make snort to work with the database. here's what i did:

./configure --with-mysql=/opt/lampp <-- which is where mysql is installed, but lacks the header file mysql.h

that command line gave (for many people!) the known output:

[B]**********************************************
ERROR: unable to find mysql headers (mysql.h)
checked in the following places
/opt/lampp/
/opt/lampp//include
/opt/lampp//include/mysql
/opt/lampp//mysql
/opt/lampp//mysql/include
**********************************************[/B]


so, the misfortune is that because of the missing header file these 2 cannot work together. i also, installed the libmysql++-devel or something like that, but it doesn't matter anyway, i think.

after that, i tried to make

**./configure --with-mysql**

and use the default settings, but this generates another problem. it doesn't use the mysql files installed by xampp (/opt/lampp), instead uses the lidmysql++-dev-whatever headers (i think), it configures right, but when trying to do something like this:

**snort -d -l ./log -c ./snort.conf**

it shows the other well known output (and it should, since there were no linking between the mysql i want to use and snort):

[B]ERROR: If this build of snort was obtained as a binary distribution (e.g., rpm,
or Windows), then check for alternate builds that contains the necessary
'mysql' support.

If this build of snort was compiled by you, then re-run the
the ./configure script using the '--with-mysql' switch.
For non-standard installations of a database, the '--with-mysql=DIR'
syntax may need to be used to specify the base directory of the DB install.

See the database documentation for cursory details (doc/README.database).
and the URL to the most recent database plugin documentation.
Fatal Error, Quitting..[/B]



so, i guess there must be a problem or a difference with the standard installation of mysql and the mysql of xampp, which misses mysql.h. i'm open to any kind of suggestions and solutions. but most of all, i want to know if it can be done with snort and Xampp! :)

huge thanx in advance from all of you guys!

---

