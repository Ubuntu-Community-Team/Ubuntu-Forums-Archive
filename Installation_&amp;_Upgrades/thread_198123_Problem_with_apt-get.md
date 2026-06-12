---
title: "Problem with apt-get"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by NYIslander on 2006-06-16
I had added some of the edgy repositories in order to install some programs that couldn't be install with the regular packages such as Opera. When I attempt to make a general upgrade by apt-get, I get the following message:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up udev (093-0ubuntu1) ...
/var/lib/dpkg/info/udev.postinst: line 82: my_persistent_disk_rules: command not found
dpkg: error processing udev (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can this be fixed or should I reinstall? Thanks for the help.

---

### Post by bruce89 on 2006-06-16
[QUOTE=NYIslander]I had added some of the edgy repositories in order to install some programs that couldn't be install with the regular packages such as Opera.
[/QUOTE]
Not a good idea, in other words, you are now running Edgy.  For the error you got see - [http://www.ubuntuforums.org/showthread.php?t=197303](http://www.ubuntuforums.org/showthread.php?t=197303)

---

### Post by NYIslander on 2006-06-16
I'm trying to do that now but it's won't allow me to access the file in root to change it. How do I get in root?

---

