---
title: "post-removal script returned error exit status 127"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by lhperez on 2009-11-19
Hi all,

I have a problem when I installed swi-prolog. My first step was a clean installation of Ubuntu 9.10 64-bits. Then I went on installing different software. First, I successfully installed eclipse, second, when installing swi-prolog some problems appear.

I select swi-prolog (and some other packages as swi-prolog-xpce or swi-prolog-odbc). This time the installation finished giving the following error message:

E: /var/cache/apt/archives/swi-prolog-clib_5.6.64-2_amd64.deb: subprocess new post-removal script returned error exit status 127
E: /var/cache/apt/archives/swi-prolog-http_5.6.64-2_amd64.deb: subprocess new post-removal script returned error exit status 127
E: /var/cache/apt/archives/swi-prolog-odbc_5.6.64-2_amd64.deb: subprocess new post-removal script returned error exit status 127
E: /var/cache/apt/archives/swi-prolog-semweb_5.6.64-2_amd64.deb: subprocess new post-removal script returned error exit status 127
E: /var/cache/apt/archives/swi-prolog-sgml_5.6.64-2_amd64.deb: subprocess new post-removal script returned error exit status 127

I have no idea why this time swi-prolog installation result unsuccessful. I read and tried several solutions discussed on different sites on the web but none of them worked. For example, downloading some other packages or executing the following command:
dpkg --remove --force-remove-reinstreq swi-prolog-odbc

or other similar versions with apt-get.. etc

After trying all different stuff I read things seem to be even worse now. How can I fix this? Does it happend because there was some necessary package (or software) missing at the time I installed it? Is there some permission problem?

If anybody have some clues about which could be the problem they would be more than welcome.

Thanks in advance.
Laura

---

### Post by diesch on 2009-11-19
Please run
```
 apt-get install swi-prolog
```
and post the complete output

---

### Post by lhperez on 2009-11-20
Thanks for your replay. Here is the complete output:

sudo apt-get install swi-prolog
[sudo] password for lhperez:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
swi-prolog is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 104 not upgraded.
5 not fully installed or removed.
Need to get 0B/538kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 195572 files and directories currently installed.)
Preparing to replace swi-prolog-clib 5.6.64-2 (using .../swi-prolog-clib_5.6.64-2_amd64.deb) ...
Unpacking replacement swi-prolog-clib ...
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/swi-prolog-clib_5.6.64-2_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace swi-prolog-http 5.6.64-2 (using .../swi-prolog-http_5.6.64-2_amd64.deb) ...
Unpacking replacement swi-prolog-http ...
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/swi-prolog-http_5.6.64-2_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace swi-prolog-odbc 5.6.64-2 (using .../swi-prolog-odbc_5.6.64-2_amd64.deb) ...
Unpacking replacement swi-prolog-odbc ...
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/swi-prolog-odbc_5.6.64-2_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace swi-prolog-semweb 5.6.64-2 (using .../swi-prolog-semweb_5.6.64-2_amd64.deb) ...
Unpacking replacement swi-prolog-semweb ...
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/swi-prolog-semweb_5.6.64-2_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace swi-prolog-sgml 5.6.64-2 (using .../swi-prolog-sgml_5.6.64-2_amd64.deb) ...
Unpacking replacement swi-prolog-sgml ...
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/swi-prolog-sgml_5.6.64-2_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/swi-prolog-clib_5.6.64-2_amd64.deb
 /var/cache/apt/archives/swi-prolog-http_5.6.64-2_amd64.deb
 /var/cache/apt/archives/swi-prolog-odbc_5.6.64-2_amd64.deb
 /var/cache/apt/archives/swi-prolog-semweb_5.6.64-2_amd64.deb
 /var/cache/apt/archives/swi-prolog-sgml_5.6.64-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Regards,
Laura

---

### Post by diesch on 2009-11-20
swi-prolog seems to be fine, but the system tries to reinstall swi-prolog-clib and some other packages but fails to remove thze installed packages.

What do you get when running
```
echo "make_library_index('/usr/lib/swi-prolog/library/')." | sudo swipl
```

---

### Post by lhperez on 2009-11-23
It seems to fine but is not running. Regarding the other packages, when removing them it says that they cannot be removed that they need to be reinstalled, but when I reinstall them the installation finishes with the error in the subject.

After running the command I get the following result:

$ echo "make_library_index('/usr/lib/swi-prolog/library/')." | sudo swipl
swipl: error while loading shared libraries: libreadline.so.5: cannot open shared object file: No such file or directory

Actually this library is not in the system instead is the library libreadline.so.6 :

/lib/libreadline.so.6
/lib/libreadline.so.6.0

Best regards,
Laura

---

### Post by diesch on 2009-11-23
That command is run by the swi-prolog-* packages when uninstalling them and causes the error if it doesn't work.

Try to install the package libreadline5 - it should be already there as swi-prolog depends on it but I guess you accidentally removed it when trying to fix things.

---

### Post by lhperez on 2009-11-25
Hi Diesch,

I installed the library libreadline.so.5 and everything started to work perfectly! 

Thank you so much for your help.

Laura

---

### Post by diesch on 2009-12-02
You're welcome

---

