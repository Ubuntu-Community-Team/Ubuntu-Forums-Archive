---
title: "php-pear is broken"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by !nkubus on 2009-09-19
I' trying to install pear package and they  never install, I always get the following message:

[PHP]
Notice: Undefined offset:  1 in Console/Getopt.php on line 214

Notice: file_exists(): Unable to find the wrapper "channel" - did you forget to enable it when you configured PHP? in PEAR/Downloader/Package.php on line 1510

Notice: is_file(): Unable to find the wrapper "channel" - did you forget to enable it when you configured PHP? in PEAR/Downloader/Package.php on line 1520

Notice: is_file(): Unable to find the wrapper "channel" - did you forget to enable it when you configured PHP? in PEAR/Downloader/Package.php on line 1520

Warning: fopen(/tmp/pear/cache/591f41a607b30c9fe288676edabe7f9erest.cacheid): failed to open stream: No such file or directory in PEAR/REST.php on line 226

Warning: fsockopen(): unable to connect to ssl://pear.phing.info:443 (Connection refused) in PEAR/Downloader.php on line 1629
pear.phing.info is using a unsupported protocal - This should never happen.
Unknown remote channel: pear.phpunit.de
pear.phing.info is using a unsupported protocal - This should never happen.
pear.phing.info is using a unsupported protocal - This should never happen.
pear.phing.info is using a unsupported protocal - This should never happen.
pear.phing.info is using a unsupported protocal - This should never happen.
phing/phing can optionally use package "pear/VersionControl_SVN" (version >= 0.3.0alpha1)
phing/phing can optionally use package "channel://pear.phpunit.de/PHPUnit" (version >= 2.3.0)
phing/phing can optionally use package "pear/PhpDocumentor" (version >= 1.3.0RC3)
phing/phing can optionally use package "pear/Xdebug" (version >= 2.0.0beta2)
phing/phing can optionally use package "pear/PEAR_PackageFileManager" (version >= 1.5.2)
Downloading "http://pear.phing.info/get/phing-2.3.3.tgz"
downloading phing-2.3.3.tgz ...
Starting to download phing-2.3.3.tgz (422,298 bytes)
.....................................................................................done: 422,298 bytes

Warning: unlink(/tmp/glibctest9rusJ5): No such file or directory in System.php on line 206
[/PHP]

anyone have the same issue or a solution?

---

### Post by !nkubus on 2009-09-21
I'm still searching the solution, but nothing so far :(

---

### Post by SatireWolf on 2009-09-29
> **!nkubus said:**
> I'm still searching the solution, but nothing so far :(

Yup it's broken for me too on the latest karmic koala build. It looks like the default pear directories are expecting there to be a /doc folder in /usr/share/php but PEAR is actually installed in /usr/share/php/PEAR by Ubuntu. Odd... very odd.... I thought debian package maintainers typically didn't much with the source default installers too much to keep this sort of thing from happening (unlike Fedora/Redhat). Although CPAN and PEAR is always broken on Fedora too. Hence the reason I'm using Ubuntu now.

root@host:~# pear upgrade pear
downloading PEAR-1.9.0.tgz ...
Starting to download PEAR-1.9.0.tgz (291,634 bytes)
.................................done: 291,634 bytes

Warning: mkdir(): File exists in System.php on line 277

Warning: mkdir(): File exists in /usr/share/php/System.php on line 277
ERROR: failed to mkdir /usr/share/php/doc/PEAR
root@host:~#

root@host:~# pear install Net_Ping
downloading Net_Ping-2.4.4.tgz ...
Starting to download Net_Ping-2.4.4.tgz (9,563 bytes)
.....done: 9,563 bytes

Warning: mkdir(): File exists in System.php on line 277

Warning: mkdir(): File exists in /usr/share/php/System.php on line 277
ERROR: failed to mkdir /usr/share/php/doc/Net_Ping/docs/examples
root@host:~#

---

### Post by SatireWolf on 2009-09-29
> **SatireWolf said:**
> Yup it's broken for me too on the latest karmic koala build. It looks like the default pear directories are expecting there to be a /doc folder in /usr/share/php but PEAR is actually installed in /usr/share/php/PEAR by Ubuntu. Odd... very odd.... I thought debian package maintainers typically didn't much with the source default installers too much to keep this sort of thing from happening (unlike Fedora/Redhat). Although CPAN and PEAR is always broken on Fedora too. Hence the reason I'm using Ubuntu now.

