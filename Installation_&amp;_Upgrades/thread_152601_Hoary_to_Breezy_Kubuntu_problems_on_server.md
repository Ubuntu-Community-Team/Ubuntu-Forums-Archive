---
title: "Hoary to Breezy Kubuntu problems on server"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by thorndike on 2006-03-30
Good morning folks,

At the request of the customer, KDE was installed on the server to enable their in-house backup guy to easily examine and swap their external backup disks.

I had a few hotplug issues with Hoary, so I ended up upgrading to Breezy.  Unfortunately, that seemed to fix the hotplug issue, but installed several others.  The main issue is this:

Something is wrong with KDE.  When I plug in the external backup disk, the disk is installed via hotplugging, but when I right click on it to mount it, mount isn't even an option.  Also, when I try to open it to look at the contents, KDE prompts me with the screen to select which application I want to open it with.  Konqueror isnt even on the list.  So I tried to install konqueror.  This is what I get:

The following packages have unmet dependencies:
  gksu: Depends: libgksu1.2-0 (>= 1.3.3) but 1.3.1-1ubuntu6 is to be installed
        Depends: libgksuui1.0-1 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


So of course I try the apt-get -f install and get this:

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  gksu

When I continue I get this:

(Reading database ... 48970 files and directories currently installed.)
Removing gksu ...
/var/lib/dpkg/info/gksu.prerm: line 5: /usr/sbin/gconf-schemas: No such file or directory
dpkg: error processing gksu (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gksu
E: Sub-process /usr/bin/dpkg returned an error code (1)


This is an endless loop that I am unable to get out of.  Any and all help would be appreciated.

Thanks.

Thorndike

---

