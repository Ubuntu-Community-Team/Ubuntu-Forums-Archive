---
title: "ProFTPD remove problem"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by FLEO on 2005-03-20
Hi everybody,

I try to install proftpd with apt-get install proftpd and now I have a problem to remove it.

It likes the remove action still in cache and always create an error when I do a apt-get action.

------------------------------------------------------------------------------------

root@FLEO:~ # apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be REMOVED:
  proftpd
The following packages have been kept back:
  hotplug linux-image-2.6-386 linux-restricted-modules-2.6-386
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 463kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 13065 files and directories currently installed.)
Removing proftpd ...
dpkg: error processing proftpd (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@FLEO:~ #

------------------------------------------------------------------------------------

Do you have a idea of how to clean it or fix my problem ?

Thanks,

FLEO

---

### Post by az on 2005-03-21
sudo apt-get -f install

Edit:

Why is it being removed by an upgrade?

Try doing a dist-upgrade.  Sometimes an upgrade will not make critical changes to your system like a dist-upgrade will.  Anyway, if you are running an ftp server, you need the latest security patches.  It seems that your kernel can be updated.

sudo apt-get dist-upgrade.

That is, if you do not have any funy repositories in you sources.list...  Do not dist-upgrade with anything other than ubuntu repositories.  

Ever.

Also, what if you just remove that package by hand?

sudo apt-get remove proftpd

---

### Post by FLEO on 2005-03-21
[B]Look i'm verry confused

That is the result to remove command.[/B]

------------------------------------------------------------
root@FLEO:~ # apt-get remove proftpd
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be REMOVED:
  proftpd
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 463kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 13065 files and directories currently installed.)
Removing proftpd ...
dpkg: error processing proftpd (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@FLEO:~ #

------------------------------------------------------------

Look the result for a dist-upgrade.

root@FLEO:~ # apt-get dist-upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
Calculating Upgrade... Done
The following packages will be REMOVED:
  proftpd
The following NEW packages will be installed:
  grepmap linux-image-2.6.8.1-5-386 linux-restricted-modules-2.6.8.1-5-386
The following packages will be upgraded:
  hotplug linux-image-2.6-386 linux-restricted-modules-2.6-386
3 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/16.9MB of archives.
After unpacking 51.1MB of additional disk space will be used.
Do you want to continue? [Y/n] y

Preconfiguring packages ...
(Reading database ... 13065 files and directories currently installed.)
Removing proftpd ...
dpkg: error processing proftpd (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@FLEO:~ #

**It is always bothering me with that proftpd ! Is there another way to remove it.**

[B]What's that /usr/bin/dpkg ??

Thanks,

FLEO[/B]

---

### Post by az on 2005-03-22
My two-year-old is having nightmares and is keeping me up.  It's 2AM.  

I just installed proftpd and it depends on proftpd-common.

I removed proftpd and it removed both proftpd and proftpd-common.

Your errors do not mention proftpd-common.  Why do you not have proftpd-common installed?   Do you have only ubuntu repositories in your sources.list or did you add some foreign ones?  Did you try to remove some files by hand?

Apt is the package management tool.  It is really a frontend for dpkg, the debian package management tool.  Usually, when a package will not remove itself from your system it is because of
1- a bug in the package install or remove scripts.  If you got your packages form Ubuntu, this is not the case as they appear to work fine.
2-  a deleted file or some other problem (a file added by something other than the package management system) that can cause a conflict or a problem with the package removal script.

You can try to reinstall the package to correct these problems:

sudo apt-get install --reinstall proftpd
sudo apt-get remove proftpd

or

dpkg -r --force-remove-reinstreq proftpd

to try to remove the package.  This may fail because I think it still tries to run the prerm and postrm scripts.  I dunno.

Did you do anything funny to your system like use a funny repository (non-ubuntu) or install some software by hand?

---

### Post by FLEO on 2005-03-22
No I don't have just ubuntu's repositories in my source.list. I had more like it explained in the ubuntu guide : [http://ubuntuguide.org/](http://ubuntuguide.org/)

What do you mean by install some software by hand ?

I just tried to install proftpd with apt-get install proftpd and now I got that error everytimes I try to do a apt-get command.


root@FLEO:~ # apt-get install --reinstall proftpd
Reading Package Lists... Done
Building Dependency Tree... Done
Reinstallation of proftpd is not possible, it cannot be downloaded.
The following packages will be REMOVED:
  proftpd
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 463kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 13065 files and directories currently installed.)
Removing proftpd ...
dpkg: error processing proftpd (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@FLEO:~ #
------------------------------------------------------------
root@FLEO:~ # apt-get remove proftpd
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be REMOVED:
  proftpd
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 463kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 13065 files and directories currently installed.)
Removing proftpd ...
dpkg: error processing proftpd (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@FLEO:~ #
------------------------------------------------------------
root@FLEO:~ # dpkg -r --force-remove-reinstreq proftpd
(Reading database ... 13065 files and directories currently installed.)
Removing proftpd ...
dpkg: error processing proftpd (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 proftpd
root@FLEO:~ #
------------------------------------------------------------

Has you can see I always get the same error.

I think you are right saying there's a error with the post-removal script. Have you ever seen a problem like this before ?

Maybe I can just remove it by hand like you say but I don't know how.

Could you send me a copy of the original source.list ?

Sould I reinstall ubuntu ?

Thanks for all your help in late time.

FLEO

---

### Post by az on 2005-03-23
"I think you are right saying there's a error with the post-removal script. Have you ever seen a problem like this before ?"

Only with buggy, badly-made packages.  This should not happen on a stable system.  Packages should remove themselves gracefully using the package tools.  What other sources did you put in your reposiroties?



"Maybe I can just remove it by hand like you say but I don't know how."

Look at:
/var/lib/dpkg/info/proftpd.postrm

Fix it (why is it spitting out an error?), or delete it.  Then, remove the package. (sudo dpkg -r proftpd)


"Could you send me a copy of the original source.list ?"

Just remove any entry that does not include the word ubuntu in it.  That should work.

Then apt-get update


"Sould I reinstall ubuntu ?"

Yes, but not on your current system.  You shouln't need to.  It should be easy to fix.  However, you should reinstall ubuntu on as many computers as you can! (Hee Hee!)

---

### Post by FLEO on 2005-03-23
OK thanks a lot I'lll try to fix it this weekend and I'll give you news.

Thanks,

FLEO

---

### Post by az on 2005-03-24
This is the postrm script:
kurn@ubuntu:/var/lib/dpkg/info $ cat proftpd.postrm
#!/bin/sh -e

if [ "$1" = "purge" -o "$1" = "remove" ]
then
    update-inetd --disable ftp
fi

# Automatically added by dh_installdebconf
if [ "$1" = purge ] && [ -e /usr/share/debconf/confmodule ]; then
        . /usr/share/debconf/confmodule
        db_purge
fi
# End automatically added section

Try running
sudo update-inetd --disable ftp
to see if you have another program preventing this from happening.

---

