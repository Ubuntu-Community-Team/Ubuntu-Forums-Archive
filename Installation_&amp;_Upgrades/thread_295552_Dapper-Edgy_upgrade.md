---
title: "Dapper-Edgy upgrade"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by akadruid on 2006-11-08
Hi,

I have tried to upgrade to Edgy using gksu "update-manager -c", and it downloaded all the required files then fell over with an error to do with x11common.  Now I get 'Software Index is broken, please run sudo apt-get install -f' if I try to run it again, and if I try to run sudo apt-get install -f I get this:

```
colin@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  x11-common
The following packages will be upgraded:
  x11-common
1 upgraded, 0 newly installed, 0 to remove and 911 not upgraded.
15 not fully installed or removed.
Need to get 0B/291kB of archives.
After unpacking 418kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Preconfiguring packages ...
(Reading database ... 85128 files and directories currently installed.)
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu6_i386.deb) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Unpacking replacement x11-common ...
Replacing files in old package xinit ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package xli
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
colin@ubuntu:~$
```
Does anyone have ideas what to do next?](*,)

---

### Post by elpresidente on 2006-11-08
I had same problem but my conflict was with xgl. Read this thread - sam eproblem as yours. Should get you going.

[http://ubuntuforums.org/showthread.php?t=286351&highlight=x11-common](http://ubuntuforums.org/showthread.php?t=286351&highlight=x11-common)

---

### Post by akadruid on 2006-11-09
Perfect! That fixed it.

Thank you.

One thing has gone very wierd post upgrade though: I used to not be able to type the £ character - the upgrade fixed it but now the @ comes out as &#937;.  Which is more annoying really.

I've tried changing the keyboard layout in the menu and resetting it to the default but no luck so far.  No luck googling or searching these forums yet either.

---

### Post by Psquared on 2006-11-11
Worked perfectly for me. Took a little tweaking, but it was the most painless upgrade I've ever done. Only problem is getting Beryl working. I can do it I just need to sit down and work on it. Beryl/Compiz is so flaky I am not sure I want to bork my box by trying, but i probably will when I have the time.

Great job Ubuntu/Gnome people. :KS

---