root@host:~# pear upgrade pear
downloading PEAR-1.9.0.tgz ...
Starting to download PEAR-1.9.0.tgz (291,634 bytes)
.................................done: 291,634 bytes

Warning: mkdir(): File exists in System.php on line 277

Warning: mkdir(): File exists in /usr/share/php/System.php on line 277
ERROR: failed to mkdir /usr/share/php/doc/PEAR
root@host:~#

root@host:~# pear install Net_Ping
downloading Net_Ping-2.4.4.tgz ...
Starting to download Net_Ping-2.4.4.tgz (9,563 bytes)
.....done: 9,563 bytes

Warning: mkdir(): File exists in System.php on line 277

Warning: mkdir(): File exists in /usr/share/php/System.php on line 277
ERROR: failed to mkdir /usr/share/php/doc/Net_Ping/docs/examples
root@host:~#

I ended up removing php-pear module and installing it from source.

This is how you do it. First, clean up the /usr/share/php dir after your remove the broken Ubuntu pear install.

Next..

as root

cd /root
mkdir pear
cd pear
wget [http://pear.php.net/go-pear](http://pear.php.net/go-pear)

php go-pear

change the install dir's to match this:

 1. Installation prefix ($prefix) : /usr/share/php
 2. Temporary files directory     : $prefix/temp
 3. Binaries directory            : /usr/bin
 4. PHP code directory ($php_dir) : /usr/share/php
 5. Documentation base directory  : $php_dir/docs
 6. Data base directory           : $php_dir/data
 7. Tests base directory          : $php_dir/tests

The following PEAR packages are bundled with PHP: PEAR_Frontend_Web-beta,
PEAR_Frontend_Gtk2, MDB2.
Would you like to install these as well? [Y/n] :

Answer N here.

Would you like to alter php.ini </etc/php5/cli/php.ini>? [Y/n] : y

Answer Y there.

All done, working Pear install. Amazing that the package maintainers managed to hose it up. I guess it's like cpan with the ever moving pearl engine. PHP 5.2 seems to have thrown a monkey wrench in quite a few things, and PEAR 1.9 is a prerequisite for it working properly.

Oh and to get your binaries working...

cd /usr/bin

ln -s /usr/share/php/bin/pear pear
ln -s /usr/share/php/bin/peardev peardev
ln -s /usr/share/php/bin/pecl pecl

---

### Post by gstanden on 2009-10-11
Hi,

This URL:

[http://azimbabu.blogspot.com/2009/09/pear-installation-problem-unsupported.html](http://azimbabu.blogspot.com/2009/09/pear-installation-problem-unsupported.html)

had a quick-fix method that worked for ubuntu 9.10 karmic koala. URL directs to do this (worked for me)

cd `pear config-get php_dir`
mv .channels .channels-broken
pear update-channels

---

### Post by slakkie on 2009-10-11
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/420639](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/420639)

---

### Post by gstanden on 2009-10-11
Hi, there is still some issue with my pear package.  I applied the fixes in the referenced bug.  No errors, but "pear install" only downloads the *.tgz file - it isn't doing the install automatically as it normally does.  Any suggestions how to get the "install" feature to work again? Thanks

---

### Post by !nkubus on 2009-10-11
The peorblems seams to reside on zlib, I still have the issue but by using the -Z option it disable compression and it works, so in the mean time use

sudo pear install -Z package name

---

### Post by rickh57 on 2009-10-13
I tried this workaround and it got further, but bailed when it was trying to install the docs. For now, I've just copied all of the pear modules that I use into a directory under /home and modified the ini's include path. I have to do that anyhow on my paid webhost, since they won't add any modules beyond their base, so it isn't that painful for me.

---

### Post by gstanden on 2009-10-20
Hi, I tried SatireWolf's fix but the install just conks out at 

Downloading package: PEAR...

also, I never get this line during the manual install:

Would you like to alter php.ini </etc/php5/cli/php.ini>? [Y/n] : y

Also:

rickh57:  Hey thanks for your post about that workaround.  However, I did not understand how to implement your workaround.  Where do I find the "pear modules" and which .ini file do I edit and what do I edit in it?  If you could give more detail that would be great.  Do I implement your workaround after installing php-pear with Synaptic or do I have to install php-pear as described by SatireWolf?

Thanks, Gil

---

### Post by rickh57 on 2009-10-20
I actually have the pear classes that I use for my pages installed in an include directory on my web host. I just ftped that directory down to my Karmic Ubuntu box. I then changed my include_path in my php.ini file to add that directory.

---

